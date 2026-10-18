---
title: "Fourier Transform"
categories:
  - Fourier Analysis
tags:
  - moderate decrease
  - Fourier transform
  - rapidly decreasing
toc: true
toc_sticky: true
use_math: true
comments: true
---

## Definition

For a continuous function $f:\mathbb{R}\to\mathbb{C}$, define

$$
\int_{\mathbb{R}}f(x)dx:=\lim_{a\to\infty}\int_{-a}^{0}f(x)dx+\lim_{b\to\infty}\int_{0}^{b}f(x)dx,
$$

provided both limits exist. Here, $a$ and $b$ tend to infinity independently.

When this integral exists, it also equals the symmetric limit

$$
\int_{\mathbb{R}}f(x)dx=\lim_{R\to\infty}\int_{-R}^{R}f(x)dx.
$$

The converse requires care. A symmetric limit alone is called a **Cauchy principal value** and need not give an improper integral. For example,

$$
\int_{-R}^{R}x\,dx=0,
$$

but the integrals over the positive and negative half-lines do not converge separately. The decay assumptions below will guarantee absolute convergence, so this distinction will cause no difficulty for the functions we study.

## Definition

A continuous function $f:\mathbb{R}\to\mathbb{C}$ is of **moderate decrease** if there is a constant $A>0$ such that

$$
\lvert f(x)\rvert\leq\frac{A}{1+x^2}
$$

for every $x\in\mathbb{R}$. Write $\mathcal{M}(\mathbb{R})$ for the vector space of these functions. The denominator controls both regions: it stays positive near the origin and behaves like $x^2$ far away.

## Exercise

Every $f\in\mathcal{M}(\mathbb{R})$ is absolutely integrable. In particular, its improper integral exists.

*Proof.*

Suppose $f\in\mathcal{M}(\mathbb{R})$. Since

$$
\int_{-R}^{R}\lvert f(x)\rvert dx\leq A\int_{-R}^{R}\frac{dx}{1+x^2}=2A\arctan R\leq A\pi,
$$

the integrals of $\lvert f\rvert$ on each half-line are increasing and bounded. Thus

$$
\lVert f\rVert_1:=\int_{\mathbb{R}}\lvert f(x)\rvert dx\leq A\pi.
$$

This is **absolute integrability**. It also guarantees convergence of the integral of $f$: differences of truncated integrals are bounded by integrals of $\lvert f\rvert$ over their tails, which tend to zero.

More explicitly, for every $R>0$,

$$
\begin{aligned}
\int_{\lvert x\rvert>R}\lvert f(x)\rvert dx
&\leq A\int_{\lvert x\rvert>R}\frac{dx}{x^2}\\
&=2A\int_R^\infty\frac{dx}{x^2}=\frac{2A}{R}.
\end{aligned}
$$

Here and below, an integral over $\lvert x\rvert>R$ means the sum of the two tail integrals. This estimate tells us exactly how a large interval captures almost all of the integral. For example,

$$
\left\lvert\int_{\mathbb{R}}f(x)dx-\int_{-R}^{R}f(x)dx\right\rvert\leq\frac{2A}{R}.
$$

<div style="text-align: right;">\(\square\)</div>

## Proposition (Properties of the improper integral)

Let $f,g\in\mathcal{M}(\mathbb{R})$, $\alpha,\beta\in\mathbb{C}$, $a\in\mathbb{R}$, and $\delta>0$. Then

(1) Linearity:

$$
\int_{\mathbb{R}}(\alpha f+\beta g)=\alpha\int_{\mathbb{R}}f+\beta\int_{\mathbb{R}}g.
$$

(2) Translation invariance:

$$
\int_{\mathbb{R}}f(x-a)dx=\int_{\mathbb{R}}f(x)dx.
$$

(3) Scaling under dilations:

$$
\delta\int_{\mathbb{R}}f(\delta x)dx=\int_{\mathbb{R}}f(x)dx.
$$

(4) Continuity under translation:

$$
\lim_{h\to0}\int_{\mathbb{R}}\lvert f(x-h)-f(x)\rvert dx=0.
$$

*Proof.*

(1) Linearity.

For $\alpha,\beta\in\mathbb{C}$,

$$
\int_{\mathbb{R}}\bigl(\alpha f(x)+\beta g(x)\bigr)dx=\alpha\int_{\mathbb{R}}f(x)dx+\beta\int_{\mathbb{R}}g(x)dx.
$$

Indeed, if $f$ and $g$ have decay constants $A_f$ and $A_g$, then

$$
\lvert\alpha f(x)+\beta g(x)\rvert\leq\frac{\lvert\alpha\rvert A_f+\lvert\beta\rvert A_g}{1+x^2}.
$$

Thus the sum is also of moderate decrease. Apply linearity on $[-R,R]$ and take $R\to\infty$; every integral involved converges absolutely.

(2) Translation invariance.

Let $f:\mathbb{R}\to\mathbb{C}$ be continuous and suppose that

$$
\lvert f(x)\rvert\leq\frac{A}{1+x^2}
$$

