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
## Reference
- Manfred Stoll**『**Introduction to Real Analysis**』**
