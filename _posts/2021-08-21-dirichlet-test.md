---
title: "Dirichlet Test and Absolute Convergence"

categories:
  - Analysis

tags:
  - Abel Partial Summation Formula
  - Dirichlet Test
  - Absolute convergence
  - Rearrangement of series
 

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Theorem 7.2.1
Let $\\{a_k\\}$ and $\\{b_k\\}$ be a sequence of real numbers.  Set $A_0:=0, A_n:=\sum_{k=1}^n a_k$ for $n\geq 1$. Then if $1\leq p \leq q$,

$$
\begin{align*}
\sum_{k=p}^q a_k b_k = \sum_{k=p}^{q-1}A_k(b_k-b_{k+1}) + A_q b_q - A_{p-1}b_p
\end{align*}
$$

<*Proof*>

$$
\begin{align*}
\sum_{n=p}^q a_nb_n &= \sum_{n=p}^q(A_n - A_{n-1})b_n \\
&=\sum_{n=p}^q A_n b_n - \sum_{n=p}^q A_{n-1}b_n\\
&=\sum_{n=p}^q A_n b_n - \sum_{n=p-1}^{q-1} A_{n}b_{n+1}\\
&=\sum_{n=p}^{q-1} A_n (b_n-b_{n+1}) + A_qb_q - A_{p-1}b_p
\end{align*}
$$

$$\tag*{$\square$}$$

## Theorem 7.2.2 (Dirichlet Test)
Suppose $\\{ a_k\\}$ and $\\{b_k\\}$ are sequences of real numbers satisfying the following:

(a) the partial sums $A_n=\sum_{k=1}^n a_k$ form a bounded sequence.

(b) $b_1\geq b_2 \geq b_3 \geq \cdots \geq 0$, and

(c) $\lim_{k\to\infty}b_k = 0$

Then $\sum_{k=1}^\infty a_k b_k$ converges.

<*Proof*>

Since $\\{A_k\\}$ is bounded, there is $M>0$ such that $\lvert A_n \rvert \leq M$ for all $n\in\mathbb{N}$. Let $\epsilon >0$ be given. Since $b_n$ is bounded below and  monotone decreasing, there is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N \Rightarrow b_n < \frac{\epsilon}{2M}.
\end{align*}
$$

If $q\geq p \geq N$,

$$
\begin{align*}
\left\lvert \sum_{k=p}^q a_k b_k \right\rvert &= \left\lvert\sum_{k=p}^{q-1}A_k(b_k - b_{k-1}) - A_{p-1}b_p - A_q b_q \right\rvert \\
&\leq \sum_{k=p}^{q-1}\lvert A_k\rvert \lvert b_k - b_{k+1}\rvert + \lvert A_{p-1}\rvert b_p + \lvert A_q \rvert b_q \\
&\leq M \left( \sum_{k=p}^{q-1}(b_k - b_{k-1}) + b_p +b_q \right) \\
&=2Mb_p \\
&<\epsilon
\end{align*}
$$

By Theorem 7.2.1 the first equality holds. By Cauchy criterion, $\sum_{k=1}^\infty a_kb_k$ converges.

$$\tag*{$\square$}$$

## Theorem 7.2.3 (Alternating Series Test)
If $\\{b_k\\}$ is a sequence of real numbers satisfying

(a) $b_1 \geq b_2 \geq \cdots \geq 0$, and 

(b) $\lim_{k\to\infty} b_k=0$

then $\sum_{k=1}^\infty (-1)^{k+1}b_k$ converges.

<*Proof*>

Let $a_k =(-1)^{k+1}$ and let $A_n=\sum_{k=1}^na_k$. Then $\lvert A_n \rvert \leq 1$ for all $n\in\mathbb{N}$. By Dirichlet test $\sum_{k=1}^\infty (-1)^{k+1}b_k$ converges.

$$\tag*{$\square$}$$

## Theorem (Leibniz's Theorem on Alternating Series)
$\sum_{n=1}^\infty c_n$ is a series such that

(a) $c_{2m}\leq 0, c_{2m+1} \geq 0$ for all $m\in\mathbb{N}$,

(b) $\lim_{n\to\infty}c_n = 0$,

(c) $\lvert c_1 \rvert \geq \lvert c_2 \rvert \geq \lvert c_3 \rvert \geq \cdots$,

then $\sum_{n=1}^\infty c_n$ converges.

<*Proof*>

Let $a_n = (-1)^{n+1}$ and let $b_n=\lvert c_n \rvert$. Then $c_n = a_n b_n$. By Dirichlet test, $\sum_{n=1}^\infty c_n$ converges.

$$\tag*{$\square$}$$

## Theorem 7.2.4 

Consider the series $\sum_{k=1}^\infty (-1)^{k+1}b_k$, where the sequence $\\{b_k\\}$ satisfies the hypothesis of Theorem 7.2.3. Let 

$$
\begin{align*}
S_n = \sum_{k=1}^n (-1)^{k+1}b_k \quad \text{and} \quad S = \sum_{k=1}^\infty (-1)^{k+1}b_k.
\end{align*}
$$

Then $\lvert s- s_n\rvert\leq b_{n+1}$ for all $n\in\mathbb{N}$.

<*Proof*>

Since $\\{b_k\\}$ is monotone decreasing $b_{k-1}-b_k \geq 0$,

$$
\begin{align*}
S_{2n} &= \sum_{k=1}^{2n} (-1)^{k+1}b_k \\
&=(b_1 - b_2) + (b_2 - b_3) + \cdots + (b_{2n-1} -b_{2n}).
\end{align*}
$$

