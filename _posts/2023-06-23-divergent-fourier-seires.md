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

For each $n\in\mathbb{Z} \setminus \\{0\\}$, the Fourier coefficient is 

$$
\begin{align*}
\hat{f}(n) &= \frac{1}{2\pi}\left(\int_{-\pi}^0 (-\frac{\pi}{2}-\frac{x}{2})e^{-inx}dx + \int_0^{\pi}(\frac{\pi}{2}-\frac{x}{2})e^{-inx}dx  \right) \\
&=-\frac{1}{4}\int_{-\pi}^0e^{-inx}dx + \frac{1}{4}\int_0^{\pi}e^{-inx}dx - \frac{1}{4\pi}\int_{-\pi}^{\pi}xe^{-inx}dx \\
&=-\frac{1}{4}\left[-\frac{1}{in}e^{-inx}\right]^0_{-\pi} + \frac{1}{4}\left[-\frac{1}{in}e^{-inx}\right]^{\pi}_0 \\
&\quad - \frac{1}{4\pi}\left(\left[-\frac{x}{in}e^{-inx}\right]_{-\pi}^{\pi} - \int_{-\pi}^{\pi}-\frac{1}{in}e^{-inx}dx\right) \\
&=\frac{1}{4in}(1-\cos(n\pi)) + \frac{1}{4in}(1-\cos(n\pi)) + \frac{1}{2in}\cos(n\pi) \\
&=\frac{1}{2in}.
\end{align*}
$$

Now we want to show that $\frac{1}{2i}\sum_{n\neq 0} \frac{e^{inx}}{n}$ converges pointwise. Pairing the positive and negative frequencies,

$$
\begin{align*}
\sum_{n\neq 0}\frac{e^{inx}}{n}
&=\sum_{n=1}^{\infty}\left(\frac{e^{inx}}{n}+\frac{e^{-inx}}{-n}\right)\\
&=\sum_{n=1}^{\infty}\frac{e^{inx}-e^{-inx}}{n}.
\end{align*}
$$

