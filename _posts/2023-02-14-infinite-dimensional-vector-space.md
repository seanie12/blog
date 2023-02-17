---
title: "Fourier Series in the Language of Infinite Dimensional Vector Space"

categories:
  - Fourier Analysis

tags:
  - Hilbert Space
  - Best Approximation Lemma
  - Infinite dimensional vector space



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Preliminaries
Let $\\{a_n: n \in\mathbb{Z}\\}$ denote a sequence of complex numbers. We define $\ell_2$ norm of $\\{a_n\\}$ by 


$$
\begin{align*}
\lVert \{a_n \}_{n\in\mathbb{Z}} \rVert_{\ell_2} = \sum_{n\in\mathbb{Z}}\lvert a_n \rvert^2
\end{align*}
$$

and let $\ell^2(\mathbb{Z})$ denote the vector space of all sequences whose $\ell_2$ norm is finite.

## Definition 1.2
For $A=\\{a_n\\}$ and $B=\\{b_n\\}$ in $\ell^2(\mathbb{Z})$, we define the *inner product*

  
$$
\begin{align*}
\langle A, B\rangle =\lim_{N\to\infty}\sum_{n=-N}^Na_n \overline{b_n}
\end{align*}
$$

and $\lVert A \rVert := \sqrt{\langle A, A \rangle}$ denote the induced norm.


## Remark
Is $\ell_2(\mathbb{Z})$ closed under addition?

<*Proof*>

Let $(\mathbb{C}^n, +, \cdot)$ be vector space over $\mathbb{C}$ and define inner product $\langle (a_1,\ldots, a_n), (b_1, \ldots, b_n)\rangle = \sum_{i=1}^n a_i \overline{b_i}$. We define norm $\lVert \mathbf{x}\rVert = \sqrt{\langle \mathbf{x}, \mathbf{x}\rangle}$. Let $\mathbf{x}= (a_1, \ldots, a_n)$ and $\mathbf{y}=(b_1, \ldots, b_n)$.

$$
\begin{align*}
\lVert \mathbf{x}+\mathbf{y}\rVert^2 &= \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + \langle \mathbf{x},\mathbf{y}\rangle + \overline{\langle \mathbf{x}, \mathbf{y}\rangle} \\
&= \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + 2\text{Re}\langle \mathbf{x},\mathbf{y}\rangle  \\
&\leq \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + 2 \lvert \langle \mathbf{x}, \mathbf{y}\rangle \rvert \\
&\leq \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + 2 \lVert \mathbf{x}\rVert^2 \lVert \mathbf{y}\rVert^2 \\
&\leq \left( \lVert \mathbf{x} \rVert + \lVert \mathbf{y}\rVert\right)^2.
\end{align*}
$$

It implies that $\lVert \mathbf{x}+\mathbf{y}\rVert \leq \lVert \mathbf{x}\rVert + \lVert \mathbf{y}\rVert$.

Thus, for all $N\in\mathbb{N}$,

$$
\begin{align*}
\sqrt{\sum_{n=-N}^N \lvert a_n+b_n\rvert^2} &\leq \sqrt{\sum_{n=-N}^N \lvert a_n\rvert^2}+ \sqrt{\sum_{n=-N}^N \lvert b_n\rvert^2} \\
&\leq \lim_{N\to\infty}\sqrt{\sum_{n=-N}^N \lvert a_n\rvert^2}+ \lim_{N\to\infty}\sqrt{\sum_{n=-N}^N \lvert b_n\rvert^2} \\
&<\infty
\end{align*}
$$


$$\tag*{$\square$}$$



Since all the sequences are monotone increasing and bounded, $\lVert A +B \rVert \in \mathbb{R}$. Thus, $\ell_2(\mathbb{Z})$ is closed under the addition.


## Definition 1.3 
An inner product space with strictly positive definite inner product, which is complete with respect to the induced metric, is called a *Hilbert space*.

## Remark
$\mathcal{R}=\\{ f:\text{ Riemann integrable function on } 2\pi\mid \sqrt{\frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(x)\rvert^2 dx} < \infty \\}$ fails to be a Hilbert space. Since $\lVert f \rVert=0$ only implies $f=0$ almost everywhere.

## Theorem (Cauchy Schwarz Inequality)

<*Proof*>

Using the fact $2AB \leq (A^2 + B^2)$, we see that for any $\lambda >0$,

