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
- Let  $[\cdot]_{\mathfrak{B}}:V \rightarrow \mathbb{R}^n$ be a function as follows.

  $$[\mathbf{v}]_{\mathfrak{B}} := (a_1, \ldots, a_n) \text{ where } \mathbf{v} = \sum_{i=1}^n a_i\mathbf{v}_i, \mathfrak{B}=\{\mathbf{v}_1, \ldots, \mathbf{v}_n \} \text{ is a basis for } V.$$
  It is easy to show that $[\cdot]_{\mathfrak{B}}$ is an isomorphism (bijective and linear map).

- Let $T: V \rightarrow W$ be a linear transformation where $V, W$ are vector spaces over $F$. $\mathfrak{B,C}$ are bases for vector space $V, W$, respectively. Then matrix representation of the linear transformation with respect to the bases $\mathfrak{B} = \{ \mathbf{v}_1, \ldots, \mathbf{v}_n \}, \mathfrak{C}=\{ \mathbf{w}_1, \ldots, \mathbf{w}_m \}$ is defined as:
$$ [L]^\mathfrak{B}_{\mathfrak{C}} := [ [L\mathbf{v}_1]_{\mathfrak{C}} \cdots[L\mathbf{v}_n]_{\mathfrak{C}}]$$

- $\mathcal{L}(V,W)$ is a vector space of linear functions which map $V$ to $W$. In other words, for every $L\in \mathcal{L}(V,W)$, $L:V\rightarrow W$ is a linear transformation where $V,W$ are vector spaces over $F$.

- $\mathfrak{M}_{m\times n}(F)$ is a vector space of $m\times n$ over the field $F$.

 
## Lemma
Let $L:V\rightarrow W$ be a linear map between vector spaces $V,W$ and $$\mathfrak{B}= \{ \mathbf{v}_1, \ldots, \mathbf{v}_n\}, \mathfrak{C}= \{ \mathbf{w}_1, \ldots, \mathbf{w}_m\}$$ be  bases for $V,W$. 
Then $[L]^{\mathfrak{B}}_{\mathfrak{C}} [\mathbf{v}]_{\mathfrak{B}} = [L\mathbf{v}]_{\mathfrak{C}}$ for all $\mathbf{v} \in V$.

<*proof*>
Put $\mathbf{v} = \sum_{i=1}^n a_i \mathbf{v}_i$. Since $\mathfrak{B}$ is a basis for $V$, all $a_i$ are unique. 
$$
\begin{align}
    \begin{split}
        [L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}]_{\mathfrak{B}} &= [L]^{\mathfrak{B}}_{\mathfrak{C}} (a_1, \ldots, a_n)^\top\\
        &= \sum_{i=1}^n a_i [L\mathbf{v}_i]_{\mathfrak{C}} \\
        &= [\sum_{i=1}^n a_i L\mathbf{v}_i]_{\mathfrak{C}} \\
        &= [L(\sum_{i=1}^n a_i \mathbf{v}_i)]_{\mathfrak{C}} \\
        &= [L\mathbf{v}]_{\mathfrak{C}}
    \end{split}
\end{align}
$$
$$\tag*{$\square$}$$
