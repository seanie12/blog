---
title: "Dirichlet Problem on the Unit Disc"

categories:
  - Fourier Analysis

tags:
  - Dirichlet Problem
  - Polar Coordinates
  - Approximation of the identity



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Preliminaries
Suppose one has an infinite plate $(\mathbb{R}^2)$ with an initial heat distribution. Let $u(x,y)$ denote the temperature of the place at position $(x,y)\in\mathbb{R}^2$. We are mainly concerned with the **steady-state heat equation**

$$
\begin{align*}
\Delta u := \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2u}{\partial y^2}=0.
\end{align*}
$$

The **Dirichlet problem** ($D$ some open domain set, and $\partial D$ its boundary):


  
$$
\begin{align*}
\begin{cases}
\Delta u = 0 \text{ on } D \\
u=f \text{ on } \partial D.
\end{cases}
\end{align*}
$$

In polar coordinates, the condition $\Delta u=0$ becomes

$$
\begin{align*}
\Delta u = \frac{\partial^2 u}{\partial r^2} + \frac{1}{r}\frac{\partial u}{\partial r} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2} =0.
\end{align*}
$$

<*Proof*>

Let $x=r\cos\theta$ and $y=r\sin\theta$. Then

$$
\begin{align*}
\frac{\partial x}{\partial r} &= \cos\theta, \quad \frac{\partial x}{\partial \theta}=-r\sin\theta \\
\frac{\partial y}{\partial r}&= \sin\theta, \quad \frac{\partial y}{\partial \theta} = r\cos\theta.
\end{align*}
$$

The first-order partial derivative of $u$ with respect to $r$,

$$
\begin{align*}
\frac{\partial u}{\partial r} &= \frac{\partial u }{\partial x} \frac{\partial x}{\partial r} + \frac{\partial u}{\partial y}\frac{\partial y}{\partial r} \\
&=\cos\theta \frac{\partial u}{\partial x} + \sin\theta \frac{\partial u}{\partial y}.
\end{align*}
$$

For the second-order derivative,

$$
\begin{align*}
\frac{\partial^2 u}{\partial r^2} &= \cos\theta \frac{\partial }{\partial r}\left(\frac{\partial u}{\partial x}\right) + \sin\theta \frac{\partial}{\partial r}\left( \frac{\partial u}{\partial y} \right) \\
&= \cos\theta \left(\frac{\partial}{\partial x}\left(\frac{\partial u}{\partial x}\right)\frac{\partial x}{\partial r}  + \frac{\partial}{\partial y}\left(\frac{\partial u}{\partial x}\right)\frac{\partial y}{\partial r}  \right) \\
&+\sin\theta\left(\frac{\partial u}{\partial x}\left(\frac{\partial u}{\partial y} \right)\frac{\partial x}{\partial r} + \frac{\partial}{\partial y}\left( \frac{\partial u}{\partial y}\right)\frac{\partial y}{\partial r} \right) \\
&= \cos^2\theta \frac{\partial^2 u}{\partial x^2} + 2\sin\theta\cos\theta \frac{\partial^2 u}{\partial x \partial y} + \sin^2\theta \frac{\partial^2 u}{\partial y^2} .
\end{align*}
$$

Similarly, we get the first order derivative of $u$ with respect to $\theta$,

$$
\begin{align*}
\frac{\partial u}{\partial \theta} &= \frac{\partial u}{\partial x} \frac{\partial x}{\partial \theta}+ \frac{\partial u}{\partial y}\frac{\partial u}{\partial \theta} \\
&=-r\cos\theta\cdot \frac{\partial u}{\partial x} + r\cos\theta \frac{\partial u}{\partial y}.
\end{align*}
$$

For the second-order derivative,

