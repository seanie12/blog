---
title: "Continuous but nowhere differentiable function"

categories:
  - Fourier Analysis

tags:
  - continuous
  - non differentiable



toc: true
toc_sticky: true

use_math : true
comments : true

---

## Theorem 1.1
If $0<\alpha <1$, then the function 

$$
\begin{align*}
f_\alpha(x) = \sum_{n=0}^\infty 2^{-n\alpha}e^{i2^nx}
\end{align*}
$$

is continuous but nowhere differentiable.

The continuity is clear because of the absolute convergence of the series. In other words, we can use [Corollary 8.3.2](https://seanie12.github.io/blog/analysis/uniform-convergence-continuity/#corollary-832) to prove continuity of $f_\alpha$.

Recall that we have a couple of ways of summing the Fourier series. With Dirichlet kernel $D_N$,

$$
\begin{align*}
g*D_N (x)&= \frac{1}{2\pi}\int_{-\pi}^\pi g(y) \sum_{n=-N}^N e^{in(x-y)}dy \\
&=\sum_{n=-N}^N e^{inx}\frac{1}{2\pi} \int_{\pi}^\pi g(y) e^{-iny}dy \\
&=\sum_{n=-N}^N \hat{g}(n) e^{inx} \\
&=S_N(g)(x).
\end{align*}
$$

Or with Fejer kernel $F_N$,

$$
\begin{align*}
g*F(x) &=g*(\frac{1}{N} \sum_{k=0}^{N-1} D_k)(x) \\
&=\frac{1}{N} \sum_{k=0}^{N-1} (f*D_k)(x) \\
&=\frac{1}{N} \sum_{k=0}^{N-1}S_k(f)(x) \\
&=\sigma_N(f)(x).
\end{align*}
$$

If we look at the partial sum $S_N$ on the Fourier coefficient side, we see that 

$$
\begin{align*}
\widehat{S_N(g)}(n) &= \widehat{g*D_N}(n) \\
&= \hat{g}(n) \cdot \hat{D}_N(n)
\end{align*}
$$

where 

$$
\begin{align*}
\hat{D}_N(n) &= \frac{1}{2\pi} \int_{-\pi}^\pi \sum_{k=-N}^N e^{ikx}e^{-inx}dx \\
&=\frac{1}{2\pi} \sum_{k=-N}^N \int_{-\pi}^\pi e^{i(k-n)x}dx \\
&=\begin{cases}
1 \quad \text{ if } \lvert n \rvert \leq N \\
0 \quad \text{ otherwise}
\end{cases}
\end{align*}
$$

Fourier coefficient of Cesaro sum,

$$
\begin{align*}
\widehat{\sigma_N(g)}(n) &= \widehat{g* F_N }(n) \\
&=\hat{g}(n) \hat{F}(n) \\
&= \hat{g}(n) \widehat{\frac{1}{N} \sum_{k=0}^{N-1}D_k}(n) \\
&= \hat{g}(n) \frac{1}{N}\left(\hat{D_0}(n) + \hat{D_1}(n) + \cdots + \hat{D}_{N-1}(n)\right) \\
&=\begin{cases}
\hat{g}(n) \frac{1}{N} \left(N - \lvert n\rvert\right) \quad \text{ if } \lvert n \rvert \leq N \\
0 \quad \text{ otherwise}
\end{cases}
\end{align*}
$$

Equivalently, 

$$
\begin{align*}
\sigma_N(g)(x)&=\frac{1}{N}\left(S_0(g)(x) + S_1(g)(x) + \cdots S_{N-1}(g)(x) \right) \\
&=\frac{1}{N} \sum_{l=0}^{N-1}\sum_{k=-l}^l \hat{g}(k) e^{ikx} \\
&= \frac{1}{N} \sum_{\lvert n \rvert \leq N}(N-\lvert n \rvert) \hat{g}(n) e^{inx}\\
&=\frac{1}{N} \sum_{\lvert n \rvert \leq N}(1- \lvert n \rvert /N)\hat{g}(n)e^{inx}
\end{align*}  
$$

$$\tag*{$\square$}$$
## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
