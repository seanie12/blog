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
&=\Im\left(e^{i(n+1)x/2}\frac{2i\sin(nx/2)}{2i\sin(x/2)} \right) \\
&=\Im\left((\cos((n+1)x/2) + i\sin((n+1)x/2))\frac{\sin(nx/2)}{\sin(x/2)} \right)  \\
&= \sin((n+1)x/2)\frac{\sin(inx/2)}{\sin(ix/2)}.
\end{align*}
$$

Thus, $\left\lvert \sum_{k=1}^n \sin(kx)\right\rvert \leq 1$ for all $n\in\mathbb{N}$. By Dirichlet-test, the Fourier series converges at every $x$.

$$\tag*{$\square$}$$

## Example 1

Consider the series 

$$
\begin{align*}
\sum_{n=-\infty}^{-1}\frac{e^{in\theta}}{n}.
\end{align*}
$$

Suppose the above is the Fourier series of some Riemann integrable function $f$. In that case, if we consider the Abel means at $0$, we get

$$
\begin{align*}
\lvert A_r(f)(0) \rvert = \left\lvert \sum_{n=-\infty}^{-1} \frac{r^{\lvert n \rvert}e^{0}}{n} \right\rvert  = \sum_{n=1}^\infty \frac{r^n}{n}
\end{align*}
$$

For $r\in(0,1]$, define a function $g(r) :=\sum_{n=1}^\infty r^n/n$.  The function is monotone increasing function but not bounded above since $g(1)=\infty$. Thus $\lim_{r\to1^-}g(r)=\infty$, i.e., $\lvert A_r(f)(0)\rvert \to \infty$ as $r\to1^-$.

However, note that $A_r(f)(\theta)=f*P_r(\theta)$. It implies that $A_r(f)(\theta)$ should be bounded since 

$$
\begin{align*}
\lvert A_r(f)(0) \lvert &= \left\lvert \frac{1}{2\pi}\int_{-\pi}^{\pi}f(0)P_r(-\theta) d\theta\right\rvert \\
&= \left\lvert \frac{1}{2\pi}\int_{-\pi}^{\pi}f(0)P_r(\theta) d\theta\right\rvert \quad( \because P_r(\theta) = 	\frac{1-r^2}{1-2r\cos\theta+r^2} ) \\
&\leq \frac{1}{2\pi} \int_{-\pi}^\pi \lvert f(0)\rvert P_r(\theta)d\theta \\
&\leq \sup_\theta \lvert f(\theta)\rvert .
\end{align*}
$$

It is a contradiction. Thus the above is not the Fourier series of aRiemann integrable function.

## Example 2 (A continuous function whose Fourier series diverges at a point)

Let 

$$
\begin{align*}
f_N(\theta) = \sum_{1\leq \lvert n \rvert \leq N} \frac{e^{in\theta}}{n} \text{ and } \tilde{f}_N(\theta) = \sum_{-N\leq n \leq -1} \frac{e^{in\theta}}{n}.
\end{align*}
$$

We want to show that 

(1) $\lvert \tilde{f}_N(0)\rvert \geq c\log N$

(2) $f_N(\theta)$ is uniformly bounded in $N$ and $\theta$.

Since 

$$
\begin{align*}
\sum_{n=1}^N \frac{1}{n} \geq \sum_{n=1}^{N-1} \int_{n}^{n+1} \frac{dx}{x}dx=\int_{1}^N \frac{dx}{x} = \log N,
\end{align*}
$$

we show that 

$$
\begin{align*}
\lvert \tilde{f}_N(0) \rvert= \sum_{n=1}^N 1/n \geq \log N.
\end{align*}
$$ 

To prove (2), we need following lemmas.

## Lemma 1.1 

Let $\sum_{n=1}^\infty c_n$ be an infinite series. If 

(1) the Abel means $A_r = \sum_{n=1}^\infty r^n c_n$ are bounded as $r\to 1^-$, and

(2) $c_n=O(1/n)$

then the partial sum sequences $S_N=\sum_{n=1}^Nc_n$ is bounded.