for some $A>0$ and every $x\in\mathbb{R}$. We prove that, for every real shift $a$,

$$
\int_{\mathbb{R}}f(x-a)dx=\int_{\mathbb{R}}f(x)dx.
$$

*Proof.*

First, $f$ is absolutely integrable because

$$
\int_{\mathbb{R}}\lvert f(u)\rvert du\leq A\int_{\mathbb{R}}\frac{du}{1+u^2}=A\pi<\infty.
$$

Write $I=\int_{\mathbb{R}}f(u)du$.

For a finite $R$, the substitution $u=x-a$ gives

$$
\int_{-R}^{R}f(x-a)dx=\int_{-R-a}^{R-a}f(u)du.
$$

We are now integrating the same function over a shifted interval. As $R$ increases, its left endpoint tends to $-\infty$ and its right endpoint tends to $+\infty$. Thus the interval still captures more and more of the whole integral.

To make this precise, the difference from $I$ consists of the two missing tails:

$$
I-\int_{-R-a}^{R-a}f(u)du=\int_{-\infty}^{-R-a}f(u)du+\int_{R-a}^{\infty}f(u)du.
$$

If $R>\lvert a\rvert$, then

$$
-R-a\leq-(R-\lvert a\rvert),\qquad R-a\geq R-\lvert a\rvert.
$$

In other words, the shifted interval contains $[-(R-\lvert a\rvert),R-\lvert a\rvert]$. Every missing point therefore satisfies $\lvert u\rvert>R-\lvert a\rvert$. By the triangle inequality and the decay assumption,

$$
\begin{aligned}
\left\lvert I-\int_{-R}^{R}f(x-a)dx\right\rvert
&\leq\int_{\lvert u\rvert>R-\lvert a\rvert}\lvert f(u)\rvert du\\
&\leq A\int_{\lvert u\rvert>R-\lvert a\rvert}\frac{du}{u^2}\\
&=2A\int_{R-\lvert a\rvert}^{\infty}\frac{du}{u^2}\\
&=\frac{2A}{R-\lvert a\rvert}\longrightarrow0.
\end{aligned}
$$

Here $a$ is fixed, so $R-\lvert a\rvert\to\infty$. This shows that the symmetric integrals of the shifted function approach $I$.

Finally, its ordinary improper integral also exists. Applying the same substitution to the absolute value gives

$$
\int_{-R}^{R}\lvert f(x-a)\rvert dx=\int_{-R-a}^{R-a}\lvert f(u)\rvert du\leq A\pi.
$$

The integrals of $\lvert f(x-a)\rvert$ on each half-line are increasing and bounded above by $A\pi$, so both converge. Thus $f(x-a)$ is absolutely integrable, and its improper integral equals its symmetric limit. Therefore,

$$
\int_{\mathbb{R}}f(x-a)dx=\lim_{R\to\infty}\int_{-R}^{R}f(x-a)dx=I=\int_{\mathbb{R}}f(x)dx.
$$

<div style="text-align: right;">\(\square\)</div>

(3) Scaling under dilations.

For $\delta>0$,

$$
\int_{\mathbb{R}}f(\delta x)dx=\frac{1}{\delta}\int_{\mathbb{R}}f(u)du.
$$

The scaled function is of moderate decrease because

$$
\lvert f(\delta x)\rvert\leq\frac{A}{1+\delta^2x^2}\leq\frac{A\max\{1,\delta^{-2}\}}{1+x^2}.
$$

On a finite interval, the substitution $u=\delta x$ gives

$$
\int_{-R}^{R}f(\delta x)dx=\frac{1}{\delta}\int_{-\delta R}^{\delta R}f(u)du.
$$

Let $R\to\infty$. The factor $1/\delta$ compensates for compressing the graph horizontally by a factor of $\delta$.

(4) Continuity under translation in the integral.

We claim that

$$
\lim_{h\to0}\int_{\mathbb{R}}\lvert f(x-h)-f(x)\rvert dx=0.
$$

Pointwise continuity says that the integrand tends to zero for each fixed $x$. To control its integral over an infinite interval, we split the real line into a bounded interval and two tails.

**Step 1: control both tails uniformly for small translations.**

Restrict to $\lvert h\rvert\leq1$ and choose $R>1$. If $\lvert x\rvert>R$, then the reverse triangle inequality gives

$$
\lvert x-h\rvert\geq\lvert x\rvert-\lvert h\rvert>R-1.
$$

Thus, after substituting $u=x-h$,

$$
\begin{aligned}
\int_{\lvert x\rvert>R}\lvert f(x-h)\rvert dx
&\leq\int_{\lvert u\rvert>R-1}\lvert f(u)\rvert du\\
&\leq\frac{2A}{R-1}.
\end{aligned}
$$

Together with the unshifted tail estimate, this gives

$$
\begin{aligned}
\int_{\lvert x\rvert>R}\lvert f(x-h)-f(x)\rvert dx
&\leq\frac{2A}{R-1}+\frac{2A}{R}\\
&\leq\frac{4A}{R-1}.
\end{aligned}
$$

