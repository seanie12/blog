---
title: "Introduction to Fourier Series"

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
(f*g)(x) :=\frac{1}{2\pi}\int_{-\pi}^\pi f(y) g(x-y)dy
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


<*Proof*>

(1) Let $x\in [-\pi, \pi]$ be given.

$$
\begin{align*}
(f*(g*h))(x) &= \frac{1}{2\pi} \int_{-\pi}^{\pi} f(y) \left[g(x-y)+h(x-y) \right]dy \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f(y) g(x-y) dy + \frac{1}{2\pi}\int_{-\pi}^\pi f(y)h(x-y)dy \\
&=(f*g)(x) + (f*h)(x)
\end{align*}
$$

$\therefore f*(g+h) = f*g + f*h$



(2) Let $x\in [-\pi, \pi]$ be given. 

$$
\begin{align*}
((cf)*g )(x) &= \frac{1}{2\pi} \int_{-\pi}^\pi (cf)(y) g(x-y)dy \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi cf(y) g(x-y)dy \\
&=\frac{c}{2\pi}\int_{-\pi}^\pi f(y) g(x-y) dy \\
&= c(f*g)(x)
\end{align*}
$$

Similarly, 
$$
\begin{align*}
((cf)*g)(x) &= \frac{1}{2\pi}\int_{-\pi}^\pi cf(y)g(x-y)dy \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi f(y) cg(x-y)dy \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f(y) (cg)(x-y) dy \\
&= (f*(cg))(x)
\end{align*}
$$

$\therefore (cf)* g= c(f*g)=f*(cg)$


(3) Let $x\in [-\pi, \pi]$ be given.  With Fubini theorem, 

$$
\begin{align*}
((f*g)*h)(x) &= \frac{1}{2\pi} \int_{-\pi}^\pi (f*g)(y) h(x-y)dy \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi  \left( \frac{1}{2\pi}\int_{-\pi}^\pi f(z)g(y-z)dz\right) h(x-y)dy \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f(z)\left(\frac{1}{2\pi}\int_{-\pi}^\pi  g(y-z)h(x-y)dy \right)dz
\end{align*}
$$

Let $w:= y-z$. With the change of variable, 

$$
\begin{align*}
((f*g)*h)(x) &= \frac{1}{2\pi}\int_{-\pi}^\pi f(z)\left( \frac{1}{2\pi}\int_{-\pi-z}^{\pi-z}g(w)h(x-z-w)dw \right)dz\\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f(z)\left(\frac{1}{2\pi}\int_{-\pi}^\pi g(w)h(x-z-w)dw \right)dz\\
&=\frac{1}{2\pi}\int_{-\pi}^\pi  f(z) (g*h)(x-z)dz \\
&=(f*(g*h))(x)
\end{align*}
$$

$\therefore f*(g*h)=(f*g)*h$.


(4) Let $x\in [-\pi, \pi]$ be given. 

$$
\begin{align*}
(g*f)(x) &= \frac{1}{2\pi}\int_{-\pi}^\pi f(x-y)g(y)dy \\
&=\frac{1}{2\pi}\int_{x+\pi}^{x-\pi } -f(w) g(x-w) dw \quad ( w:= x-y) \\
&= \frac{1}{2\pi}\int_{x-\pi}^{x+\pi} f(w) g(x-w)dw \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi f(w)g(x-w) dw \\
&=(f*g)(x)
\end{align*}
$$

$\therefore f*g = g* f$.

(6) Let $n\in\mathbb{Z}$ be given.