<*Proof*>

For 

$$
\begin{align*}
S_N - A_r = \sum_{n=1}^N(c_r - r^nc_n) - \sum_{n=N+1}^\infty r^n c_n,
\end{align*}
$$

we want to bound 

$$
\begin{align*}
\lvert S_N - A_r\rvert \leq \sum_{n=1}^N \lvert c_n \rvert \lvert 1-r^n\rvert + \sum_{n=N+1}^\infty \lvert r^n \rvert \lvert c_n\rvert.
\end{align*}
$$

Given following observations

(i) $(1-r^n) = (1-r)(1+r+\cdots + r^{n-1}) \leq n(1-r)$ for $r\in (0,1]$.

(ii) Since $c_n=O(1/n)$, there is $M_1 >0$ and $N\in\mathbb{N}$ such that $\lvert c_n \rvert \leq M_1/n$ for all $n>N$.  So $\lvert c_n\rvert \leq M_1 /n \leq M_1/N$ for all $n\geq N+1$.

(iii) That is $n\lvert c_n \rvert$ is bounded, so there is $M_2>0$ such that $n\lvert c_n \rvert <M_2$ for all $n\in\mathbb{N}$.

Using those observations, we can continue to bound 

$$
\begin{align*}
\lvert S_N - A_r\rvert &\leq \sum_{n=1}^N \lvert c_n \rvert \lvert 1-r^n\rvert + \sum_{n=N+1}^\infty \lvert r^n \rvert \lvert c_n\rvert \\
&\leq M_2\sum_{n=1}^N(1-r) + \frac{M_1}{N} \sum_{n=N+1}^\infty r^n \\
&\leq M_2N(1-r) + \frac{M_1}{N} \frac{1}{1-r} \\
&\leq MN(1-r) + \frac{M}{N}\frac{1}{1-r} \quad (M:=\max\{M_1, M_2\}) .
\end{align*}
$$

If w take $r=1-1/N$, then we get 

$$
\begin{align*}
\lvert S_n - A_r\rvert \leq 2M.
\end{align*}
$$

Since the $A_r$ are bounded for large enough $N$, we see that $S_N$ are also bounded.

$$\tag*{$\square$}$$

## Corollary
$f_N(\theta)=\sum_{1\leq \lvert n \rvert \leq N} \frac{e^{in\theta}}{n}$ is uniformly bounded in $N$ and $\theta$.

<*Proof*>

$f_N(\theta)$ is the partial sum of the Fourier series $\sum_{n\neq 0}\frac{e^{in\theta}}{n}$, the Fourier series of the sawtooth function which is odd in $\theta$ and equals to$f(\theta)=i(\pi-\theta)$ for $\theta \in (0,\pi)$. Since $A_r(f) = f*P_r$ and $f$ is bounded,

$$
\begin{align*}
\lvert A_r(f)(\theta)\rvert &= \left\lvert\frac{1}{2\pi}\int_{-\pi}^\pi f(\theta-\phi)P_r(\theta )d\phi \right\rvert \\
&\leq \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(\theta-\phi) \rvert P_r(\theta)d\phi \\
&\leq \sup_\theta \lvert f(\theta)\rvert 
\end{align*}
$$

the Abel means are bounded.

Clearly $n\lvert c_n \rvert = \lvert e^{in\theta} + e^{-in\theta}\rvert =2\lvert \cos(n\theta)\rvert \leq 2$. Thus $c_n$ is $O(1/n)$. 

$\therefore S_N(f)(\theta)$ is uniformly bounded in $N$ and $\theta$.

$$\tag*{$\square$}$$

## Lemma 1.2
Recall that

$$
\begin{align*}
f_N(\theta) = \sum_{1\leq \lvert n \rvert \leq N} \frac{e^{in\theta}}{n} \text{ and } \tilde{f}_N(\theta) = \sum_{-N\leq n \leq -1} \frac{e^{in\theta}}{n}.
\end{align*}
$$