The bound does not depend on the particular $h$ as long as $\lvert h\rvert\leq1$. The condition $R>1$ simply ensures that $R-1$ is positive: a shift of at most $1$ can bring a point at most $1$ unit closer to the origin.

Given $\varepsilon>0$, choose

$$
R>1+\frac{8A}{\varepsilon}.
$$

The tail contribution is then less than $\varepsilon/2$.

**Step 2: control the bounded interval by uniform continuity.**

For $\lvert x\rvert\leq R$ and $\lvert h\rvert\leq1$, both $x$ and $x-h$ belong to $[-R-1,R+1]$. Since $f$ is continuous on this closed bounded interval, it is uniformly continuous there. Therefore, there is an $\eta>0$ such that

$$
u,v\in[-R-1,R+1],\quad\lvert u-v\rvert<\eta
\Longrightarrow\lvert f(u)-f(v)\rvert<\frac{\varepsilon}{4R}.
$$

If $\lvert h\rvert<\min\{1,\eta\}$, then

$$
\begin{aligned}
\int_{-R}^{R}\lvert f(x-h)-f(x)\rvert dx
&\leq2R\sup_{\lvert x\rvert\leq R}\lvert f(x-h)-f(x)\rvert\\
&\leq\frac{\varepsilon}{2}.
\end{aligned}
$$

Combining the two regions gives a total smaller than $\varepsilon$. The order matters: **first choose $R$ to control the tails, then choose $h$ to control the fixed bounded interval.**

<div style="text-align: right;">\(\square\)</div>

## Definition

For $f\in\mathcal{M}(\mathbb{R})$, define its **Fourier transform** by

$$
\widehat f(\xi)=\int_{\mathbb{R}}f(x)e^{-2\pi ix\xi}dx,\qquad\xi\in\mathbb{R}.
$$

Euler's formula gives

$$
e^{-2\pi ix\xi}=\cos(2\pi x\xi)-i\sin(2\pi x\xi).
$$

For fixed $\xi$, this factor oscillates as $x$ varies. Its absolute value is always $1$, so multiplying by it does not affect absolute integrability:

$$
\int_{\mathbb{R}}\lvert f(x)e^{-2\pi ix\xi}\rvert dx=\lVert f\rVert_1<\infty.
$$

In particular, the Fourier transform is well-defined and bounded:

$$
\lvert\widehat f(\xi)\rvert\leq\lVert f\rVert_1
\qquad\text{for every }\xi\in\mathbb{R}.
$$

## Remark

We will repeatedly use

$$
\lvert e^{iu}-1\rvert\leq\lvert u\rvert
\qquad(u\in\mathbb{R}).
$$

Geometrically, $1$ and $e^{iu}$ lie on the unit circle. Their straight-line distance is no greater than the length $\lvert u\rvert$ of the circular path joining them, including any full turns.

Here is an algebraic derivation. By the fundamental theorem of calculus,

$$
e^{iu}-1=\int_0^1\frac{d}{dt}e^{itu}dt=iu\int_0^1e^{itu}dt.
$$

Taking absolute values and using $\lvert e^{itu}\rvert=1$ gives

$$
\lvert e^{iu}-1\rvert\leq\lvert u\rvert\int_0^1 1\,dt=\lvert u\rvert.
$$

The same bound can be recognized from

$$
\lvert e^{iu}-1\rvert=2\lvert\sin(u/2)\rvert\leq\lvert u\rvert.
$$

The useful general idea is that **a difference can be bounded by integrating the derivative**.

## Proposition

The Fourier transform of a function in $\mathcal{M}(\mathbb{R})$ is uniformly continuous.

*Proof.*

For any $\xi,h\in\mathbb{R}$,

$$
\widehat f(\xi+h)-\widehat f(\xi)=\int_{\mathbb{R}}f(x)e^{-2\pi ix\xi}\bigl(e^{-2\pi ixh}-1\bigr)dx.
$$

On $\lvert x\rvert\leq R$, use the exponential bound:

$$
\lvert e^{-2\pi ixh}-1\rvert\leq2\pi\lvert x\rvert\lvert h\rvert\leq2\pi R\lvert h\rvert.
$$

On $\lvert x\rvert>R$, use the triangle inequality:

$$
\lvert e^{-2\pi ixh}-1\rvert\leq2.
$$

Consequently,

$$
\lvert\widehat f(\xi+h)-\widehat f(\xi)\rvert
\leq2\pi R\lvert h\rvert\lVert f\rVert_1
+2\int_{\lvert x\rvert>R}\lvert f(x)\rvert dx.
$$

Given $\varepsilon>0$, first choose $R\geq1$ so that the tail integral is less than $\varepsilon/4$. Then choose

$$
\lvert h\rvert<\frac{\varepsilon}{4\pi R(1+\lVert f\rVert_1)}.
$$

Both terms together are less than $\varepsilon$. Since the bound is independent of $\xi$, this proves that $\widehat f$ is **uniformly continuous** on $\mathbb{R}$.

<div style="text-align: right;">\(\square\)</div>

