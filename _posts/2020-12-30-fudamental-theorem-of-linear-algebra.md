---
title: "Fundamental Theorem of Linear Algebra"

categories:
  - Linear Algrbra

tags:
  - fundamental theorem
  - isomorphism
  - linear transformation

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Notation
- Let  $[\cdot]_{\mathfrak{B}}:V \rightarrow \mathbb{R}^n$ be a function with a basis $\mathfrak{B}=${ $\mathbf{v_1}, \ldots, \mathbf{v}_n$}  as follows:  
$$[\mathbf{v}]_{\mathfrak{B}} := (a_1, \ldots, a_n) \text{ where } \mathbf{v} = \sum_{i=1}^n a_i\mathbf{v}_i$$   It is easy to show that $[\cdot]_{\mathfrak{B}}$ is an isomorphism (bijective and linear map).

- Let $T: V \rightarrow W$ be a linear transformation where $V, W$ are vector spaces over $F$. $\mathfrak{B,C}$ are bases for vector space $V, W$, respectively. Then matrix representation of the linear transformation with respect to the bases $\mathfrak{B} = \{ \mathbf{v}_1, \ldots, \mathbf{v}_n \}, \mathfrak{C}=\{ \mathbf{w}_1, \ldots, \mathbf{w}_m \}$ is defined as:
$$ [L]^\mathfrak{B}_{\mathfrak{C}} := [ [L\mathbf{v}_1]_{\mathfrak{C}} \cdots[L\mathbf{v}_n]_{\mathfrak{C}}]$$

- $\mathcal{L}(V,W)$ is a vector space of linear functions which map $V$ to $W$. In other words, for every $L\in \mathcal{L}(V,W)$, $L:V\rightarrow W$ is a linear transformation where $V,W$ are vector spaces over $F$.

- $\mathfrak{M}_{m\times n}(F)$ is a vector space of $m\times n$ over the field $F$.

 
