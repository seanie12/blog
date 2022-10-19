---
title: "Convergence Test - (1)"

categories:
  - Analysis

tags:
  - comparison test
  - root test
  - ratio test
 

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition
Let $\\{a_n\\}$ be a sequence. Define a new sequence of $s_n := \sum_{k=1}^na_k$ for $n\geq 1$. We call the $s_n$ is the $n$-th partial sum of $\\{a_n\\}$. If the sequence of partial sums converges (say $s_n\to s$), we write $\sum_{n=1}^\infty a_n=s$ and say **the infinite series** $\sum_{n=1}^na_n$ sums to $s$.


## Theorem 7.1.1
Suppose that $\sum_{n=1}^\infty a_n = \alpha, \sum_{n=1}^\infty b_n =\beta$ where $\alpha,\beta\in\mathbb{R}$.

(a) $\sum_{n=1}^\infty c a_n = c \sum_{n=1}^\infty a_n= c\alpha$

(b) $\sum_{n=1}^\infty a_n + b_n = \sum_{n=1}^\infty a_n + \sum_{n=1}^\infty b_n=\alpha +\beta$

<*Proof*>

(a)

$$
\begin{align*}
\sum_{n=1}^\infty c a_n&= \lim_{n\to\infty} \sum_{k=1}^n c a_k \\
&= \lim_{n\to\infty}c \sum_{k=1}^n a_k \\
&=c \lim_{n\to\infty}\sum_{k=1}^n a_k \\
&= c \sum_{n=1}^\infty a_n \\
&= c\alpha
\end{align*}
$$

(b) 

$$
\begin{align*}
\sum_{n=1}^\infty a_n + b_n &= \lim_{n\to\infty}\sum_{k=1}^n a_k + b_k \\
&=\lim_{n\to\infty}\left(\sum_{k=1}^na_k + \sum_{k=1}^n b_k \right) \\
&=\sum_{n=1}^\infty a_n + \sum_{n=1}^\infty b_n \\
&=\alpha + \beta
\end{align*}
$$

$$\tag*{$\square$}$$

## Remark
If $\sum_{n=1}^\infty  a_n$ converges, then $\lim_{n\to\infty}a_n=0$.

<*Proof*>
Let $S_n = \sum_{k=1}^n a_k$ and let $L=\sum_{n=1}^\infty a_n$.
For given $\epsilon >0$, there exists $N\in\mathbb{N}$ such that $n\geq N \Rightarrow \lvert S_n - L \rvert$. Since $S_n$ converges, $S_n$ is Cauchy. Thus there exists $N_2\in \mathbb{N}$ such that $n+1>n\geq N_2 \Rightarrow \lvert S_{n+1}-S_n\rvert =\lvert a_{n+1}\rvert < 0$.

$\therefore \lim_{n\to\infty} a_n=0$ 

$$\tag*{$\square$}$$


## Theorem 7.1.2 (Comparison Test)
Let $\\{a_n\\}, \\{b_n\\},\text{and } \\{c_n\\}$ be sequences in $\mathbb{R}$. 

(1) Suppose that $\lvert a_n\rvert \leq b_n$ for all $n\geq N_0$ for some $N_0\in\mathbb{N}$. If $\sum_{n=1}^\infty b_n$ converges, then $\sum_{n=1}^\infty a_n$ converges.

(2) Suppose that $a_n \geq c_n$ for all $n\geq N_0$ for some $N_0\in\mathbb{N}$. If $\sum_{n=1}^\infty c_n$, then $\sum_{n=1}^\infty a_n$ diverges.


<*Proof*>

(1)
Let $\epsilon >0$ be given. Since $\sum_{n=1}^\infty b_n$ converges, there is $N\in\mathbb{N}$ such that $m>n\geq N_1 \Rightarrow \lvert \sum_{k=n}^m b_k\rvert < \epsilon$ .

For all $m,n$ with $m>n\geq N$, 

$$
\begin{align*}
\left\lvert \sum_{k=n}^m a_k \right\rvert &\leq \left\lvert \sum_{k=n}^m a_k\right\rvert \\
&\leq \sum_{k=n}^m \lvert a_k \rvert \\
&\leq \sum_{k=n}^m b_k \\
&< \epsilon
\end{align*}
$$

By Cauchy Criterion, $\sum_{n=1}^\infty a_n$ converges.

(2) By (1), if $\sum_{n=1}^\infty a_n$ converges, then $\sum_{n=1}^\infty c_n$ converges. Thus, if $\sum_{n=1}^\infty c_n$ diverges, $\sum_{n=1}^\infty a_n$ diverges.

## Corollary 7.1.3 (Limit Comparison Test)
Let $\\{a_n\\}$ and $\\{b_n \\}$ be positive sequences in $\mathbb{R}$.

(a) 

$$
\begin{align*}
\lim_{n\to\infty}\frac{a_n}{b_n}=L \text{ with } 0<L<\infty \Rightarrow \sum_{n=1}^\infty a_n \text{ converges if and only if } \sum_{n=1}^\infty b_n \text{ converges}.
\end{align*}
$$

(b) 

$$
\begin{align*}
\lim_{n\to\infty}\frac{a_n}{b_n}=0, \sum_{n=1}^\infty b_n \text{ converges} \Rightarrow  \sum_{n=1}^\infty a_n \text{ converges}.
\end{align*}
$$

<*Proof*>

Take $\epsilon_0:=\frac{L}{2}>0$. Then there is $k_0\in\mathbb{N}$ such that $k\geq k_0 \Rightarrow \left\lvert \frac{a_k}{b_k}-L \right\rvert <\frac{L}{2}$. In other words,

$$
\begin{equation}
0<\frac{L}{2} < \frac{a_k}{b_k} < \frac{3}{2}L
\label{eq:1}
\end{equation}
$$

$\Rightarrow$ Suppose that $\sum_{n=1}^\infty a_n <\infty$. By equation$~\ref{eq:1}$, $b_k < \frac{2}{L}a_k$ for all $k\geq k_0$. Since $\sum_{n=1}^\infty a_n < \infty$, $\sum_{n=1}^\infty b_n <\infty$ by comparison test.

$\Leftarrow$ Conversely, suppose that $\sum_{n=1}^\infty b_n < \infty$. By equation $\ref{eq:1}$, 

$$
\begin{align*}
a_k < \frac{3}{2}Lb_k
\end{align*}
$$

for all $k\geq k_0$.

Since $\sum_{n=1}^\infty  b_n <\infty$, $\sum_{n=1}^\infty <\infty$ by comparison test.

(b) 
## Reference
- Stephen Friedberg, Arnold Insel, and Lawrence Spence **『**Linear Algebra**』**
