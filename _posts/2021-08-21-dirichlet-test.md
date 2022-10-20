---
title: "Dirichlet Test "

categories:
  - Analysis

tags:
  - Abel Partial Summation Formula
  - Dirichlet Test

 

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
## Reference
- Manfred Stoll**『**Introduction to Real Analysis**』**