## Definition

A continuous function $f:\mathbb{R}\to\mathbb{C}$ is **rapidly decreasing** if, for every integer $k\geq0$,

$$
\sup_{x\in\mathbb{R}}\lvert x\rvert^k\lvert f(x)\rvert<\infty.
$$

For $k=0$, the weight is understood to be $1$. This condition says that we can multiply $f$ by any fixed power of $\lvert x\rvert$ and still obtain a bounded function.

It also implies that $\lvert x\rvert^k\lvert f(x)\rvert\to0$ as $\lvert x\rvert\to\infty$. Indeed, the condition for $k+1$ gives a constant $C_{k+1}$ such that

$$
\lvert x\rvert^k\lvert f(x)\rvert\leq\frac{C_{k+1}}{\lvert x\rvert}
\qquad(\lvert x\rvert\geq1).
$$

Rapid decrease implies moderate decrease. If

$$
B_0=\sup_x\lvert f(x)\rvert,\qquad B_2=\sup_x\lvert x\rvert^2\lvert f(x)\rvert,
$$

then

$$
(1+x^2)\lvert f(x)\rvert\leq B_0+B_2.
$$

More generally, every polynomially weighted function $x^mf(x)$ is rapidly decreasing, since its $k$th weighted bound is one of the bounds for $f$. In particular,

$$
\int_{\mathbb{R}}\lvert x\rvert^m\lvert f(x)\rvert dx<\infty
\qquad(m=0,1,2,\ldots).
$$

## Definition

An infinitely differentiable function $f$ belongs to the **Schwartz class** $\mathcal{S}(\mathbb{R})$ if every derivative is rapidly decreasing. Equivalently,

$$
\sup_{x\in\mathbb{R}}\lvert x\rvert^k\lvert f^{(m)}(x)\rvert<\infty
\qquad\text{for all integers }k,m\geq0.
$$

Thus $f$, its derivatives, and their polynomially weighted versions are absolutely integrable. These bounds justify the operations used below.

## Proposition

Let $f\in\mathcal{S}(\mathbb{R})$, $h\in\mathbb{R}$, and $\delta>0$. With the Fourier convention above, we have

$$
\begin{aligned}
\mathcal{F}[f(\cdot+h)](\xi)&=e^{2\pi ih\xi}\widehat f(\xi),\\
\mathcal{F}[f(\cdot)e^{-2\pi ih(\cdot)}](\xi)&=\widehat f(\xi+h),\\
\mathcal{F}[f(\delta\cdot)](\xi)&=\delta^{-1}\widehat f(\xi/\delta),\\
\widehat{f'}(\xi)&=2\pi i\xi\widehat f(\xi),\\
\widehat{-2\pi i(\cdot)f}(\xi)&=\frac{d}{d\xi}\widehat f(\xi).
\end{aligned}
$$

Here, $\mathcal{F}[g]=\widehat g$, and the dot denotes the input variable. For example, $\widehat{xf}(\xi)$ below means the Fourier transform of the function $x\mapsto xf(x)$, evaluated at $\xi$.

The first three identities follow from changes of variables or combining exponentials. The last two explain the relationship between differentiation and multiplication.

*Proof.*

(1) Translation becomes modulation.

Set $u=x+h$, so $x=u-h$. Then

$$
\begin{aligned}
\mathcal{F}[f(\cdot+h)](\xi)
&=\int_{\mathbb{R}}f(x+h)e^{-2\pi ix\xi}dx\\
&=\int_{\mathbb{R}}f(u)e^{-2\pi i(u-h)\xi}du\\
&=e^{2\pi ih\xi}\int_{\mathbb{R}}f(u)e^{-2\pi iu\xi}du\\
&=e^{2\pi ih\xi}\widehat f(\xi).
\end{aligned}
$$

A shift in the original function introduces a phase factor in its Fourier transform. Absolute convergence justifies the substitution on the whole real line.

(2) Modulation becomes translation.

Multiplying two exponentials adds their exponents:

$$
\begin{aligned}
\mathcal{F}[f(\cdot)e^{-2\pi ih(\cdot)}](\xi)
&=\int_{\mathbb{R}}f(x)e^{-2\pi ixh}e^{-2\pi ix\xi}dx\\
&=\int_{\mathbb{R}}f(x)e^{-2\pi ix(\xi+h)}dx\\
&=\widehat f(\xi+h).
\end{aligned}
$$

Thus multiplying $f$ by an oscillation shifts the frequency argument of its transform.

(3) Dilation reverses the frequency scale.

Set $u=\delta x$, so $dx=du/\delta$. Then

$$
\begin{aligned}
\mathcal{F}[f(\delta\cdot)](\xi)
&=\int_{\mathbb{R}}f(\delta x)e^{-2\pi ix\xi}dx\\
&=\frac{1}{\delta}\int_{\mathbb{R}}f(u)e^{-2\pi iu(\xi/\delta)}du\\
&=\frac{1}{\delta}\widehat f(\xi/\delta).
\end{aligned}
$$

If $\delta>1$, the original function is compressed horizontally. Its transform is stretched horizontally, with a compensating factor $1/\delta$.

(4) Differentiation becomes multiplication.

For a finite $R$, integration by parts gives

$$
\begin{aligned}
\int_{-R}^{R}f'(x)e^{-2\pi ix\xi}dx
&=\left[f(x)e^{-2\pi ix\xi}\right]_{-R}^{R}\\
&\quad+2\pi i\xi\int_{-R}^{R}f(x)e^{-2\pi ix\xi}dx.
\end{aligned}
$$

Since $f$ is rapidly decreasing, $f(R)$ and $f(-R)$ tend to zero. More precisely,

$$
\left\lvert\left[f(x)e^{-2\pi ix\xi}\right]_{-R}^{R}\right\rvert
\leq\lvert f(R)\rvert+\lvert f(-R)\rvert\longrightarrow0.
$$

Both $f$ and $f'$ are absolutely integrable, so taking $R\to\infty$ yields

$$
\widehat{f'}(\xi)=2\pi i\xi\widehat f(\xi).
$$

The factor $2\pi i\xi$ comes from differentiating the exponential during integration by parts.

(5) Multiplication becomes differentiation.

We now prove

$$
\widehat f'(\xi)=-2\pi i\widehat{xf}(\xi)=\int_{\mathbb{R}}(-2\pi ix)f(x)e^{-2\pi ix\xi}dx.
$$

Formally, this is what we get by differentiating $e^{-2\pi ix\xi}$ with respect to $\xi$. To justify differentiating the improper integral, we must show that its difference quotient approaches the claimed derivative.

**Step 1: isolate the error.**

For $h\neq0$, define

$$
R_h(x):=\frac{e^{-2\pi ixh}-1}{h}+2\pi ix.
$$

Linearity of absolutely convergent integrals gives

$$
\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}+2\pi i\widehat{xf}(\xi)
=\int_{\mathbb{R}}f(x)e^{-2\pi ix\xi}R_h(x)dx.
$$

Therefore,

$$
\left\lvert\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}+2\pi i\widehat{xf}(\xi)\right\rvert
\leq\int_{\mathbb{R}}\lvert f(x)\rvert\lvert R_h(x)\rvert dx.
$$

