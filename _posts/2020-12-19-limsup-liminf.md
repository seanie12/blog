---
title: "Limit Superior and Inferior of a Sequence"

categories:
  - Analysis


tags:
  - limit superior
  - limit inferior
 

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 2.5.1
Let $\\{s_n\\}$ be a sequence in $\mathbb{R}$. The **limit superior** of $\\{s_n\\}$, denoted as $\limsup_{n\to\infty}s_n$,  is defined as

$$
\begin{align*}
\limsup_{n\to\infty}s_n:=\lim_{k\to\infty}b_k:=\inf_{k\in\mathbb{N}}\sup\{s_n: n\geq k \} \in \mathbb{R} \cup\{ \pm \infty\}
\end{align*}
$$

The **limit inferior** of $\\{s_n\\}$, denoted as $\liminf_{n\to\infty}s_n$, defined as 

$$
\begin{align*}
\liminf_{n\to\infty}s_n:=\lim_{k\to\infty}a_k :=\sup_{k\in\mathbb{N}}\inf\{s_n: n\geq k\} \in \mathbb{R} \cup\{ \pm \infty\}
\end{align*}
$$

## Theorem 2.5.3 
Let t $\\{s_n\\}$  be a sequence in $\mathbb{R}$.

(a) $\beta=\limsup_{n\to\infty}s_n$  is a real number if and only if

$$
\begin{align}
\forall \epsilon >0, \exists n_0\in\mathbb{N} \text{ such that } n\geq n_0 \Rightarrow s_n < \beta +\epsilon \\
\forall \epsilon >0, \forall n\in\mathbb{N}, \exists k\in\mathbb{N} \text{ with } k\geq n \text{ such that } s_k > \beta-\epsilon
\end{align}
$$

(b) $\limsup_{n\to\infty}s_n=\infty$ if and only if 

$$
\begin{align}
\forall M\in\mathbb{R}, \forall n\in\mathbb{R}, \exists k\in\mathbb{N} \text{ with } k\geq n \text { such that } s_k\geq M
\end{align}
$$

(c) $\limsup_{n\to\infty}s_n = -\infty$ if and only if $\lim_{n\to\infty}s_n =-\infty$
$$\tag*{$\square$}$$


## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
