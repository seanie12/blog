---
title: "Cesaro and Abel Summability"

categories:
  - Fourier Analysis

tags:
  - Fejer's Theorem
  - Fejer Kernel
  - Approximation of the identity



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition 1.1
Given a sequence $\\{c_n\\}$, let $s_n:=\sum_{k=0}^nc_k$ be the sequence of partial sums. We define $N$-th *Cesaro mean* $\sigma_N$ of the sequence $\\{s_k\\}$ (a.k.a the $N$-th Cesaro sum of the series $\sum_{k=0}^\infty c_k$) by 


  
$$
\begin{align*}
\sigma_N :=  \frac{s_0 + s_1 + \cdots + s_{N-1}}{N}
\end{align*}
$$

## Remark
If $\lim_{n\to\infty}s_n = s$, then $\lim_{n\to\infty}\sigma_n=s$.

<*Proof*>

Let $\epsilon >0$ be given.  Since $\lim_{n\to\infty}s_n=s$, there exists $N_1\in\mathbb{N}$ such that if $n>N_1$ then $\lvert s_n - s\rvert <\epsilon/2$. With triangular inequality, for $n> N_1$, we get 

$$
\begin{align*}
\lvert \sigma_n - s\vert &= \left \lvert \sum_{k=0}^{n-1} \frac{s_k}{n} - s \right\rvert \\
&\leq \frac{1}{n}\sum_{k=0}^{n-1}\lvert s_k - s\rvert \\
&= \frac{1}{n}(\lvert s_0-s\rvert + \cdots +\lvert s_{N_1-1}-s\rvert) + \frac{1}{n}(\lvert s_{N_1}-s\rvert + \cdots + \lvert s_{n-1}-s\rvert) \\
&< \frac{N_1}{n}\max_{i\in \{0,1, \ldots, N_1-1\}} \lvert s_i-s\rvert + \frac{n-N_1}{n}\frac{\epsilon}{2} \\
&< \frac{N_1}{n}\max_{i\in \{0,1, \ldots, N_1-1\}} \lvert s_i-s\rvert + \frac{\epsilon}{2} \\
\end{align*}
$$

Let $M= \max_{i\in \\{0,1, \ldots, N_1-1\\}} \lvert s_i-s\rvert\in\mathbb{R}$. By Archimedean property, there is $N_2\in\mathbb{N}$ such that $\frac{MN_1}{N_2} < \frac{\epsilon}{2}$. For $n>\max\\{N_1, N_2\\}$, we get 

$$
\begin{align*}
\lvert \sigma_n - s\rvert < \frac{\epsilon}{2} + \frac{\epsilon}{2} =\epsilon.
\end{align*}
$$

$\therefore \sigma_n \to s$ as $n\to\infty$.


$$\tag*{$\square$}$$

## Definition 2.1 (Fejer Kernel)
We define the *Fejer Kernel*, $F_N$, by letting $F_N(x)$ be the $N$-th Cesaro means of $\\{D_K(x)\\}$; i.e.,

$$
\begin{align*}
F_n(x) := \frac{1}{N}\sum_{k=0}^{N-1}D_k(x).
\end{align*}
$$


## Remark
Then consider

$$
\begin{align*}
f*F_N (x) &= f * \left(\frac{1}{N} \sum_{k=0}^{N-1} D_k\right)(x)  \\
&= \frac{1}{N}\sum_{k=0}^{N-1}f* D_k (x) \\
&=\frac{1}{N} \sum_{k=0}^{N-1} S_k(f)(x),
\end{align*}
$$

the average of the first $N$ partial sum of the Fourier series of $f$.

## Lemma 2.2

One has,

$$
\begin{align*}
F_N(x) =\frac{1}{N}\frac{\sin^2(Nx/2)}{\sin^2(x/2)};
\end{align*}
$$

further, the Fejer Kernel is a **good kernel**.

<*Proof*>