Our task is to make the integral on the right small.

**Step 2: predict the useful bound from cancellation.**

Taylor expansion suggests why the error is small. In

$$
e^{-2\pi ixh}=1-2\pi ixh+\frac{(-2\pi ixh)^2}{2}+\cdots,
$$

subtracting $1$ and adding $2\pi ixh$ cancels the constant and linear terms. The numerator of $R_h(x)$ should therefore have size $x^2h^2$, and division by $h$ suggests a bound proportional to $x^2\lvert h\rvert$.

This is a way to discover the estimate. We next prove it exactly, without assuming that an omitted Taylor remainder is small uniformly in $x$.

**Step 3: derive the explicit bound.**

Apply the fundamental theorem of calculus in the parameter $t$:

$$
e^{-2\pi ixh}-1=-2\pi ixh\int_0^1e^{-2\pi ixht}dt.
$$

After dividing by $h$ and adding $2\pi ix$,

$$
R_h(x)=2\pi ix\int_0^1\bigl(1-e^{-2\pi ixht}\bigr)dt.
$$

Use $\lvert1-e^{iu}\rvert\leq\lvert u\rvert$, already proved above:

$$
\begin{aligned}
\lvert R_h(x)\rvert
&\leq2\pi\lvert x\rvert\int_0^1\lvert1-e^{-2\pi ixht}\rvert dt\\
&\leq2\pi\lvert x\rvert\int_0^1 2\pi\lvert x\rvert\lvert h\rvert t\,dt\\
&=2\pi^2x^2\lvert h\rvert.
\end{aligned}
$$

In particular, on a fixed interval $[-R,R]$,

$$
\sup_{\lvert x\rvert\leq R}\lvert R_h(x)\rvert\leq2\pi^2R^2\lvert h\rvert.
$$

The same choice of $h$ works for every $x$ in the interval. This explicitly proves the uniform convergence that a pointwise limit alone would not establish.

**Step 4: obtain a bound for the tails that is independent of $h$.**

For any real $x$ and any $h\neq0$,

$$
\begin{aligned}
\lvert R_h(x)\rvert
&\leq\frac{\lvert e^{-2\pi ixh}-1\rvert}{\lvert h\rvert}+2\pi\lvert x\rvert\\
&\leq2\pi\lvert x\rvert+2\pi\lvert x\rvert\\
&=4\pi\lvert x\rvert.
\end{aligned}
$$

This estimate holds for every nonzero $h$, so the outside part does not require a small-$h$ approximation. Its advantage is that it uses only the integrable weight $\lvert x\rvert\lvert f(x)\rvert$.

**Step 5: combine the bounds and choose the parameters.**

Splitting at $R\geq1$ gives

