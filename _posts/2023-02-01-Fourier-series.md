---
title: "Introduction to Fourier Series"

categories:
  - Fourier Analysis

tags:
  - Fourier Sereis
  - Dirichlet kernel
  - Poisson kernel


toc: true
toc_sticky: true

use_math : true
comments : true

---
## Basic Knowledge
We focus on a class of functions

(1)  Continuous functions $[0, L]$

(2) Piecewise continuous functions (only finitely many discontinuities)

(3) Riemann integrable functions 

(4) Functions on the circle (correspondence with $2\pi$ periodic functions on $\mathbb{R}$ such that $f(0)=f(2\pi)$.

## Definition 2.1
Given an integrable function $f:[a,b]\to\mathbb{C}$, we define the *Fourier series* of $f$ as 

$$
\begin{align*}
\sum_{n=-\infty}^{\infty} \hat{f}(n)e^{\frac{2\pi inx}{b-a}},
\end{align*}
$$

where 

$$
\begin{align*}
\hat{f}(n) = \frac{1}{b-a}\int_a^b f(x) \exp\left(-\frac{2\pi inx }{b-a}\right)dx
\end{align*}
$$

denotes the $n$-th *Fourier coefficient* of $f$ for $n\in\mathbb{N}$.

## Remark
One can define inner product $\langle f,g \rangle = \frac{1}{b-a}\int_a^b f(x) \bar{g}(x) dx$. Then 

$$
\begin{align*}
\hat{f}(n) = \left\langle f, \exp\left(\frac{2\pi inx}{b-a}\right) \right\rangle .
\end{align*}
$$

## Example
The Fourier series of the $2\pi$-periodic odd function defined on $[0,\pi]$ by $f(\theta) = \theta(\pi-\theta)$. For $\theta>0$ the given function is $f(\theta)=\theta(\pi+\theta)$ with its derivative $f^\prime(\theta)=\pi-2\theta$. On the other hand, $f(\theta)= \theta(\pi+\theta)$ with its derivative $f^\prime(\theta)=\pi+2\theta$ for $\theta<0$.  Then using the integration by parts,

$$
\begin{align*}
\hat{f}(n) &= \frac{1}{2\pi} \int_{-\pi}^\pi f(\theta) \exp\left( \frac{-2\pi in\theta}{2\pi} \right) \\
&=\frac{1}{2\pi}\left(\left[\frac{-f(\theta)\exp(-in\theta)}{in} \right]_{-\pi}^\pi  + \int_{-\pi}^\pi f^\prime(\theta) \frac{e^{-in\theta}}{in} d\theta \right) \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f^\prime(\theta) \frac{e^{-in\theta}}{in} d\theta \quad (\because f(\pi)=f(-\pi)=0) \\
&=\frac{1}{2\pi}\left(\int_{-\pi}^0 (\pi+2\theta)\frac{e^{-in\theta}}{in}d\theta + \int_{0}^\pi (\pi-2\theta)\frac{e^{-in\theta}}{in}d\theta \right) \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi \pi \frac{e^{-in\theta}}{in}d\theta + \frac{1}{in\pi}\left(\int_{-\pi}^0 \theta e^{-in\theta} d\theta - \int_0^\pi \theta e^{-in\theta}d\theta \right)
\end{align*}
$$

By Euler formula $e^{i\theta}=$, for all non-zero integer $k\in\mathbb{Z}\setminus \{0\}$
$$
\begin{align*}
\int_{-\pi}^\pi e^{ikx} dx &= \left[\frac{1}{ik} e^{ikx} \right]_{-\pi}^\pi  \\
&=\frac{1}{ik}(e^{ik\pi}-e^{-ik\pi}) \\
&= \frac{1}{ik}\left(\cos(k\pi)+i\sin(k\pi) - \cos(-k\pi)-i\sin(-k\pi) \right) \\
&= \frac{1}{ik}\left(\cos(k\pi) + i\sin(k\pi) -\cos(k\pi)+i\sin(k\pi) \right) \\
&=\frac{1}{ik}2i\sin(k\pi) \\
&=0.
\end{align*}
$$

Then 
$$
\begin{align*}
\frac{1}{in\pi}\int_{-\pi}^\pi \pi \frac{e^{-in\theta}}{in}d\theta &= \frac{1}{in\pi}\int_{-\pi}^\pi e^{-in\theta}d\theta \\
&=0.
\end{align*}
$$

With the change of variable $\gamma=-\theta$,
$$
\begin{align*}
\hat{f}(n) &= \frac{1}{in}\left(\int_{-\pi}^0 \theta e^{-in\theta} d\theta - \int_0^\pi \theta e^{-in\theta}d\theta \right)  \\
&= \frac{1}{in\pi}\left(-\int^\pi_0 \gamma e^{in\gamma}d\gamma -\int_{0}^\pi \gamma e^{-in\gamma}d\gamma\right) \\
&= -\frac{1}{in\pi}\left(\int_{0}^\pi \theta(e^{in\theta}+e^{-in\theta})d\theta \right).
\end{align*}
$$

Since 

$$
\begin{align*}
\int e^{in\theta} + e^{-in\theta}d\theta &= \frac{1}{in}\left( e^{in\theta}-e^{-in\theta}\right) + C \\
&=\frac{1}{in}(cos(n\theta) + i\sin(n\theta) - \cos(-n\theta)-i\sin(-n\theta)) + C \\
&= \frac{1}{in}2i\sin(n\theta) +C \\
&= \frac{2}{n}\sin(n\theta)+C,
\end{align*}
$$

we get the following equation with the integration by parts:
$$
\begin{align*}
\hat{f}(n) &= -\frac{2}{in\pi}\left(\left[\frac{\theta}{n}\sin(n\theta) \right]_0^\pi - \int_0^\pi \frac{1}{n}\sin(n\theta)d\theta\right) \\
&= \frac{2}{in^2\pi}\int_0^\pi \sin(n\theta)d\theta \\
&= \frac{2}{in^2\pi}\left[-\frac{1}{n}\cos(n\theta) \right]_0^\pi \\
&= \frac{2}{in^2\pi}\left( \frac{1-\cos(n\pi)}{n}\right) \\
&= \frac{2}{in^3\pi}(1+(-1)^{n+1}) \\
&= \frac{4}{in^3\pi}
\end{align*}
$$
for odd $n$, and $0$ otherwise.

Thus,
$$
\begin{align*}
f(\theta) \sim \sum_{k \text{ odd}}\frac{4}{ik^3\pi}e^{ikx}
\end{align*}
$$

$$\tag*{$\square$}$$

## Definition 2.2
We define $N$-th partial sum of the Fourier series of $f, N\in\mathbb{N}$ by 

$$
\begin{align*}
S_N(f)(x) := \sum_{n=-N}^N\hat{f}(n)\exp\left(\frac{2\pi inx}{L} \right).
\end{align*}
$$

## Remark 
"Convergence of the Fourier series to $f$" will always mean convergence of the partial sum $S_N(f)$ to $f$.

## Definition 3.1
We define the *Dirichlet Kernel* $D_N$ by 

$$
\begin{align*}
D_N(x) = \sum_{n=-N}^N e^{inx}
\end{align*}
$$

where $x\in [-\pi, \pi]$.

## Lemma 3.2
$$
\begin{align*}
D_N(x)  = \frac{\sin((N+\frac{1}{2})x)}{\sin (x/2)} 
\end{align*}
$$

<*Proof*>

$$
\begin{align*}
D_N(x) &= \sum_{n=0}^N e^{inx} + \sum_{n=-1}^{-N}e^{inx} \\
&= \frac{1-(e^{ix})^{N+1}}{1-e^{ix}} + \frac{e^{-ix}(1-(e^{-ix})^N)}{1-e^{-ix}} \\
&= \frac{1-e^{(N+1)ix}}{1-e^{ix}} + \frac{1-e^{-Nix}}{e^{ix}-1} \\
&=\frac{1-e^{(N+1)ix}}{1-e^{ix}} + \frac{e^{-Nix}-1}{1-e^{ix}}  \\
&= \frac{e^{-Nix}-e^{(N+1)ix}}{1-e^{ix}} \\
&= \frac{e^{-(N+\frac{1}{2})ix}-e^{(N+\frac{1}{2})ix}}{e^{-\frac{ix}{2}}-e^{\frac{ix}{2}}} \\
&=\frac{\sin((N+\frac{1}{2})x)}{\sin(x/2)}
\end{align*}
$$


$$\tag*{$\square$}$$

## Remark
Dumb question. What are the Fourier coefficients of $D_N$?

$$
\begin{align*}
\hat{f}(n) &= \frac{1}{2\pi}\int_{-\pi}^\pi D_N(x) e^{-inx}dx \\
&=\sum_{m=-N}^N \frac{1}{2\pi} \int_{-\pi}^\pi e^{imx}e^{-inx}dx \\
&= \mathbf{1}\{n\leq N \}
\end{align*}
$$


## Definition 3.3 
We define *Poisson kernel* $P_r(\theta)$ by

$$
\begin{align*}
P_r(\theta) = \sum_{n=-\infty}^\infty r^{\lvert n \rvert} e^{in\theta}
\end{align*}
$$

where $\theta\in [-\pi, \pi]$ and $r\in [0,1)$.
## Remark
Note that 
$$
\sum_{n=-\infty}^\infty \left\lvert r^{\lvert n \rvert} e^{in\theta}\right\rvert = \sum_{n=-\infty}^\infty r^{\lvert n\rvert}
$$

and $\sum_{n=-\infty}^\infty r^{\lvert n \rvert}$ converges. By [Weierstrass M-Test](https://seanie12.github.io/blog/analysis/pointwise-uniform-convergence/#theorem-827-weierstrass-m-test),  $P_r(\theta)$ converges uniformly.  Then the Fourier coefficients of Poisson kernel are 

$$
\begin{align*}
\hat{P}_r(m) & = \frac{1}{2\pi}\int_{-\pi}^\pi \sum_{m=-\infty}^\infty r^{\lvert m \rvert} e^{im\theta} \overline{e^{in\theta}}d\theta \\
&=\sum_{m=-\infty}^\infty \frac{1}{2\pi}r^{\lvert m\rvert} \int_{-\pi}^\pi e^{im\theta}e^{-in\theta}d\theta \quad (\because \text{ uniform convergent}) \\
&=r^{\lvert m\rvert}.
\end{align*}
$$

## Lemma 3.4
$P_r(\theta) = \frac{1-r^2}{1-2r\cos\theta+r^2}$

<*Proof*>

Letting $\omega = re^{i\theta}$, we have a sum of geometric series:

$$
\begin{align*}
P_r(\theta) &= \sum_{n=0}^\infty \omega^n + \sum_{n=1}^\infty \bar{\omega}^n \\
&=\frac{1}{1-\omega} + \frac{\bar{\omega}}{1-\bar{\omega}} \\
&= \frac{1-\bar{\omega}+\bar{\omega}-\omega\bar{\omega}}{1-\omega-\bar{\omega} + \omega\bar{\omega}} \\
&=\frac{1	-r^2}{1-2r\cos\theta +r^2}
\end{align*}
$$

$$\tag*{$\square$}$$

## Theorem 4.1 (Uniqueness)
Let $f$ be integrable function on the circle. Suppose $\hat{f}(n)=0$ for all $n\in\mathbb{Z}$. If $f$ is continuous at $\theta_0$, then $f(\theta_0)=0$.


<*Proof*>
Without loss of generality, assume $\theta_0=0$ and $f(\theta_0) >0$. By continuity of $f$ there is a $\delta>0$ such that 

$$
\begin{align*}
x\in N_{\delta}(0) &\Rightarrow  \lvert f(x) - f(0)\rvert <\frac{1}{2}f(0) \\
&\Rightarrow f(x) > \frac{1}{2}f(0)
\end{align*}
$$

Now, we create a sequence of trigometric polynomials (finite linear combination of $\\{ e^{inx}: n\in\mathbb{Z}\\}$ as follows: Let 

$$
\begin{align*}
p(\theta) = \cos\theta + \epsilon
\end{align*}
$$

where $\epsilon>0$ is chosen so small that out side of $(-\delta, \delta)$, we still have 

$$
\begin{align*}
\lvert p(\theta) \rvert < 1- \frac{\epsilon}{2}.
\end{align*}
$$

Since $\cos\theta$ is continuous,  we can choose a small $\eta>0$ such that 

$$
\begin{align*}
\theta \in (-\eta, \eta) &\Rightarrow \lvert p(\theta) - p(0)\rvert < \frac{\epsilon}{2} \\
&\Rightarrow p(\theta) > p(0) + \frac{\epsilon}{2}
\end{align*}
$$

Let $P_k(\theta) = [p(\theta)]^k$. We know that $\hat{f}(n) = \langle f, e^{inx}\rangle = 0$ for all $n\in\mathbb{Z}$ Thus, $\langle f, \sum_{n=1}^N c_ne^{inx}\rangle=0$ for all $N\in\mathbb{N}$. Since $\cos\theta = \frac{e^{i\theta}+ e^{-i\theta}}{2}$, 

$$
\begin{align*}
(\cos\theta + \epsilon)^n &= \sum_{k=0}^n{n\choose k}\epsilon^{n-k}\cos^n\theta \\
&=\sum_{k=0}^n{n \choose k}\epsilon^{n-k} \sum_{l=0}^k \frac{e^{il\theta}+ e^{-i(k-l)\theta}}{2^k} \\
&\in \text{span}\{e^{inx}: n\in\mathbb{Z} \}.
\end{align*}
$$

Thus, $\langle f, p_k\rangle$ should be zero. But we will show that $\lim_{k\to\infty}\langle f, p_k\rangle =\infty$ which is a contradiction.

Now consider 

$$
\begin{align*}
2\pi\langle f, p_k(\theta) \rangle &= \int_{-\pi}^\pi f(\theta) p_k(\theta) d\theta \\
&=\int_{(-\eta, \eta)} f(\theta) p_k(\theta) d\theta+\int_{(-\delta, \delta)^c} f(\theta) p_k(\theta) d\theta + \int_{(-\delta, \delta)\setminus (-\eta, \eta)} f(\theta) p_k(\theta) d\theta
\end{align*}
$$

(1) In the $\eta$-neighborhood, we have

$$
\begin{align*}
\int_{-\eta}^\eta f(\theta) p_k(\theta) d\theta \geq \frac{f(0)}{2}\left(1+\frac{\epsilon}{2}\right)^k 2\eta
\end{align*}
$$

and it goes to infinity as $k\to\infty$.

(2) Outside of $\delta$-neighborhood,  we have 

$$
\begin{align*}
\int_{[-\pi, \pi]\setminus (-\delta, \delta)} f(\theta) p_k(\theta)d\theta  &\leq \left\lvert\int_{[-\pi, \pi]\setminus (-\delta, \delta)} f(\theta) p_k(\theta)d\theta\right\rvert \\
&\leq \int_{[-\pi, \pi]\setminus (-\delta, \delta)} \lvert f(\theta) \rvert \lvert p_k(\theta)\rvert d\theta \\
&\leq 2\pi B\left( 1-\frac{\epsilon}{2}\right)^k
\end{align*}
$$

where $B$ is the bound on integrable function $f$. It converges to $0$ as $k\to \infty$.

(3) Between $(-\delta, \delta)$ and $(-\eta, \eta)$, $f(\theta) > \frac{f(0)}{2} >0$. Since we can take $\delta <\frac{\pi}{2}$, $p(\theta)>0$. Thus,

$$
\begin{align*}
\int_{(-\delta, \delta)\setminus (-\eta, \eta)} f(\theta) p_k(\theta) d\theta > 0.
\end{align*}
$$

Together, the above prove that 

$$
\begin{align*}
\lim_{k\to\infty}\int_{-\pi}^\pi f(\theta)p_k(\theta) d\theta = \infty
\end{align*}
$$

, which contradicts to $\langle f, p_k \rangle = 0$.

$$\tag*{$\square$}$$

## Corollary 2.1
Suppose $f$ is continuous on the circle. If $\hat{f}(n)=0$ for all $n\in\mathbb{Z}$, then $f\equiv 0$. If $f,g$ are $2\pi$ periodic function and $\hat{f}(n)=\hat{g}(n)$ for all $n\in\mathbb{Z}$, then $f= g$.


## Corollary 2.2
Suppose $f$ is a continuous function on the circle, and $\sum_{n=-\infty}^\infty \lvert \hat{f}(n)\rvert <\infty$. Then 

$$
\begin{align*}
\lim_{N\to\infty}S_N(f)(\theta) &=f(\theta)
\end{align*}
$$

uniformly on the circle. 

<*Proof*>

Since 

$$
\begin{align*}
\sum_{n=-N}^N \lvert \hat{f}(n)\rvert \left\lvert e^{in\theta}\right\rvert = \sum_{n=-N}^N\lvert \hat{f}(n)\rvert
\end{align*}
$$

and it absolutely converges and is independent of $\theta$, $S_N(f)$ converges uniformly on the circle by [Weierstrass M-test](https://seanie12.github.io/blog/analysis/pointwise-uniform-convergence/#theorem-827-weierstrass-m-test). Since $S_N(f)$ is continuous and uniform convergent, $S_N(f)$ uniformly converges to some continuous function.

Fourier coefficient of $\lim_{N\to\infty}\sum_{n=-N}^N \hat{f}(n)e^{in\theta}$ is 

$$
\begin{align*}
\left\langle\lim_{N\to\infty}\sum_{n=-N}^N \hat{f}(n)e^{in\theta}, e^{im\theta}  \right\rangle &= \frac{1}{2\pi}\int_{-\pi}^\pi \lim_{N\to\infty} \sum_{n=-N}^N \hat{f}(n)e^{in\theta} e^{-im\theta}d\theta \\
&=\frac{1}{2\pi}\lim_{N\to\infty}\sum_{n=-N}^N \int_{-\pi}^\pi  \hat{f}(n)e^{in\theta} e^{-im\theta}d\theta \\
&=\frac{1}{2\pi}\lim_{N\to\infty} \sum_{n=-N}^N \hat{f}(n)\int_{-\pi}^\pi \delta_{n,m}d\theta \\
&=\hat{f}(m)
\end{align*}
$$

So two continuous functions have  the identical Fourier coefficients. By previous corollary, they must be the same functions.

$$\tag*{$\square$}$$

## Big O-Notation
We say $f(x) = O(g(x))$ as $x\to a$ if there exists a $C>0$ such that 

$$
\begin{align*}
\lim_{x\to a} \frac{f(x)}{g(x)} \leq C.
\end{align*}
$$

## Corollary 2.4
Let $f$ be a function on the circle. If $f$ is twice continuously differentiable (i.e. is of class $\mathscr{C}^2$), then $\hat{f}(n) = O(1/\lvert n \rvert^2)$ as $\lvert n\rvert\to \infty$.

<*Proof*>

$$
\begin{align*}
2\pi \hat{f}(n) &= \int_0^{2\pi} f(\theta) e^{-in\theta}d\theta \\
&=\left[ f(\theta) \frac{-e^{-in\theta}}{in}\right]_0^{2\pi} + \frac{1}{in}\int_0^{2\pi} f^\prime(\theta) e^{-in\theta}d\theta \\
&=\frac{1}{in}\int_0^{2\pi}f^\prime (\theta)e^{-in\theta}d\theta \\
&=\frac{1}{in}\left[f^\prime(\theta)\frac{-e^{-in\theta}}{in} \right]^{2\pi}_0 + \frac{1}{(in)^2}\int_0^{2\pi}f^{\prime\prime}(\theta)e^{-in\theta}d\theta \\
&= -\frac{1}{n^2} \int_0^{2\pi}f^{\prime\prime}(\theta)e^{-in\theta}d\theta
\end{align*}
$$

So

$$
\begin{align*}
\lvert \hat{f}(\theta) \rvert n^2 &\leq \frac{1}{2\pi}\int_0^{2\pi} \lvert f^{\prime\prime}(\theta) e^{-in\theta}\rvert d\theta \\
&=\frac{1}{2\pi}\int_0^{2\pi}\lvert f^{\prime\prime}(\theta)\rvert d\theta \\
&\leq C
\end{align*}
$$
$$\tag*{$\square$}$$

## Definition 2.5
Let $f$ be a function for which there exists a constant $A\in\mathbb{R}$ such that for all $x,h$

$$
\begin{align*}
\lvert f(x+h) - f(x) \rvert \leq A \lvert h \rvert^\alpha,
\end{align*}
$$

Then we say that $f$ satisfies a *Holder continuous* of order $\alpha$.

## Remark 
If a function is Holder continuous order $\alpha> 1/2$, then the Fourier series converges absolutely and thus uniformly to $f$. 

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