$$
\begin{align*}
\frac{\partial^2 u}{\partial \theta^2} &= \frac{\partial}{\partial\theta}\left(-r\sin\theta \frac{\partial u}{\partial x}\right) +  \frac{\partial}{\partial \theta}\left(r\cos\theta \frac{\partial u}{\partial y}\right) \\
&= -r\cos\theta \frac{\partial u}{\partial x} -r\sin\theta \frac{\partial^2}{\partial \theta \partial x}-r\sin\theta \frac{\partial u}{\partial y} + r\cos\theta \frac{\partial^2 u}{\partial \theta \partial y} \\
&= -r\cos\theta \frac{\partial u}{\partial x}-r\sin\theta \left(\frac{\partial}{\partial x}\frac{\partial u}{\partial x}\frac{\partial x}{\partial \theta}+ \frac{\partial}{\partial y}\frac{\partial u}{\partial x}\frac{\partial y}{\partial \theta}  \right) - r\sin\theta \frac{\partial u}{\partial y} \\
&+r\cos\theta \left( \frac{\partial }{\partial x}\frac{\partial y}{\partial y}\frac{\partial x}{\partial \theta} + \frac{\partial }{\partial y}\frac{\partial u}{\partial y}\frac{\partial y}{\partial \theta} \right) \\
&=-r\cos\theta \frac{\partial u}{\partial x}  - r\sin\theta\left(\frac{\partial^2 u}{\partial x^2}(-r\sin\theta)+\frac{\partial}{\partial x \partial y}r\cos\theta \right) -r\sin\theta \frac{\partial u}{\partial y} + r\cos\theta \left( \frac{\partial^2 u}{\partial x\partial y}(-r\sin\theta) + \frac{\partial^2 u}{\partial y^2}r\cos\theta\right) \\
&=-r\frac{\partial u}{\partial r} + r^2\sin^2\theta \frac{\partial^2 u}{\partial x^2} - 2r^2\sin\theta\cos\theta \frac{\partial^2 u}{\partial x \partial y} + r^2\cos^2\theta \frac{\partial^2 u}{\partial x \partial y}.
\end{align*} 
$$

Thus, 

$$
\begin{align*}
\frac{\partial^2u}{\partial r^2} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2}&=\cos^2\theta \frac{\partial^2 u}{\partial x^2} + 2\sin\theta\cos\theta \frac{\partial^2 u}{\partial x \partial y} +\sin^2\theta \frac{\partial^2 u}{\partial y^2} \\
&-\frac{1}{r}\frac{\partial u}{\partial r} + \sin^2\theta \frac{\partial^2 u}{\partial x^2}-2\sin\theta\cos\theta \frac{\partial^2 u}{\partial x \partial y}+ \cos^2\theta \frac{\partial^2 u}{\partial y^2} \\
&= \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} - \frac{1}{r}\frac{\partial u}{\partial r}.
\end{align*}
$$

By rearranging the terms, we get 

$$
\begin{align*}
\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} = \frac{\partial^2 u}{\partial r^2} + \frac{1}{r}\frac{\partial u}{\partial r} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2}. 
\end{align*}
$$ 

$$\tag*{$\square$}$$





## Theorem 1.1
Let $f$ be an integrable function on the unit circle. Then the Poisson integral
One has,

$$
\begin{align*}
u(r,\theta) := (f*P_r)(\theta)
\end{align*}
$$

solves the heat equation on the disk. That is $u\in\mathscr{C}^2(D)$ and satisfies

i) $\Delta u =0$.

ii) If $f$ is continuous at $\theta$, then $\lim_{r\to1^-}u(r,\theta)=f(\theta)$ and if $f$ is continuous everywhere then the convergence is uniform.

iii) If $f$ is continuous, then $u(r,\theta)$ is the unique solution to the steady heat equation on the disc satisfying (i) and (ii).

<*Proof*>

i) Since $f$ is integrable,  there is a $B>0$ such that $\lvert f(\theta)\rvert \leq B$ for all $\theta \in[-\pi, \pi]$. Thus,

$$
\begin{align*}
\lvert \hat{f}(m) r^{\lvert m\rvert} e^{im\theta}\rvert &= \lvert \hat{f}(\theta) r^{\lvert m\rvert}\rvert \\
&=r^{\lvert m\rvert}\left  \lvert \frac{1}{2\pi}\int_{-\pi}^\pi f(\theta)e^{-im\theta}d\theta\right\rvert \\
&\leq r^{\lvert m\rvert} \cdot \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(\theta) \rvert d\theta  \\
&\leq r^{\lvert m\rvert}  B.
\end{align*}
$$

