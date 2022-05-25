---
title: "Dimension Theorem and Rank Theorem"

categories:
  - Linear Algebra

tags:
  - dimension theorem
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

## Dimension Theorem
Let $(V,+,\cdot)$, $(W,+,\cdot)$ be  finite dimensional  vector spaces of $F$. Let $\varphi: V\rightarrow W$ be a linear map. Then $\dim V= \dim \ker \varphi + \dim \text{im}\varphi$.

<*proof*>

Suppose that $\dim V = n$. Let 
$$S=\{\mathbf{v}_1, \ldots, \mathbf{v}_k \}$$
be a basis for $\ker\varphi$. 
By the basis extension theorem, we get a basis $$\{ \mathbf{v}_1, \ldots, \mathbf{v}_k, \mathbf{v}_{k+1}, \ldots, \mathbf{v}_n\}$$  for $V$ by extending the set S. It suffices to show that $$\{ \varphi(\mathbf{v}_{k+1}), \ldots, \varphi(\mathbf{v}_n)\}$$ is a basis for im$\varphi$.

Suppose that 

$$
\begin{equation}
a_{k+1}\varphi(\mathbf{v}_{k+1}) + \cdots + a_{n}\varphi(\mathbf{v}_n) =\mathbf{0}.
\end{equation}
$$

By linearity of $\varphi$, 

$$
\begin{equation}
a_{k+1}\varphi(\mathbf{v}_{k+1}) + \cdots + a_{n}\varphi(\mathbf{v}_n)=\varphi\left(\sum_{i=k+1}^na_i\mathbf{v}_i\right) = \mathbf{0}.
\end{equation}
$$

That is $\sum_{i=k+1}^na_i\mathbf{v}_i\in \ker\varphi$. Since $S$ is a basis for $\ker\varphi$,

$$
\begin{equation}
\sum_{i=k+1}^na_i\mathbf{v}_i = \sum_{j=1}^k b_j\mathbf{v}_j \Rightarrow \sum_{i=k+1}^na_i\mathbf{v}_i - \sum_{j=1}^k b_j\mathbf{v}_j = \mathbf{0}.
\end{equation}
$$

Since $$\{\mathbf{v}_1, \ldots, \mathbf{v}_n\}$$ is a basis for $V$, $a_i=0, b_j=0$ for all  $i=1,\ldots, k$ and $j=k+1, \ldots, n$. Thus, $$\{ \varphi(\mathbf{v}_{k+1}), \ldots, \varphi(\mathbf{v}_n)\}$$ is linearly independent subset.

Let $\mathbf{w}\in \text{im}\varphi$ be given. Then $\mathbf{w} = \varphi(\mathbf{v})$ for some $\mathbf{v}\in V$. Since $$\{\mathbf{v}_1, \ldots, \mathbf{v}_n\}$$ is a basis for $V$, we get a unique linear combination of $\mathbf{v}=\sum_{i=1}^n a_i \mathbf{v}_i$.

$$
\begin{align*}
\varphi(\mathbf{v})&=\varphi\left(\sum_{i=1}^n a_i \mathbf{v}_i\right) \\
&=\sum_{i=1}^na_i\varphi(\mathbf{v}_i) \\
&=\sum_{i=k+1}^n a_i\varphi(\mathbf{v}_i) \\
&\in \text{span}\{ \varphi(\mathbf{v}_{k+1}, \ldots, \varphi(\mathbf{v}_n)\}
\end{align*}
$$

The last equality holds since $\mathbf{v}_j \in \ker\varphi$, i.e., $\varphi(\mathbf{v}_j)=\mathbf{0}$ for all $j=1,\ldots,k$.  Thus, $$\{\varphi(\mathbf{v}_{k+1}), \ldots, \varphi(\mathbf{v}_n)\}$$ generates im$\varphi$.

$$\tag*{$\square$}$$
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
