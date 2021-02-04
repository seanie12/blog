---
title: "Cantor Set"

categories:
  - Analysis

tags:
  - Cantor set
  - measure zero
  - uncountable
  

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition of Cantor Set
For each $P_i$ is non empty compact set and $P_0 \supset P_1 \supset P_2 \cdots$. Define $P$ as follows:
$$
\begin{align}
P := \cap_{n=0}^\infty P_n
\end{align}
$$
By the theorem 3.2.7, $P$ is nonempty compact set. We say that $P$ is the **Cantor Set**.
## Properties of Cantor Set
(1) $P \neq \emptyset$ and $P$ is compact

(2)$P$ contains all the end points of $J_{n,k} \text{ for all } n=0,1,2,\ldots, k=1,2,\ldots, 2^n$.

(3) Every point of $P$ is a limit point of $P$.

<*proof*>
Let $p \in P$ and let $\epsilon >0$ be given. Choose $m \in \mathbb{N}$ such that $\frac{1}{3^n} < \epsilon$.
Sine $p \in P_m$, $p \in J_{m,k}$ for some $k$. $J_{m,k}$ can be written as follows:
$$
J_{m,k} := [\frac{x_k}{3^m}, \frac{x_k +1}{3^m}]
$$
for some $0 < x_k <3^m$. So, we have $J_{m,k} \subset N_\epsilon (p)$ since the length of the intervals $J_{m,k} = \frac{1}{3^m} < \epsilon$. It implies that $P \cap N^{\prime} (p)$ has at least one of the end points of $J_{m,k}.$

$\therefore p$ is a limit point of $P$.
 $$\tag*{$\square$}$$
(4) The sum of the lengths of the intervals removed is 1.

<*proof*>
$$
\begin{align}
\begin{split}
\frac{1}{3} + 2\times \frac{1}{3^2} + 2^2 \times \frac{1}{3^3} + \cdots &= \sum_{n=1}^\infty \frac{2^{n-1}}{3^n} \\
&= \frac{1}{3} \sum_{n=1}^\infty \frac{2^{n-1}}{3^n}\\
&=\frac{1}{3} \cdot \frac{1}{1-\frac{2}{3}} \\
&=1
\end{split}
\end{align}
$$
 $$\tag*{$\square$}$$

(5) $P$ contains no intervals
<*proof*> Let be an interval $[a,b]$ for some $a,b \in \mathbb{R}$. Choose $n \in \mathbb{N}$ such that $\frac{1}{3^n} < b-a$.  Then any $[a,b] \not\subset J_{n,k}$.  Since $P$ is countable intersection of $P_i$ and each $P_i = \cup_{i=1}^{2^i} J_{i,k}$, $[a,b] \not\subset P.$
 $$\tag*{$\square$}$$


(6) Fore each $x \in [0,1], x = 0.n_1n_2n_3\cdots$ is the ternary expansion of $x$.
$$
x \in P \iff n_k \in \{0, 2\}
$$
<*proof*>
$\Rightarrow$
If $x=0$, it is trivial case.   Suppose $x\neq 0$.

By Remark 1.6.3, $x$ has an infinite expansion of $x$. As described in Definition 1.6.1 we choose the largest integers among 0,1,2 such that $\frac{n_1}{3} < x$. Since $\frac{1}{3} \lneq x \lneq \frac{2}{3}$, $n_1 \neq 1$.  Since $x\neq0$, $n_1= 1$. Now suppose $n_k \neq 1$
Then choose the largest integer $n_{k+1}$ among 0, 1,2 such that 
$$
\frac{n_1}{3} + \cdots + \frac{n_k}{3^{n_k}} + \frac{n_{k+1}}{3} < x. 
$$
Since $x \in P \subset P_{k+1}, x \in J_{k+1,m}$ for some $m$. Since we cut out the first middle third of $J_{k,i} \text{ for } i=1, \ldots, 2^k$ to construct $J_{k+1,j}$ for $j=1, \ldots, 2^{k+1}$, $n_{k+1} \neq 1$. 

$\therefore n_k \neq 0$ for all $k=1,2,\ldots$

$\Leftarrow$
Let  $x =0.n_1n_2\ldots$ where for all $n_i$ is 0 or 1. If $x$ has a finite ternary expansion, we can rewrite it with infinite ternary expansion by Remark 1.6.3.  