$$
\begin{align*}
F_N(x) &= \frac{1}{N}\sum_{k=0}^{N-1} D_k(x)  \\
&= \frac{1}{N} \sum_{k=0}^{N-1} \frac{\sin (x(k+\frac{1}{2}))}{\sin(x/2)} \\
&=\frac{1}{2N\sin^2(x/2)}\sum_{k=0}^{N-1}2\sin(x(k+1/2))\sin(x/2) 
\end{align*}
$$ 

By trigometric identity $\sin\alpha \cdot \sin\beta= \frac{1}{2}(\cos (\alpha-\beta) -\cos (\alpha+\beta))$,

$$
\begin{align*}
\frac{1}{2N\sin^2(x/2)}\sum_{k=0}^{N-1}2\sin(x(k+1/2))\sin(x/2) &=\frac{1}{2N\sin^2(x/2)} \sum_{k=0}^{N-1} (\cos(kx)-\cos ((k+1)x) \\
&= \frac{1- \cos (Nx)}{2N\sin^2(x/2)} \\
&= \frac{1- 1+2\sin^2(Nx/2)}{2N\sin^2(x/2)} \quad ( \because \cos(2\theta) = 1-2\sin^2(\theta)) \\
&=\frac{\sin^2(Nx/2)}{\sin^2(x/2)}.
\end{align*}
$$

(1) 

$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^{\pi} F_N(x) dx &= \frac{1}{2\pi}\int_{-\pi}^{\pi} \frac{1}{N}\sum_{k=0}^{N-1} D_k(x)dx \\
&= \sum_{k=0}^{N-1}\frac{1}{2N\pi}\int_{-\pi}^{\pi} D_k(x) dx \\
&= \sum_{k=0}^{N-1}\frac{1}{2N\pi}\int_{-\pi}^{\pi} \sum_{m=-k}^k e^{imx}dx \\
&=\frac{1}{N}\sum_{k=0}^{N-1} \frac{1}{2\pi} \sum_{m=-k}^k\int_{-\pi}^\pi \mathbf{1}\{m=0 \}dx \\
&= 1
\end{align*}
$$

(2) Since $F_N(x)>0$ for all $x\in[-\pi, \pi]$ and 

$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^{\pi} F_N(x)dx =1,
\end{align*}
$$

$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^{\pi}\lvert F_N(x)\rvert dx = \frac{1}{2\pi}\int_{-\pi}^{\pi}F_N(x)dx = 1
\end{align*}
$$
for all $x\in[-\pi, \pi]$.

(3) Let $\delta>0$ be given. Since $\sin^2 x \leq 1$ and $\sin^2(x/2) \geq \sin^2(\delta/2)$ for $x\in [\delta, \pi]$, 

$$
\begin{align*}
\frac{1}{2\pi}\int_{\delta \leq \lvert x \rvert \leq \pi}\frac{1}{N} \frac{\sin^2(Nx/2)}{\sin^2 (x/2)}dx &\leq \frac{1}{2\pi}\int_{\delta \leq \lvert x \rvert \leq \pi} \frac{1}{N\sin^2(\delta/2)} \\
&=\frac{\pi-\delta}{2\pi} \frac{1}{N\sin^2(\delta/2)} \\
&\to 0 \text{ as } N\to\infty.
\end{align*}
$$

## Theorem 2.3
Let $f$ be integrable function on the circle. If $f$ is continuous at $\theta_0$, then the Fourier series of $f$ is Cesaro summable to $f$ at $\theta_0$. In other words, $\lim_{N\to\infty}f*F_N(\theta_0) = f(\theta_0)$. Note that

$$
\begin{align}
\begin{split}
\sigma_N(f)(x) &:=\frac{1}{N}\sum_{k=0}^{N-1} \sum_{n=-k}^k\hat{f}(n)e^{inx} \\
&= \frac{1}{N}\sum_{k=0}^{N-1}S_k(f)(x) \\
&=\frac{1}{N}\sum_{k=0}^{N-1}f*D_k(x) \\
&= f*\left(\frac{1}{N}\sum_{k=0}^{N-1}D_k \right)(x) \\
&=f*F_N(x).
\end{split}
\label{eq:1}
\end{align}
$$

Further, if $f$ is continuous on the entire circle, then the convergence of the Cesaro sums is uniform. 

<*Proof*>

Since the Fejer kernel $F_N$ is a good kernel, $\lim_{N\to\infty}f*F_N(\theta_0)=f(\theta_0)$ by the previous [theorem](https://seanie12.github.io/blog/fourier%20analysis/convolution-good-kernels/#theorem-32).
$$\tag*{$\square$}$$

## Corollary 2.4
Let $f$ be integrable function on the circle. If $\hat{f}(n)=0$ for all $n\in\mathbb{Z}$, then $f=0$ at all points of continuity of $f$.

<*Proof*>

By  Equation $\ref{eq:1}, f * F_N(x)=0$ for all $N\in\mathbb{N}_0$. Thus, 

$$
\begin{align*}
f(x)=\lim_{N\to\infty}f*F_N(x) = 0.
\end{align*}
$$

$$\tag*{$\square$}$$

## Corollary 2.5
Any continuous function on the circle can be uniformly approximated by trigometric polynomials. Note that it is the periodic analogue of [Stone-Weierstrass approximation Theorem](https://seanie12.github.io/blog/analysis/real-analysis-final/#theorem-stone-weierstrass)

<*Proof*>

It is obvious since

$$
f*F_N(x) = \frac{1}{N}\sum_{k=0}^{N-1} \sum_{n=-k}^k \hat{f}(n) e^{inx}
$$

for all $x\in [-\pi, \pi]$ and $f*F_N\rightrightarrows f$.

$$\tag*{$\square$}$$

## Definition 3.1 (Abel Means and Abel summable)
Let $\sum_{k=0}^\infty c_k$ be a series of complex numbers.

i. We define the *Abel Means* $A(r)$ of the series $\sum c_k$ by 

$$
A(r) := \sum_{k=0}^\infty c_k r^k
$$ 

ii. If for every $0\leq r <1$, the abel means $A(r)$ converges, and

$$
\lim_{r\to 1} A(r) =s
$$

then we say the series $\sum_{k=0}^\infty c_k$ is *Abel summable* to $s$.

## Example
1. Consider $\sum_{k=0}^\infty(-1)^k$. It diverges, but is Abel summable to $s=\frac{1}{2}$.

$$
\begin{align*}
A(r) &= \sum_{k=0}^\infty (-1)^k r^k \\
&= \frac{1}{1+r}.
\end{align*}
$$

2. Consider $\sum_{k=0}^\infty(-1)^k (k+1)$. It diverges, but is Abel summable to $s=\frac{1}{4}$.
 
$$
\begin{align*}
A(r) = \sum_{k=0}^\infty (-1)^k (k+1)r^k = \frac{k+1}{(1+r)^2}.
\end{align*}
$$

## Definition 4.1
Suppose we know the Fourier series of a function $f$:

$$
\begin{align*}
f(\theta)\sim \sum_{n=-\infty}^\infty a_n e^{in\theta}.
\end{align*}
$$

We define the *Abel means* of $A_r(f)(\theta)$ *of the Fourier Series* of the function $f$ by

$$
\begin{align*}
A_r(f)(\theta) = \sum_{n=-\infty}^\infty r^{\lvert n \rvert}a_n e^{in\theta}
\end{align*}
$$

## Remarks
1. If we let $c_0=a_0$ and $c_n = a_n e^{in\theta} + a_{-n}e^{-in\theta}$, then the Abel means of the Fourier series above equals the Abel means of the series $\sum_{k=0}^\infty c_k$.

2.  For integrable $f, \lvert a_n \rvert$   is uniformly bounded in $n\in\mathbb{N}$. So $A_r(f)(\theta)$ converges absolutely. By Weierstrass M-test, it also uniformly converges for each fixed $0\leq r <1$.

$$
\lvert a_n  \rvert= \left\lvert\frac{1}{2\pi}\int_{-\pi}^\pi f(\theta) e^{-in\theta}d\theta \right\rvert \leq \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(\theta)\rvert d\theta \leq B
$$

## Lemma 4.2 (Abel means as a convolution)

$$
\begin{align*}
A_r(f)(\theta) = (f*P_r)(\theta)
\end{align*}
$$

where $P_r(\theta) = \sum_{n=-\infty}^\infty r^{\lvert n \rvert} e^{in\theta}$ is the Poisson Kernel.

<*Proof*>

$$
\begin{align*}
A_r(f)(\theta) &= \sum_{n=-\infty}^\infty r^{\lvert n \rvert} a_ne^{in\theta} \\
&= \sum_{n=-\infty}^\infty r^{\lvert n \rvert}\left( \frac{1}{2\pi}\int_{-\pi}^\pi f(\phi) e^{-in\phi}d\phi\right)e^{in\theta} \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi f(\phi)\sum_{n=-\infty}^\infty r^{\lvert n\rvert} e^{in(\theta-\phi)}d\phi \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f(\phi) P_r(\theta-\phi)d\phi \\
&= (f*P_r)(\theta).
\end{align*}
$$

$$\tag*{$\square$}$$
 
 ## Lemma 4.3
The Poisson Kernel is an approximation of the identity as ($r\uparrow 1$).

<*Proof*>

We know that $P_r(\theta)=\sum_{n=-\infty}^\infty r^{\lvert n \rvert}e^{in\theta}$ converges absolutely and uniformly and already showed that 

$$
\begin{align*}
P_r(\theta) = \frac{1-r^2}{1-2r\cos\theta + r^2} = \frac{1-\lvert \omega \rvert}{\lvert 1 -\omega\rvert^2} > 0
\end{align*}
$$

for $0<r<1$, where $\omega = re^{i\theta}$.

1. 
$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^\pi P_r(\theta)d\theta &= \frac{1}{2\pi}\int_{-\pi}^\pi\sum_{n=-\infty}^\infty r^{\lvert n\rvert} e^{in\theta}d\theta \\
&=\sum_{n=-\infty}^\infty \frac{1}{2\pi}\int_{-\pi}^\pi r^{\lvert n\rvert} e^{in\theta}d\theta \quad (\because \text{ uniform convergence}) \\
&= \sum_{n=-\infty}^\infty \frac{1}{2\pi}\int_{-\pi}^\pi\mathbf{1}\{n=0\}d\theta \\
&=1
\end{align*}
$$

2.  Since $P_r(\theta)>0$ for all $\theta \in [-\pi, \pi]$,

$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^\pi\lvert P_r(\theta) \rvert d\theta= \frac{1}{2\pi}\int_{-\pi}^\pi P_r(\theta)d\theta=1.
\end{align*}
$$

3. Note that $1-2r\cos\theta + r^2=(1-r)^2 + 2r(1-\cos\theta)$. For $\frac{1}{2} \leq r <1$ and $\delta \leq \lvert \theta \rvert \leq \pi$, 

$$
\begin{align*}
1-2r\cos\theta+r^2 &= (1-r)^2 + 2r(1-\cos\theta) \\
&\geq \left(\frac{1}{2}\right)^2 + (1-\cos\theta) \\
&\geq \frac{1}{4} + (1-\cos\delta) =:c_\delta
\end{align*}
$$

which implies that $P_r(\theta) \leq (1-r^2)/ c_\delta$.

Thus,

$$
\lim_{r\to 1^{-}} \frac{1}{2\pi}\int_{\delta \leq \lvert \theta \rvert \leq \pi} P_r(\theta)d\theta =0.
$$


## Corollary 4.4
Let $f$ be integrable function on the circle. Then the Abel means of the Fourier series of $f$ pointwise to $f$ at every point of continuity. If, further, $f$ is continuous on the circle, then the convergence is uniform.

$$
A_r(f) = f * P_r \rightrightarrows f.
$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
