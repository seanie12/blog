---
title: "Uniform Convergence and Integration"

categories:
  - Analysis

tags:
  - integration
  - uniform convergence
  - Dini Theorem
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

## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
