---
title: "Product Topology and Subspace Topology"

categories:
  - Topology

tags:
  - product topology
  - subspace

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition (Product Topology on $X \times Y$)
Let $(X,\mathfrak{T}_X)$ and $(Y,\mathfrak{T}_Y)$ be topological spaces. The **product space topology** on $X\times Y$ is the topology having as basis the collection $\mathcal{B} = \\{U\times V \mid  U\in \mathfrak{T}_X, V\in \mathfrak{T}_Y\\}$.

We want to show that $\mathcal{B}$ is a basis for the topology on $X\times Y$. Since $X$ and $Y$ are itself open, $X\times Y \in \mathcal{B}$. Thus, for every $x\times y \in X\times Y$, there is $B=X\times Y\in \mathcal{B}$ such that $x\times y \in B$. Now let $x\times y \in (U_1\times V_1) \cap (U_2\times V_2)$. Since $(U_1\times V_1) \cap (U_2\times V_2) = (U_1 \cap U_2)\times (V_1\cap V_2)$ and $U_1\cap U_2 \in \mathfrak{T}_X, V_1\cap V_2 \in \mathfrak{T}_Y$, $x\times y \in  (U_1 \cap U_2)\times (V_1\cap V_2) = (U_1\times V_1) \cap (U_2\times V_2)$. Thus, $\mathcal{B}$ is a basis
$$\tag*{$\square$}$$

## Theorem 15.1 
If $\mathcal{B}$ is a basis for the topology of $X$ and $\mathcal{C}$ is a basis for the topology of $Y$, then the collection

$$
\begin{equation*}
\mathcal{D} = \{B\times C \mid B\in\mathcal{B}, C \in \mathcal{C}\}
\end{equation*}
$$

is a basis for the topology of $X\times Y$.

<*proof*>
We apply [Lemma 13.2](https://seanie12.github.io/blog/topology/open-basis/#lemma-132).  Given an open set $W$ of $X\times Y$ and a point $x\times y\in W$, there are open sets $U_x$ of $X$ containing $x$ and $V_y$ of $Y$ containing $y$. Thus, $x\times y \in U_x\times V_y \subset W$, by the definition of product topology. Since $\mathcal{B},\mathcal{C}$ are bases for $X$ and $Y$, respectively, there is a $B\in\mathcal{B}$ such that $x\in B\subset U_x$ and $C\in\mathcal{C}$ such that $y\in C\subset V_y$. Then $x\times y \in B\times C \subset W$. Thus, the collection $\mathcal{D}$ meets the criterion of Lemma 13.2, so $\mathcal{D}$ is a basis for $X\times Y$.

## Reference
- James Munkres, **『**Topology**』**, Pearson
