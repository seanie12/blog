---
title: "Pointwise Convergence and Uniform Convergence"

categories:
  - Analysis

tags:
  - Sequence of functions
  - Series of functions
  - Pointwise convergence
  - Uniform convergence
 

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 8.1.1
A sequence of real valued functions $\\{f_n\\}$ defined on a set $E (\subset \mathbb{R})$ **converges pointwise** on $E$ if $\\{f_n(x)\\}$ converges for every $x\in E$. If this is the case, then $f$ defined by

$$
\begin{align*}
f(x) = \lim_{n\to\infty}f_n(x), \quad x \in E,
\end{align*}
$$

defines a function on $E$. The function $f$ is called the **limit of the sequence** $\\{f_n\\}$.


## Remark

In terms of $\epsilon$ and $N$, the sequence $\\{f_n\\}$ converges pointwise to $f$ if for each $x\in E$ there is $f(x)\in\mathbb{R}$, given $\epsilon >0$, there exists $N=N(x,\epsilon)\in\mathbb{N}$ such that 

$$
\begin{align*}
\lvert f_n(x) - f(x) \rvert < \epsilon
\end{align*}
$$

for all $n\geq N$.

## Remark
Let $\\{f_n\\}$ be a sequence of functions on $E$. We can associate the $\\{S_n\\}$ of $n$-th **partial sums**, where for each $n\in\mathbb{N}$, $S_n$ is the real valued function on $E$ defined by for all $x\in E$

$$
\begin{align*}
S_n(x) = (f_1 + \cdots + f_n)(x) = \sum_{k=1}^n f_k(x).
\end{align*}
$$

$\sum_{k=1}^\infty f_k$ **converges pointwise** if $\\{S_n(x)\\}$ converges for all $x\in E$.

## Examples 8.1.2
(a) $E=[0,1], f_n(x) = x^n$ for each $x\in E$. Note that each $f_n$ is continuous on $E$.

$$
\begin{align*}
f(x) = \begin{cases}
0 & \text{if }  x\in [0,1) \\
1 & \text{if } x=1
\end{cases}
\end{align*}
$$

$\therefore f$ is not continuous at $x=1$.

(b) $f_k (x) = x^2 / (1+x^2)^k$,  $x\in\mathbb{R}$.

$$
\begin{align*}
\sum_{k=0}^\infty = \sum_{k=0}^\infty x^2\left( \frac{1}{1+x^2}\right)^k=\begin{cases}
0 & \text{if } x=0 \\
1+x^2 & \text{if } x\neq 0
\end{cases}
\end{align*}
$$

$\therefore f$ is not continuous at $x=0$.

(c) $\\{x_k\\}_{k=1}^\infty$ is an enumeration of $\mathbb{Q}$ in $[0,1]$.

$$
\begin{align*}
f_n(x) = \begin{cases}
0 & \text{if } x = x_k, 1\leq k \leq n \\
1 & \text{otherwise}
\end{cases}
\end{align*}
$$

Each $f_n$ is Riemann integrable on $[0,1]$. 

Let $x\in \mathbb{Q}$ be given. Then there is $x_{n_0}$ such that $x=x_{n_0}$ for some $n_0\in\mathbb{N}$. Then $f_{n_0}(x)= 0$. 

Let $\epsilon >0$ be given. If $n\geq n_0$, by the definition of $f_n$ 

$$
\begin{align*}
\lvert f_n (x)\rvert = 0 < \epsilon.
\end{align*}
$$

If $x \notin \mathbb{Q}, f_n(x)= 0$ for all $n\in\mathbb{N}$.  Thus,

$$
\begin{align*}
f(x) = \lim_{n\to\infty} f_n(x) = \begin{cases}
0 & \text{if } x\in \mathbb{Q} \\
1 & \text{if } x \notin \mathbb{Q}
\end{cases}
\end{align*}
$$

$\therefore f$ is not Riemann integrable.


## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