Let $a_n=e^{inx}-e^{-inx}$ and $b_n=1/n$. Then $b_n$ is a monotone decreasing sequence and $\lim_{n\to\infty}b_n=0$. By [Dirichlet-test](https://seanie12.github.io/blog/analysis/dirichlet-test/#theorem-722-dirichlet-test), it suffices to show that the sequence of partial sums $A_n=\sum_{k=1}^n a_k$ is bounded. 

Let $x\in [-\pi, \pi] \setminus \\{0\\}$ be given. 

$$
\begin{align*}
\left\lvert \sum_{k=1}^n \left(e^{ikx}-e^{-ikx}\right) \right\rvert
&= \left\lvert \sum_{k=1}^n \left(\cos(kx)+i\sin(kx)-\cos(-kx)-i\sin(-kx)\right) \right\rvert \\
&= \left\lvert \sum_{k=1}^n 2i\sin(kx) \right\rvert.
\end{align*}
$$ 

Now we show that $\sum_{k=1}^n \sin(kx)$ is bounded for all $n\in\mathbb{N}$. By Euler's formula,

$$
\begin{align*}
\sum_{k=1}^n\sin(kx) &= \Im\left(\sum_{k=1}^n e^{ikx}\right) \\
&=\Im\left(e^{ix}\frac{e^{inx}-1}{e^{ix}-1} \right) \\
&=\Im\left(e^{ix}\frac{e^{inx/2}(e^{inx/2}-e^{-inx/2})}{e^{ix/2}(e^{ix/2}-e^{-ix/2})} \right) \\
&=\Im\left(e^{i(n+1)x/2}\frac{2i\sin(nx/2)}{2i\sin(x/2)} \right) \\
&=\Im\left((\cos((n+1)x/2) + i\sin((n+1)x/2))\frac{\sin(nx/2)}{\sin(x/2)} \right) \\
&=\sin((n+1)x/2)\frac{\sin(nx/2)}{\sin(x/2)}.
\end{align*}
$$

Thus,

$$
\begin{align*}
\left\lvert \sum_{k=1}^n \sin(kx)\right\rvert
\leq \frac{1}{\lvert\sin(x/2)\rvert}
\end{align*}
$$

for all $n\in\mathbb{N}$. For each fixed $x\neq0$, the right-hand side is finite and independent of $n$. By the Dirichlet test, the Fourier series converges for every $x\neq0$. At $x=0$, every paired term is zero, so the series also converges there.

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
\lvert A_r(f)(0) \rvert
&= \left\lvert \sum_{n=-\infty}^{-1} \frac{r^{\lvert n \rvert}}{n} \right\rvert \\
&= \sum_{n=1}^\infty \frac{r^n}{n}.
\end{align*}
$$

For $r\in(0,1)$, define a function $g(r):=\sum_{n=1}^\infty r^n/n$. Since

$$
\begin{align*}
g(r)=-\log(1-r),
\end{align*}
$$

we have $\lim_{r\to1^-}g(r)=\infty$, i.e., $\lvert A_r(f)(0)\rvert \to \infty$ as $r\to1^-$.

However, note that $A_r(f)(\theta)=f*P_r(\theta)$. It implies that $A_r(f)(0)$ should be bounded since 

$$
\begin{align*}
\lvert A_r(f)(0) \rvert
&= \left\lvert \frac{1}{2\pi}\int_{-\pi}^{\pi}f(-\theta)P_r(\theta) d\theta\right\rvert \\
&\leq \frac{1}{2\pi} \int_{-\pi}^\pi \lvert f(-\theta)\rvert P_r(\theta)d\theta \\
&\leq \sup_\theta \lvert f(\theta)\rvert
\frac{1}{2\pi}\int_{-\pi}^{\pi}P_r(\theta)d\theta \\
&= \sup_\theta \lvert f(\theta)\rvert .
\end{align*}
$$

Since a Riemann integrable function on $[-\pi,\pi]$ is bounded, this is a contradiction. Thus the above is not the Fourier series of a Riemann integrable function.

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
\sum_{n=1}^N \frac{1}{n} \geq \sum_{n=1}^{N-1} \int_{n}^{n+1} \frac{1}{x}dx=\int_{1}^N \frac{dx}{x} = \log N,
\end{align*}
$$

we have

$$
\begin{align*}
\lvert \tilde{f}_N(0) \rvert
= \sum_{n=1}^N \frac{1}{n}
\geq \log N.
\end{align*}
$$ 

To prove (2), we need the following lemma.

## Lemma 1.1 

Let $\sum_{n=1}^\infty c_n$ be an infinite series. If 

(1) the Abel means $A_r = \sum_{n=1}^\infty r^n c_n$ are bounded as $r\to 1^-$, and

(2) $c_n=O(1/n)$,

then the partial sum sequence $S_N=\sum_{n=1}^Nc_n$ is bounded.

<*Proof*>

We have

$$
\begin{align*}
S_N - A_r
&= \sum_{n=1}^N(c_n-r^nc_n) - \sum_{n=N+1}^\infty r^n c_n.
\end{align*}
$$

Thus,

$$
\begin{align*}
\lvert S_N - A_r\rvert \leq \sum_{n=1}^N \lvert c_n \rvert \lvert 1-r^n\rvert + \sum_{n=N+1}^\infty \lvert r^n \rvert \lvert c_n\rvert.
\end{align*}
$$

We use the following observations.

(i) $(1-r^n) = (1-r)(1+r+\cdots + r^{n-1}) \leq n(1-r)$ for $r\in (0,1)$.

(ii) Since $c_n=O(1/n)$, there exist $M_1>0$ and $N_0\in\mathbb{N}$ such that $\lvert c_n\rvert \leq M_1/n$ for all $n>N_0$.

(iii) For the finitely many indices $1\leq n\leq N_0$, define

$$
\begin{align*}
M_0:=\max_{1\leq n\leq N_0} n\lvert c_n\rvert.
\end{align*}
$$

Then, if we set

$$
\begin{align*}
M_2:=\max\{M_0,M_1\},
\end{align*}
$$

we have

$$
\begin{align*}
n\lvert c_n\rvert\leq M_2
\end{align*}
$$

for every $n\in\mathbb{N}$. Thus the sequence $\\{n\lvert c_n\rvert\\}_{n=1}^\infty$ is bounded.
Using these observations, we can continue to bound

$$
\begin{align*}
\lvert S_N - A_r\rvert &\leq \sum_{n=1}^N \lvert c_n \rvert \lvert 1-r^n\rvert + \sum_{n=N+1}^\infty \lvert r^n \rvert \lvert c_n\rvert \\
&\leq M_2\sum_{n=1}^N(1-r) + \frac{M_2}{N} \sum_{n=N+1}^\infty r^n \\
&\leq M_2N(1-r) + \frac{M_2}{N}\frac{1}{1-r}.
\end{align*}
$$

If we take $r=1-1/N$ for $N\geq2$, then

$$
\begin{align*}
\lvert S_N-A_r\rvert
&\leq M_2 + M_2\\
&\leq 2M_2.
\end{align*}
$$

Since $r=1-1/N\to1^-$ as $N\to\infty$ and the $A_r$ are bounded for $r$ sufficiently close to $1$, we see that $S_N$ is bounded for all sufficiently large $N$. The remaining finitely many partial sums are also bounded.

$$\tag*{$\square$}$$

## Corollary
$f_N(\theta)=\sum_{1\leq \lvert n \rvert \leq N} \frac{e^{in\theta}}{n}$ is uniformly bounded in $N$ and $\theta$.

<*Proof*>

$f_N(\theta)$ is the partial sum of the Fourier series $\sum_{n\neq 0}\frac{e^{in\theta}}{n}$, which is the Fourier series of the bounded function

$$
\begin{align*}
f(\theta) =
\begin{cases}
-i(\pi+\theta) & \text{if } \theta\in(-\pi,0),\\
0 & \text{if } \theta=0,\\
i(\pi-\theta) & \text{if } \theta\in(0,\pi).
\end{cases}
\end{align*}
$$

Since $A_r(f)=f*P_r$ and $f$ is bounded,

$$
\begin{align*}
\lvert A_r(f)(\theta)\rvert
&= \left\lvert\frac{1}{2\pi}\int_{-\pi}^\pi f(\theta-\phi)P_r(\phi)d\phi \right\rvert \\
&\leq \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(\theta-\phi) \rvert P_r(\phi)d\phi \\
&\leq \sup_\theta \lvert f(\theta)\rvert.
\end{align*}
$$

Thus the Abel means are bounded uniformly in $\theta$.

For each fixed $\theta$, let

$$
\begin{align*}
c_n=\frac{e^{in\theta}-e^{-in\theta}}{n}.
\end{align*}
$$

Then

$$
\begin{align*}
f_N(\theta)=\sum_{n=1}^Nc_n.
\end{align*}
$$

Moreover,

$$
\begin{align*}
n\lvert c_n\rvert
&=\lvert e^{in\theta}-e^{-in\theta}\rvert \\
&=2\lvert\sin(n\theta)\rvert\\
&\leq2.
\end{align*}
$$

Thus $c_n=O(1/n)$ uniformly in $\theta$. Since both constants in Lemma 1.1 can be chosen independently of $\theta$, $f_N(\theta)$ is uniformly bounded in $N$ and $\theta$.

$$\tag*{$\square$}$$

## Lemma 1.2
Recall that

$$
\begin{align*}
f_N(\theta) = \sum_{1\leq \lvert n \rvert \leq N} \frac{e^{in\theta}}{n} \text{ and } \tilde{f}_N(\theta) = \sum_{-N\leq n \leq -1} \frac{e^{in\theta}}{n}.
\end{align*}
$$

They are trigonometric polynomials of degree $N$. We define frequency-shifted versions of $f_N$ and $\tilde{f}_N$,

$$
\begin{align*}
P_N(\theta) = e^{i2N\theta}f_N(\theta) \text{ and } \tilde{P}_N(\theta)=e^{i2N\theta}\tilde{f}_N(\theta),
\end{align*}
$$

which are trigonometric polynomials of degree $3N$ and $2N-1$, respectively. Indeed, the frequencies of $P_N$ are

$$
\begin{align*}
\{N,\ldots,2N-1\}\cup\{2N+1,\ldots,3N\},
\end{align*}
$$


and the frequencies of $\tilde{P}_N$ are

$$
\begin{align*}
\\{N,\ldots,2N-1\\}.
\end{align*}
$$

Then, if we consider the partial sums of $P_N$, we see

$$
\begin{align*}
S_M(P_N) &= \begin{cases}
P_N & \quad \text{if } M \geq 3N \\
\tilde{P}_N & \quad \text{if } M = 2N \\
0 & \quad \text{if } M < N.
\end{cases}
\end{align*}
$$

Moreover, choose a convergent positive series $\sum_k \alpha_k$ and a sequence of integers $\\{N_k\\}$ such that 

(i) $N_{k+1} > 3N_k$,

(ii) $\lim_{k\to\infty} \alpha_k \log N_k=\infty$.

For example, $\alpha_k=1/k^2$ and $N_k=3^{2^k}$. Define a function

$$
\begin{align*}
f(\theta) = \sum_{k=1}^\infty \alpha_k P_{N_k}(\theta).
\end{align*}
$$

Since $\lvert P_N(\theta)\rvert = \lvert f_N(\theta)\rvert$, which is uniformly bounded by the corollary, and $\sum_k\alpha_k<\infty$, the above series converges uniformly by the Weierstrass $M$-test. Thus $f$ is a continuous periodic function.

Moreover,

$$
\begin{align*}
\lvert S_{2N_m}(f)(0)\rvert \geq \alpha_m\log N_m.
\end{align*}
$$

<*Proof*>

Since the series defining $f$ converges uniformly, we can interchange the infinite sum with the integral when computing the Fourier coefficients. Therefore,

$$
\begin{align*}
S_{2N_m}(f)(0)
&= S_{2N_m}\left(\sum_{k=1}^\infty \alpha_kP_{N_k}\right)(0) \\
&=\sum_{k=1}^\infty \alpha_k S_{2N_m}(P_{N_k})(0) \\
&=\sum_{k<m}\alpha_k S_{2N_m}(P_{N_k})(0)
+\alpha_m S_{2N_m}(P_{N_m})(0)
+\sum_{k>m}\alpha_k S_{2N_m}(P_{N_k})(0).
\end{align*}
$$

If $k<m$, then $N_m>3N_k$, so $2N_m>3N_k$. Hence

$$
\begin{align*}
S_{2N_m}(P_{N_k})=P_{N_k}.
\end{align*}
$$

Moreover,

$$
\begin{align*}
P_{N_k}(0)
&=f_{N_k}(0)\\
&=\sum_{1\leq\lvert n\rvert\leq N_k}\frac{1}{n}\\
&=0.
\end{align*}
$$

Thus,

$$
\begin{align*}
\sum_{k<m}\alpha_k S_{2N_m}(P_{N_k})(0)=0.
\end{align*}
$$

For $k=m$, since $M=2N_m$, we have

$$
\begin{align*}
S_{2N_m}(P_{N_m})
=\tilde{P}_{N_m}.
\end{align*}
$$

Therefore,

$$
\begin{align*}
S_{2N_m}(P_{N_m})(0)
&=\tilde{P}_{N_m}(0)\\
&=\tilde{f}_{N_m}(0).
\end{align*}
$$

If $k>m$, then

$$
\begin{align*}
N_k\geq N_{m+1}>3N_m>2N_m.
\end{align*}
$$

Since every frequency of $P_{N_k}$ is at least $N_k$, we have

$$
\begin{align*}
S_{2N_m}(P_{N_k})=0.
\end{align*}
$$

Thus,

$$
\begin{align*}
\sum_{k>m}\alpha_k S_{2N_m}(P_{N_k})(0)=0.
\end{align*}
$$

Combining the three cases,

$$
\begin{align*}
S_{2N_m}(f)(0)
&=\alpha_m\tilde{f}_{N_m}(0).
\end{align*}
$$

Therefore,

$$
\begin{align*}
\lvert S_{2N_m}(f)(0)\rvert
&=\alpha_m\lvert\tilde{f}_{N_m}(0)\rvert\\
&\geq \alpha_m\log N_m.
\end{align*}
$$

Since $\alpha_m\log N_m\to\infty$,

$$
\begin{align*}
\lvert S_{2N_m}(f)(0)\rvert\to\infty.
\end{align*}
$$

Therefore, the partial sums of the Fourier series diverge at $0$ despite the function being continuous everywhere.

$$\tag*{$\square$}$$

## Reference
- Elias M. Stein and Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
