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

We want to show that $\mathcal{B}$ is a basis for the topology on $X\times Y$. Since $X$ and $Y$ are itself open, $X\times Y \in \mathcal{B}$. Thus, for every $x\times y \in X\times Y$, there is $B=X\times Y\in \mathcal{B}$ such that $x\times y \in B$. Now let $x\times y \in (U_1\times V_1) \cap (U_2\times V_2)$. Since $(U_1\times V_1) \cap (U_2\times V_2) = (U_1 \cap U_2)\times (V_1\cap V_2)$ and $U_1\cap U_2 \in \mathfrak{T}_X, V_1\cap V_2 \in \mathfrak{T}_Y$, $x\times y \in  (U_1 \cap U_2)\times (V_1\cap V_2) = (U_1\times V_1) \cap (U_2\times V_2)$. Thus, $\mathcal{B}$ is a basis.

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

$$\tag*{$\square$}$$


## Definition (Projection)
Let $\pi_1: X\times Y \rightarrow X$ be defined by the equation

$$
\begin{equation*}
\pi_1(x,y) = x.
\end{equation*}
$$

Similarly, let $\pi_2:X\times Y \rightarrow Y$ be defined by the equation

$$
\begin{equation*}
\pi_2(x,y) = y.
\end{equation*}
$$

The maps $\pi_1,\pi_2$ are called the **projections** of $X\times Y$ onto its first and second factors, respectively.

## Remark
The projections $\pi_1,\pi_2$ are surjective. If $U$ is an open subset of $X$, then the preimage $\pi_1^{-1}(U) = U\times Y$, which is open in $X\times Y$. Similarly, if $V$ is an open subset of $Y$, then the preimage $\pi_2^{-1}(V) = X\times V$, which is also open in $X\times Y$.

## Theorem 15.2
The collection

$$
S = \{ \pi_1^{-1}(U)\mid U \text{ is open in } X\} \cup \{ \pi_2^{-1}(V)\mid V \text{ is open in } Y\}
$$

is a subbasis for the product topology on $X\times Y$.

<*proof*>

Let $\mathfrak{T}_X$ be the  topology on $X$ and let $\mathfrak{T}_Y$ be the topology on $Y$. We want to show that 

$$
\left({U\in\mathfrak{T}_X}\pi_1^{-1}(U)\right)\cup \left(\bigcup_{V\in\mathfrak{T}_Y}\pi_2^{-1}(V) \right) = X\times Y.
$$

Since

$$
\begin{align*}
\pi_1^{-1}(X) &= X\times Y \subset \bigcup_{U\in \mathfrak{T}_X}\pi_1^{-1}(U) \text{ and} \\
\pi_2^{-1}(Y) &= X\times Y \subset \bigcup_{V\in \mathfrak{T}_Y}\pi_2^{-1}(V), 
\end{align*}
$$

$$X\times Y\subset \Big(\bigcup_{U\in\mathfrak{T}_X}\pi_1^{-1}(U)\Big)\cup \Big(\bigcup_{V\in\mathfrak{T}_Y}\pi_2^{-1}(V) \Big)$$.

Conversely, $\pi_1^{-1}(U)\subset X\times Y$ for all open set $U$ of $X$. Similarly, $\pi_2^{-1}(V) \subset X\times Y$ for all open set $V$ in $Y$.

$$
\begin{equation*}
\therefore \left(\bigcup_{U\in\mathfrak{T}_X}\pi_1^{-1}(U)\right)\cup \left(\bigcup_{V\in\mathfrak{T}_Y}\pi_2^{-1}(V) \right) = X\times Y.
\end{equation*}
$$

$$\tag*{$\square$}$$

## Definition (Subspace Topology)
Let $X$ be a topological space with topology $\mathfrak{T}$. If $Y$ is a subset of $X$, the collection

$$
\mathfrak{T}_Y = \{ Y\cap U \mid U \in \mathfrak{T}\}
$$

is a topology on $Y$, called the **subspace topology**. With this topology, $Y$ is called **subspace** of $X$.

## Remark
We want to show that $\mathfrak{T}_Y$ is a topology. It contains $\emptyset$ and $Y$ since 

$$
\begin{equation*}
\emptyset = Y\cap \emptyset \quad \text{ and}\quad Y = Y\cap X.
\end{equation*}
$$

For arbitrary union and finite intersections of open sets,

$$
\begin{equation*}
\bigcup_{\alpha \in \Lambda}(U_\alpha \cap Y) = \left(\bigcup_{\alpha\in\Lambda}U_\alpha\right)\cap Y
\end{equation*}
$$

$$
\begin{equation*}
\bigcap_{i=1}^n(U_i \cap Y) = \left(\bigcap_{i=1}^nU_i\right)\cap Y
\end{equation*}
$$

## Lemma 16.1
If $\mathcal{B}$ is a basis for the topology of $X$, then the collection 

$$
\begin{equation*}
\mathcal{B}_Y = \{B\cap Y\mid B\in\mathcal{B} \}
\end{equation*}
$$
 
 is a basis for the subspace topology on $Y$.

<*proof*>

Let $U$ be an open subset of $X$ and let $y\in U\cap Y$ be given. Then there is a basis element $B\in\mathcal{B}$ such that $y\in B \subset U$ since $\mathcal{B}$ is a basis for $X$. Thus, $y\in B\cap Y \subset U\cap Y$. By [Lemma 13.2](https://seanie12.github.io/blog/topology/open-basis/#lemma-132), the collection $\mathcal{B}_Y$ is a basis for the subspace topology on $Y$.


$$\tag*{$\square$}$$


## Lemma 16.2 
Let $(Y,\mathfrak{T}_Y)$ is a subspace of $(X,\mathfrak{T}_X)$. If $U$ is open in $Y$ and $Y$ is open in $X$, then $U$ is open in $X$.

<*proof*>

Let $U$ be an open in $Y$. Then $U=Y\cap V$ for some open subset $V$ of $X$. Since $Y$ is open in $X$, finite intersection $Y\cap V$ is open in $X$. Thus, $U$ is open in $X$.

$$\tag*{$\square$}$$



## Lemma 16.3
If $(A, \mathfrak{T}_A)$ is a subspace of  $(X,\mathfrak{T}_X)$ and $(B,\mathfrak{T}_Y)$ is a subspace of $(Y ,\mathfrak{T}_Y)$, then the product topology on $A\times B$ is the same as the topology $A\times B$ inherits as a subspace of $(X \times Y, \mathfrak{T}_{X \times Y})$.

<*proof*>

The set $U\times V$ is the general basis element for the topology on $X\times Y$, where $U\in\mathfrak{T}_X$ and $V\in\mathfrak{T}_Y$. Then $(U\times V)\cap (A\times B)$ is a basis element for the subspace topology on $A\times B$. 
We know that 

$$
\begin{equation*}
(U\times V)\cap (A\times B) = (U\cap A) \times (V\cap B).
\end{equation*}
$$

Since $U\cap A$ is open set in $A$ and $V\cap B$ is open set in $B$,  $(U\cap A) \times (V\cap B)$ is a basis element on the product topology on $A\times B$. Thus we can conclude that the bases for the subspace topology on $A\times B$ and for the product topology on $A\times B$ are the same. Hence the two topologies are the same.

$$\tag*{$\square$}$$

## Reference
- James Munkres, **『**Topology**』**, Pearson