$\therefore x \in P.$
 $$\tag*{$\square$}$$
 
 (7) $P$ is uncountable
<*proof*>
Construct a function $f: P \rightarrow [0,1]$. We want to show that the $f$ is surjective. If so, the cardinality of $P$ is greater than or equal to $[0,1]$. 

Since every $x \in P$, $x=0.n_1 n_2 \cdots$ where $n_k \neq 1$ with ternary expansion. Then the function $f$ is defined by replacing all the occurrences of 2 with 1.  

For every $a \in [0,1]$,  represent it with binary in binary form. Then there is $b \in P$ such that $f(b) = a$ because replacing all the occurrences of 1 with 2 of $a$ is ternary expression of $x$ for some $x \in P$. 

$\therefore$ the cardinality of $P$ is greater than or equal to $[0,1]$.

Moreover, we already know that $P \subset [0,1]$. 

$\therefore$ the cardinality of the two sets are equal, i.e. $P$ is uncountable.
 $$\tag*{$\square$}$$
## Definition 1.6.1
Let $$n_1 \in \{0,1,2\}$$ be the largest integer such that 
$$\frac{n_1}{3} <x,$$  where $0<x\leq1$.
Having chosen $n_1, \ldots, n_k$ let $$n_{k+1} \in \{0,1,2\}$$ be the largest integer such that 
$$
\frac{n_1}{3} + \frac{n_2}{3^2} + \cdots + \frac{n_k}{3^k} + \frac{n_{k+1}}{3} < x.
$$ 
The expression $.n_1n_2n_3\cdots$ is called the **ternary expansion** of $x$.

## Theorem 1.6.3
Let $x \in \mathbb{R}$ with $0<x\leq1$, and with $$\{n_k\}$$ as defined in Definition 1.6.1, let
$$
\begin{align}
E = \{ \frac{n_1}{3} + \cdots + \frac{n_k}{3^k}: k =1,2,\ldots \}.
\end{align}
$$
Then $\sup E =x$.

<*proof*>
Since $E \neq \emptyset$ and is bounded above by $x$, there exists $\sup E$ by the least upper bound property. Let $\alpha = \sup E$. Since $x$ is an upper bound, $\alpha \leq x$. 

Suppose $\alpha \lneq x$. Let $k$ be the smallest positive integer such that

$$
\begin{align}
\frac{1}{3^k} < x-\alpha \quad \text{or} \quad \alpha + \frac{1}{3^k} < x
\end{align}
$$
But
$$
\begin{align}
\frac{n_1}{3} + \cdots + \frac{n_k}{3} + \frac{1}{3^k} = \frac{n_1}{3} + \cdots + \frac{n_k + 1}{3} <x.
\end{align}
$$
If $n_k=0$ or 1, this contradicts the choice of $n_k$. If $n_k=2$, then we have 
$$
\begin{align}
\frac{n_1}{3} + \cdots + \frac{n_{k-1}}{3^{k-1}} < x.
\end{align}
$$

If any $n_j, 1\leq j\leq k-1$ is 0 or 1, we have a contradiction to the choice of $n_j$. If all the $n_j=2$, then we obtain
$$
\begin{align}
\frac{2}{3} + \frac{2}{3^2} + \cdots + \frac{2}{3^k} &= \frac{2}{3}\cdot \frac{1}{1-\frac{1}{3}} \\
&<x 
\leq 1
\end{align}
$$
which is also a contradiction.
 $$\tag*{$\square$}$$

## Remark 1.6.4
For a given $0<x \leq1$,  its ternary expansion $.n_1n_2n_3\cdots$ is not unique. The finite expansion can be expressed with infinite expansion. If x has a finite expansion,
$$
\begin{align}
x = \frac{n_1}{3} + \cdots + \frac{n_k}{3^k}, \quad n_k \in \{1,2\}
\end{align}
$$
Alternatively, it has infinite expansion as follows:

$$
\begin{align}
x = \frac{n_1}{3} + \cdots + \frac{0}{3^k} + \sum_{m=k+1}^\infty \frac{2}{3^k} \quad \text{ when } n_k = 1,
\end{align}
$$
or

$$
\begin{align}
x = \frac{n_1}{3} + \cdots + \frac{1}{3^k} + \sum_{m=k+1}^\infty \frac{2}{3^k} \quad \text{ when } n_k = 2.
\end{align}
$$

