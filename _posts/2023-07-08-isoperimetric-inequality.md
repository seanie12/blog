---
title: "Fourier series and the isoperimetric inequality"

categories:
  - Fourier Analysis

tags:
  - Curve
  - Isoperimetric Inequality





toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 1.1
A $\mathscr{C}^1$ mapping 

$$
\begin{align*}
\gamma: [a,b] \to \mathbb{R}^2,
\end{align*}
$$

such that $\gamma^\prime(s)\neq 0$, is called a **parameterized curve**. We call the image of $\gamma$ a **curve** (denoted by $\Gamma$). If $\gamma$ is 1-1, we call $\Gamma$ simple' if $\gamma(a) = \gamma(b)$ we call $\Gamma$ closed.




## Definition 1.2 
We define the **length** of the curve $\Gamma$, parameterized by $\gamma(s)= (x(s), y(s))$ by

$$
\begin{align*}
\ell = \int^b_a \lVert \gamma^\prime(s) \rVert ds = \int^b_a (x^\prime(s)^2 + y^\prime(s)^2)^{1/2} ds
\end{align*}
$$



## Definition 1.3
Let $s: [c,d] \to [a,b]$ be a bijective and $\mathscr{C}^1$ mapping. Then we call 


$$
\begin{align*}
\eta(t) := \gamma \circ s (t)
\end{align*}
$$
a **re-parameterization** of $\Gamma$. If, further, 

$$
\begin{align*}
\lVert \eta^\prime(t) \rVert = 1 \text{ for all } t \in [c,d]
\end{align*}
$$

we call $\eta$ the **arclength parameterization** of $\Gamma$.


## Remark
The length of the curve $\gamma: [a,b]\to \mathbb{R}^2$ is independent of parameterization.

By the change of variable, 
$$
\begin{align*}
\int_a^b \lVert \gamma^\prime(s) \rVert ds = \int^d_c \lvert s^\prime(t) \rvert \rVert  \gamma^\prime(s(t))\lVert  dt =
\int^d_c\lVert \eta^\prime(t)\rVert dt
\end{align*}
$$


## Lemma 1
Let $\gamma: [a,b] \to \mathbb{R}^2$ be a $\mathscr{C}^1$ parametric curve. Now define a function $s: [a,b] \to [0,\ell]$ by 

$$
\begin{align*}
t(s)= \int_a^s \lVert \gamma^\prime (x)\lVert dx.
\end{align*}
$$

Then it is bijective function. Now consider a reparameterization $\eta(t) := \gamma \circ s (t)$, where $s(t)$ is the inverse of $t(s)$. Since 

$$
\begin{align*}
\lVert \eta^\prime(t) \rVert = \lvert s^\prime(t) \rvert \lVert \gamma^\prime (s(t)) \rVert &=\frac{1}{\lvert t^\prime(s(t))\rvert} \lVert \gamma^\prime (s(t))\rVert = \lVert \gamma^\prime (s(t))\rVert^{-1} \lVert \gamma^\prime(s(t))\rVert =1,
\end{align*}
$$

$\eta(t)$ is an arclength parameterization.

$$\tag*{$\square$}$$
## Theorem 2.1
Let $\Gamma \subset \mathbb{R}^2$ be a simple closed curve. Let $\ell$ denote the length of $\Gamma, A$ the area of its enclosed region. Then


$$
\begin{align*}
A \leq \frac{\ell^2}{2\pi},
\end{align*}
$$

with equality if and only if $\Gamma$ is a circle. 

<*Proof*>
Observe that we can rescale the problem by a factor of $\delta>0$. Consider the mappling of the plane $\mathbb{R}^2$ to $\mathbb{R}^2$ where $(x,y)\mapsto (\delta x, \delta y).$ Then the length $\ell$ is scaled to $\delta \ell$ and its area $A$ is rescaled to $\delta^2 A$. But the inequality does not change

$$
\begin{align*}
\delta^2 A \leq \frac{\delta ^2\ell^2}{2\pi} \iff A \leq \frac{\ell^2}{2\pi}.
\end{align*}
$$

By taking $\delta = 2\pi / \ell$, if suffices to prove that if $\ell=2\pi$ then $A \leq \pi$, with equality only if $\Gamma$ is a circle. Note that any curve admits a parameterization by arc	length by Lemma 1. Then, after a possible additional translation,  we can consider a parameterization $\gamma(s)=(x(s), y(s))$ of $\Gamma$ by arc-length defined on $[0,\ell]=[0,2\pi]$. Then 

$$
\begin{align*}
\frac{1}{2\pi} \int_0^{2\pi} x^\prime(s)^2 + y^\prime(s)^2 ds &=1 \\
\lVert x^\prime \rVert^2_{L^2}  + \lVert y^\prime \rVert^2_{L^2} &=1
\end{align*}
$$

$x(s)$ and $y(s)$ are $2\pi$ periodic  functions, and have Fourier coefficients $\\{a_n\\}$ and $\\{b_n\\}$, respectively. Their derivatives have coefficients $\\{ina_n\\}$ and $\\{inb_n\\}$, respectively. 

Using [Parseval's identity](https://seanie12.github.io/blog/fourier%20analysis/L2-recovery/#corollary-12-parsevals-identity) on the above, we get 

$$
\begin{align*}
1 &=\lVert \\{ina_n\\}\rVert^2_{\ell^2} + \lVert \\{inb_n\\}\rVert^2_{\ell_2} \\
&=\sum_{n=-\infty}^\infty  ina_n (-in\overline{a}_n) +\sum_{n=-\infty}^\infty inb_n(-in\overline{b}_n) \\ &= \sum_{n=-\infty}^\infty \lvert n\rvert^2(\lvert a_n\rvert^2 + \lvert b_n \rvert^2) 
\end{align*}
$$ 


Now, the area is by definition

$$
\begin{align*}
A = \frac{1}{2} 2\pi \left\lvert \frac{1}{2\pi}\int_a^b x(s) y^\prime(s) - y(s)x^\prime(s) ds\right\rvert
\end{align*}
$$

Using Parseval Again,  we get

$$
\begin{align*}
A &= \pi \left\lvert \sum_{n\in\mathbb{Z}} a_n(-in\overline{b}_n) - b_n(-in\overline{a}_n) \right\rvert \\
&\leq \pi \sum_{n\in\mathbb{Z}} \lvert n \rvert \lvert a_n\overline{b}_n-\overline{a}_nb_n \rvert 
\end{align*}
$$

Since 

$$
\begin{align*}
\lvert a_n \overline{b}_n - \overline{a}_n b_n \rvert  \leq \lvert a_n\overline{b}_n\rvert + \lvert \overline{a}_n b_n\rvert = 2\lvert a_n b_n\rvert \leq \lvert a_n \rvert^2 + \lvert b_n \rvert^2,
\end{align*}
$$

we bound the area 

$$
\begin{align}
A &\leq \pi \sum_{n\in\mathbb{Z}} \lvert n \rvert \lvert a_n\overline{b}_n-\overline{a}_nb_n \rvert  \label{eq:6}\\
&\leq \pi\sum_{n\in\mathbb{Z}} \lvert n \rvert^2 (\lvert a_n \rvert^2+ \lvert b_n \rvert^2) =\pi \label{eq:7}.
\end{align}
$$


$$\tag*{$\square$}$$
## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
