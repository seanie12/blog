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
\mathbb{N}_n:=\{1,2,\ldots,n \}
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
Set $f(k) = x_{n_k}$. Since $E$ is infinite, $f$ is defined on $\mathbb{N}$. <br /> If $m >k$, then $n_m > n_k$ and thus $x_{n_m} \neq x_{n_k}$. Therefore $f$ is one-to-one. The function $f$ is onto $E$ since if $x\in E$, then $x=x_j$ for some $j$. By construction, $n_k = j$ for some $k$ and thus $f(k) = x_{n_k}=x_j.$

$$\tag*{$\square$}$$

## Theorem 1.7.7
If $f$ maps $\mathbb{N}$ onto $A$, then $A$ is at most countable.

<*proof*>
If $A$ is finite, the result is certainly true. Suppose that $A$ is infinite. Since $f$ maps $\mathbb{N}$ onto $A$, each $a\in A$ is of the form $f(n)$ for some $n\in\mathbb{N}$. For each $a\in A$, by the well ordering principle
$$
\begin{align}
f^{-1}(a):= \{ n\in\mathbb{N}:f(n)=a\}
\end{align}
$$
has a smallest integer, which we denote by $n_a$.  Consider the mapping $a\mapsto n_a$. Since $f$ is a function,   $a\neq b \Rightarrow n_a \neq n_b$. It implies that such mapping is one-to-one. Since $f$ is onto, $f^{-1}(a) \neq \empty$ for all $a\in A$. Thus, the map is one-to-one and onto. Also, since $A$ is infinite, 
$$
\{n_a:a\in A\}
$$
is an infinite subset of $\mathbb{N}$, so it is countable by Theorem 1.7.6. 

$\therefore a\mapsto n_a$ is a one-to-one mapping of $A$ onto countable set.

$\therefore A$ is at most countable.
$$\tag*{$\square$}$$

## Theorem 1.7.15
If $$\{E_n\}_{n=1}^\infty$$ is a sequence of countable sets and 
$$
\begin{align}
S = \cup_{n=1}^\infty E_n
\end{align}
$$
then $S$ is countable.

<*proof*>
Since $E_n$ is countable for each $n\in \mathbb{N}$, we can write 
$$
\begin{align}
E_n =\{x_{n,k}: k=1,2,\ldots\}
\end{align}
$$
Since $E_n$ is an infinite subset of $S$, the set $S$ is itself is infinite.  Consider the function $h:\mathbb{N}\times\mathbb{N}\to S$ by
$$
\begin{align}
h(n,k) = x_{n,k}
\end{align}
$$
The function $h$ is onto. Also, since $\mathbb{N}\times\mathbb{N}\sim \mathbb{N}$, there exists a mapping of $\mathbb{N}$ onto S. Hence by Theorem 1.7.7, the set $S$ is countable.
$$\tag*{$\square$}$$

## Corollary 1.7.16
$\mathbb{Q}$ is countable.

<*proof*>
For each $m\in\mathbb{N}$, let 
$$
\begin{align}
E_m = \{\frac{n}{m}:n\in\mathbb{Z}\}
\end{align}
$$
The $E_m$ is countable, and since $\mathbb{Q} = \cup_{m=1}^\infty E_m$, by Theorem 1.7.15 the set $\mathbb{Q}$ is countable.

$$\tag*{$\square$}$$ 

## Theorem 1.7.17
The closed interval $[0,1]$ is uncountable.

<*proof*>
We want to show that every countable subset of $[0,1]$ is a proper subset of $[0,1]$. Thus, $[0,1]$ cannot be countable.

Let $$E=\{x_n, n=1,2,\ldots \}$$ be a countable subset of $[0,1]$. Then for each $x_n$ has a decimal expansion:
$$
\begin{align}
x_n = 0.x_{n,1}x_{n,2}x_{n,3}\cdots
\end{align}
$$
where for each $$k\in \mathbb{N}, x_{n,k}\in \{0,1,\ldots, 9\}$$. We now define a new number 
$$
y:= 0.y_1y_2y_3\cdots
$$
as follows: If $x_{n,n} \leq 5$, define $y_n :=6$; if $x_{n,n} \geq 6$, define $y_n=3$. Then $y\in [0,1]$, and since $y_n \neq 0$ or 9, $y \neq x_{n,n}$, we have $y\neq x_n$ for any $n$.

$\therefore y\not\in E$ <br /> $\therefore E$ is a proper subset of $[0,1]$. 
$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
