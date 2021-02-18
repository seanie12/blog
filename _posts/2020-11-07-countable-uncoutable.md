---
title: "Countable and Uncountable sets"

categories:
  - Analysis


tags:
  - countable
  - uncountable
  - Cantor's diagonal process

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 1.7.2
For each positive integer $n\in \mathbb{N}$, let $$
N_n:=\{1,2,\ldots,n \}
$$. If $A$ is a set, we say <br /> (a) $A$ is **finite** if $A\sim \mathbb{N}_n$ for some $n$, or if $A=\emptyset$, where $\sim$ denotes equivalence relation if there exists a one-to-one function of $A$ onto $\mathbb{N}_n$. <br /> (b) If $A$ is **infinite** if $A$ is not finite. <br /> (c) $A$ is **countable** if $A\sim \mathbb{N}$. <br /> (d) $A$ is **uncountable** if $A$ is neither finite nor countable. <br /> (e) $A$ is **at most countable** if $A$ is finite or countable. 

## Theorem 1.7.4
$\mathbb{N}\times\mathbb{N}$ is countable

<*proof*>
Construct a one-to-one mapping of $\mathbb{N}\times \mathbb{N}$ onto $\mathbb{N}$. Such a function is given by
$$
\begin{align}
f(m,n):=2^{m-1}(2n-1), \text{where } n,m \in \mathbb{N}
\end{align}
$$
First we want to show that the function $f$ is injective. Suppose that $f(m_1,n_1) = f(m_2, n_2)$ for $(m_1,n_1), (m_2,n_2)\in \mathbb{N}\times\mathbb{N}$. Since the prime factorization is unique, $2^{m_1-1}=2^{m_2-1}$, in other words, $m_1=m_2$. Therefore, $2n_1-1=2n_2-1$, i.e. $n_1=n_2$. 

$\therefore f$ is injective.

Now we want to show that $f$ is onto. Let $a\in\mathbb{N}$ be given. Since $(2n-1)$ is odd number, the powers of 2 in the prime decomposition of $a$ are exactly $m-1$ and from there $n$ is determined. 

$\therefore f$ is onto 

$$\tag*{$\square$}$$

## Theorem 1.7.6
Every infinite subset of a countable set is countable.

<*proof*>
Let $A$ be a countable set and let $$\{x_n:n=1,2,\ldots\}$$ be an enumeration of $A$.  Suppose $E$ is an infinite subset of $A$. Then each $x\in E$ is of the form of $x_k$ for some $k\in \mathbb{N}$.

We inductively construct a function $f:\mathbb{N}\to E$ as follows: Let $n_1$ be the smallest integer such that $x_{n_1}\in E$. Such an integer exists by the well ordering principle. Having chosen $n_1,\ldots, n_{k-1}$, let $n_k$ be the smallest integer greater than $n_{k-1}$ such that 
$$
\begin{align}
x_{n_k}\in E\setminus \{x_{n_1},\ldots, x_{n_{k-1}} \}
\end{align}
$$
Set $f(k) = x_{n_k}$. Since $E$ is infinite, $f$ is defined on $\mathbb{N}$. <br /> If $m >k$, then $n_m > n_k$ and thus $x_{n_m} \neq x_{n_k}$. Therefore $f$ is one-to-one. The function $f$ is onto $E$ since if $x\in E$, then $x=x_j$ for some $j$. By construction, $n_k = j$ for some $k$ and thus $f(k) = x.

$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