It implies that $u(r,\theta)=\sum_{m=-\infty}^\infty \hat{f}(m)r^{\lvert m\rvert}e^{im\theta}$ converges absolutely and uniformly on any disc of radius $0\leq r <1$. As a consequence of the uniform convergence, using the [theorem](https://seanie12.github.io/blog/analysis/uniform-convergence-integration/#theorem-851), $u$ is differentiable  term by  term. Now, we want to show that $\Delta u=0$. Using the polar form of the Laplacian



$$
\begin{align*}
\Delta u = \frac{\partial^2 u}{\partial r^2} + \frac{1}{r}\frac{\partial u}{\partial r} + \frac{1}{r^2}\frac{\partial^2 u}{\partial \theta^2}.
\end{align*}
$$


$$
\begin{align*}
\Delta u(r,\theta) &= \sum_{m=-\infty}^\infty \lvert m \rvert (\lvert m \rvert -1) \hat{f}(m)r^{\lvert m\rvert-2}e^{im\theta} \\
&+ \lvert m \rvert \hat{f}(m)r^{\lvert m\rvert-2}e^{im\theta} \\
&- m^2\hat{f}(m)r^{\lvert m\rvert-2}e^{im\theta} \\
&=0.
\end{align*}
$$

So the Poisson integral is indeed harmonic.


ii) Restatement of the previous [theorem](https://seanie12.github.io/blog/fourier%20analysis/convolution-good-kernels/#theorem-32).

iii) Suppose that $v(r,\theta)$ is another solution. Since $v$ is twice continuously differentiable, we know that  Fourier series of $v(r,\cdot)$ converges to the original function by [Theorem](https://seanie12.github.io/blog/fourier%20analysis/Fourier-series/#corollary-24) 

$$
\begin{align*}
\sum_{n=-\infty}^\infty a_n(r) e^{in\theta}, \quad \text{where } a_n(r) = \frac{1}{2\pi}\int_{-\pi}^\pi v(r,\theta) e^{-in\theta}d\theta.
\end{align*}
$$

Since  $v(r,\theta)$ is a solution, 

$$
\begin{align*}
\Delta v(r,\theta) = \frac{\partial^2 v}{\partial r^2} + \frac{1}{r}\frac{\partial v}{\partial r} +\frac{1}{r^2}\frac{\partial^2 v}{\partial \theta} =0.
\end{align*}
$$

Thus, its Fourier coefficient

$$
\begin{align*}
\left\langle \Delta v(r,\theta), e^{in\theta}\right\rangle = \frac{1}{2\pi}\int_{-\pi}^\pi \left( \frac{\partial^2 v}{\partial r^2} + \frac{1}{r}\frac{\partial v}{\partial r} +\frac{1}{r^2}\frac{\partial^2 v}{\partial \theta} \right) e^{-in\theta}d\theta = 0.
\end{align*}
$$

By  Leibniz integral rule,



$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^\pi \left( \frac{\partial^2 v}{\partial r^2} + \frac{1}{r}\frac{\partial v}{\partial r} +\frac{1}{r^2}\frac{\partial^2 v}{\partial \theta} \right) e^{-in\theta}d\theta &= \left(\frac{\partial}{\partial r}\right)^2 \frac{1}{2\pi} \int_{-\pi}^\pi v(r,\theta) e^{-in\theta} \\
&+ \frac{1}{r}\frac{\partial}{\partial r} \frac{1}{2\pi}\int_{-\pi}^\pi v(r,\theta) e^{-in\theta} d\theta\\
&+\frac{1}{r^2} \frac{1}{2\pi} \int_{-\pi}^\pi \frac{\partial^2 v}{\partial\theta^2} e^{-in\theta}d\theta \\
&=a^{\prime\prime}_n(r) + \frac{1}{r}a^\prime_n(r) -\frac{n^2}{r^2}a_n(r)\\
&=0
\end{align*}
$$

for all $n\in\mathbb{Z}$.






By the Exercise 11 from chapter 1, 

$$
\begin{align*}
a_n(r) = \begin{cases}
A_n r^n + B_n r^{-n} \quad &(\text{if } n\neq 0) \\
A_n + B_n\log r \quad &(\text{if } n =0)
\end{cases}
\end{align*}
$$

for some $A_n, B_n$.  Since $v(r, \cdot)$ is continuous on $[-\pi, \pi]$, $v(r,\cdot)$ is bounded. Thus, $a_n(r)$ is bounded uniformly in $r\in (0,1)$  since

$$
\begin{align*}
\lvert a_n(r) \rvert &= \left \lvert\frac{1}{2\pi}\int_{-\pi}^\pi v(r,\theta) e^{in\theta} d\theta \right \rvert  \\
&\leq \frac{1}{2\pi}\int_{-\pi}^\pi\lvert v(r,\theta) \rvert d\theta \\
&\leq M.
\end{align*}
$$ 

For $n\geq 1, B_n=0$. Otherwise $\lim_{r\to0}B_nr^{-n}=\infty$.  Then

$$
\begin{align*}
A_n &= \lim_{r\to 1^-} a_n(r) \\
&=\lim_{r\to1^-} \frac{1}{2\pi}\int_{-\pi}^\pi v(r,\theta) e^{-in\theta}d\theta \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi \lim_{r\to1^-} v(r,\theta) e^{-in\theta}d\theta \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi  f(\theta)e^{-in\theta}d\theta \\
&=\hat{f}(n).
\end{align*}
$$


Similarly,  $A_n$ should be $0$ for $n\leq -1$. Otherwise $\lim_{r\to0}A_n r^n=\infty$. Then we get $B_n=\hat{f}(n)$. Lastly, $B_n$ should be $0$ for $n=0$ since $\lim_{r\to0}B_n\log r=-\infty$, which leads to $A_n=\hat{f}(n)$. Combining all these,  we get 

$$
a_n(r) = \begin{cases}
\hat{f}(n) r^n \quad &(n\geq 1) \\
\hat{f}(n) r^{-n} \quad &(n \leq -1) \\
\hat{f}(n) \quad &(n=0).
\end{cases}
$$

Thus, we conclude that 

$$
\begin{align*}
v(r,\theta) = \sum_{m=-\infty}^\infty \hat{f}(m)r^{\lvert m\rvert}e^{im\theta} = u(r,\theta).
\end{align*}
$$

$$\tag*{$\square$}$$

## Theorem (Cauchy Schwarz Inequality)
Let $V$ be vector space over $\mathbb{C}$. 

$$
\begin{align*}
\lvert \langle \mathbf{x},\mathbf{y}\rangle \rvert \leq \lVert \mathbf{x}\rVert \cdot \lVert \mathbf{y} \rVert
\end{align*}
$$

for all $\mathbf{x,y}\in V$.

<*Proof*>

First, suppose that $\lVert \mathbf{y} \rVert=0$. Since $\langle \mathbf{y},\mathbf{y}\rangle \geq 0$, $\lVert \mathbf{y} \rVert=0$ does not imply $\mathbf{y}=\mathbf{0}$. For all $t\in\mathbb{R}$,

$$
\begin{align*}
0 &\leq \lVert \mathbf{x}+t\mathbf{y}\rVert^2 \\
&=\langle \mathbf{x}+t\mathbf{y}, \mathbf{x}+t\mathbf{y}\rangle  \\
&= \lVert \mathbf{x}\rVert^2 + 2t \mathcal{R}(\langle \mathbf{x},\mathbf{y}\rangle ) + \lVert \mathbf{y}\rVert^2 \\
&=\lVert \mathbf{x}\rVert^2 + 2t \mathcal{R}(\langle \mathbf{x},\mathbf{y}\rangle ) \\
&\leq \lVert \mathbf{x}\rVert^2  + 2t\lvert \langle \mathbf{x},\mathbf{y}\rangle \rvert.
\end{align*}
$$

If $\lvert \langle \mathbf{x},\mathbf{y} \rangle \rvert \neq 0$, then taking $t\ll0$ gives a contradiction. Thus, $\lvert \langle \mathbf{x},\mathbf{y} \rangle \rvert=0$.

Second, suppose that $\lVert \mathbf{y} \rVert\neq0$. Let

$$
\begin{align*}
c = \frac{\langle \mathbf{x}, \mathbf{y}\rangle}{\langle \mathbf{y},\mathbf{y}\rangle}.
\end{align*}
$$

Then $\langle \mathbf{x}-c\mathbf{y}, \mathbf{y}\rangle=0$. So,

$$
\begin{align*}
\lVert \mathbf{x}\rVert^2 &= \lVert \mathbf{x}-c\mathbf{y}\rVert^2 + \lVert c\mathbf{y}\rVert^2 \\
&\geq \lvert c\rvert^2 \lVert \mathbf{y}\rVert^2
\end{align*}
$$

Then, 

$$
\begin{align*}
\lVert \mathbf{x}\rVert^2 &\geq \frac{\lvert \langle \mathbf{x},\mathbf{y}\rangle \rvert^2}{(\lVert \mathbf{y}\rVert^2)^2} \lVert \mathbf{y} \rVert^2 \Rightarrow \lvert \langle \mathbf{x},\mathbf{y}\rangle\rvert  \leq \lVert \mathbf{x}\rVert \lVert \mathbf{y} \rVert 
\end{align*}
$$

$$\tag*{$\square$}$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
