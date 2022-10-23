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

## Definition 8.1.1 (Pointwise Convergence)
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

$\sum_{k=1}^\infty f_k$ **converges pointwise** if for each $x\in $, $\\{S_n(x)\\}$ converges.

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
\sum_{k=0}^\infty f_k(x) = \sum_{k=0}^\infty x^2\left( \frac{1}{1+x^2}\right)^k=\begin{cases}
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


## Examples
(a) $f_n:\mathbb{R}\to\mathbb{R}$.

$$
\begin{align*}
f_n(x) = \chi_{[n,n+1]}(x) = \begin{cases}
1 & \text{if } x \in [n,n+1] \\
0 & \text{otherwise}
\end{cases}
\end{align*}
$$

converges pointwise to $f(x)=0$.

(b) 

$$
\begin{align*}
f_m (x) =
\begin{cases}
1 & \text{if } m!x\in \mathbb{Z} ( \text{i.e., if } x= \frac{p}{m!} \text{ for some } p\in\mathbb{Z} \\
0 & \text{otherwise} 
\end{cases}
\end{align*}
$$

If $x\notin \mathbb{Q}$, then $\lim_{m\to\infty}f_m(x)=0$.

If $x\in\mathbb{Q}$, we can write $x=\frac{p}{q}$. Then $f_q(x)=1$, i.e., $f_m(\frac{p}{q})=1$ for all $m\geq q$.

$\therefore \lim_{m\to\infty}f_m(x)=1$

 $\therefore \lim_{m\to\infty}f_m(x) = \chi_\mathbb{Q}(x)$.

## Definition 8.2.1 (Uniform Convergence)
A sequence of real-valued functions $\\{f_n\\}$ defined on a set $E(\subset \mathbb{R})$ converges **uniformly** to $f$ on $E$, if for every $\epsilon>0$, there exists a positive integer $\mathbb{N}\in\mathbb{N}$ such that 

$$
\begin{align*}
\lvert f_n(x) - f(x)\rvert < \epsilon
\end{align*}
$$
for all $x\in E$ and for all $n\geq N$. We write $f_n\rightrightarrows f.$ Similarly, a series $\sum_{k=1}^\infty f_k$ of real-valued functions converges uniformly on a set $E$ if and only if the sequences $\\{S_n=\sum_{k=1}^n f_k\\}$ of partial sums converges uniformly on $E$.

## Remark
(a) If $f_n \rightrightarrows f$, then $f_n\rightarrow f$. 

(b) Moreover, if $f_n\rightrightarrows f$ and $f_n\to g$, then. $f=g$

<*Proof*>
(a) It is clear.

(b) Let $\epsilon >0$ be given and let $x\in E$ be given. Then there is $N_1\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N_1 \Rightarrow \lvert f_n(x) -f(x) \rvert < \frac{\epsilon}{2}.
\end{align*}
$$

Similarly, for a given $x\in E$, there is $N_2\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N_2 \Rightarrow \lvert f_n(x) -g(x)\rvert < \frac{\epsilon}{2}.
\end{align*}
$$

Take $N=\max\\{N_1, N_2\\}$. Then

$$
\begin{align*}
\lvert f(x)-g(x)\vert &\leq \lvert f_n(x)-f(x)\rvert + \lvert f_n(x)-g(x) \rvert \\
&< \frac{\epsilon}{2} +\frac{\epsilon}{2} \\
&=\epsilon
\end{align*}
$$

Since $\epsilon >0$ is arbitrary, $f(x)=g(x)$ for all $x\in E$.

$\therefore f=g$.
$$\tag*{$\square$}$$

## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
