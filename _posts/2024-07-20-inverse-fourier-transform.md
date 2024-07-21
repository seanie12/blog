---
title: "Fourier Inversion Formula"

categories:
  - Fourier Analysis

tags:
  - Fourier inversion 
  - Inverse Fourier transform
  - Plancherel's theorem



toc: true
toc_sticky: true

use_math : true
comments : true

---

## Proposition (Multiplication formula) 

Let $f,g\in\mathcal{S}(\mathbb{R})$. Then

$$
\begin{align*}
\int_{-\infty}^\infty f(x)\hat{g}(x) dx = \int_{-\infty}^\infty \hat{f}(y) d(y) dy
\end{align*}
$$

## Remark
Recall Fubini's theorem: if $F(x,y)$ is a continuous function on $\mathbb{R}^2$ satisfying the condition

$$
\begin{align*}
\lvert F(x,y) \rvert \leq \frac{A}{(1+x^2)(1+y^2)},
\end{align*}
$$

then 

$$
\begin{align*}
\int_{-\infty}^\infty \int_{-\infty}^\infty F(x,y) dxdy = \int_{-\infty}^\infty \int_{-\infty}^\infty F(x,y) dy dx.
\end{align*}
$$

<*Proof*>

Let $F(x,y)= f(x)g(y)e^{-2\pi i xy}$. Then $F$ satisfies the decay conditions for Fubini's theorem. Applying the theorem to the function, 

$$
\begin{align*}
\int_{-\infty}^\infty f(x)\hat{g}(x) dx = \int_{-\infty}^\infty\int_{-\infty}^\infty f(x) g(y) e^{-2\pi i xy}dy dx = \int_{-\infty}^\infty\int_{-\infty}^\infty g(y) f(x) e^{-2\pi i xy} dx dy = \int_{-\infty}^\infty g(y) \hat{f}(y) dy
\end{align*}
$$

$$\tag*{$\square$}$$

## Theorem (Fourier inversion)

If $f\in\mathcal{S}(\mathbb{R})$, then 

$$
\begin{align*}
f(x) = \int_{-\infty}^\infty \hat{f}(\xi) e^{2\pi i x \xi} d\xi
\end{align*}
$$

<*Proof*>

First prove for $x=0$. Take $G_\delta(x)$ to be *what should be the inverse Fourier transform of $K_\delta(x)=\delta^{-1/2} \exp(-\pi x^2/\delta)$*, i.e.,

$$
\begin{align*}
G_\delta(x) = e^{-\pi\delta x^2}, \widehat{G_\delta}(\xi)=K_\delta(\xi).
\end{align*}
$$

By the multiplication formula,

$$
\begin{align}
\int_{-\infty}^\infty f(x) K_\delta(x) dx = \int_{-\infty}^\infty \hat{f}(\xi) G_\delta (\xi) d\xi.
\label{eq:1}
\end{align}
$$

Since 

$$
\begin{align*}
f*K_\delta(x) &= \int_{-\infty}^\infty f(x-t) K_\delta (t) dt \\
&=\int_{-\infty}^\infty f(y) K_\delta (y-x) dy
\end{align*}
$$

by the change of variable and uniform convergence of $f*K_\delta$,  the left hand side of Equation $\ref{eq:1}$

$$
\begin{align*}
f*K_\delta (0)=\int_{-\infty}^\infty f(y) K_\delta(y)dy \to f(0)
\end{align*}
$$

as $\delta \to 0^+$. Clearly, right hand side of Equation $\ref{eq:1}$,

$$
\begin{align*}
\int_{-\infty}^\infty \hat{f}(\xi) e^{-\pi \delta \xi^2}d\xi \to \int_{-\infty}^\infty \hat{f}(\xi) d\xi \text{ as } \delta \to 0.
\end{align*}
$$

Thus,

$$
\begin{align*}
f(0)= \int_{-\infty}^\infty \hat{f}(\xi) d\xi.
\end{align*}
$$