$$
\begin{align*}
\widehat{f*g}(n) & = \frac{1}{2\pi}\int_{-\pi}^\pi (f*g)(x) e^{-inx}dx \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi \left(\frac{1}{2\pi}\int_{-\pi}^\pi  f(y) g(x-y)dy \right)e^{-inx}dx \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi f(y)\left(\frac{1}{2\pi}\int_{-\pi}^\pi g(x-y)e^{-inx}dx \right) dy \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi f(y) e^{-iny} \left(g(x-y)e^{-in(x-y)} dx \right)dy \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi f(y) e^{-iny}\left(\frac{1}{2\pi}\int_{-\pi}^\pi g(w) e^{-inw}dw \right)dy \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f(y- e^{-iny} \hat{g}(n) dy \\
&= \hat{f}(n) \hat{g}(n)
\end{align*}
$$


(5) First, we assume that $f$ and $g$ are continuous on $-[\pi, \pi]$. Let $\epsilon >0$ be given. We want to show that there exists a $\delta>0$ such that 

$$
\begin{align*}
\lvert x_1 -x_2 \rvert < \delta \Rightarrow \lvert (f*g)(x_1) - (f*g)(x_2)\rvert < \epsilon.
\end{align*}
$$

Note that $g$ is continuous on the compact set $[-\pi, \pi]$, $g$ is uniformly continuous on $[-\pi, \pi]$. Thus, there exists  $\delta>0$ such that  $\lvert p -q \rvert <\delta \Rightarrow\lvert g(p) - g(q)\rvert <\epsilon/ B$, where $B$ is a bound on $g$, i.e., $\lvert g(x)\rvert \leq B$ for all $x\in[-\pi, \pi]$. Now consider,
$$
\begin{align*}
\lvert (f*g)(x_1) - (f*g)(x_2) \rvert  &= \left\lvert \frac{1}{2\pi}\int_{-\pi}^\pi f(y)[g(x_1-y)-g(x_2)]dy \right\rvert \\
&\leq \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(y) \rvert \lvert g(x_1-y) - g(x_2-y)\rvert dy \\
&\leq \frac{1}{2\pi}\int_{-\pi}^\pi B \frac{\epsilon}{B}dy \\
&<\epsilon.
\end{align*}
$$

$\therefore f*g$ is continuous on $[-\pi, \pi]$.


**Lemma $(L^1$ approximation$)$**. Given any integrable function $f$ on the circle, there exists a sequence of continuous function $\\{f_k\\}$ such that 

$$
\begin{align*}
\lim_{k\to\infty} \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f -f_k\rvert dx = 0.
\end{align*}
$$

Now, suppose that $f,g$ are integrable functions. By the lemma, there are sequences $\\{f_k\\}$ and $\\{g_k\\}$ such that

$$
\begin{align*}
\frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(x)-f_k(x) \rvert dx &\to 0 \\
\frac{1}{2\pi}\int_{-\pi}^\pi \lvert g(x) - g_k(x) \rvert dx &\to 0
\end{align*}
$$
 
 as $k\to \infty$. It will suffice to show that $f_k * g_k$ uniformly converges to $f*g$ on $[-\pi, \pi]$. We know that $f_k*g_k$ is continuous by the previous proof. If $f_k*g_k$ uniformly converges to $f*g$, then $f*g$ is still continuous by the [uniform convergence](https://seanie12.github.io/blog/analysis/uniform-convergence-continuity/#corollary-832). 

$$
\begin{align*}
\left\lvert f*g - f_k*g_k\right\rvert &= \left\lvert (f-f_k)*g + f_k * (g-g_k)\right\rvert \\
&=\left \lvert \frac{1}{2\pi}\int_{-\pi}^\pi[f(x-y)-f_k(x-y)]g(y)dy\right\rvert \\
&\leq \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(x-y)-f_k(x-y)\rvert \lvert g(y) \rvert dy \\
&\leq \frac{B}{2\pi}\int_{-\pi}^\pi \lvert f(x-y)-f_k(x-y) \rvert dy \\
&= \frac{B}{2\pi}\int_{x+\pi}^{x-\pi} - \lvert f(w) - f_k(w) \rvert dw \\
&=\frac{B}{2\pi}\int_{-\pi}^\pi \lvert f(w) - f_k(w) \rvert dw \\
&< \frac{\epsilon}{2}.
\end{align*}
$$

Similarly, we get 

$$
\begin{align*}
\lvert f_k *(g-g_k) \rvert < \frac{\epsilon}{2}.
\end{align*}
$$

$\therefore f_k*g_k \rightrightarrows f*g$ and $f*g$ is continuous.


$$\tag*{$\square$}$$


