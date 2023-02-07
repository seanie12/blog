---
title: "Convolution and Good Kernels"

categories:
  - Fourier Analysis

tags:
  - Convolution
  - Good Kernels
  - Approximation of the identity



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition 1.1
Let $f,g:\mathbb{R}\to\mathbb{C}$ be $2\pi$-periodic functions. The *convolution* $f*g$ of $f$ and $g$ is the function defined by $[-\pi, \pi]$ by
  
$$
\begin{align*}
(f*g)(x) =\frac{1}{2\pi}\int_{-\pi}^\pi f(y) g(x-y)dy
\end{align*}
$$

## Remark
(1) Convolution as weighted average.

(2) Turns out that many important construction can be expressed in terms of convolution. For example, consider $f* D_N$, the Dirichlet kernel

$$
\begin{align*}
(f*D_N)(x) &= \frac{1}{2\pi} \int_{-\pi}^\pi f(y) \sum_{n=-N}^N e^{in(x-y)}dy \\
&=\sum_{n=-N}^N e^{inx}\frac{1}{2\pi} \int_{-\pi}^\pi f(y) e^{-iny}dy  \\
&=\sum_{n=-N}^N \hat{f}(n)e^{inx} \\
&= S_N(f)(x)
\end{align*}
$$

is $N$-th partial sum of the Fourier series. However, $\lim_{N\to\infty}(f*D_N)(x)\neq f(x)$.


## Theorem 2.1 (Basic properties)
Let $f,g,h$ be $2\pi$-periodic **integrable** functions, and $c\in\mathbb{C}$. Then

(1) (Linearity 1) $f*(g+h) = f*g + f*h$ 

(2) (Linearity 2)$(cf)*g= c(f*g)=f*(cg)$

(3) (Commutativity) $f*g = g*f$

(4) (Associativity) $(f*g) * h= f*(g*h)$

(5) (Continuity) $f*g$ is continuous

(6) Multiplication $\widehat{f*g}(n) =\hat{f}(n)\hat{g}(n)$

Note that $L^1(\pi)=\\{f: \text{integrable}\mid \int_{-\pi}^\pi \lvert f(x)\rvert dx <\infty\\}$ with convolution operation is called *Banach algebra*.