$$
\begin{align*}
\lvert f(x) \overline{g(x)}\rvert \leq \frac{1}{2}( \lambda \lvert f(x)\rvert^2 + \lambda^{-1}\lvert g(x)\rvert^2).
\end{align*}
$$

Then

$$
\begin{align*}
\lvert \langle f, g \rangle \rvert &\leq \frac{1}{2}\int_0^{2\pi} \lvert f(x) \overline{g(x)}\rvert dx \\
&\leq \frac{1}{2}( \lambda \lVert f\rVert^2 + \lambda^{-1}\lVert g\rVert^2).
\end{align*}
$$

Taking  $\lambda=\lVert g\rVert / \lVert f\rVert$ yields the Cauchy-Schwarz inequality. 



$$\tag*{$\square$}$$

## Remark
Let $\mathcal{R}$ be integrable functions on the circle and we define an inner product

$$
\begin{align*}
\langle f, g\rangle := \frac{1}{2\pi}\int_0^{2\pi}f(\theta)\overline{g(\theta)}d\theta
\end{align*}
$$

with induced norm $\lVert f\rVert^2_2 =\langle f, f\rangle$. Let $e_n(\theta) = e^{in\theta}$. Since $e^{in\theta}e^{im\theta}=\mathbf{1}\\{m=n \\}$, $\\{e_n: n\in\mathbb{Z}\\}$ is an orthonormal set.

Remark that the Fourier coefficients are precisely the coefficient of $f$ in terms of $\\{e_n: n\in\mathbb{Z}\\}$:

$$
\begin{align*}
\hat{f}(n) = \langle f, e_n \rangle.
\end{align*}
$$

For example, we can express the partial sum of Fourier series as 

$$
\begin{align*}
S_N(f) = \sum_{n=-N}^N\langle f, e_n\rangle e_n.
\end{align*}
$$

## Observation
1. $f -\sum_{\lvert n \rvert \leq N}\langle f , e_n\rangle e_n$ is orthonormal to  $e_k$ for all $\lvert k \rvert \leq N$.

2. Using the above, we can show the Pythagorean theorem.

Since, $f-S_N(f)$ is orthogonal to $S_N(f)$,

$$
\begin{align*}
\langle f- S_N(f), S_N(f) \rangle &= \langle f, S_N(f)\rangle - \langle S_N(f) ,S_N(f)\rangle\\
&= \sum_{\lvert n \rvert \leq N}\langle  f, e_n \rangle \overline{\langle f, e_n \rangle} - \sum_{\lvert n \rvert \leq N} \sum_{\lvert m \rvert \leq N} \langle f, e_n\rangle \overline{\langle f, e_m \rangle} \langle e_m, e_n\rangle\\ 
&= \sum_{\lvert n \rvert \leq N}\langle  f, e_n \rangle \overline{\langle f, e_n \rangle}.  \\
\end{align*}
$$

Thus, we get the Pythagorean theorem as

$$
\begin{align*}
\lVert f \rVert^2  & = \lVert f - S_N(f) \rVert^2 + \lVert S_N(f)\rVert^2 \\
&=\lVert f - S_N(f) \rVert^2 +  \sum_{\lvert n \rvert \leq N}\ \langle f, e_n\rangle \overline{\langle f, e_n \rangle} \\
&=\lVert f - S_N(f) \rVert^2 +  \sum_{\lvert n \rvert \leq N}\ \lvert\langle f, e_n\rangle \rvert^2.
\end{align*}
$$

## Best Approximation Lemma
For any $\sum_{\lvert n \rvert \leq N}c_ne_n$, we have

$$
\begin{align*}
\lVert f-S_N(f) \rVert \leq \lVert f - \sum_{\lvert n \rvert \leq N} c_n e_n \rVert.
\end{align*}
$$

<*Proof*>

Since 

