---
title: "Rank Theorem"

categories:
  - Linear Algebra

tags:
  - rank
  - rank theorem
 

toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition 
Let $A\in \mathfrak{M}_{m\times n}(\mathbb{R})$ be a matrix. We define the column rank of $A$ as dimension of $\langle [A]^1, \ldots, [A]^n \rangle$, i.e., span of column vectors, where $[A]^j\in \mathbb{R}^m$ denotes $j$-th column of the matrix $A$. Similarly, we define the row rank of $A$ as dimension of $\langle [A]_1, \ldots, [A]_m\rangle$, where $[A]_i\in\mathbb{R}^n$ denotes a $i$-th row of $A$.

## Remark
Note that column space $\langle [A]^1, \ldots, [A]^n\rangle$ and row space $\langle [A]_1, \ldots , [A]_m\rangle$ is subspace of $\mathbb{R}^m$ and $\mathbb{R}^n$, respectively. Moreover column space is equal to the image of $L_A$, where $L_A: \mathbb{R}^n \rightarrow \mathbb{R}^m$ is a linear map such that $\mathbf{x}\mapsto A\mathbf{x}$.

$$
\begin{align*}
\text{im} L_A &= \{A\mathbf{x} \mid \mathbf{x}\in\mathbb{R}^n \} \\
&=\{x_1[A]^1 + \cdots x_n[A]^n \mid (x_1, \ldots, x_n)\in \mathbb{R}^n \} \\
&=\langle [A]^1, \ldots, [A]^n \rangle
\end{align*}
$$

## Rank Theorem



$$\tag*{$\square$}$$
## Reference
- James Munkres, **『**Topology**』**, Pearson