$$
\begin{aligned}
\int_{\mathbb{R}}\lvert f(x)\rvert\lvert R_h(x)\rvert dx
&=\int_{-R}^{R}\lvert f(x)\rvert\lvert R_h(x)\rvert dx
+\int_{\lvert x\rvert>R}\lvert f(x)\rvert\lvert R_h(x)\rvert dx\\
&\leq2\pi^2R^2\lvert h\rvert\int_{-R}^{R}\lvert f(x)\rvert dx
+4\pi\int_{\lvert x\rvert>R}\lvert x\rvert\lvert f(x)\rvert dx\\
&\leq2\pi^2R^2\lvert h\rvert\lVert f\rVert_1
+4\pi\int_{\lvert x\rvert>R}\lvert x\rvert\lvert f(x)\rvert dx.
\end{aligned}
$$

Given $\varepsilon>0$, choose $R\geq1$ large enough that

$$
\int_{\lvert x\rvert>R}\lvert x\rvert\lvert f(x)\rvert dx<\frac{\varepsilon}{8\pi}.
$$

Such an $R$ exists because $xf(x)$ is absolutely integrable. The outside term is then less than $\varepsilon/2$, independently of $h$.

With this $R$ fixed, choose

$$
0<\lvert h\rvert<\frac{\varepsilon}{4\pi^2R^2(1+\lVert f\rVert_1)}.
$$

Then the inside term is less than $\varepsilon/2$. Therefore the difference quotient approaches the claimed derivative. Every estimate is also independent of $\xi$.

**A useful shortcut for Schwartz functions.** Since $x^2f(x)$ is absolutely integrable, the stronger estimate from Step 3 can also be integrated over the whole line:

$$
\left\lvert\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}+2\pi i\widehat{xf}(\xi)\right\rvert
\leq2\pi^2\lvert h\rvert\int_{\mathbb{R}}x^2\lvert f(x)\rvert dx\longrightarrow0.
$$

Thus, in the Schwartz setting, we can even finish without splitting the integral. The longer proof shows how to proceed with only $f$ and $xf$ absolutely integrable, and explains the inside-versus-outside argument used elsewhere in this post.

<div style="text-align: right;">\(\square\)</div>

## Definition

A **Gaussian** is a function of the form

$$
g_a(x)=e^{-ax^2},\qquad a>0.
$$

## Remark

**Schwartz class.**

Repeated differentiation gives a polynomial times the same Gaussian:

$$
g_a^{(m)}(x)=P_m(x)e^{-ax^2}.
$$

To see this, start with $P_0(x)=1$. If the formula holds for $m$, the product rule gives

$$
P_{m+1}(x)=P_m'(x)-2axP_m(x),
$$

which is again a polynomial.

It remains to explain why the exponential dominates any polynomial. For any nonnegative integer $q$, choose an integer $n$ with $2n>q$. The exponential series, whose terms are nonnegative for $ax^2\geq0$, gives

$$
e^{ax^2}\geq\frac{(ax^2)^n}{n!}.
$$

Hence, for $\lvert x\rvert\geq1$,

$$
\lvert x\rvert^qe^{-ax^2}\leq\frac{n!}{a^n}\lvert x\rvert^{q-2n}\longrightarrow0.
$$

This expression is also bounded on $[-1,1]$ by continuity. Applying the bound to each term of $x^kP_m(x)$ shows that every derivative is rapidly decreasing. Therefore,

$$
g_a\in\mathcal{S}(\mathbb{R}).
$$

**Normalization.**

Let

$$
I=\int_{\mathbb{R}}e^{-\pi x^2}dx.
$$

The integral exists because the Gaussian is rapidly decreasing. We will show that $I=1$.

The familiar idea is to square the one-dimensional integral and switch to polar coordinates. To justify the unbounded regions carefully, first work with bounded squares and disks. Let

$$
Q_R=[-R,R]^2,\qquad D_R=\{(x,y):x^2+y^2\leq R^2\}.
$$

On the square, ordinary iterated integration of a continuous function gives

$$
\iint_{Q_R}e^{-\pi(x^2+y^2)}dxdy=\left(\int_{-R}^{R}e^{-\pi x^2}dx\right)^2.
$$

On the disk, polar coordinates give

$$
\begin{aligned}
\iint_{D_R}e^{-\pi(x^2+y^2)}dxdy
&=\int_0^{2\pi}\int_0^R e^{-\pi r^2}r\,dr\,d\theta\\
&=2\pi\int_0^R e^{-\pi r^2}r\,dr\\
&=1-e^{-\pi R^2}.
\end{aligned}
$$

The factor $r$ is the polar-coordinate area factor. Since

$$
D_R\subseteq Q_R\subseteq D_{\sqrt{2}R},
$$

and the integrand is nonnegative,

$$
1-e^{-\pi R^2}\leq\left(\int_{-R}^{R}e^{-\pi x^2}dx\right)^2\leq1-e^{-2\pi R^2}.
$$

Both outer expressions tend to $1$. Thus $I^2=1$, and $I>0$ gives

$$
\int_{\mathbb{R}}e^{-\pi x^2}dx=1.
$$

<div style="text-align: right;">\(\square\)</div>

## Theorem