are trigonometric polynomials of degree $N$. We define frequency-shifted version of $f_N$ and $\tilde{f}_N$, 

$$
\begin{align*}
P_N(\theta) = e^{i2N\theta}f_N(\theta) \text{ and } \tilde{P}_N(\theta)=e^{i2N\theta}\tilde{f}_N(\theta),
\end{align*}
$$

which are trigonometric polynomials of degree $3N$ and $2N-1$, respectively.  Then if we consider the partial sums of $P_N$, we see 

$$
\begin{align*}
S_M(P_N) &= \begin{cases} P_N & \quad \text{if } M \geq 3N \\
\tilde{P}_N & \text{if } M = 2N \\
0 & \text{if } M <N
\end{cases}
\end{align*}
$$

Moreover, choose any convergent positive series $\sum a_k$ and sequence of integers $\\{N_k\\}$ such that 

(i) $N_{k+1} > 3N_k$

(ii) $\lim_{k\to\infty} \alpha_k \log N_k=\infty$.

For example. $\alpha_k=1/k^2$ and $N_k=3^{2^k}$. Define a function


$$
\begin{align*}
f(\theta) = \sum_{k=1}^\infty \alpha_k P_{N_k}(\theta).
\end{align*}
$$

Since $\lvert P_N(\theta)\rvert = \lvert f_N(\theta)\rvert$, which is uniformly bounded by lemma1, the above series converges uniformly to a continuous periodic function. Moreover, 


$$
\begin{align*}
\lvert S_{2N_m}(f)(0)\rvert \geq c\alpha_m \log N_m + O(1)
\end{align*}
$$

<*Proof*>

$$
\begin{align*}
S_{2N_m}(f)(0) &= S_{2N_m}(\sum_k \alpha_k P_{N_k})(0) \\
&=\sum_{n=-2N_m}^{2N_m} \left(\frac{1}{2\pi}\int_{-\pi}^\pi \left(\sum_{k=1}^\infty a_kP_{N_k}(\theta)\right)e^{-in\theta}d\theta \right) e^0 \\
&=\sum_{n=-2N_m}^{2N_m} \left( \sum_{k=1}^\infty \alpha_k \left( \frac{1}{2\pi}\int_{-\pi}^\pi P_{N_k}(\theta)e^{-in\theta}d\theta\right)\right) e^0 \\
&=\sum_{k=1}^\infty \alpha_k\left( \sum_{n=-2N_m}^{2N_m}\left(\frac{1}{2\pi}\int_{-\pi}^\pi P_{N_k}(\theta)e^{-in\theta}d\theta \right)e^0 \right) \\
&=\sum_{k=1}^\infty \alpha_k S_{2N_m}(P_{N_k})(0) \\
&= \alpha_m S_{2N_m}(P_{N_m})(0) + \sum_{m<k} \alpha_k S_{2N_m}(P_{N_k})(0) + \sum_{m>k} \alpha_k S_{2N_m}(P_{N_k})(0) \\
&=\alpha_m \tilde{P}_{N_m}(0) + 0+ \sum_{m>k} \alpha_k P_{N_k}(0) \\
&=\alpha_m\tilde{f}_{N_m}(0) + \sum_{m>k} \alpha_k P_{N_k}(0)
\end{align*} 
$$

by lemma 1.2. 

Since $f_{N_k}(\theta)$ is uniformly bounded and $\lvert f_{N_k}(\theta)\rvert = \lvert P_{N_k}(\theta)\rvert$, 

$$
\begin{align*}
\left\lvert \sum_{m>k} \alpha_k P_{N_k}(0) \right\rvert \leq B \left\lvert \sum_{m>k} \alpha_k \right\rvert \leq BA.
\end{align*}
$$

But $\lvert \tilde{f}_{N_m}(0)\rvert \geq c \log N$. 

$\therefore \lvert S_{2N_m}(f)(0) \rvert \geq c \alpha_m \log N_m + O(1)$, i.e., the partial sums of the Fourier series diverges at $0$ despite the function being continuous everywhere.

$$\tag*{$\square$}$$
## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