For general $x\in\mathbb{R}$, let $F(y) = f(y+x)$. By the [Proposition](https://seanie12.github.io/blog/fourier%20analysis/fourier-transform-1/#proposition), 

$$
\begin{align*}
f(x) = F(0) = \int_{-\infty}^\infty \hat{F}(\xi) d\xi = \int_{-\infty}^\infty \hat{f}(\xi) e^{2\pi i x\xi} d\xi.
\end{align*}
$$

$$\tag*{$\square$}$$

## Definition (Inverse Fourier transform)
Given $g\in\mathcal{S}(\mathbb{R})$, we define the **inverse Fourier transform**   $\check{g}$ of $g$ by

$$
\begin{align*}
\mathcal{F}^*(g)(x) = \check{g}(x) = \int_{-\infty}^\infty g(\xi) e^{2\pi ix\xi}d\xi
\end{align*}
$$

## Theorem 
Let $\mathcal{F}: \mathcal{S}(\mathbb{R}) \to\mathcal{S}(\mathbb{R})$ be Fourier transform and let $\mathcal{F}^*: \mathcal{S}(\mathbb{R}) \to\mathcal{S}(\mathbb{R})$ be inverse Fourier transform. Then Fourier transform is a bijective mapping on the Schwartz spzce.

<*Proof*>

By Fourier inversion,  

$$
\begin{align*}
(\mathcal{F}^* \circ \mathcal{F})(g)(y)&=\int_{-\infty}^\infty \left( \int^\infty_{-\infty}g(y)e^{-2\pi iy\xi}dy\right)e^{2\pi i y\xi}d\xi  \\
&=\int_{-\infty}^\infty \hat{g}(\xi) e^{2\pi iy\xi}d\xi \\
&=g(y)
\end{align*}
$$

for all $y\in\mathbb{R}$. Thus $\mathcal{F}^* \circ \mathcal{F}=I$.

Since $\mathcal{F}(g)(y) = \mathcal{F}^*(g)(-y)$,  by setting  $\zeta=-\xi$,

$$
\begin{align*}
(\mathcal{F}\circ \mathcal{F}^*)(g)(y)&=\int_{-\infty}^\infty\left(\int_{-\infty}^\infty g(y)e^{2\pi i y \xi}dy \right)e^{-2\pi i y \xi}d\xi  \\
&=\int_{-\infty}^\infty \left(\int_{-\infty}^\infty g(y)e^{-2\pi i y \zeta}dx\right)e^{2\pi i y\zeta} d\xi \\
&=\int_{-\infty}^\infty \hat{g}(\zeta) e^{2\pi i y\zeta} d\zeta \\
&=(\mathcal{F}^* \circ \mathcal{F}) (g)(y).
\end{align*}
$$

Thusm $F^*$ ins the inverse of the Fourier transform on $\mathcal{S}(\mathbb{R})$.

$$\tag*{$\square$}$$

## Plancherel's theorem
For any $f,g\in\mathcal{S}(\mathbb{R})$, we have

$$
\begin{align*}
\lVert \hat{f}\rVert_{L^2(\mathbb{R})} = \lVert f\rVert_{L^2(\mathbb{R})}
\end{align*}
$$

<*Proof*>

By the multiplication theorem, we get

$$
\begin{align*}
\int_{-\infty}^\infty f(x)\hat{g}(x) dx = \int_{-\infty}^\infty \hat{f}(y)g(y).
\end{align*}
$$

Define $g$ such that $\hat{g}=\bar{f}$, i.e., $g=\check{\bar{f}}$.

$$
\begin{align*}
\int_{-\infty}^\infty f(x)\bar{f}(x) dx &= \int_{-\infty}^\infty \hat{f}(y) \check{\bar{f}}(y) dy \\
&=\int_{-\infty}^\infty \hat{f}(y) \bar{\hat{f}}(y) dy 
\end{align*}
$$

$$\tag*{$\square$}$$
## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
