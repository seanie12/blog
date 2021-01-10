---
title: "Open and closed set"

categories:
  - Analysis

tags:
  - open set
  - closed set
  - derived set
  - closure

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 3.1.1
$E$ is a subset of $\mathbb{R}$. $p\in E$ is an *interior point* of $E$ if  there is $epsilon >0$ such that $N_{\epsilon} (p) \subset E$.
$$\text{Int}(E) := \{\text{all interior points of } E\} \subset E$$

### Example
1. $E=[1,2)$, $\text{int}(E) = (1,2]$.
2. $E =\mathbb{R} \setminus \mathbb{Q}$, $\text{Int}(E) = \emptyset$.


## Definition 3.1.3
(a) $O \subset \mathbb{R}$ is *open* if $\text{Int}(O) = O.$
(b) $F \subset \mathbb{R}$ is *closed* if $F^c = \mathbb{R}\setminus F$ is open.

## Examples 3.1.4
(a) $\mathbb{R}$ is open and closed set. It is one of axioms in topology.
(b) Every $\epsilon$-neighborhood is open. (basis in topology)
<*proof*>
We want to show that $N_\epsilon (p)$ is open for every $p \in \mathbb{R}$.  Let $q \in N_\epsilon (p)$ be given. Define $\delta >0$ as follows:
$$\delta := \min\{ |p-q|, \epsilon - |p-q|\}$$
For every $x \in N_\delta (q)$,
$$
\begin{align*}
\begin{split}
|x-p| &\leq |x-q| + |p-q| \\
&< \delta + |p-q| \\
&\leq \epsilon-|p-q| + |p-q|\\
&=\epsilon
\end{split}
\end{align*}
$$
$\therefore N_\delta (q) \subset N_\epsilon (p)$. i.e. $N_\epsilon (p)$ is open.
$$\tag*{$\square$}$$

## Theorem 3.1.6 
(a) $$\{O_\alpha \}_{\alpha \in \Lambda}: \text{ a family of open sets}\Rightarrow \cup_{\alpha \in \Lambda}O_\alpha \text{ is open.}  $$
(b) $$\{O_1, \ldots, O_n \}: \text{ a finite collection of open sets} \Rightarrow \cap_{i=1}^n O_i \text{ is open}.$$

<*proof*>
