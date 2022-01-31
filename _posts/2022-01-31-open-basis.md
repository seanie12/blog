---
title: "Topology and Basis"

categories:
  - Topology

tags:
  - open set
  - basis

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition
A **topology** on a set $X$ is a collection $\mathfrak{T}$ having the following properties:
(1) $\emptyset$ and $X$ are in $\mathfrak{T}$
(2) The union of the elements of any subcollection of $\mathfrak{T}$ is in $\mathfrak{T}$. In other words,
$$
\begin{equation*}
\text{If } \{U_\alpha\}_{\Lambda} \subset \mathfrak{T}, \text{ then } \cup_{\alpha\in \Lambda}U_\alpha \in \mathfrak{T}.
\end{equation*}
$$
(3) The intersection of the elements of any finite subcollection of $\mathfrak{T}$ is in $\mathfrak{T}$. In other words,

$$
\begin{equation*}
\text{If }U_1, \ldots, U_n \in \mathfrak{T}, \text{ then } \cap_{i=1}^n U_i \in \mathfrak{T}.
\end{equation*}
$$

$$\tag*{$\square$}$$
 


## Reference
- James Munkres, **『**Topology**』**, Pearson
