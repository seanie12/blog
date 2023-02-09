---
title: "Pointwise Convergence and Uniform Convergence"

categories:
  - Analysis

tags:
  - Sequence of functions
  - Series of functions
  - Pointwise convergence
  - Uniform convergence
  - Cauchy criterion
  - Weierstrass M-Test

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


## Examples 8.2.2
(a) $f_n(x) = x^n$ on $E=[0,1]$. Then $f_n \to f$ as $n\to\infty$ where

$$
\begin{align*}
f(x) = \begin{cases}
0 & \text{if } x \in [0, 1) \\
1 & \text{if } x = 1.
\end{cases}
\end{align*}
$$

We want to show that $f_n$ does not converge uniformly to $f$. Suppose that $f_n\rightrightarrows f$ . Given $\epsilon>0$, there is $n_0\in\mathbb{N}$ such that 

$$
\begin{align*}
\lvert f_n(x) -f(x)\rvert <\epsilon
\end{align*}
$$

for all $x\in E$ and for all $n \geq n_0$. If $x\in [0,1)$, then $x^{n_0}<\epsilon$. Take $0<\epsilon_0 <1-\epsilon$.

Since $f_{n_0}$ is continuous on $E$, there is a $\delta>0$ such that 

$$
\begin{align*}
\lvert x-1 \rvert <\delta \text{ with } x\in E \Rightarrow \lvert x^{n_0}-1\rvert < \epsilon_0.
\end{align*}
$$

In other words,

$$
\begin{align*}
x\in (1-\delta, 1+\delta) \cap E \Rightarrow 1-\epsilon_0 < x^{n_0} < 1+\epsilon_0.
\end{align*}
$$

But it implies that $x^{n_0} < \epsilon < 1-\epsilon_0< x^{n_0}$, which is a contradiction.

$\therefore f_n$ does not converge uniformly.

On the other hand, if we set the domain $E=[0,a)$ with $0<a<1$, then $f_n\rightrightarrows f$ on $[0,a)$. 

Let $\epsilon >0$ be given. Since $0<x<a,  \lvert x^n\rvert <a^n$. Since $0<a<1$, there is $n_0\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq n_0 \Rightarrow a^n <\epsilon.
\end{align*}
$$

Thus, for $n\geq n_0, x\in [0,a)$, $\lvert x^n\rvert <\epsilon$.

$\therefore f_n \rightrightarrows f$ on $[0,a)$.

$$\tag*{$\square$}$$

## Theorem 8.2.3 (Cauchy Criterion)
A sequence $\\{f_n\\}$ of real-valued functions defined on a set $E$ converges uniformly on $E$ if and only if for every $\epsilon>0$, there exists $n_0\in\mathbb{N}$ such that 

$$
\begin{align*}
\lvert f_n(x) - f_m(x) \rvert <\epsilon
\end{align*}
$$
for all $x\in E$ and all $n,m \geq n_0$.

<*Proof*>

$\Rightarrow$ Let $\epsilon >0$ be given. There is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
m,n\geq N, x\in E \Rightarrow \lvert f_n(x) - f_m(x) \rvert <\frac{\epsilon}{2}.
\end{align*}
$$

For $n,m\in\mathbb{N}$ with $m,n \geq N$,

$$
\begin{align*}
\lvert f_m(x) - f_n(x) \rvert &= \lvert f_m(x) - f(x) + f(x) - f_n(x) \rvert \\
&\leq \lvert f_m(x) - f(x) \rvert + \lvert f(x) - f_n(x)\rvert \\
&\leq \frac{\epsilon}{2} + \frac{\epsilon}{2} \\
&=\epsilon.
\end{align*}
$$

$\Leftarrow$ Let $\epsilon >0$ be given. By the given hypothesis, there is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
m,n \geq N, x\in E \Rightarrow \lvert f_m(x) - f_n(x)\rvert  <\frac{\epsilon}{2}.
\end{align*}
$$

For each $x\in E, (f_n(x))_{n=1}^\infty$ is Cauchy sequence and hence it converges. Let $f(x) = \lim_{n\to\infty}f_n(x)$ for every $x\in E$.

Fix $m\geq N$ and $x\in E$. Then,

