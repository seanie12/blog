---
title: "Uniform Convergence, Integration, and Differentiation"

categories:
  - Analysis

tags:
  - integration
  - uniform convergence
  - differentiation
 
toc: true
toc_sticky: true

use_math : true
comments : true

---

## Theorem 8.4.1 
Suppose $f_n\in \mathscr{R}[a,b]$ for all $n\in\mathbb{N}$ ans suppose that the sequence $\\{f_n\\}$ converges uniformly to $f$ on $[a,b]$. Then $f\in\mathscr{R}[a,b]$ and



$$
\begin{align*}
\int_a^bf(x) dx=\lim_{n\to\infty}\int_a^bf_n(x)dx.
\end{align*}
$$



<*Proof*>

Define 

$$
\begin{align*}
\epsilon_n :=\sup_{x\in[a,b]}\lvert f_n(x) -f(x)\rvert
\end{align*}
$$

for all $n\in\mathbb{N}$.

Since $f_n \rightrightarrows f$, we get $\lim_{n\to\infty}\epsilon_n=0$. For each $x\in [a,b]$,

$$
\begin{align*}
f_n(x)- \epsilon_n \leq f(x) \leq f_n(x) + \epsilon_n.
\end{align*}
$$

It implies that 

$$
\begin{align*}
\int_a^b (f_n-\epsilon_n)  \leq \underline{\int}_a^b f \leq \overline{\int}_a^bf \leq \int_a^b (f_n+\epsilon_n).
\end{align*}
$$

Therefore,

$$
\begin{align*}
0\leq \overline{\int}_a^bf - \underline{\int}_a^b f \leq 2\epsilon_n(b-a)
\end{align*}
$$

Since $2\epsilon_n (b-a) \to 0$ as $n\to \infty$, $f\in\mathscr{R}[a,b]$. Since $f\in\mathscr{R}[a,b]$,

$$
\begin{align*}
\int_a^b (f_n-\epsilon_n) \leq \int_a^b f \leq \int_a^b (f_n+\epsilon_n).
\end{align*}
$$

Then,

$$
\begin{align*}
\left\lvert \int_a^b f(x)dx - \int_a^bf_n(x) \right\rvert \leq 2\epsilon_n(b-a).
\end{align*}
$$


Since $2\epsilon_n(b-a)\to 0$ as $n\to\infty$, 

$$
\begin{align*}
\int_a^b f_n(x) dx = \lim_{n\to\infty}\int_a^b f_n(x)dx.
\end{align*}
$$

$$\tag*{$\square$}$$

## Corollary 8.4.2
If $f_k\in\mathscr{R}[a,b]$ for all $k\in\mathbb{N}$, and if 

$$
\begin{align*}
f(x) = \sum_{k=1}^\infty f_k(x), \quad x\in [a,b],
\end{align*}
$$

where the series converges uniformly on $[a,b]$, then $f\in\mathscr{R}[a,b]$ and

$$
\begin{align*}
\int_a^b f(x) dx = \sum_{k=1}^\infty f_k(x)dx.
\end{align*}
$$

Apply the previous theorem to $S_n(x) = \sum_{k=1}^n f_k(x)$, which by Theorem 6.2.1 is integrable for each $n\in\mathbb{N}$.

$$\tag*{$\square$}$$

## Theorem 8.4.3 (Bounded Convergence Theorem)
Suppose $f$ and $f_n$ are Reimann integrable functions on $[a,b]$ for all $n\in\mathbb{N}$ with $\lim_{n\to\infty}f_n(x)=f(x)$ for all $x\in [a,b]$. Suppose also that there exists a positive constant $M$ such that $\lvert f_n(x) \rvert\leq M$ for all $x\in [a,b]$ and all $n\in\mathbb{N}$. Then

$$
\begin{align*}
\lim_{n\to\infty}\int_a^b f_n(x) dx = \int_a^b f(x)dx
\end{align*}
$$


## Theorem 8.5.1 
Suppose $\\{f_n\\}$ is a sequence of differentiable functions on $[a,b]$. If

(a) $\\{f^\prime_n\\}$ converges uniformly on $[a,b]$, and

(b) $\\{f_n(x_0)\\}$ converges for some $x_0\in [a,b]$,

then $\\{f_n\\}$ converges uniformly to a function $f$ on $[a,b]$, with

$$
\begin{align*}
f^\prime(x) = \lim_{n\to\infty}f^\prime_n(x).
\end{align*}
$$

<*Proof*>

Let $\epsilon>0$ be given. By our assumptions, there exists $n_0\in \mathbb{N}$ such that 

$$
\begin{align*}
\lvert f_n(x_0) - f_m(x_0) \rvert <\frac{\epsilon}{2}
\end{align*}
$$

for all $m,n \geq n_0$ and

$$
\begin{align*}
\lvert f^\prime_n (t) - f^\prime_m(t)\rvert < \frac{\epsilon}{2(b-a)}
\end{align*}
$$

