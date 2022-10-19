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
Let $\\{a_n\\}$ be a sequence. Define a new sequence of $s_n := \sum_{k=1}^na_k$ for $n\geq 1$. We call the $s_n$ is the $n$-th partial sum of $\\{a_n\\}$. If the sequence of partial sums converges (say $s_n\to s$), we write $\sum_{n=1}^\inftya_n=s$ and say **the infinite series** $\sum_{n=1}^na_n$ sums to $s$.


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


## Reference
- Stephen Friedberg, Arnold Insel, and Lawrence Spence **『**Linear Algebra**』**
