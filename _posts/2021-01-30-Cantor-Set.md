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

(2) $P$ contains all the end points of $J_{n,k}$ for all $n=0,1,2,\ldots, k=1,2,\ldots, 2^n$.

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
\begin{align}
\begin{split}
$$
\frac{1}{3} + 2\times \frac{1}{3^2} + 2^2 \times \frac{1}{3^3} + \cdots &= \sum_{n=1}^\infty \frac{2^{n-1}}{3^n} \\
&= \frac{1}{3} \sum_{n=1}^\infty \frac{2^{n-1}}{3^n}\\
&=\frac{1}{3} \cdot \frac{1}{1-\frac{2}{3}} \\
&=1
\end{split}
\end{align}
$$

$$\tag*{$\square$}$$
