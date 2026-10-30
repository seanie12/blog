---
title: "A Fix for Softmax and Cross-Entropy: Derivations and Intuition"
categories:
  - Machine Learning
tags:
  - softmax
  - cross-entropy
  - numerical stability
  - knowledge distillation
  - automatic differentiation
toc: true
toc_sticky: true
use_math: true
comments: true
excerpt: "Why subtracting the maximum logit is not enough, and how to preserve small gradients in classification and knowledge distillation."
---

Subtracting the largest logit is the standard way to evaluate softmax without overflow. It is tempting to conclude that the resulting loss and gradient are numerically reliable. However, preventing overflow does not prevent a small gradient from disappearing through rounding.

Consider two situations. A classifier is extremely confident in the correct answer, so its target gradient should be small but negative. Or a student model nearly matches its teacher, so its distillation gradient should reflect their small remaining difference. In both cases, the quantity we want is much smaller than the intermediate probabilities used to calculate it.

[A Fix for Softmax and Cross-Entropy](https://arxiv.org/abs/2610.31642v3), by Jonathan T. Barron, Dan Gnanapragasam, and Michael Tschannen, studies these problems. The paper calls them **Softmax Collapse** and **Softmax Cancellation**. Its approach is to preserve the mathematical objective while changing the arithmetic and, where necessary, the computation graph used for differentiation.

This post expands the derivations behind both fixes, including the target shift, the centered student–teacher differences, the final gradient correction, and the custom backward pass. The implementation follows version 3, revised on October 29, 2026, including its correction for extreme logits. The additional interpretations of the zero-sum correction below are explanatory derivations, rather than extra claims made by the paper.

## Softmax, cross-entropy, and the gradients we expect

Let $z\in\mathbb{R}^K$ be a vector of logits, with $K\geq2$. Define

$$
Z=\sum_{j=1}^K e^{z_j},\qquad q_k=\operatorname{softmax}(z)_k=\frac{e^{z_k}}{Z}.
$$

For finite logits, each $q_k$ is positive and $\sum_k q_k=1$. A fixed target distribution $p$ gives the cross-entropy

$$
\mathcal{L}(z,p)=-\sum_i p_i\log q_i.
$$

Throughout the derivations, $p$ is normalized and is held fixed when differentiating the student. This includes a one-hot target, where $p_t=1$ for the correct class $t$.

### Deriving the cross-entropy gradient

Since $\log q_i=z_i-\log Z$,

$$
\begin{aligned}
\mathcal{L}(z,p)
&=-\sum_i p_i(z_i-\log Z)\\
&=-\sum_i p_i z_i+\left(\sum_i p_i\right)\log Z\\
&=-\sum_i p_i z_i+\log Z.
\end{aligned}
$$

The first term contributes $-p_k$ when differentiating with respect to $z_k$. For the second term, all logits other than $z_k$ are held fixed, so

$$
\frac{\partial Z}{\partial z_k}=e^{z_k},\qquad
\frac{\partial\log Z}{\partial z_k}=\frac{e^{z_k}}{Z}=q_k.
$$

Therefore,

$$
\boxed{g_k:=\frac{\partial\mathcal{L}}{\partial z_k}=q_k-p_k.}
$$

For a hard target, this becomes

$$
g_t=q_t-1,\qquad g_j=q_j\quad(j\ne t).
$$

The target gradient is negative, encouraging gradient descent to increase $z_t$. The non-target gradients are positive, encouraging the other logits to decrease.

### Why the logit gradients sum to zero

Normalization immediately gives

$$
\sum_k g_k=\sum_k q_k-\sum_k p_k=0.
$$

There is also a geometric reason. Adding a common scalar $c$ to all logits does not change softmax:

$$
\frac{e^{z_k+c}}{\sum_j e^{z_j+c}}=\frac{e^{z_k}}{\sum_j e^{z_j}}.
$$

The loss is consequently constant along the direction that increases every logit equally. Its directional derivative in that direction must be zero:

$$
\left.\frac{d}{dc}\mathcal{L}(z+c\mathbf{1},p)\right|_{c=0}=\sum_k g_k=0.
$$

This is a statement about the gradient with respect to the **logits**. Gradients with respect to arbitrary network parameters need not sum to zero.

## What subtracting the maximum fixes

Directly evaluating $e^{z_k}$ can overflow. To avoid this, define

$$
z_{\max}=\max_j z_j,\qquad \widetilde z_k=z_k-z_{\max}.
$$

The common factor $e^{z_{\max}}$ cancels, giving

$$
q_k=\frac{e^{\widetilde z_k}}{\sum_j e^{\widetilde z_j}},\qquad
\log q_k=\widetilde z_k-\log\sum_j e^{\widetilde z_j}.
$$

Every shifted logit is nonpositive, so these exponentials are at most one. This handles exponential overflow. It does not ensure that the denominator retains every small contribution, or that subtracting two probabilities retains their small difference.

### Does log-sum-exp include zero when choosing its shift?

For a general vector $x$, the usual stable log-sum-exp chooses the largest **actual input**:

$$
c=\max_j x_j,\qquad
\operatorname{LSE}(x)=c+\log\sum_j e^{x_j-c}.
$$

The shift $c$ can be negative. There is no extra zero input in this expression. Any common shift gives the same identity in exact arithmetic, but using $c=\max_j x_j$ makes every exponential at most one and ensures that at least one equals one. This also prevents the entire exponential sum from underflowing.

For example, if $x=(-1000,-1001)$, then $c=-1000$ and

$$
\operatorname{LSE}(x)=-1000+\log(1+e^{-1}).
$$

Choosing $c=\max(0,\max_j x_j)=0$ instead would unnecessarily exponentiate $-1000$ and $-1001$, both of which underflow in fp32.

Zero enters the maximum when zero is itself one of the inputs. In particular,

$$
\log\left(1+\sum_{j\ne t}e^{a_j}\right)
=\operatorname{LSE}\bigl(0,(a_j)_{j\ne t}\bigr).
$$

Here the explicit $1=e^0$ is the target contribution, so the largest input is $\max(0,\max_{j\ne t}a_j)$. This is the second shift used below.

## A floating-point fact behind both bugs

A floating-point format has limited **relative** precision. A tiny number may be representable by itself, even when its contribution disappears after adding it to one.

For example, in fp32,

$$
\operatorname{fl}(1+10^{-8})=1,
$$

although $10^{-8}$ itself is readily representable. Here, $\operatorname{fl}$ denotes the rounded result of an operation.

Near one, the spacing between consecutive fp32 values is $2^{-23}$. Under round-to-nearest, a positive increment below $2^{-24}$ cannot change one. More generally, with $b$ significand bits, including the leading bit, the corresponding threshold is approximately $2^{-b}$.

If the increment is $e^{-m}$, it disappears once

$$
e^{-m}<2^{-b},\qquad\text{or equivalently}\qquad m>b\log2.
$$

This yields the paper's approximate precision cliffs:

| Arithmetic format | Significand bits $b$ | Approximate cliff $b\log2$ |
| --- | ---: | ---: |
| bf16 | 8 | 5.5 |
| fp32 | 24 | 16.6 |
| fp64 | 53 | 36.7 |

These thresholds describe the operative arithmetic, rather than necessarily the storage dtype of a model's weights. Reduction order, accumulation precision, and kernel implementation can affect the observed transition.

### Why `log1p` and `expm1` are separate functions

The identities

$$
\operatorname{log1p}(x)=\log(1+x),\qquad
\operatorname{expm1}(x)=e^x-1
$$

define the same real-valued expressions as their naive counterparts. The implementations evaluate the combined expressions accurately near zero.

If we first round $1+x$ to one, applying an ordinary logarithm afterward cannot recover $x$. Similarly, if we first round $e^x$ to one, subtracting one afterward gives zero. The specialized functions avoid these intermediate losses.

```python
import numpy as np

x = np.float32(1e-8)
one = np.float32(1)

print(np.log(one + x))       # 0.0
print(np.log1p(x))           # approximately 1e-8
print(np.exp(x) - one)       # 0.0
print(np.expm1(x))           # approximately 1e-8
```

## Softmax Collapse: losing the target gradient

Assume first that the correct class has the largest logit, $z_t=z_{\max}$. Define the margin against the combined non-target mass:

$$
m=z_t-\log\sum_{j\ne t}e^{z_j}.
$$

This compares the target with the log-sum-exp of **all** other logits, rather than only the runner-up. Being the largest logit alone does not ensure $m>0$; the confident regime of interest has large positive $m$.

The useful identity is

$$
\begin{aligned}
e^{-m}
&=\exp\left(\log\sum_{j\ne t}e^{z_j}-z_t\right)\\
&=\frac{\sum_{j\ne t}e^{z_j}}{e^{z_t}}\\
&=\sum_{j\ne t}e^{z_j-z_t}.
\end{aligned}
$$

Write this non-target mass as $S=e^{-m}$. After shifting by $z_t$, the target contributes $e^{z_t-z_t}=1$, so

$$
q_t=\frac{1}{1+S},\qquad q_j=\frac{e^{z_j-z_t}}{1+S}\quad(j\ne t).
$$

The hard-target loss is

$$
\mathcal{L}(z,t)=-\log q_t=\log(1+S)=\log(1+e^{-m}).
$$

### Two equal expressions with different numerical behavior

The usual target gradient is

$$
g_t=\frac{1}{1+S}-1.
$$

Algebraically,

$$
\frac{1}{1+S}-1=\frac{1-(1+S)}{1+S}=-\frac{S}{1+S}.
$$

But when $1+S$ rounds to one, the first evaluation becomes

$$
\frac11-1=0.
$$

The second evaluation instead gives approximately

$$
-\frac{S}{1}=-S,
$$

which remains nonzero while $S$ is representable. Losing a tiny contribution in a denominator near one is relatively harmless here; losing the entire numerator is not.

Meanwhile, the non-target gradients

$$
g_j=\frac{e^{z_j-z_t}}{1+S}
$$

have small numerators that can remain nonzero. Thus, the standard arithmetic may eliminate only the negative target contribution, leaving positive non-target contributions behind.

This is an artificial discontinuity. The exact target gradient decays smoothly as $m$ grows; it does not suddenly become zero at $m\approx16.6$.

### A concrete example

Take

$$
z=(9,-9,-9),\qquad t=1,
$$

using one-based class indices. Then

$$
S=2e^{-18}\approx3.046\times10^{-8}.
$$

The exact gradient is approximately

$$
g\approx(-3.046\times10^{-8},\;1.523\times10^{-8},\;1.523\times10^{-8}).
$$

A standard fp32 evaluation can instead produce

$$
\widetilde g\approx(0,\;1.523\times10^{-8},\;1.523\times10^{-8}).
$$

The missing component is small in absolute terms, but it is the entire gradient on the target logit.

## Rewriting the loss so autodiff preserves the target contribution

For a hard target, shift by the **target logit** directly:

$$
a_j=z_j-z_t\quad(j\ne t),\qquad S=\sum_{j\ne t}e^{a_j}.
$$

The target's own shifted slot is the constant zero. Its exponential is the constant one. Therefore,

$$
\boxed{\mathcal{L}(z,t)=\log\left(1+\sum_{j\ne t}e^{z_j-z_t}\right).}
$$

This is the same cross-entropy for **any** target, including a target that is not the largest logit.

### Deriving the non-target gradients

For $j\ne t$, only one summand of $S$ depends on $z_j$:

$$
\frac{\partial S}{\partial z_j}=e^{z_j-z_t}.
$$

For example, with target class one,

$$
S=e^{z_2-z_1}+e^{z_3-z_1}.
$$

Differentiating with respect to $z_2$ gives $e^{z_2-z_1}$ from the first term and zero from the second. All other logits, including $z_1$, are held fixed in this partial derivative.

The chain rule consequently gives

$$
g_j=\frac{1}{1+S}\frac{\partial S}{\partial z_j}=\frac{e^{z_j-z_t}}{1+S}.
$$

### Deriving the target gradient

Every non-target summand contains $-z_t$, so

$$
\begin{aligned}
\frac{\partial S}{\partial z_t}
&=-\sum_{j\ne t}e^{z_j-z_t}\\
&=-S.
\end{aligned}
$$

Thus,

$$
\boxed{g_t=-\frac{S}{1+S}=-\sum_{j\ne t}g_j.}
$$

The computation graph now accumulates negative contributions through the differences $z_j-z_t$. It does not need to calculate the small target gradient as a probability near one minus one.

One easy mistake is to add an extra derivative from the shifted target logit. Under target shifting,

$$
\widetilde z_t=z_t-z_t=0,\qquad
\frac{\partial(-\widetilde z_t)}{\partial z_t}=-1+1=0.
$$

Both occurrences refer to the same variable. Under a maximum shift, a non-maximal target instead has $\widetilde z_t=z_t-z_{\max}$; the intermediate derivatives differ, while the final exact cross-entropy gradient remains the same.

### Why target shifting does not require unsafe exponentials

If the target is much smaller than another logit, some $z_j-z_t$ can be large and positive. Directly exponentiating those differences would overflow.

For analysis, the paper writes

$$
m=-\operatorname{LSE}_{j\ne t}(z_j-z_t),\qquad
\mathcal{L}=\operatorname{softplus}(-m),
$$

where $\operatorname{LSE}(x)=\log\sum_i e^{x_i}$ and $\operatorname{softplus}(x)=\log(1+e^x)$. These are mathematical identities; their numerical implementations matter.

A stable evaluation can introduce a second shift. Let

$$
b=\max\left(0,\max_{j\ne t}a_j\right),\qquad
V=\sum_{j\ne t}e^{a_j-b}.
$$

The zero in this maximum is the target's shifted logit, $a_t=0$. Equivalently,

$$
b=\max_j(z_j-z_t)=z_{\max}-z_t\geq0.
$$

If $z_t$ is maximal, every $a_j=z_j-z_t$ is nonpositive, so taking the maximum with zero gives $b=0$. Otherwise, $b>0$ is the gap from the target to the largest logit. All exponentials in $V$ have nonpositive arguments.

To derive the loss, factor out $e^b$ from the entire sum, including the target's contribution:

$$
\begin{aligned}
\mathcal{L}
&=\log\left(1+\sum_{j\ne t}e^{a_j}\right)\\
&=\log\left(1+e^bV\right)\\
&=\log\left[e^b(e^{-b}+V)\right]\\
&=b+\log(e^{-b}+V)\\
&=b+\operatorname{log1p}\left(V+\operatorname{expm1}(-b)\right).
\end{aligned}
$$

The last equality follows because

$$
e^{-b}+V=1+\left[V+(e^{-b}-1)\right]
=1+\left[V+\operatorname{expm1}(-b)\right].
$$

The implementation never computes $e^b$. Factoring it out algebraically turns its logarithm into the safe additive term $b$.

When the target is maximal, $b=0$ and this reduces to $\operatorname{log1p}(S)$. When another logit is much larger, the second shift prevents overflow. This is the form used by the corrected hard-target implementation below.

### An important implementation erratum

The identity

$$
\operatorname{log1p}(S)=\operatorname{softplus}(\log S)
$$

holds for $S>0$. However, if every non-target exponential underflows to zero, the right-hand computation introduces $\log0$. Its backward pass can encounter an undefined intermediate derivative and produce NaNs, despite the limiting loss being well behaved.

Version 3 of the paper explicitly notes this issue in earlier code. Using `log1p(S)` directly avoids differentiating through that unnecessary logarithm. This is another example of why simplifying a real-valued expression is not sufficient to validate its floating-point backward pass.

### Which formula does the paper actually implement?

The version-3 code in Section 2 implements the second-shift formula above. Its function is named `cross_entropy(z, t)`. The JAX function `stable_hard_cross_entropy` and the PyTorch function `stable_hard_cross_entropy_torch` below follow that same computation, with renamed variables and batch handling.

The implementation has five steps:

1. Gather the target logit $z_t$.
2. Form $a_j=z_j-z_t$ for non-target classes and put a constant zero in the target slot.
3. Take $b=\max_j a_j$ over this full vector, including the target slot. This is exactly $\max(0,\max_{j\ne t}a_j)$; the code does not need a separate maximum with zero.
4. Sum $V=\sum_{j\ne t}e^{a_j-b}$, excluding the target exponential.
5. Return $b+\operatorname{log1p}(V+\operatorname{expm1}(-b))$ and use ordinary autodiff.

In the complete [JAX implementation](#a-jax-implementation) and [PyTorch implementation](#pytorch-implementations-and-examples) below, `relative`, `shift`, and `other_mass` correspond to $a$, $b$, and $V$, respectively.

The `softplus` expression in Equation (6) explains the mathematical loss; the published version-3 implementation evaluates it using `log1p` and `expm1` directly. It does not form $m$ or differentiate through a non-target `logsumexp`.

The paper also provides `soft_target_cross_entropy(z_S, z_T)` in Section 3. That function handles teacher distributions and installs the corrected gradient derived later in this post. The hard-target function above already obtains its gradient through ordinary autodiff; it does not use the soft-target custom backward rule.

## How the corrected log-softmax implementation works

Log-softmax returns all values $\log q_k$ and has no designated target. We select one maximal class as the anchor:

$$
w=\arg\max_j z_j,\qquad
r_k=
\begin{cases}
0,&k=w,\\
z_k-z_w,&k\ne w.
\end{cases}
$$

Every $r_k$ is nonpositive. The selected class contributes exactly one to the shifted exponential sum. Keep this contribution separate and define

$$
S_w=\sum_{j\ne w}e^{r_j}.
$$

Then the full log-softmax vector is

$$
\begin{aligned}
\log q_k
&=\log\frac{e^{r_k}}{\sum_j e^{r_j}}\\
&=r_k-\log(1+S_w)\\
&=\boxed{r_k-\operatorname{log1p}(S_w)}.
\end{aligned}
$$

For the selected class specifically,

$$
\boxed{\log q_w=-\operatorname{log1p}(S_w).}
$$

This explains the implementation's main steps:

| Code variable or operation | Mathematical role |
| --- | --- |
| `winner = argmax(logits)` | Select the index $w$. |
| `anchor = gather(logits, winner)` | Retrieve $z_w$, retaining its autograd connection. |
| `relative = where(is_winner, 0, logits - anchor)` | Construct $r$, with a constant zero at the selected slot. |
| Mask the selected exponential and sum the others | Compute $S_w$, excluding the contribution $e^0=1$. |
| `relative - log1p(other_mass)` | Return all $\log q_k$. |

The selected exponential is excluded from the sum because `log1p` already accounts for its contribution of one. If several logits tie for the maximum, select one of them; all the other maximal logits remain in $S_w$ and each contributes one.

### Why the anchor must remain connected to autodiff

For a locally fixed selected index $w$, each non-selected difference $z_j-z_w$ depends on $z_w$. Therefore,

$$
\frac{\partial S_w}{\partial z_w}
=-\sum_{j\ne w}e^{z_j-z_w}
=-S_w.
$$

The selected output consequently has derivative

$$
\frac{\partial\log q_w}{\partial z_w}
=-\frac{1}{1+S_w}(-S_w)
=\boxed{\frac{S_w}{1+S_w}}.
$$

For a non-selected input $z_j$,

$$
\frac{\partial\log q_w}{\partial z_j}
=-\frac{e^{z_j-z_w}}{1+S_w}.
$$

These are the usual log-softmax derivatives, evaluated through expressions that preserve the small mass. In particular,

$$
\frac{S_w}{1+S_w}=1-q_w,
$$

but the implementation obtains this quantity without subtracting a rounded probability from one. If the anchor were detached in this computation graph, these paths through $-z_w$ would disappear and the selected output would have an incorrect zero derivative with respect to $z_w$. Autodiff does not differentiate the integer index returned by `argmax`; it does differentiate the gathered logit at that index.

The explicit constant zero at the selected slot also makes clear that its derivative is zero: $z_w-z_w$ represents the same variable twice. The relevant dependence on $z_w$ comes from all the other slots.

For example, with $z=(9,-9,-9)$ and $w=1$,

$$
S_w=2e^{-18}\approx3.046\times10^{-8}.
$$

An ordinary fp32 evaluation can round $1+S_w$ to one, returning $\log q_w=0$. The corrected evaluation instead retains

$$
\log q_w\approx-3.046\times10^{-8},\qquad
\frac{\partial\log q_w}{\partial z_w}\approx3.046\times10^{-8}.
$$

No second shift is needed here: the anchor is already a maximal logit. The hard-target loss needs the additional shift only because its anchor is the target, which may be smaller than the maximum.

## The related issue in standalone softmax

Let $a$ be the index of the largest logit, held fixed locally, and consider the scalar output $F(z)=q_a$. Using the quotient rule,

$$
\begin{aligned}
\frac{\partial q_a}{\partial z_a}
&=\frac{e^{z_a}Z-e^{z_a}e^{z_a}}{Z^2}\\
&=q_a-q_a^2\\
&=q_a(1-q_a).
\end{aligned}
$$

For $j\ne a$,

$$
\frac{\partial q_a}{\partial z_j}=-q_aq_j.
$$

If $q_a$ rounds to one, the usual diagonal expression becomes $1(1-1)=0$, while the off-diagonal terms can remain negative and nonzero.

Writing $S=\sum_{j\ne a}e^{z_j-z_a}$ shows the positive diagonal derivative that has been lost:

$$
\frac{\partial q_a}{\partial z_a}=\frac{S}{(1+S)^2}.
$$

The corrected log-softmax retains the small value $\log q_a=-\operatorname{log1p}(S)$. Differentiating through this expression can preserve the small derivative even if the final probability $\exp(\log q_a)$ rounds to one.

For an arbitrary downstream loss, the backward pass also depends on its incoming gradient. The example above concerns the derivative of the largest softmax output itself; it does not mean that the maximal logit's gradient is always zero for every possible downstream objective.

## Softmax Cancellation: losing the student–teacher difference

Now let the target distribution come from a frozen teacher:

$$
p_k=\operatorname{softmax}(z_{\mathrm T})_k,\qquad
q_k=\operatorname{softmax}(z_{\mathrm S})_k.
$$

The student gradient is still $q_k-p_k$. As the student approaches the teacher, this difference should approach zero. When their logits are identical, it should be zero.

Suppose the computed probabilities are

$$
\widehat q_k=q_k+\epsilon_{q,k},\qquad
\widehat p_k=p_k+\epsilon_{p,k}.
$$

Subtracting them gives

$$
\widehat q_k-\widehat p_k=(q_k-p_k)+(\epsilon_{q,k}-\epsilon_{p,k}).
$$

If the true difference is tiny, the probability-rounding errors can dominate it. The subtraction itself can even be exact for the rounded operands; the problem is that those operands have already lost information.

There is a second implementation detail. A teacher probability may be computed with `softmax`, while the student's effective backward probability is reconstructed with `exp(log_softmax)`. Those mathematically equivalent evaluation paths can round differently. This can leave a residual gradient even for identical logits. Repeated deterministic calls to the same implementation with identical inputs are not being claimed to produce random differences.

The paper's strategy is to start with the logit difference, before rounding two complete probability vectors separately.

## Deriving the stable soft-target gradient

### Express the student as a reweighted teacher

Define

$$
\delta_k=z_{\mathrm S,k}-z_{\mathrm T,k}.
$$

Then

$$
\begin{aligned}
q_k
&=\frac{e^{z_{\mathrm T,k}+\delta_k}}{\sum_i e^{z_{\mathrm T,i}+\delta_i}}\\
&=\frac{e^{z_{\mathrm T,k}}e^{\delta_k}}{\sum_i e^{z_{\mathrm T,i}}e^{\delta_i}}\\
&=\boxed{\frac{p_k e^{\delta_k}}{\sum_i p_i e^{\delta_i}}}.
\end{aligned}
$$

The final step divides both numerator and denominator by the teacher's normalizing constant. Intuitively, the student starts with $p$, multiplies each class's probability by $e^{\delta_k}$, and normalizes the result.

Consequently, the exact log-ratio is

$$
\log\frac{q_k}{p_k}=\delta_k-\log\sum_i p_i e^{\delta_i}.
$$

### Center the logit differences

Set

$$
\mu=\sum_i p_i\delta_i,\qquad d_k=\delta_k-\mu.
$$

Here, $\mu$ is the teacher-weighted mean of the **logit differences**. The exponential normalization $\sum_i p_i e^{\delta_i}$ is a different quantity.

Since $\delta_k=d_k+\mu$,

$$
\begin{aligned}
q_k
&=\frac{p_k e^{d_k+\mu}}{\sum_i p_i e^{d_i+\mu}}\\
&=\frac{e^{\mu}p_k e^{d_k}}{e^{\mu}\sum_i p_i e^{d_i}}\\
&=\frac{p_k e^{d_k}}{\sum_i p_i e^{d_i}}.
\end{aligned}
$$

Thus, centering introduces **no mathematical approximation**, even though $\mu$ depends on the student logits. The common factor cancels identically for every input.

Any common scalar shift would preserve this ratio. The weighted mean is chosen because it also gives

$$
\sum_i p_i d_i=\sum_i p_i\delta_i-\mu\sum_i p_i=\mu-\mu=0.
$$

If all logits change by the same scalar, the probabilities do not change. Centering removes this irrelevant common component and leaves changes relative to the teacher-weighted average.

### Derive the log-ratio from the centered differences

We now derive the expression for $s_k$ explicitly. From the student-as-reweighted-teacher identity,

$$
\frac{q_k}{p_k}
=\frac{e^{\delta_k}}{\sum_i p_i e^{\delta_i}}.
$$

Taking the logarithm of the numerator and denominator separately gives

$$
\begin{aligned}
s_k
&:=\log\frac{q_k}{p_k}\\
&=\log e^{\delta_k}-\log\sum_i p_i e^{\delta_i}\\
&=\delta_k-\log\sum_i p_i e^{\delta_i}.
\end{aligned}
$$

Since $d_i=\delta_i-\mu$, we have $\delta_i=d_i+\mu$ for every class, including class $k$. Substitute this into **both** occurrences of $\delta$:

$$
\begin{aligned}
s_k
&=(d_k+\mu)-\log\sum_i p_i e^{d_i+\mu}\\
&=d_k+\mu-\log\left(e^{\mu}\sum_i p_i e^{d_i}\right)\\
&=d_k+\mu-\left[\mu+\log\sum_i p_i e^{d_i}\right]\\
&=\boxed{d_k-\log\sum_i p_i e^{d_i}}.
\end{aligned}
$$

The factor $e^{\mu}$ can be pulled outside the sum because $\mu$ is the same scalar for every class. Its logarithm is $\mu$, which cancels the $+\mu$ outside the logarithm. This cancellation is exact algebra; no Taylor approximation is involved.

Equivalently, using the already-centered probability expression,

$$
\begin{aligned}
s_k
&=\log\left(\frac{p_k e^{d_k}}{\sum_i p_i e^{d_i}}\right)-\log p_k\\
&=\log p_k+d_k-\log\sum_i p_i e^{d_i}-\log p_k\\
&=d_k-\log\sum_i p_i e^{d_i}.
\end{aligned}
$$

Here, the two $\log p_k$ terms cancel. Both derivations lead to the same expression. Numerically, we calculate it from $d$ and its shared log-normalizer; the displayed derivation does not instruct us to form the probability ratio $q_k/p_k$ first.

### Rewrite the log-normalization using `expm1` and `log1p`

Define the exact log-ratio

$$
s_k=\log\frac{q_k}{p_k}=d_k-\log\sum_i p_i e^{d_i}.
$$

Now expand only the algebra, without making a Taylor approximation:

$$
\begin{aligned}
\sum_i p_i e^{d_i}
&=\sum_i p_i\left[1+(e^{d_i}-1)\right]\\
&=1+\sum_i p_i(e^{d_i}-1).
\end{aligned}
$$

Let

$$
A=\sum_i p_i\operatorname{expm1}(d_i).
$$

Then the stable expression is

$$
\boxed{s_k=d_k-\operatorname{log1p}(A).}
$$

This is the middle expression in the paper's Equation (9). The normalization is close to one, but its logarithm is evaluated without first forming and rounding $1+A$.

### Why centering helps numerically

For small $d_i$, the Taylor expansion gives

$$
\operatorname{expm1}(d_i)=d_i+\frac{d_i^2}{2}+\cdots.
$$

Therefore,

$$
\begin{aligned}
A
&=\sum_i p_i d_i+\frac12\sum_i p_i d_i^2+\cdots\\
&=\frac12\sum_i p_i d_i^2+\cdots.
\end{aligned}
$$

The first-order contribution vanishes. The centered differences $d_k$ retain the first-order changes, while $\operatorname{log1p}(A)$ provides the smaller nonlinear normalization correction.

For intuition, this implies

$$
s_k\approx d_k,\qquad q_k-p_k\approx p_k d_k
$$

when the logit differences are small. These approximations explain the behavior; the actual algorithm keeps the full nonlinear expressions.

The paper also notes that $A$ is nonnegative in exact arithmetic. Indeed, $e^x-1\geq x$, so

$$
A=\sum_i p_i(e^{d_i}-1)\geq\sum_i p_i d_i=0.
$$

Finite-precision evaluation can still introduce rounding error. In particular, the nonnegativity proof is an algebraic property, not a guarantee that every implementation of the sum is error-free.

### Recover the probability difference from its log-ratio

Because $e^{s_k}=q_k/p_k$,

$$
\begin{aligned}
q_k-p_k
&=p_k\left(\frac{q_k}{p_k}-1\right)\\
&=p_k(e^{s_k}-1)\\
&=\boxed{p_k\operatorname{expm1}(s_k)}.
\end{aligned}
$$

The paper calls this quantity $u_k$. It is already a numerically stable evaluation of the desired gradient; it is not another loss that must be differentiated to obtain the gradient.

The two special functions protect different operations:

| Computation | Small quantity being preserved |
| --- | --- |
| $\operatorname{expm1}(d_i)$ | The exponential increment $e^{d_i}-1$ |
| $\operatorname{log1p}(A)$ | The normalization correction $\log(1+A)$ |
| $\operatorname{expm1}(s_k)$ | The relative probability change $e^{s_k}-1$ |

They do not cancel as inverse functions: a weighted sum and a subtraction from $d_k$ occur between them.

### A two-class example

Let

$$
z_{\mathrm T}=(0,0),\qquad z_{\mathrm S}=(\varepsilon,0).
$$

Then

$$
p=\left(\frac12,\frac12\right),\qquad
\delta=(\varepsilon,0),\qquad
\mu=\frac{\varepsilon}{2},\qquad
d=\left(\frac{\varepsilon}{2},-\frac{\varepsilon}{2}\right).
$$

To first order,

$$
u\approx\left(\frac{\varepsilon}{4},-\frac{\varepsilon}{4}\right).
$$

For $\varepsilon=10^{-8}$, this is approximately $(2.5\times10^{-9},-2.5\times10^{-9})$. The student probabilities are approximately

$$
q=(0.5000000025,\;0.4999999975).
$$

Both can round to $0.5$ in fp32, making direct probability subtraction return zero. The rewritten calculation works with small representable changes directly.

When the stored student and teacher logits are identical, $\delta=0$, hence $d=0$, $A=0$, $s=0$, and $u=0$. The forward cross-entropy generally remains the teacher's entropy; its gradient, rather than its loss value, is zero.

### Why the implementation has two branches

The corrected implementation uses

$$
u_k=
\begin{cases}
p_k\operatorname{expm1}(s_k),&|s_k|<1,\\
q_k-p_k,&|s_k|\geq1.
\end{cases}
$$

Near $s_k=0$, the exponential-difference expression protects the small gradient. Away from zero, the probabilities are sufficiently separated for direct subtraction.

Specifically, $\lvert s_k\rvert\geq1$ means $q_k\geq e\thinspace p_k$ or $p_k\geq e\thinspace q_k$. Thus,

$$
|q_k-p_k|\geq(1-e^{-1})\max(q_k,p_k)\approx0.632\max(q_k,p_k).
$$

The result is substantial relative to the inputs, so subtraction does not severely amplify relative input errors. The fallback also avoids multiplying a probability that underflows to zero by an `expm1` result that overflows to infinity. The cutoff one is a practical numerical choice; both branches represent the same exact gradient.

## What the final zero-sum correction does

After calculating $u$, the paper sets

$$
r=\sum_i u_i,\qquad g_k=u_k-q_k r.
$$

In exact arithmetic, $u_k=q_k-p_k$ and $r=0$, so this changes nothing. With numerical errors, $r$ measures a violation of the known zero-sum identity.

Because $q$ is normalized,

$$
\sum_k g_k=\sum_k u_k-r\sum_k q_k=r-r=0.
$$

The correction distributes the residual according to the probabilities: class $k$ receives the fraction $q_k$ of the total correction. Actual floating-point evaluation can leave a further small residual; the algebra does not guarantee a bitwise-zero reduction under every summation order.

### Why the weights are $q_k$

A useful interpretation comes from log-softmax's backward operation. Temporarily treat $u$ as a fixed vector and define the auxiliary scalar

$$
H(z)=\sum_i u_i\log q_i.
$$

Since $\log q_i=z_i-\log Z$,

$$
H(z)=\sum_i u_i z_i-\left(\sum_i u_i\right)\log Z.
$$

Differentiating gives

$$
\frac{\partial H}{\partial z_k}=u_k-\left(\sum_i u_i\right)\frac{\partial\log Z}{\partial z_k}=u_k-q_k r.
$$

The $q_k$ factor appears because it is the derivative of the shared log-normalizer. This auxiliary scalar explains the correction's form; it is not the paper's forward cross-entropy loss. The zero-sum condition alone does not uniquely force this weighting.

### A shared normalization error can be removed exactly

There is a stronger explanatory case for this particular correction. Suppose the computed log-ratios have a common additive error $\eta$, while the other quantities are exact:

$$
\widehat s_k=s_k+\eta.
$$

Then

$$
u_k=p_k(e^{s_k+\eta}-1)=e^{\eta}q_k-p_k.
$$

Their sum is $r=e^{\eta}-1$, so

$$
u_k-q_k r=e^{\eta}q_k-p_k-q_k(e^{\eta}-1)=q_k-p_k.
$$

A single residual can correct every coordinate in this special case because all errors share one scalar source. Errors in a shared log-normalization term have precisely this structure when the remaining arithmetic is exact.

### Zero sum is not exact coordinatewise recovery

Let $g^{\ast}$ be the exact gradient and write $u_k=g_k^{\ast}+\epsilon_k$. Since $\sum_k g_k^{\ast}=0$,

$$
r=\sum_i\epsilon_i,\qquad
g_k-g_k^{\ast}=\epsilon_k-q_k\sum_i\epsilon_i.
$$

The remaining error need not vanish in every coordinate. For example, if $q=(0.9,0.1)$ and the original error is $(0,\eta)$, the corrected error is $(-0.9\eta,0.9\eta)$. The first coordinate was initially accurate and is changed by the correction.

There is nevertheless an algebraic weighted-error guarantee. For normalized positive $q$, ignoring additional rounding in the correction itself,

$$
\begin{aligned}
\sum_k\frac{(g_k-g_k^{\ast})^2}{q_k}
&=\sum_k\frac{(\epsilon_k-q_k r)^2}{q_k}\\
&=\sum_k\frac{\epsilon_k^2}{q_k}-2r\sum_k\epsilon_k+r^2\sum_k q_k\\
&=\sum_k\frac{\epsilon_k^2}{q_k}-r^2.
\end{aligned}
$$

This reduces a particular weighted total error, rather than guaranteeing improvement in each component. The main protection against cancellation comes from how $u$ is computed; the residual correction restores additional consistency.

## How autodiff receives the calculated gradient

At this point, the algorithm already has the desired vector $g$. Differentiating $u$ or $g$ would calculate derivatives of a gradient, rather than the first-order loss gradient we want to supply.

Instead, the paper constructs a scalar with the usual forward loss value and a prescribed backward gradient.

Write $\operatorname{sg}$ for `stop_gradient`. It returns its input unchanged but treats it as constant during autodiff:

| Expression | Forward value | Derivative used by autodiff |
| --- | --- | --- |
| $x$ | $x$ | $1$ |
| $\operatorname{sg}(x)$ | $x$ | $0$ |
| $x-\operatorname{sg}(x)$ | $0$ | $1$ |

These are custom autodiff rules. Although the last expression evaluates to zero, replacing its computation graph by a constant zero would discard the gradient annotation.

For one example, the returned scalar is

$$
\widetilde{\mathcal{L}}
=-\sum_i p_i\operatorname{sg}(\log q_i)
+\sum_i\operatorname{sg}(g_i)\left[z_{\mathrm S,i}-\operatorname{sg}(z_{\mathrm S,i})\right].
$$

In the forward pass, the added term is zero. The returned numerical value is the ordinary cross-entropy.

In the backward pass, the first term has zero student gradient because `log_q` is stopped. Every $g_i$ in the second term is also stopped. For a particular coordinate $z_{\mathrm S,k}$, only its direct unstopped occurrence contributes, giving

$$
\boxed{\frac{\partial_{\mathrm{AD}}\widetilde{\mathcal{L}}}{\partial z_{\mathrm S,k}}=0+\operatorname{sg}(g_k)(1-0)=g_k.}
$$

Here, $\partial_{\mathrm{AD}}$ emphasizes the specified autodiff rule. At the current logits $z_0$, the backward calculation behaves like the local affine expression

$$
\mathcal{L}_0+g_0^{\mathsf T}(z-z_0).
$$

It has value $\mathcal{L}_0$ at $z_0$ and slope $g_0$. On the next forward pass, all these values are recomputed.

For network parameters $\theta$, ordinary backpropagation then gives

$$
\frac{\partial\widetilde{\mathcal{L}}}{\partial\theta}=\sum_k g_k\frac{\partial z_{\mathrm S,k}}{\partial\theta}.
$$

The construction supplies a first-order backward rule. Because the supplied $g$ is stopped, differentiating this expression again does not automatically recover the original cross-entropy Hessian.

## A JAX implementation

The following implementation adapts the corrected version-3 formulas. Classes occupy the final axis, and each loss returns one value per example; a batch reduction can be applied outside the function. The code uses zero-based class indices. The teacher is explicitly frozen. The soft-target function here assumes finite student and teacher logits; an entirely masked row does not define a probability distribution.

```python
import jax
import jax.numpy as jnp


def stable_log_softmax(logits):
    winner = jnp.argmax(logits, axis=-1, keepdims=True)
    anchor = jnp.take_along_axis(logits, winner, axis=-1)
    is_winner = jnp.arange(logits.shape[-1]) == winner

    # The selected slot is a constant zero in the computation graph.
    relative = jnp.where(is_winner, 0.0, logits - anchor)
    other_mass = jnp.sum(
        jnp.where(is_winner, 0.0, jnp.exp(relative)),
        axis=-1,
        keepdims=True,
    )
    return relative - jnp.log1p(other_mass)


def stable_hard_cross_entropy(logits, target):
    target = jnp.asarray(target)
    target_logit = jnp.take_along_axis(
        logits, target[..., None], axis=-1
    )
    is_target = jnp.arange(logits.shape[-1]) == target[..., None]
    relative = jnp.where(is_target, 0.0, logits - target_logit)

    # A second shift handles targets below the largest logit.
    shift = jnp.max(relative, axis=-1, keepdims=True)
    other_mass = jnp.sum(
        jnp.where(is_target, 0.0, jnp.exp(relative - shift)),
        axis=-1,
    )
    shift = shift[..., 0]
    return shift + jnp.log1p(other_mass + jnp.expm1(-shift))


def stable_soft_cross_entropy(student_logits, teacher_logits):
    sg = jax.lax.stop_gradient
    teacher_logits = sg(teacher_logits)
    log_q = stable_log_softmax(student_logits)
    q = jnp.exp(log_q)
    p = jnp.exp(stable_log_softmax(teacher_logits))

    delta = student_logits - teacher_logits
    mean_delta = jnp.sum(p * delta, axis=-1, keepdims=True)
    centered = delta - mean_delta
    normalizer_increment = jnp.sum(
        p * jnp.expm1(centered), axis=-1, keepdims=True
    )
    log_ratio = centered - jnp.log1p(normalizer_increment)
    u = jnp.where(
        jnp.abs(log_ratio) < 1,
        p * jnp.expm1(log_ratio),
        q - p,
    )
    residual = jnp.sum(u, axis=-1, keepdims=True)
    gradient = u - q * residual

    forward_loss = -jnp.sum(p * sg(log_q), axis=-1)
    zero_with_gradient = jnp.sum(
        sg(gradient) * (student_logits - sg(student_logits)), axis=-1
    )
    return forward_loss + zero_with_gradient
```

For example, the hard-target case can be inspected with

```python
z = jnp.array([9.0, -9.0, -9.0], dtype=jnp.float32)
value, gradient = jax.value_and_grad(stable_hard_cross_entropy)(z, 0)
print(value)
print(gradient)
```

The value should be about $3.046\times10^{-8}$, with gradient approximately $(-3.046,1.523,1.523)\times10^{-8}$. Exact printed digits can depend on the backend and evaluation details.

For soft targets, identical logits should give a zero student gradient:

```python
teacher = jnp.array([2.0, 1.0, 0.0], dtype=jnp.float32)
value, gradient = jax.value_and_grad(stable_soft_cross_entropy)(
    teacher, teacher
)
print(value)       # The teacher's entropy, generally positive.
print(gradient)    # Zero for identical finite logits.
```

The examples were checked on CPU with JAX 0.12.0.1 using fp32. Additional checks covered a non-maximal target, non-target exponentials underflowing to zero, a single finite logit with negative-infinity masks, the small student–teacher perturbation in the paper, the large-log-ratio fallback, and leading batch dimensions.

## PyTorch implementations and examples

In PyTorch, `tensor.detach()` supplies the same forward value while removing its connection to the autograd graph. In particular, `z - z.detach()` evaluates to zero but has derivative one with respect to `z`.

The following functions mirror the JAX implementation. They use the final axis for classes, zero-based target indices, and return one loss per example. Targets for a batch have the same shape as the logits' leading dimensions. Floating-point dtype and device follow the input logits.

The hard-target loss and log-softmax use ordinary autograd. For the soft-target loss, we calculate the forward value and corrected gradient inside `torch.no_grad()`, since their derivative graph is unnecessary. The final zero-valued term then installs the calculated gradient. This also freezes the teacher.

```python
import torch
import torch.nn.functional as F


def stable_log_softmax_torch(logits):
    winner = logits.argmax(dim=-1, keepdim=True)
    anchor = logits.gather(-1, winner)
    classes = torch.arange(logits.shape[-1], device=logits.device)
    is_winner = classes == winner

    relative = torch.where(
        is_winner, torch.zeros_like(logits), logits - anchor
    )
    other_mass = torch.where(
        is_winner, torch.zeros_like(logits), relative.exp()
    ).sum(dim=-1, keepdim=True)
    return relative - torch.log1p(other_mass)


def stable_hard_cross_entropy_torch(logits, target):
    # Steps 1-2: gather the target and form target-relative logits.
    target = torch.as_tensor(
        target, dtype=torch.long, device=logits.device
    )
    target_logit = logits.gather(-1, target.unsqueeze(-1))
    classes = torch.arange(logits.shape[-1], device=logits.device)
    is_target = classes == target.unsqueeze(-1)
    relative = torch.where(
        is_target, torch.zeros_like(logits), logits - target_logit
    )

    # Step 3: the target slot is zero, so this maximum is >= 0.
    shift = relative.amax(dim=-1, keepdim=True)
    # Step 4: sum non-target exponentials after the second shift.
    other_mass = torch.where(
        is_target, torch.zeros_like(logits), (relative - shift).exp()
    ).sum(dim=-1)
    shift = shift.squeeze(-1)
    # Step 5: evaluate the loss; ordinary autograd gives its gradient.
    return shift + torch.log1p(other_mass + torch.expm1(-shift))


def stable_soft_cross_entropy_torch(student_logits, teacher_logits):
    with torch.no_grad():
        log_q = stable_log_softmax_torch(student_logits)
        q = log_q.exp()
        p = stable_log_softmax_torch(teacher_logits).exp()

        delta = student_logits - teacher_logits
        mean_delta = (p * delta).sum(dim=-1, keepdim=True)
        centered = delta - mean_delta
        normalizer_increment = (p * torch.expm1(centered)).sum(
            dim=-1, keepdim=True
        )
        log_ratio = centered - torch.log1p(normalizer_increment)
        u = torch.where(
            log_ratio.abs() < 1,
            p * torch.expm1(log_ratio),
            q - p,
        )
        residual = u.sum(dim=-1, keepdim=True)
        gradient = u - q * residual
        forward_loss = -(p * log_q).sum(dim=-1)

    # Only this term records a graph linking the loss to the student.
    zero_with_gradient = (
        gradient * (student_logits - student_logits.detach())
    ).sum(dim=-1)
    return forward_loss + zero_with_gradient
```

Inside the soft-target function, `gradient` and `forward_loss` are already constants for autograd because they were calculated under `no_grad()`. The last expression is therefore exactly the construction derived earlier: it contributes zero to the forward value and `gradient` to the student-logit backward pass.

### Inspecting the maximal log-softmax output

This example isolates the log-softmax fix before using it in a loss:

```python
z = torch.tensor(
    [9.0, -9.0, -9.0], dtype=torch.float32, requires_grad=True
)

usual_output = F.log_softmax(z, dim=-1)[0]
stable_output = stable_log_softmax_torch(z)[0]
stable_gradient = torch.autograd.grad(stable_output, z)[0]

print("usual maximal log-probability:", usual_output.item())
print("stable maximal log-probability:", stable_output.item())
print("stable gradient:", stable_gradient)
```

The corrected output should be approximately $-3.046\times10^{-8}$, with gradient $(3.046,-1.523,-1.523)\times10^{-8}$. Negating this output gives the high-confidence hard-target loss, so negating its gradient gives the hard-target gradient derived above.

### High-confidence hard targets

We can compare the usual cross-entropy with the rewritten version on the same logits. Each function call below builds a separate graph, so the first call to `autograd.grad` does not require retaining a graph for the second calculation.

```python
z = torch.tensor([9.0, -9.0, -9.0], dtype=torch.float32)
z.requires_grad_()

usual_loss = F.cross_entropy(z.unsqueeze(0), torch.tensor([0]))
usual_gradient = torch.autograd.grad(usual_loss, z)[0]

stable_loss = stable_hard_cross_entropy_torch(z, 0)
stable_gradient = torch.autograd.grad(stable_loss, z)[0]

print("usual loss:", usual_loss.item())
print("usual gradient:", usual_gradient)
print("stable loss:", stable_loss.item())
print("stable gradient:", stable_gradient)
```

The stable loss should be approximately $3.046\times10^{-8}$, and the stable gradient should be approximately $(-3.046,1.523,1.523)\times10^{-8}$. The usual implementation can lose the target contribution; its exact behavior depends on the PyTorch version, backend, and dtype.

### Nearly identical student and teacher logits

The two-class example provides a direct test of Softmax Cancellation:

```python
teacher = torch.tensor([0.0, 0.0], dtype=torch.float32)
student = torch.tensor(
    [1e-8, 0.0], dtype=torch.float32, requires_grad=True
)

p = teacher.softmax(dim=-1)
usual_loss = -(p * student.log_softmax(dim=-1)).sum()
usual_gradient = torch.autograd.grad(usual_loss, student)[0]

stable_loss = stable_soft_cross_entropy_torch(student, teacher)
stable_gradient = torch.autograd.grad(stable_loss, student)[0]

print("usual gradient:", usual_gradient)
print("stable gradient:", stable_gradient)
```

The desired gradient is approximately $(2.5\times10^{-9},-2.5\times10^{-9})$. The stable computation should retain this difference even when the separately computed probabilities round to the same values.

For an exact match, the gradient should instead be zero:

```python
teacher = torch.tensor([2.0, 1.0, 0.0], dtype=torch.float32)
student = teacher.clone().requires_grad_()

loss = stable_soft_cross_entropy_torch(student, teacher)
gradient = torch.autograd.grad(loss, student)[0]

print(loss.item())   # The teacher's entropy, generally positive.
print(gradient)      # Zero for identical finite logits.
```

### Batch reduction and ordinary backpropagation

The returned per-example losses can be averaged before calling `backward()`:

```python
teacher_batch = torch.tensor(
    [[2.0, 1.0, 0.0], [0.0, 0.0, 0.0]], dtype=torch.float32
)
student_batch = torch.tensor(
    [[2.0, 1.0, 0.0], [1e-8, 0.0, 0.0]],
    dtype=torch.float32,
    requires_grad=True,
)

per_example_loss = stable_soft_cross_entropy_torch(
    student_batch, teacher_batch
)
loss = per_example_loss.mean()
loss.backward()

print(per_example_loss.shape)  # torch.Size([2])
print(student_batch.grad)
```

The first row receives a zero gradient because its distributions match. The second row receives the calculated logit gradient divided by two, because the batch loss is a mean. When `student_batch` is a model's output rather than a leaf tensor, the same backward signal continues through the model to its parameters.

These examples explicitly use fp32. In mixed-precision training, the precision of these loss calculations must be chosen deliberately; `no_grad()` controls graph recording, not arithmetic precision. The same finite-logit and first-order-gradient assumptions described above apply to the soft-target PyTorch function.

The PyTorch examples were checked on CPU with PyTorch 2.15.0+cpu. Seventeen checks covered the examples above, extreme and masked hard-target logits, the large-log-ratio fallback, teacher freezing, batch scaling, float64 agreement with the analytical gradient, and propagation of the custom gradient to model parameters.

## Why these small errors can affect optimization

The paper connects Softmax Collapse with the **slingshot** behavior observed in small grokking experiments: long periods of tiny training loss interrupted by abrupt loss spikes.

Its explanation involves the interaction between the precision cliff and Adam's moving second moment. After memorization, margins increase and gradients shrink. Crossing the cliff abruptly removes the target-logit contribution. During a low-gradient period, the second moment decays. Weight decay or residual updates can then move examples back across the cliff, restoring a target contribution while the optimizer's denominator is small. The resulting step can be disproportionately large.

This explanation concerns how logit-gradient errors propagate through the tested networks and optimizer. It does not require every parameter gradient to become exactly zero, and it is not a claim that all large-scale training instabilities have this cause.

For soft targets, the paper uses an especially clean diagnostic: initialize the student with the teacher's weights. With a fixed teacher, fresh optimizer state, and no weight decay, the true distillation gradient is zero and no update is expected. Their standard implementation can nevertheless move the student because Adam amplifies small residual gradients. The corrected implementation keeps the student stationary in the reported experiment. This makes the numerical error observable as parameter drift, rather than only as an inaccurate number in a gradient printout.

### Why a corrected margin can still plateau

Removing the precision cliff does not imply that the margin must increase forever. With weight decay, the paper studies a balance between the gradient update and parameter shrinkage.

For a deterministic stationary parameter coordinate, write $G_i=\partial\mathcal{L}/\partial\theta_i$. AdamW's moving averages converge to $G_i$ and $G_i^2$, so a stationary update requires

$$
\frac{G_i}{|G_i|+\epsilon}+\lambda\theta_i=0.
$$

Here, $\epsilon$ is Adam's stabilizing constant and $\lambda$ is the weight-decay coefficient. When $\lvert G_i\rvert\ll\epsilon$,

$$
\frac{G_i}{|G_i|+\epsilon}\approx\frac{G_i}{\epsilon}.
$$

Balancing this against weight decay gives approximately

$$
|G_i|\approx\epsilon\lambda|\theta_i|.
$$

If the relevant gradient magnitude scales like $C_i e^{-m}$, this suggests

$$
m\approx\log\frac{C_i}{\epsilon\lambda|\theta_i|}.
$$

When the remaining factors vary moderately, the leading dependence is the paper's rule of thumb

$$
m_\star\approx\log(1/\epsilon).
$$

For $\epsilon=10^{-8}$, this is about $18.4$, slightly beyond the fp32 cliff near $16.6$. A standard implementation can encounter an artificial numerical boundary before reaching the optimizer's natural balance. The approximation is not an exact universal equilibrium independent of the model, gradient prefactors, or weight decay.

## What to check when using these ideas

The paper's experiments demonstrate the effects in controlled grokking and distillation settings. They motivate accurate primitives, while leaving the practical benefit for a particular large model to measurement.

A useful numerical check examines individual gradient coordinates as well as the residual sum. High-confidence examples, identical student–teacher logits, small representable logit perturbations, and extreme or masked logits exercise different failure modes. A zero gradient sum alone does not certify coordinatewise accuracy.

Input precision matters too. If a student–teacher difference has already disappeared when the logits were stored, a later loss function cannot reconstruct it. These rewrites preserve information available in the inputs and intermediate arithmetic; they do not recover information that was never represented.

Finally, the end of the usable exponential range depends on the format and runtime. Normal fp32 numbers extend to roughly $10^{-38}$, while subnormal numbers extend further, to roughly $10^{-45}$. Some hardware paths flush subnormals to zero. The precision cliff near one is a different phenomenon and occurs much earlier than either limit in the examples above.

The practical question is therefore broader than whether the forward loss avoids overflow: does the chosen computation graph preserve the small quantities needed by its backward pass?

## References

1. Jonathan T. Barron, Dan Gnanapragasam, and Michael Tschannen. [A Fix for Softmax and Cross-Entropy](https://arxiv.org/abs/2610.31642v3). arXiv:2610.31642v3, 2026. See Sections 2–3 for the numerical fixes, Sections 4–7 for optimization and experiments, and the erratum for the corrected extreme-logit implementation.
2. Pierre Blanchard, Desmond J. Higham, and Nicholas J. Higham. [Accurately Computing the Log-Sum-Exp and Softmax Functions](https://eprints.maths.manchester.ac.uk/2765/). IMA Journal of Numerical Analysis, 2021.
3. JAX documentation. [`jax.lax.stop_gradient`](https://docs.jax.dev/en/latest/_autosummary/jax.lax.stop_gradient.html).
4. NumPy documentation. [`numpy.log1p`](https://numpy.org/doc/stable/reference/generated/numpy.log1p.html) and [`numpy.expm1`](https://numpy.org/doc/stable/reference/generated/numpy.expm1.html).
5. PyTorch documentation. [`Tensor.detach`](https://docs.pytorch.org/docs/stable/generated/torch.Tensor.detach.html), [`torch.no_grad`](https://docs.pytorch.org/docs/stable/generated/torch.no_grad.html), and [`torch.autograd.grad`](https://docs.pytorch.org/docs/stable/generated/torch.autograd.grad.html).