Let $g(x)=e^{-\pi x^2}$. Then $\widehat{g}=g$.

*Proof.*

Set

$$
g(x)=e^{-\pi x^2},\qquad F(\xi)=\widehat g(\xi).
$$

The key observation is that differentiating a Gaussian gives a multiple of $x$ times the same Gaussian:

$$
g'(x)=-2\pi xg(x).
$$

Our two differentiation identities translate this into an equation for $F$:

$$
\begin{aligned}
F'(\xi)
&=\widehat{-2\pi i(\cdot)g}(\xi)\\
&=i\widehat{g'}(\xi)\\
&=i(2\pi i\xi)\widehat g(\xi)\\
&=-2\pi\xi F(\xi).
\end{aligned}
$$

To solve this equation, multiply by $e^{\pi\xi^2}$, whose derivative cancels the term on the right:

$$
\begin{aligned}
\frac{d}{d\xi}\bigl(e^{\pi\xi^2}F(\xi)\bigr)
&=e^{\pi\xi^2}\bigl(2\pi\xi F(\xi)+F'(\xi)\bigr)\\
&=0.
\end{aligned}
$$

Thus $e^{\pi\xi^2}F(\xi)$ is constant. At $\xi=0$,

$$
F(0)=\int_{\mathbb{R}}e^{-\pi x^2}dx=1.
$$

Therefore,

$$
\widehat g(\xi)=e^{-\pi\xi^2}=g(\xi).
$$

The calculation avoids directly integrating an oscillating Gaussian. Instead, it shows that the Fourier transform satisfies the same differential equation and initial value as the Gaussian itself.

<div style="text-align: right;">\(\square\)</div>

## Corollary

For $\delta>0$, define

$$
K_\delta(x)=\delta^{-1/2}g(x/\sqrt{\delta})=\frac{1}{\sqrt{\delta}}e^{-\pi x^2/\delta}.
$$

As $\delta$ decreases, the kernel becomes narrower and taller. Its horizontal scale is $\sqrt{\delta}$, and the factor $1/\sqrt{\delta}$ keeps its total integral equal to $1$.

*Proof.*

The dilation identity gives

$$
\begin{aligned}
\widehat{K_\delta}(\xi)
&=\delta^{-1/2}\frac{1}{\delta^{-1/2}}\widehat g\bigl(\xi/\delta^{-1/2}\bigr)\\
&=\widehat g(\sqrt{\delta}\xi)\\
&=e^{-\pi\delta\xi^2}.
\end{aligned}
$$

<div style="text-align: right;">\(\square\)</div>

## Theorem

The Gaussian kernels $\{K_\delta\}_{\delta>0}$ form an approximate identity as $\delta\to0^+$.

A family of absolutely integrable kernels $\{K_\delta\}_{\delta>0}$ is an **approximate identity** as $\delta\to0^+$ if:

1. Each kernel has total integral $1$.
2. There is a constant $C$, independent of $\delta$, such that $\int_{\mathbb{R}}\lvert K_\delta(x)\rvert dx\leq C$.
3. For every fixed $\eta>0$, the absolute mass outside $[-\eta,\eta]$ tends to zero.

The first property preserves constants when averaging. The second controls the total size of the averaging weights. The third says that those weights become concentrated near the origin.

*Proof.*

We verify all three properties for the Gaussian kernels.

**Total integral.** Substitute $u=x/\sqrt{\delta}$, so $dx=\sqrt{\delta}du$:

$$
\begin{aligned}
\int_{\mathbb{R}}K_\delta(x)dx
&=\int_{\mathbb{R}}\frac{1}{\sqrt{\delta}}e^{-\pi x^2/\delta}dx\\
&=\int_{\mathbb{R}}e^{-\pi u^2}du=1.
\end{aligned}
$$

**Uniform bound on the absolute integral.** Since $K_\delta(x)>0$,

$$
\int_{\mathbb{R}}\lvert K_\delta(x)\rvert dx=\int_{\mathbb{R}}K_\delta(x)dx=1.
$$

Thus we may take $C=1$ for every $\delta>0$.

**Concentration near the origin.** For any fixed $\eta>0$, the same substitution gives

$$
\int_{\lvert x\rvert>\eta}K_\delta(x)dx=\int_{\lvert u\rvert>\eta/\sqrt{\delta}}e^{-\pi u^2}du.
$$

The threshold $\eta/\sqrt{\delta}$ tends to infinity as $\delta\to0^+$. We are therefore integrating over tails farther and farther from the origin, so the integral tends to zero.

There is also an explicit bound. For $L>0$, symmetry and $u/L\geq1$ when $u\geq L$ give

$$
\begin{aligned}
\int_{\lvert u\rvert>L}e^{-\pi u^2}du
&=2\int_L^\infty e^{-\pi u^2}du\\
&\leq\frac{2}{L}\int_L^\infty ue^{-\pi u^2}du\\
&=\frac{e^{-\pi L^2}}{\pi L}.
\end{aligned}
$$

Setting $L=\eta/\sqrt{\delta}$ yields

$$
\int_{\lvert x\rvert>\eta}K_\delta(x)dx
\leq\frac{\sqrt{\delta}}{\pi\eta}e^{-\pi\eta^2/\delta}\longrightarrow0.
$$

This proves that the Gaussian kernels form an approximate identity.

<div style="text-align: right;">\(\square\)</div>

## Definition

For $f,g\in\mathcal{S}(\mathbb{R})$, define their **convolution** by

$$
(f*g)(x)=\int_{\mathbb{R}}f(x-t)g(t)dt.
$$

For each fixed $x$, this integral converges absolutely, because $f$ is bounded and $g$ is absolutely integrable:

$$
\int_{\mathbb{R}}\lvert f(x-t)g(t)\rvert dt\leq\lVert f\rVert_\infty\lVert g\rVert_1<\infty,
$$

where $\lVert f\rVert_\infty=\sup_{x\in\mathbb{R}}\lvert f(x)\rvert$.

In particular, $(f*K_\delta)(x)$ is a weighted average of values of $f$ near $x$. As $K_\delta$ concentrates near $t=0$, the values being averaged should approach $f(x)$.

## Corollary

For every $f\in\mathcal{S}(\mathbb{R})$,

$$
\lim_{\delta\to0^+}\sup_{x\in\mathbb{R}}\lvert(f*K_\delta)(x)-f(x)\rvert=0.
$$

*Proof.*

We give both an averaging argument and a quantitative estimate.

**Step 1: obtain a uniform continuity bound.**

Since $f'$ is rapidly decreasing, it is bounded. Set

$$
L=\lVert f'\rVert_\infty<\infty.
$$

For any $x,t\in\mathbb{R}$, the fundamental theorem of calculus gives

$$
f(x-t)-f(x)=-t\int_0^1f'(x-st)ds.
$$

Hence

$$
\lvert f(x-t)-f(x)\rvert\leq L\lvert t\rvert.
$$

This proves uniform continuity on the whole real line, with the same bound for every $x$. Also, with $B=\lVert f\rVert_\infty$,

$$
\lvert f(x-t)-f(x)\rvert\leq2B.
$$

**Step 2: split the average into nearby and distant values.**

Because $\int_{\mathbb{R}}K_\delta(t)dt=1$,

$$
(f*K_\delta)(x)-f(x)=\int_{\mathbb{R}}K_\delta(t)\bigl(f(x-t)-f(x)\bigr)dt.
$$

For any $\eta>0$, positivity of $K_\delta$ and the two bounds above imply

$$
\begin{aligned}
\lvert(f*K_\delta)(x)-f(x)\rvert
&\leq\int_{\lvert t\rvert\leq\eta}K_\delta(t)L\lvert t\rvert dt
+\int_{\lvert t\rvert>\eta}K_\delta(t)2B\,dt\\
&\leq L\eta+2B\int_{\lvert t\rvert>\eta}K_\delta(t)dt.
\end{aligned}
$$

Neither term depends on $x$. Given $\varepsilon>0$, first choose

$$
\eta=\frac{\varepsilon}{2(1+L)}.
$$

Then $L\eta<\varepsilon/2$. With this $\eta$ fixed, concentration of the kernels gives a $\delta_0>0$ such that, whenever $0<\delta<\delta_0$,

$$
\int_{\lvert t\rvert>\eta}K_\delta(t)dt<\frac{\varepsilon}{4(1+B)}.
$$

The distant contribution is then less than $\varepsilon/2$ as well. This proves uniform convergence. Here the order is **first choose the neighborhood size $\eta$, then choose $\delta$ so that almost all the kernel mass lies in that neighborhood**.

Notice that the height of $K_\delta$ is not bounded independently of $\delta$: $K_\delta(0)=\delta^{-1/2}$. What controls the nearby contribution is its total integral, which is $1$.

**An explicit convergence rate.** For these Gaussian kernels, we can integrate the bound $L\lvert t\rvert$ directly:

$$
\begin{aligned}
\lvert(f*K_\delta)(x)-f(x)\rvert
&\leq L\int_{\mathbb{R}}\lvert t\rvert K_\delta(t)dt\\
&=L\sqrt{\delta}\int_{\mathbb{R}}\lvert u\rvert e^{-\pi u^2}du\\
&=2L\sqrt{\delta}\int_0^\infty ue^{-\pi u^2}du\\
&=\frac{L\sqrt{\delta}}{\pi}.
\end{aligned}
$$

Therefore,

$$
\sup_{x\in\mathbb{R}}\lvert(f*K_\delta)(x)-f(x)\rvert
\leq\frac{\lVert f'\rVert_\infty}{\pi}\sqrt{\delta}.
$$

The bound has a direct interpretation: $\lVert f'\rVert_\infty$ controls how quickly $f$ can change, while $\sqrt{\delta}/\pi$ is the average distance from the origin under the Gaussian kernel. Their product controls the averaging error.

<div style="text-align: right;">\(\square\)</div>

## Reference

- Elias M. Stein and Rami Shakarchi, *Fourier Analysis: An Introduction*.
- [Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing).
