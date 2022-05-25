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
&=\{x_1[A]^1 + \cdots +x_n[A]^n \mid (x_1, \ldots, x_n)\in \mathbb{R}^n \} \\
&=\langle [A]^1, \ldots, [A]^n \rangle
\end{align*}
$$

## Rank Theorem
For any $m\times n$ matrix $A$, the column rank of $A$ is equal to the row rank of $A$. 

<*proof*>
Since 
$$
\begin{align}
\begin{split}
n&=\dim \ker L_A + \dim \text{im}L_A \\
&=\dim \ker L_A + (\text{column rank of } A)
\end{split}
\label{eq:1}
\end{align}
$$
by dimension theorem,  it suffices to show that 
$$
\begin{equation}
n= \dim \ker L_A + (\text{row rank of } A)
\label{eq:2}
\end{equation}
$$

Let $R$ be the reduced row-echelon form of $A$. We know that $R$ is unique.  In general, the reduced row-echelon form is

$$
R= 
\begin{pmatrix}
0 &1 & * & 0  & * & 0 & * & \cdots  \\
0&0&0&1&*&0&*&\cdots \\
0&0&0&0&*&1&*&\cdots \\
0&0&0&0&0&0&0&\cdots\\
\vdots&\vdots&\vdots&\vdots &\vdots &\vdots&\vdots&\ddots \\
0&0&0&0&0&0&0&\cdots
\end{pmatrix}
$$

We know that elementary row operation does not change the row space of $A$, thus row space of $R$ is equal to the row space of $A$. We observe that dimension of the row space is the number of non-zero rows, i.e., the rows with leading one.
For the dimension of $\ker L_R$, it is same as the dimension of the solution space of $R\mathbf{x}=\mathbf{0}$. Then its dimension is the number of free variables, i.e., the number of columns with no leading one. Since elementary row operation does not change the solution space of $A\mathbf{x}=0$,  we get $\dim \ker L_A = \dim \ker L_R$. Thus, row rank of $A$ is equal to the column rank of $A$ by Equation $\ref{eq:1}$ and $\ref{eq:2}$.

$$\tag*{$\square$}$$

## Reference
- 이인석, **『**선형대수와 군**』**
