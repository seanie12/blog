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

## Theorem 
If $0<\alpha <1$, then the function 

$$
\begin{align*}
f_\alpha(x) = \sum_{n=0}^\infty 2^{-n\alpha}e^{i2^nx}
\end{align*}
$$

is continuous but nowhere differentiable.

The continuity is clear because the series are absolutely convergent by Weistrass M-test. In other words, we can use [Corollary 8.3.2](https://seanie12.github.io/blog/analysis/uniform-convergence-continuity/#corollary-832) to prove continuity of $f_\alpha$.

Recall that we have a couple of ways of summing the Fourier series. With Dirichlet kernel $D_N$,

$$
\begin{align*}
g*D_N (x)&= \frac{1}{2\pi}\int_{-\pi}^\pi g(y) \sum_{n=-N}^N e^{in(x-y)}dy \\
&=\sum_{n=-N}^N e^{inx}\frac{1}{2\pi} \int_{\pi}^\pi g(y) e^{-iny}dy \\
&=\sum_{n=-N}^N \hat{g}(n) e^{inx} \\
&=S_N(g).
\end{align*}
$$

Or with Fejer kernel $F_N$,

$$
\begin{align*}
g*F(x) &=g*(\frac{1}{N} \sum_{k=0}^{N-1} D_k)(x) \\
&=\frac{1}{N} \sum_{k=0}^{N-1} (f*D_k)(x) \\
&=\frac{1}{N} \sum_{k=0}^{N-1}S_k(f)(x) \\
&=\sigma_N(f).
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

## Definition 
We define the **delayed means** $\Delta_N(g)$ of the Fourier series of $g$ by

$$
\begin{align*}
\Delta_N(g) &:= 2\sigma_{2N}(g) - \sigma_N(g)\\
&=2g* F_{2N} - g* F_N \\
&=g*(2F_{2N}-F_N)
\end{align*}
$$

On the Fourier coefficient side, it is  easy to see that 

$$
\begin{align*}
\widehat{\Delta_N(g)}(n) = \begin{cases}
\hat{g}(n) \quad \text{ if } \lvert n \rvert \leq N \\
\hat{g}(n)2(1-\frac{\lvert n \rvert}{N}) \quad \text{ if } N < \lvert n\rvert  \leq 2N \\
0 \quad \text{ if } \lvert n \rvert > 2N
\end{cases}
\end{align*}
$$



For delayed means 

$$
\begin{align*}
\Delta_N(g) &= 2\sigma_{2N}(g) - \sigma_N(g) \\
&= 2 \frac{1}{2N} \sum_{\lvert n \rvert \leq 2N} (2N - \lvert n \rvert) \hat{g}(n) e^{inx} - \frac{1}{N}\sum_{\lvert n \rvert \leq N}(N-\lvert n \rvert) \hat{g}(n) e^{inx} \\
&=\frac{1}{N} \sum_{\lvert n \rvert \leq N} N \hat{g}(n)e^{inx} + \sum_{N< \lvert n \rvert \leq 2N} (2- \lvert n \rvert /N)e^{inx}\\
&=S_N(g) + \sum_{N < \lvert n \rvert \leq 2N}(2-\lvert n \rvert / N)\hat{g}(n) e^{inx}.
\end{align*}
$$

Recall that our function is 

$$
\begin{align*}
f_\alpha(x) = \sum_{n=0}^\infty 2^{-n\alpha}e^{i2^nx}
\end{align*}
$$

with $\alpha \in (0,1)$. The Fourier coefficient of $f_\alpha$ is 

$$
\begin{align*}
\hat{f_\alpha}(n) = \begin{cases}
2^{-n\alpha} \quad \text{ if } n=2^k \\
0 \quad \text{ otherwise}.
\end{cases}
\end{align*}
$$

## Observation
For fixed $N$, if we choose the largest $k$ for which $2^k \leq N$, then

$$
\begin{align*}
\Delta_{2^k}(f_\alpha) &= \sum_{\lvert n \rvert \leq 2^k}\hat{f_\alpha}(n) e^{inx} + \sum_{2^k < \lvert n\rvert \leq 2^{k+1}} (2-\lvert n\rvert /2^k) \hat{f_\alpha}(n) e^{inx} \\
&= \sum_{\lvert n \rvert \leq 2^k}\hat{f_\alpha}(n) e^{inx} \\
&= S_N(f_\alpha)
\end{align*}
$$

since there is no $\hat{f_\alpha}(n)$ for $2^k < \lvert n \rvert < 2^{k+1}$ by the definition of $f_\alpha$.

## Dumb Observation
If $2N= 2^n$, then 

$$
\begin{align*}
\Delta_{2N}(f) - \Delta_N(f) = 2^{-n\alpha} e^{i2^nx}.
\end{align*}
$$

Our contradiction will be obtained as follows. By the above dumb observation, for any point $x_0$,

$$
\begin{align*}
\left\lvert \Delta_{2N}(f)^\prime(x_0) - \Delta_N(f)^\prime (x_0)\right\rvert &= \lvert i2^n 2^{-n\alpha}e^{i2^nx_0}\rvert \\
&=2^{n(1-\alpha)} = (2N)^{1-\alpha}.
\end{align*}
$$

However, with the following lemma,

## Lemma
Let $g$ be continuous. If $g$ is differentiable at $x_0$, then 

$$
\begin{align*}
\sigma_N(g)^\prime(x_0) = O(\log N).
\end{align*}
$$

Since $\Delta_N(g)^\prime (x_0)= 2\sigma_{2N}(g)^\prime (x_0) - \sigma(g)^\prime (x_0) = O(\log N)$, we would have a contradiction if we assume $f_\alpha$ is differentiable at $x_0$.

<*Proof of lemma*>

$$
\begin{align*}
\sigma_N(g)^\prime(x_0) &= (F_N * g)^\prime (x_0) \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi F^\prime (x_0-t) g(t) dt  \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi F^\prime (t) g(x_0 - t) dt. \\ 
\end{align*}
$$

The second equality holds because of [Leibniz rule](https://en.wikipedia.org/wiki/Leibniz_integral_rule).

Since $F_N$ is $2\pi$ periodic function,

$$
\begin{align*}
 \int_{-\pi}^\pi F^\prime_N(t) dt = F_N(\pi) - F_N(-\pi) =0.
\end{align*}
$$

Using this fact , we get 

$$
\begin{align*}
\sigma_N(g)^\prime(x_0) = \frac{1}{2\pi} \int_{-\pi}^\pi F^\prime_N(t) [g(x_o-t) - g(x_0)]dt.
\end{align*}
$$

Using the differentiability of $g$ at $x_0$,

$$
\begin{align*}
\lvert \sigma_N(g)^\prime(x_0)\rvert \leq C \int_{-\pi}^\pi F^\prime_N(t) \lvert t\rvert dt.
\end{align*}
$$

## FACTS
$$
\begin{align*}
\lvert F^\prime_N(t) \rvert &\leq AN^2 \\
\lvert F^\prime_N(t) \rvert &\leq \frac{A}{\lvert t \rvert^2}
\end{align*}
$$

Putting it all together, we see


$$
\begin{align*}
\lvert \sigma_N(g)^\prime(x_0)\rvert &\leq C \int_{-\pi}^\pi F^\prime_N(t) \lvert t\rvert dt \\
&\leq C \int_{\lvert t \rvert \geq \frac{1}{N}} \lvert F^\prime_N(t) \rvert \lvert t \rvert dt + C \int_{\lvert t \rvert \leq \frac{1}{N}} \lvert F^\prime_N(t) \rvert \lvert t \rvert dt  \\
&=O(\log N)
\end{align*}
$$


$$\tag*{$\square$}$$


## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
