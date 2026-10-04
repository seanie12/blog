---
title: "Continuous but nowhere differentiable function"

categories:
  - Fourier Analysis

tags:
  - continuous
  - non differentiable

toc: true
toc_sticky: true

use_math: true
comments: true
---

## Theorem

If $0<\alpha<1$, then the function

$$
f_\alpha(x)=\sum_{n=0}^{\infty}2^{-n\alpha}e^{i2^n x}
$$

is continuous but nowhere differentiable.

The series converges absolutely and uniformly by the Weierstrass M-test, since

$$
\left\lvert2^{-n\alpha}e^{i2^n x}\right\rvert=2^{-n\alpha},
\qquad
\sum_{n=0}^{\infty}2^{-n\alpha}<\infty.
$$

Thus, $f_\alpha$ is a continuous $2\pi$-periodic function. We will prove that it is nowhere differentiable using delayed means of its Fourier series.

Recall two ways of summing the Fourier series of a continuous $2\pi$-periodic function $g$. We use the normalized convolution and Fourier coefficients

$$
\begin{aligned}
(g*h)(x)&:=\frac{1}{2\pi}\int_{-\pi}^{\pi}g(y)h(x-y)\,dy,\\
\widehat g(n)&:=\frac{1}{2\pi}\int_{-\pi}^{\pi}g(y)e^{-iny}\,dy.
\end{aligned}
$$

With the Dirichlet kernel $D_N(x)=\sum_{n=-N}^{N}e^{inx}$, we obtain

$$
\begin{aligned}
(g*D_N)(x)
&=\frac{1}{2\pi}\int_{-\pi}^{\pi}g(y)\sum_{n=-N}^{N}e^{in(x-y)}\,dy\\
&=\sum_{n=-N}^{N}e^{inx}\frac{1}{2\pi}\int_{-\pi}^{\pi}g(y)e^{-iny}\,dy\\
&=\sum_{n=-N}^{N}\widehat g(n)e^{inx}\\
&=S_N(g)(x).
\end{aligned}
$$

With the Fejér kernel

$$
F_N:=\frac{1}{N}\sum_{k=0}^{N-1}D_k,
\qquad N\geq 1,
$$

we obtain the Cesàro mean

$$
\begin{aligned}
(g*F_N)(x)
&=\frac{1}{N}\sum_{k=0}^{N-1}(g*D_k)(x)\\
&=\frac{1}{N}\sum_{k=0}^{N-1}S_k(g)(x)\\
&=\sigma_N(g)(x).
\end{aligned}
$$

On the Fourier coefficient side,

$$
\widehat{S_N(g)}(n)
=\widehat g(n)\widehat D_N(n),
$$

where

$$
\begin{aligned}
\widehat D_N(n)
&=\frac{1}{2\pi}\sum_{k=-N}^{N}\int_{-\pi}^{\pi}e^{i(k-n)x}\,dx\\
&=\begin{cases}
1,& \lvert n\rvert\leq N,\\
0,& \lvert n\rvert>N.
\end{cases}
\end{aligned}
$$

Similarly,

$$
\begin{aligned}
\widehat{\sigma_N(g)}(n)
&=\widehat g(n)\widehat F_N(n)\\
&=\widehat g(n)\frac{1}{N}\sum_{k=0}^{N-1}\widehat D_k(n)\\
&=\begin{cases}
\left(1-\dfrac{\lvert n\rvert}{N}\right)\widehat g(n),& \lvert n\rvert\leq N,\\
0,& \lvert n\rvert>N.
\end{cases}
\end{aligned}
$$

Equivalently,

$$
\begin{aligned}
\sigma_N(g)(x)
&=\frac{1}{N}\sum_{l=0}^{N-1}\sum_{n=-l}^{l}\widehat g(n)e^{inx}\\
&=\frac{1}{N}\sum_{\lvert n\rvert\leq N}(N-\lvert n\rvert)\widehat g(n)e^{inx}\\
&=\sum_{\lvert n\rvert\leq N}\left(1-\frac{\lvert n\rvert}{N}\right)\widehat g(n)e^{inx}.
\end{aligned}
$$

The terms with $\lvert n\rvert=N$ have weight zero, so including them in the summation does not change its value.

## Definition

We define the *delayed mean* $\Delta_N(g)$ by