$$
\begin{align*}
\left\langle f-S_N(f), S_N(f) - \sum_{\lvert n \rvert \leq N} c_n e_n\right\rangle &= \left\langle f-S_N(f), -\sum_{\lvert n \rvert \leq N} c_ne_n\right\rangle \\
&=-\left \langle f, \sum_{\lvert n \rvert \leq N}c_ne_n \right\rangle + \left\langle S_N(f), \sum_{\lvert n \rvert \leq N}c_n e_n \right\rangle \\
&=-\sum_{\lvert n\rvert \leq N} \overline{c_n}\langle f, e_n\rangle+ \sum_{\lvert n \rvert \leq N}\overline{c_n}\left\langle \sum_{\lvert m \rvert \leq N} \langle f,e_m\rangle e_m, e_n \right\rangle \\
&=-\sum_{\lvert n\rvert \leq N} \overline{c_n}\langle f, e_n\rangle+ \sum_{\lvert n \rvert \leq N}\overline{c_n}\left\langle f, e_n \right\rangle \\
&= 0,
\end{align*}
$$

we can conclude that

$$
\begin{align*}
\lVert f- \sum_{\lvert n\rvert \leq N}c_ne_n\rVert^2 &=\lVert f - S_N(f) + S_N(f) - \sum_{\lvert n\rvert \leq N}c_ne_n\rVert^2 \\
&= \lVert f -S_N(f) \rVert^2 + \lVert S_N(f) - \sum_{\lvert n\rvert \leq N}c_ne_n\rVert^2 \\
&\geq \lVert f-S_N(f) \rVert^2.
\end{align*}
$$

$$\tag*{$\square$}$$

## Theorem 3.1
Let $f$ be an integrable function on the circle. Then

$$
\begin{align*}
\left(\frac{1}{2\pi}\int_0^{2\pi} \lvert f(\theta) - S_N(f)\vert d\theta\right)^{1/2} \to 0 \text{ as } N\to\infty,
\end{align*}
$$

i.e., the Fourier series converges to $f$ in the $L^2$ sense.

<*Proof*>

Suppose $f$ is continuous. Using [Weierstrass approximation theorem](https://seanie12.github.io/blog/fourier%20analysis/cesaro-abel-summability/#corollary-25), we can choose a trigometric polynomial $p_M$ of degree $M$ such that $p_M \rightrightarrows f$. In other words, for all $\epsilon>0$ there is $N_1\in\mathbb{N}$ such that if  $M \geq N_1$,

$$
\begin{align*}
\lvert f(x) - p_M(x) \rvert < \epsilon.
\end{align*}
$$

It implies that 

$$
\begin{align*}
\lVert f - P_M\rVert_{2} = \left( \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(x) - p_M(x)\rvert^2\right)^{1/2} < \epsilon.
\end{align*}
$$

By the best approximation lemma, 

$$
\begin{align*}
\lVert f - S_N(f)\rVert <\epsilon
\end{align*}
$$

for all $N\geq M$.

Now, suppose that $f$ is integrable. Applying the [approximation lemma](https://seanie12.github.io/blog/fourier%20analysis/convolution-good-kernels/), choose a continuous function $g$ on the circle such that 

$$
\begin{align*}
\int_{-\pi}^\pi \lvert f(\theta) -g(\theta)\rvert d\theta < \epsilon^2.
\end{align*}
$$

Since we $f-g$ in integrable, $\sup_{\theta \in [0,2\pi]} \lvert f(\theta) -g(\theta)\rvert < B$.

Then we get 

$$
\begin{align*}
\lVert f - g\rVert^2_2 &= \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(\theta) - g(\theta)\rvert^2 d\theta \\
&= \frac{1}{2\pi}\int_{-\pi}^\pi \lvert f(\theta) - g(\theta)\rvert \cdot \lvert f(\theta) - g(\theta)\rvert d\theta \\
&\leq \frac{B}{\pi} \int_{-\pi}^\pi \lvert f(\theta) - g(\theta)\rvert d\theta \\
&\leq C\epsilon^2,
\end{align*}
$$

where $C >0$ is some constant. Now we approximate the continuous function $g$ by a trigometric polynomial $p_M$ so that 

$$
\lvert p_M(x) - g(x) \rvert < \epsilon
$$

for all $x\in[0,2\pi]$. As shown previously, $\lVert g(x)- p_M(x)\rVert_2 < \epsilon$. By the triangular ineqaulity, $\lVert f - p_M\rVert_2 < C^\prime \epsilon$. Using the best approximation lemma, 


$$
\begin{align*}
\lVert f - S_N(f) \rVert_2 < C^\prime \epsilon 
\end{align*}
$$

for all $N\geq M$.

$\therefore \lim_{N\to\infty}S_N(f) = f$.

$$\tag*{$\square$}$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
