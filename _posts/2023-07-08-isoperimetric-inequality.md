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
\ell = \int^a_b \lVert \gamma^\prime(s) \rVert ds = \int^a_b (x^\prime(s)^2 + y^\prime(s)^2)^{1/2} ds
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
\int_b^a \lVert \gamma^\prime(s) \rVert ds = \int^c_d \lvert s^\prime(t) \rvert \rVert  \gamma^\prime(s(t))\lVert  dt =
\int^c_d\lVert \eta^\prime(t)\rVert dt
\end{align*}
$$




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
\delta^2 A \leq \frac{\delta ^2\ell^2}{2\pi}.
\end{align*}
$$

By taking $\delta = 2\pi / \ell$, if suffices to prove that if $\ell=2\pi$ then $A \leq \pi$, with equality only if $\Gamma$ is a circle. 


$$\tag*{$\square$}$$



$$\tag*{$\square$}$$
## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