$$
\begin{aligned}
\Delta_N(g)
&:=2\sigma_{2N}(g)-\sigma_N(g)\\
&=2g*F_{2N}-g*F_N\\
&=g*(2F_{2N}-F_N).
\end{aligned}
$$

Its Fourier coefficients are

$$
\widehat{\Delta_N(g)}(n)
=\begin{cases}
\widehat g(n),& \lvert n\rvert\leq N,\\
2\left(1-\dfrac{\lvert n\rvert}{2N}\right)\widehat g(n),& N<\lvert n\rvert\leq 2N,\\
0,& \lvert n\rvert>2N.
\end{cases}
$$

Indeed,

$$
\begin{aligned}
\Delta_N(g)(x)
&=2\sum_{\lvert n\rvert\leq 2N}\left(1-\frac{\lvert n\rvert}{2N}\right)\widehat g(n)e^{inx}\\
&\quad-\sum_{\lvert n\rvert\leq N}\left(1-\frac{\lvert n\rvert}{N}\right)\widehat g(n)e^{inx}\\
&=\sum_{\lvert n\rvert\leq N}\widehat g(n)e^{inx}\\
&\quad+\sum_{N<\lvert n\rvert\leq 2N}\left(2-\frac{\lvert n\rvert}{N}\right)\widehat g(n)e^{inx}\\
&=S_N(g)(x)\\
&\quad+\sum_{N<\lvert n\rvert\leq 2N}\left(2-\frac{\lvert n\rvert}{N}\right)\widehat g(n)e^{inx}.
\end{aligned}
$$

Recall that

$$
f_\alpha(x)=\sum_{k=0}^{\infty}2^{-k\alpha}e^{i2^k x}.
$$

By uniform convergence and orthogonality of the exponentials, its Fourier coefficients are

$$
\widehat f_\alpha(n)
=\begin{cases}
2^{-k\alpha},& n=2^k\text{ for some integer }k\geq 0,\\
0,& \text{otherwise}.
\end{cases}
$$

## Observation

Fix an integer $N\geq 1$, and choose the largest integer $k\geq 0$ for which $2^k\leq N$. Then $2^k\leq N<2^{k+1}$, and

$$
\begin{aligned}
\Delta_{2^k}(f_\alpha)(x)
&=\sum_{\lvert n\rvert\leq 2^k}\widehat f_\alpha(n)e^{inx}\\
&\quad+\sum_{2^k<\lvert n\rvert\leq 2^{k+1}}
\left(2-\frac{\lvert n\rvert}{2^k}\right)\widehat f_\alpha(n)e^{inx}\\
&=\sum_{\lvert n\rvert\leq 2^k}\widehat f_\alpha(n)e^{inx}\\
&=S_N(f_\alpha)(x).
\end{aligned}
$$

The second sum is zero because the Fourier coefficients vanish for $2^k<\lvert n\rvert<2^{k+1}$, while the multiplier $2-\lvert n\rvert/2^k$ vanishes at $\lvert n\rvert=2^{k+1}$. In particular, although $\widehat f_\alpha(2^{k+1})\neq 0$, its contribution to this sum is zero. The final equality follows because there are no nonzero Fourier coefficients with $2^k<\lvert n\rvert\leq N$.

## A second observation

If $2N=2^n$ for an integer $n\geq 1$, then

$$
\begin{aligned}
\Delta_{2N}(f_\alpha)(x)-\Delta_N(f_\alpha)(x)
&=S_{2N}(f_\alpha)(x)-S_N(f_\alpha)(x)\\
&=2^{-n\alpha}e^{i2^n x}.
\end{aligned}
$$

Differentiating these trigonometric polynomials gives, for every $x_0\in\mathbb{R}$,

$$
\begin{aligned}
\left\lvert\Delta_{2N}(f_\alpha)'(x_0)-\Delta_N(f_\alpha)'(x_0)\right\rvert
&=\left\lverti2^n2^{-n\alpha}e^{i2^n x_0}\right\rvert\\
&=2^{n(1-\alpha)}\\
&=(2N)^{1-\alpha}.
\end{aligned}
$$

We will obtain a contradiction from the following lemma.

## Lemma

Let $g$ be continuous and $2\pi$-periodic. If $g$ is differentiable at $x_0$, then

$$
\sigma_N(g)'(x_0)=O(\log N)
\qquad\text{as }N\to\infty.
$$

*Proof.* Since $F_N$ is a trigonometric polynomial, we may differentiate the kernel under the integral. A change of variables, using periodicity, gives