$$
\begin{align*}
\lvert f(x) - f_m (x)\rvert &=\lvert \lim_{n\to\infty}f_n(x)-f_m(x)\rvert \\
 &= \lim_{n\to\infty}\lvert f_n(x) - f_m(x) \rvert \quad (\because y\mapsto \lvert y-f_m(x)\rvert \text{ is continuous})\\
&\leq \frac{\epsilon}{2}  \\
&< \epsilon
\end{align*}
$$

$\therefore f_n\rightrightarrows f$.

$$\tag*{$\square$}$$

## Corollary 8.2.4
The series $\sum_{k=1}^\infty f_k$ of real-valued functions on $E$ converges uniformly on $E$ if and only if given $\epsilon >0$, there exists a positive integer $n_0\in\mathbb{N}$ such that 

$$
\begin{align*}
\left\lvert \sum_{k=n+1}^m f_k \right\rvert  < \epsilon
\end{align*}
$$

for all $x\in E$ and for all integers $m>n\geq n_0$.

## Theorem 8.2.5
Suppose the sequence $\\{f_n\\}$ of real-valued functions on the set $E$ converges pointwise to $f$ on $E$. For each $n\in\mathbb{N}$, set 

$$
\begin{align*}
M_n = \sup_{x\in E}\lvert f_n(x) - f(x)\rvert.
\end{align*}
$$

Then $\\{f_n\\}$ converges uniformly to $f$ on $E$ if and only if $\lim_{n\to\infty} M_n =0$.

$\Rightarrow$ Let $\epsilon >0$ be given. Since $f_n \rightrightarrows f$, there exists a $N\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N, x\in E \Rightarrow \lvert f_n(x) - f(x) \rvert < \frac{\epsilon}{2}.
\end{align*}
$$

For $n\geq N, \frac{\epsilon}{2}$ is an upper bound of $\\{\lvert f_n (x) -f(x) \rvert : x\in E\\}$. Thus, 

$$
\begin{align*}
M_n=\sup_{x\in E} \lvert f_n(x) - f(x) \rvert \leq \frac{\epsilon}{2} < \epsilon
\end{align*}
$$

for all $n\geq N$.

$\therefore \lim_{n\to\infty}M_n = 0.$

$\Leftarrow$ Let $\epsilon >0$ be given. Since $M_n\to 0$ as $n\to\infty$, there is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N\Rightarrow \lvert M_n \rvert <\epsilon.
\end{align*}
$$

Thus, for $n\geq N$ and for all $x\in E$,

$$
\begin{align*}
\lvert f_n(x) -f(x) \rvert \leq \sup_{x\in E} \lvert f_n(x) -f(x)\rvert <\epsilon.
\end{align*}
$$

$\therefore f_n \rightrightarrows f$.

$$\tag*{$\square$}$$

## Theorem 8.2.7 (Weierstrass M-Test)
Suppose $\\{f_k\\}$ is a sequence of real-valued functions defined on a set $E$, and $\\{M_k\\}$ is a sequence of real numbers satisfying 

$$
\begin{align*}
\lvert f_k(x) \rvert \leq M_k \quad \text{for all } x\in E \text{ and } k\in\mathbb{N}.
\end{align*}
$$

If $\sum_{k=1}^\infty M_k$ converges, then $\sum_{k=1}^\infty f_k(x)$ converges uniformly and absolutely on $E$.

<*Proof*>

Let $\epsilon >0$ be given and let $T_n = \sum_{k=1}^n M_k$. Since $T_n$ converges, $T_n$ is Cauchy sequence. Thus, for given $\epsilon >0$, there is $N\in\mathbb{N}$ such that

$$
\begin{align*}
n>m\geq N \Rightarrow \lvert T_n - T_m \rvert = \left\lvert \sum_{k=m+1}^n M_k \right\rvert < \epsilon.
\end{align*}
$$

Define $S_n(x) = \sum_{k=1}^n f_k(x)$. If $n>m\geq N$,  

$$
\begin{align*}
\left \lvert S_n (x) - S_m(x)\right \rvert &= \left\lvert \sum_{k=m+1}^n f_k(x) \right\rvert \\
&\leq \sum_{k=m+1}^n\lvert f_k(x) \rvert \\
&\leq \sum_{k=m+1}^n M_k \\
&<\epsilon.
\end{align*}
$$

By Cauchy criterion, $\sum_{k=1}^\infty f_k$ converges uniformly on $E$.

$$\tag*{$\square$}$$
## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