Thus $\\{S_{2n}\\}$ is a monotone increasing sequence. Similarly, $\\{S_{2n-1}\\}$ is monotone decreasing sequence. Since $S_n\to S$, we have $S_{2n} \to S$ and $S_{2n-1}\to S$ as $n\to\infty$. In other words,

$$
\begin{align*}
\sup_{n\in\mathbb{N}} S_{2n} = S = \inf_{n\in\mathbb{N}}S_{2n-1},
\end{align*}
$$

which implies that $S_{2n} \leq S \leq S_{2n+1}$ for all $n\in\mathbb{N}$. Thus, $\lvert S- S_{2n}\rvert \leq \lvert S_{2n} -S_{2n-1}\rvert$ and $\lvert S - S_{2n-1}\rvert \leq \lvert S_{2n} - S_{2n-1}\rvert$for all $n\in\mathbb{N}$, i.e., 

$$
\begin{align*}
\lvert S -S_n \vert \leq |S_{n+1}-S_n\rvert = b_{n+1}
\end{align*}
$$

for all $n\in\mathbb{N}$.

$$\tag*{$\square$}$$

## Definition 7.3.1
A series $\sum_{k=1}^\infty a_k$ of real numbers is said to be **absolutely convergence** if $\sum_{k=1}^n \lvert a_k\rvert$ converges. The series is said to be **conditionally convergent** if it is convergent but not absolutely convergent.

## Theorem 7.3.3
if $\sum_{k=1}^\infty a_k$ converges absolutely, then $\sum_{k=1}^\infty a_k$ converges and 

$$
\begin{align*}
\left\lvert \sum_{k=1}^\infty a_k \right\rvert \leq \sum_{k=1}^\infty \lvert a_k \rvert.
\end{align*}
$$

Let $\epsilon >0$ be given. Since $\sum_{k=1}^\infty \lvert a_k\rvert$ converges, by Cauchy criterion there is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
m > n \geq N \Rightarrow \sum_{k=n}^m \lvert a_k \rvert < \epsilon.
\end{align*}
$$

By triangle inequality, 

$$
\left\lvert \sum_{k=n}^m a_k \right\rvert \leq \sum_{k=n}^m \lvert a_k \rvert < \epsilon
$$ 

for all $m>n\geq N$. Thus $\sum_{k=1}^\infty a_k$ converges.

Finally,

$$
\begin{align*}
\left\lvert \sum_{k=1}^\infty a_k\right\rvert  &= \left\lvert \lim_{n\to\infty} \sum_{k=1}^n a_k\right\rvert \\
&=\lim_{n\to\infty}  \left\lvert \sum_{k=1}^n a_k\right\rvert \quad (\because x\mapsto \lvert x\rvert \text{ is continous}) \\
&=\lim_{n\to\infty}\sum_{k=1}^n \lvert a_k \rvert \\
&=\sum_{k=1}^\infty \lvert a_k \rvert
\end{align*}
$$

$$\tag*{$\square$}$$


## Definition 7.3.6
A series $\sum a^\prime_k$ is a **rearrangement** of the series $\sum a_k$ if there exists a one-to-one function $j$ from $\mathbb{N}$ onto $\mathbb{N}$ such that $a^\prime_k = a_{j(k)}$ for all $k\in\mathbb{N}$.


## Theorem 7.3.8
If the series $\sum a_k$ converges absolutely, then every rearrangement of $\sum a_k$ converges to the same sum.

<*Proof*>

Let $\sum a_k^\prime$ be a rearrangement of $\sum a_k$. Let $\epsilon >0$ be given. Then there exists $N\in\mathbb{N}$ such that 

$$
\begin{align}
m>n\geq N \Rightarrow \sum_{k=n}^m \lvert a_k \rvert < \epsilon.
\label{eq:1}
\end{align}
$$

Suppose that $a^\prime_k = a_{j(k)}$, where $j$ is a one-to-one function of $\mathbb{N}$ onto $\mathbb{N}$. Choose an integer $p (p\geq N)$ such that 

$$
\begin{align*}
\{1,2,\ldots, N\} \subset \{j(1), j(2), \ldots, j(p)\}.
\end{align*}
$$

Such a $p$ exists since $j$ is bijective. For example, we can set $p=\max\\{j^{-1}(1), j^{-1}(2), \ldots, j^{-1}(N) \\}$. Let 

$$
\begin{align*}
s_n = \sum_{k=1}^n a_k \quad \text{and}\quad s^\prime_n = \sum_{k=1}^n a^\prime_k.
\end{align*}
$$

If $n\geq p$, 

$$
\begin{align*}
s_n - s^\prime_n = \sum_{k=1}^n a_k - \sum_{k=1}^n a_{j(k)}.
\end{align*}
$$

By the choice of $p$, the numbers $a_1, \ldots, a_N$ appear in both sums and consequently cancel. Thus, the only terms remaining will have index $k$ or $j(k)$ greater than $N$. Let $\Lambda$ be the set of indices of the remaining terms. Then

$$
\begin{align*}
\lvert s_n - s^\prime_n \rvert &\leq \sum_{\lambda \in \Lambda} \lvert a_\lambda \rvert\\
& \leq \sum_{k=\min\Lambda}^{\max\Lambda+1} \lvert a_k \rvert \\
&< \epsilon \quad (\because \max\Lambda \geq \min\Lambda >N \text{ and by equation }\ref{eq:1})
\end{align*}
$$

$\therefore \lim_{n\to\infty} s^\prime_n = \lim_{n\to\infty}s_n$.

$$\tag*{$\square$}$$

## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