$$
\begin{aligned}
\sigma_N(g)'(x_0)
&=\frac{1}{2\pi}\int_{-\pi}^{\pi}F_N'(x_0-t)g(t)\,dt\\
&=\frac{1}{2\pi}\int_{-\pi}^{\pi}F_N'(t)g(x_0-t)\,dt.
\end{aligned}
$$

Because $F_N$ is $2\pi$-periodic,

$$
\int_{-\pi}^{\pi}F_N'(t)\,dt
=F_N(\pi)-F_N(-\pi)=0.
$$

Therefore,

$$
\sigma_N(g)'(x_0)
=\frac{1}{2\pi}\int_{-\pi}^{\pi}F_N'(t)\bigl(g(x_0-t)-g(x_0)\bigr)\,dt.
$$

Differentiability at $x_0$ implies that $\lvert g(x_0-t)-g(x_0)\rvert\leq C\lvert t\rvert$ for sufficiently small $\lvert t\rvert$. Since $g$ is bounded, increasing $C$ makes this bound valid for all $\lvert t\rvert\leq\pi$. Hence

$$
\left\lvert\sigma_N(g)'(x_0)\right\rvert
\leq C\int_{-\pi}^{\pi}\lvert F_N'(t)\rvert\,\lvert t\rvert\,dt.
$$

We use the following kernel bounds to estimate this integral.

## Kernel bounds

There is a constant $A>0$, independent of $N$ and $t$, such that

$$
\lvert F_N'(t)\rvert\leq AN^2,
\qquad
\lvert F_N'(t)\rvert\leq\frac{A}{\lvert t\rvert^2}
\quad(0<\lvert t\rvert\leq\pi).
$$

The first bound follows from the finite Fourier expansion of $F_N$. For the second, when $\lvert t\rvert\geq 1/N$, differentiate

$$
F_N(t)=\frac{1}{N}\left(\frac{\sin(Nt/2)}{\sin(t/2)}\right)^2
$$

and use $\lvert \sin(t/2)\rvert\geq \lvert t\rvert/\pi$ to obtain

$$
\lvert F_N'(t)\rvert
\leq C\left(\frac{1}{\lvert t\rvert^2}+\frac{1}{N\lvert t\rvert^3}\right)
\leq\frac{A}{\lvert t\rvert^2}.
$$

For $0<\lvert t\rvert<1/N$, the first bound implies the second after increasing $A$ if necessary.

Splitting the integral at $\lvert t\rvert=1/N$, we obtain, for $N\geq 2$,

$$
\begin{aligned}
\left\lvert\sigma_N(g)'(x_0)\right\rvert
&\leq C\int_{\lvert t\rvert\leq 1/N}\lvert F_N'(t)\rvert\,\lvert t\rvert\,dt\\
&\quad+C\int_{1/N<\lvert t\rvert\leq\pi}\lvert F_N'(t)\rvert\,\lvert t\rvert\,dt\\
&\leq CAN^2\int_{\lvert t\rvert\leq 1/N}\lvert t\rvert\,dt\\
&\quad+CA\int_{1/N<\lvert t\rvert\leq\pi}\frac{1}{\lvert t\rvert}\,dt\\
&=O(1)+O(\log N)\\
&=O(\log N).
\end{aligned}
$$

This proves the lemma. $\square$

To finish the proof of the theorem, suppose that $f_\alpha$ is differentiable at some point $x_0$. The lemma gives

$$
\begin{aligned}
\Delta_N(f_\alpha)'(x_0)
&=2\sigma_{2N}(f_\alpha)'(x_0)-\sigma_N(f_\alpha)'(x_0)\\
&=O(\log N).
\end{aligned}
$$

Consequently,

$$
\left\lvert\Delta_{2N}(f_\alpha)'(x_0)-\Delta_N(f_\alpha)'(x_0)\right\rvert
=O(\log N).
$$

But for $N=2^{n-1}$, the same quantity equals $(2N)^{1-\alpha}$. Since $1-\alpha>0$,

$$
\frac{(2N)^{1-\alpha}}{\log N}\longrightarrow\infty,
$$

which is a contradiction. Thus, $f_\alpha$ is nowhere differentiable. $\square$

## References

- Elias M. Stein and Rami Shakarchi, *Fourier Analysis: An Introduction*.
- [Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing).
