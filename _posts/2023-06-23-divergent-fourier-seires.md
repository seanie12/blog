---
title: "Fourier series need not converge at points of continuity"

categories:
  - Fourier Analysis

tags:
  - Sawtooth Function
  - Divergent Fourier series of continuous function





toc: true
toc_sticky: true

use_math : true
comments : true

---

## Exercise 2.8
Verify that $\frac{1}{2i}\sum_{n\neq 0} \frac{e^{inx}}{n}$ is the Fourier series of the $2\pi$-periodic **sawtooth** function, defined by $f(0)=0$, and 

$$
\begin{align*}
f(x) = \begin{cases}
-\frac{\pi}{2}-\frac{x}{2} \quad &\text{if } x \in (-\pi, 0) \\
\frac{\pi}{2}-\frac{x}{2} & \text{if } x \in (0, \pi).
\end{cases}
\end{align*}
$$

Show that the series converges for every $x$. 


<*Proof*>
For each $n\in\mathbb{Z} \setminus \\{0\\}$, Fourier coefficient is 

$$
\begin{align*}
\hat{f}(n) &= \frac{1}{2\pi}\left(\int_{-\pi}^0 (-\frac{\pi}{2}-\frac{x}{2})e^{-inx}dx + \int_0^{\pi}(\frac{\pi}{2}-\frac{x}{2})e^{-inx}dx  \right) \\
&=-\frac{1}{4}\int_{-\pi}^0e^{-inx}dx + \frac{1}{4}\int_0^{\pi}e^{-inx}dx - \frac{1}{4\pi}\int_{-\pi}^{\pi}xe^{inx}dx \\
&=-\frac{1}{4}[-\frac{1}{in}e^{-inx}]^0_{-\pi} + \frac{1}{4}[-\frac{1}{in}e^{-inx}]^{\pi}_0 - \frac{1}{4\pi}([-\frac{x}{in}e^{-inx}]_{-\pi}^{\pi} - \int_{-\pi}^{\pi}-\frac{1}{in}e^{-inx}dx) \\
&=\frac{1}{4in}[\cos(-nx)+i\sin(-nx)]_{-\pi}^0 -\frac{1}{4in}[\cos(-nx)+i\sin(-nx)]_{0}^\pi + \frac{1}{4\pi in}[x\cos(-nx)+ix\sin(-nx)]_{-\pi}^\pi \\
&=\frac{1}{4in}(\cos0 - \cos(n\pi)) - \frac{1}{4in}(\cos(-n\pi)-\cos0) + \frac{1}{4\pi in}(2\pi\cos(n\pi)) \\
&=\frac{1}{2in}(1- \cos(n\pi)) + \frac{1}{2in}\cos(n\pi) \\
&=\frac{1}{2in}.
\end{align*}
$$

Now we want to show that $\frac{1}{2i}\sum_{n\neq 0} \frac{e^{inx}}{n}$ pointwise converges. Let $a_n=e^{inx}-e^{-inx}$ and  $b_n= \frac{1}{n}$. Then $b_n$ is monotone decreasing sequence and $\lim_{n\to\infty}b_n=0$. By [Dirichlet-test](https://seanie12.github.io/blog/analysis/dirichlet-test/#theorem-722-dirichlet-test), it suffices to show a sequence  of partial sum $A_n=\sum_{k=1}^n a_n$ is bounded. 

Let $x\in [-\pi, \pi] \setminus \\{0 \\}$ be given. 

$$
\begin{align*}
\left\lvert \sum_{k=1}^n e^{ikx}-e^{-ikx} \right\rvert &= \left\lvert \sum_{k=1}^n \cos(kx)+i\sin(kx)-\cos(-kx) -i\sin(-kx) \right\rvert \\
&= \left\lvert \sum_{k=1}^n 2i\sin(kx) \right\rvert \\
\end{align*}
$$ 

Now we show that $\sum_{k=1}^n \sin(kx)$ is bounded for all $n\in\mathbb{N}$.  By Euler formula,

$$
\begin{align*}
\sum_{k=1}^n\sin(kx) &= \Im\left({\sum_{k=1}^n e^{ikx}}\right) \\
&=\Im\left(e^{ix}\frac{e^{inx}-1}{e^{ix}-1} \right) \\
&=\Im\left(e^{ix}\frac{e^{inx/2}(e^{inx/2}-e^{-inx/2})}{e^{ix/2}(e^{ix/2}-e^{-ix/2})} \right) \\
&=\Im\left(e^{i(n+1)x/2}\frac{2\sin(inx/2)}{2\sin(ix/2)} \right) \\
&=\Im\left((\cos((n+1)x/2) + i\sin((n+1)x/2))\frac{\sin(inx/2)}{\sin(ix/2)} \right)  \\
&= \sin((n+1)x/2)\frac{\sin(inx/2)}{\sin(ix/2)}.
\end{align*}
$$

Thus, $\left\lvert \sum_{k=1}^n \sin(kx)\right\rvert \leq 1$ for all $n\in\mathbb{N}$.
$$\tag*{$\square$}$$



## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