for all $m,n \geq n_0$ and for all $t\in[a,b]$.

By mean value theorem for $m, n \geq n_0$,

$$
\begin{align}
\lvert (f_n(x) - f_m(x)) - (f_n(y) - f_m(y))\rvert &= \lvert (f^\prime_n(t) - f^\prime_m(t))(x-y)\rvert \\ 
\label{eq:1}
\end{align}
$$

for some $t\in (x,y)$. Take $y=x_0$ in equation $\ref{eq:1}$. Then


$$
\begin{align*}
\lvert f_n(x) - f_m(x) \rvert &\leq \lvert f_n(x) - f_m(x) - (f_n(x_0) -f_m(x_0)) \rvert + \lvert f_n(x_0) - f_m(x_0)\rvert \\
&= \lvert (f^\prime_n (t) - f^\prime_m(t))(x-x_0)\rvert + \lvert f_n(x_0) - f_m(x_0)\rvert  \\
&< \frac{\epsilon}{2(b-a)} (b-a) + \frac{\epsilon}{2}\\
&=\epsilon
\end{align*}
$$

By Cauchy criterion, $\\{f_n\\}$ converges uniformly on $[a,b]$. Let $f(x) = \lim_{n\to\infty}f_n(x)$ for each $x\in [a,b]$. We want to show that $f$ is differentiable on $[a,b]$ and $f^\prime(x) = \lim_{n\to\infty}f^\prime_n(x)$ for all $x\in[a,b]$.

Fix $p\in [a,b]$. Define 

$$
\begin{align*}
g_n(t) := \frac{f_n(t) - f_n(p)}{t-p}, \quad g(t) = \frac{f(t)-f(p)}{t-p}.
\end{align*}
$$

Then $g_n(t) \to g_(t)$  for each $t\in [a,b] \setminus \\{ p\\}$ and 

$$
\begin{align*}
\lim_{t\to p} g_n(t) = \lim_{t\to p} \frac{f_n(t) - f_n(p)}{t-p} = f^\prime_n (p).
\end{align*}
$$

Let $A:= [a,b] \setminus \\{p\\}$. Take $y=p$ in equation $\ref{eq:1}$,

$$
\begin{align*}
\lvert g_n(t) - g_m (t) \rvert &= \left\lvert \frac{f_n(t) - f_n(p)}{t-p} - \frac{f_m(t) - f_n(t)}{t-p}\right\rvert \\
&=\frac{1}{\lvert t-p \rvert} \left\lvert (f_n(t) - f_m(t)) - (f_n(p) - f_m(p))\right\rvert \\
&=\frac{1}{\lvert t-p \rvert} \left\lvert (f^\prime_n(c) - f^\prime_m(c)) (t-p) \right\rvert \\
&< \frac{\epsilon}{2(b-a)}
\end{align*}
$$


for some $c \in [t,p]$ and for all $m,n \geq n_0$.

$\therefore \\{g_n\\}$ converges uniformly to $g$ on $A$.

By [Theorem 8.3.1](https://seanie12.github.io/blog/analysis/uniform-convergence-continuity/#theorem-831) 

$$
\begin{align*}
f^\prime(p)&=\lim_{t\to p} g(t)\\
&= \lim_{t\to p} \left(\lim_{n\to\infty}g_n(t) \right)\\
&=\lim_{n\to\infty}\left(\lim_{t\to p} g_n(t) \right) \\
&=\lim_{n\to\infty}f^\prime_n (p)
\end{align*}
$$

$$\tag*{$\square$}$$

## Example 8.5.2
Consider the series

$$
\begin{align*}
\sum_{k=1}^\infty \frac{\sin kx}{2^k}.
\end{align*}
$$

Since $\lvert 2^{-k}\sin kx \rvert \leq 2^{-k}$ for all $x\in \mathbb{R}$ by the [Weierstrass M-test](https://seanie12.github.io/blog/analysis/pointwise-uniform-convergence/#theorem-827-weierstrass-m-test) this series converges uniformly to a function $S$ on $\mathbb{R}$. For $n\in\mathbb{N}$, let 

$$
\begin{align*}
S_n(x) = \sum_{k=1}^n \frac{\sin kx}{2^k}.
\end{align*}
$$


Then

$$\begin{align*}
S^\prime_n(x) = \sum_{k=1}^n \frac{k\cos kx}{2^k}.
\end{align*}
$$

Since $\sum k 2^{-k}$ converges, by the Weierstrass M-test the sequence $\\{S^\prime_n\\}$ converges uniformly on $\mathbb{R}$. Thus by Theorem 8.5.1,


$$
\begin{align*}
S^\prime(x) = \lim_{n\to\infty}S^\prime_n(x) = \sum_{k=1}^\infty \frac{k \cos kx}{2^k}.
\end{align*}
$$
































## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
