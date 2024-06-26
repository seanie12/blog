---
title: "Fundamental Theorem of Linear Algebra"

categories:
  - Linear Algebra

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
- Let  $$\mathfrak{B}=\{\mathbf{v}_1, \ldots, \mathbf{v}_n \} \text{ is a basis for } V.$$ Define a function   $$[\cdot]_{\mathfrak{B}}:V \rightarrow \mathbb{R}^n$$  as follows.
  $$\left[\sum_{i=1}^n a_i\mathbf{v}_i\right]_{\mathfrak{B}} \mapsto(a_1, \ldots, a_n)$$
  It is easy to show that $[\cdot]_{\mathfrak{B}}$ is an isomorphism (bijective and linear map).

- Let $T: V \rightarrow W$ be a linear transformation where $V, W$ are vector spaces over $F$. $\mathfrak{B,C}$ are bases for vector space $V, W$, respectively. Then matrix representation of the linear transformation with respect to the bases $$\mathfrak{B}=\{\mathbf{v}_1, \ldots, \mathbf{v}_n\}, \mathfrak{C}=\{ \mathbf{w}_1, \ldots, \mathbf{w}_m \}$$ is defined as:
$$ [L]^\mathfrak{B}_{\mathfrak{C}} := [ [L\mathbf{v}_1]_{\mathfrak{C}} \cdots[L\mathbf{v}_n]_{\mathfrak{C}}]$$
- $\mathcal{L}(V,W)$ is a vector space of linear functions which map $V$ to $W$. In other words, for every $L\in \mathcal{L}(V,W)$, $L:V\rightarrow W$ is a linear transformation where $V,W$ are vector spaces over $F$.

- $\mathfrak{M}_{m\times n}(F)$ is a vector space of $$m \text{ by } n$$ matrices over the field $$F$$.


## Lemma1
Let $V$ be a vector space over $F$ and $$\mathfrak{B}=\{ \mathbf{v}_1, \ldots, \mathbf{v}_n\} $$ be a basis for $V$. Define a function $$[\cdot]_{\mathfrak{B}}: V\rightarrow \mathbb{R}^n $$ by $$[\mathbf{v}]_{\mathfrak{B}} := (a_1, \ldots, a_n) \text{ where } \mathbf{v} = \sum_{i=1}^n a_i \mathbf{v}_i.$$Then $$[\cdot]_{\mathfrak{B}}$$ is isomorphism.

<*proof*>
Let $\mathbf{v,w} \in V, c \in F$ be given. We want to show that $$[\mathbf{v}+c\mathbf{w}]_{\mathfrak{B}} = [\mathbf{v}]_{\mathfrak{B}} + c[\mathbf{w}]_{\mathfrak{B}}.$$ Put $$\mathbf{v} = \sum_{i=1}^n a_i \mathbf{v}_i \text{ and } \mathbf{w} = \sum_{i=1}^n b_i \mathbf{v}_i.$$
$$
\begin{align}
\begin{split}
[\mathbf{v} + c\mathbf{w}]_{\mathfrak{B}} &= [\sum_{i=1}^n a_i \mathbf{v}_i + \sum_{i=1}^n c b_i \mathbf{v}_i]_{\mathfrak{B}}\\
&= [\sum_{i=1}^n (a_i + c b_i)\mathbf{v}_i]_{\mathfrak{B}} \\
&= (a_1 +cb_1, \ldots, a_n + cb_n) \\
&= (a_1, \ldots, a_n) + c(b_1, \ldots, b_n) \\
&= [\mathbf{v}]_{\mathfrak{B}} + c[\mathbf{w}]_{\mathfrak{B}}
\end{split}
\end{align}
$$
Now, we want to show that the function is one-to-one. Let $$\mathbf{u}, \mathbf{v} \in V$$ be given. Suppose $$[\mathbf{u}]_{\mathfrak{B}} = [\mathbf{v}]_{\mathfrak{B}}.$$ There exist unique $$a_i, b_i$$ for $$i=1,\ldots, n$$ such that  $$\mathbf{u} = \sum_{i=1}^n a_i \mathbf{v}_i \text{ and } \mathbf{v} = \sum_{i=1}^n b_i \mathbf{v}_i$$. Then $$(a_1, \ldots, a_n) = (b_1, \ldots, b_n)$$. Therefore, $$\mathbf{u} = \mathbf{v}$$, i.e. the function is one-to-one.

Lastly, we want to show that the function is onto. Let $$(a_1, \ldots, a_n)$$ be given.  Define $$\mathbf{v} := \sum_{i=1}^n a_i \mathbf{v}_i$$. Clearly, $$(a_1,\ldots, a_n) = [\mathbf{v}]_\mathfrak{B} \in\text{im}\left( [\cdot]_\mathfrak{B}\right)$$. Therefore, the function is onto.

$$\tag*{$\square$}$$
 
## Lemma2
Let $L:V\rightarrow W$ be a linear map between vector spaces $V,W$ and $$\mathfrak{B}= \{ \mathbf{v}_1, \ldots, \mathbf{v}_n\}, \mathfrak{C}= \{ \mathbf{w}_1, \ldots, \mathbf{w}_m\}$$ be  bases for $V,W$. 
$$[L]^{\mathfrak{B}}_{\mathfrak{C}} [\mathbf{v}]_{\mathfrak{B}} = [L\mathbf{v}]_{\mathfrak{C}}$$ for all $\mathbf{v} \in V$.

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
    \label{lemma2}
\end{align}
$$
$$\tag*{$\square$}$$



## Fundamental theorem of linear algebra
Let $U,V,W$ be vector spaces over $F$ and $$\mathfrak{A} = \{\mathbf{u}_1, \ldots, \mathbf{u}_k \},\mathfrak{B} =\{\mathbf{v}_1, \ldots, \mathbf{v}_n \}, \mathfrak{C} = \{\mathbf{w}_1, \ldots, \mathbf{w}_m \}$$ be bases for $U,V,W$, respectively. 
Define  a function $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}: \mathfrak{M}_{m\times n}(F) \rightarrow \mathcal{L}(V,W)$$ by 
$$\begin{align}[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v}]_{\mathfrak{C}} := A[\mathbf{v}]_{\mathfrak{B}}\end{align}$$, where $A \in \mathfrak{M}_{m\times n}(F), \mathbf{v} \in V$. 
Similarly, define a function 
$$\begin{align}\begin{split}\Psi^{\mathfrak{B}}_{\mathfrak{C}}: \mathcal{L}(V,W) &\rightarrow \mathfrak{M}_{m\times n}(F)\\
\Psi^{\mathfrak{B}}_{\mathfrak{C}}(L) &:= [L]^{\mathfrak{B}}_{\mathfrak{C}} \text{ for all } L \in \mathcal{L}(V,W)\end{split}\end{align}\\$$ 

1. $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}, \Psi^{\mathfrak{B}}_{\mathfrak{C}}$$ are isomorphism and inverse each other. 

2. $$\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) = \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M \circ L) \text{ where } M \in \mathcal{L}(V,W) \text{ and } L \in \mathcal{L}(U,V)$$.

3. $$\Phi^\mathfrak{B}_\mathfrak{C}(A)\circ\Phi^\mathfrak{A}_\mathfrak{B}(B)=\Phi^\mathfrak{A}_\mathfrak{C}(BA)$$ where $$A\in\mathfrak{M}_{m\times n}(F), B\in\mathfrak{M}_{n\times k}(F).$$

<*proof*>

Let $$A, B \in \mathfrak{M}_{m\times n }(F), c \in F$$ be given. We want to show that $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB) = \Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B)$$.  i.e. $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB) \mathbf{v} = \{\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B) \}  \mathbf{v} \text{ for all } \mathbf{v} \in V$$.

$$\begin{align}
\begin{split}
\left[\left(\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c\cdot\Phi^{\mathfrak{B}}_{\mathfrak{C}} (B)\right) \mathbf{v} \right]_{\mathfrak{C}} &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v} + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B)\mathbf{v}]_{\mathfrak{C}} \\
&= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v}]_{\mathfrak{C}} + c\cdot[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(B)\mathbf{v}]_{\mathfrak{C}}  \\
&= A[\mathbf{v}]_{\mathfrak{B}} + cB[\mathbf{v}]_{\mathfrak{B}} \\
&= (A + cB)[\mathbf{v}]_{\mathfrak{B}} \\
&= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB)\mathbf{v}]_{\mathfrak{C}}
\end{split}
\end{align}$$
The second equality holds due to the linearity of $$[\cdot]_{\mathfrak{C}}$$. Since $$[\cdot]_{\mathfrak{C}}$$ is one-to-one correspondence, $$ \left[\left(\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c\cdot\Phi^{\mathfrak{B}}_{\mathfrak{C}} (B)\right) \mathbf{v} \right]_{\mathfrak{C}} = [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB)\mathbf{v}]_{\mathfrak{C}} \Longrightarrow  (\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B) ) = \Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB) \mathbf{v}$$. Therefore, $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}$$ is a linear map.

On the other hand, we want to show that $$\Psi^{\mathfrak{B}}_{\mathfrak{C}}$$ is a linear transformation. In other words, we want to show that $$\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M + cL) = \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) + c \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L)$$ where $$M, L \in \mathcal{L}(V,W)$$ and $$c \in F$$. However, it suffices to show that $$\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M + cL) \mathbf{e}_j= (\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) + c \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L))\mathbf{e}_j$$ for $$j=1, \ldots,n$$ where $$\mathbf{e}_j \in \mathbb{R}^n$$ is a standard basis for $$\mathbb{R}^n$$ and only the $$\text{j}^{\text{th}}$$ component is 1 and zero for the others.
 
$$\begin{align}
    \begin{split}
        \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M+L) \mathbf{e}_j & = \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M+L)[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= [M+L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= [(M+L)\mathbf{v}_j]_{\mathfrak{C}} \:(\because \text{by Equation \ref{lemma2} from Lemma2}) \\
        &= [M\mathbf{v}_j + L\mathbf{v}_j]_{\mathfrak{C}} \\
        &= [M\mathbf{v}_j]_{\mathfrak{C}} + [L\mathbf{v}_j]_{\mathfrak{C}} \\
        &= [M]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} + [L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M)\mathbf{e}_j + \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L) \mathbf{e}_j \\
        &= (\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) + \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L))\mathbf{e}_j
    \end{split}
\end{align}
$$


Now, we want to show that $$(\Phi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Psi^{\mathfrak{B}}_{\mathfrak{C}})L = L$$ for every $$L \in \mathcal{L}(V,W)$$.
$$(\Phi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Psi^{\mathfrak{B}}_{\mathfrak{C}})L = \Phi^{\mathfrak{B}}_{\mathfrak{C}}(\Psi^{\mathfrak{B}}_{\mathfrak{C}}(L)) = \Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})$$.
By the linear extension theorem, it suffices to show that $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})\mathbf{v}_j = L\mathbf{v}_j$$ for all $$j=1,\ldots, n$$.  Since $$\left[\Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})\mathbf{v}_j \right]_{\mathfrak{C}} = [L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} = \left[L\mathbf{v}_j\right]_{\mathfrak{C}}$$ and $$[\cdot]_{\mathfrak{C}}$$ is bijective, $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}\left([L]^{\mathfrak{B}}_{\mathfrak{C}}\right)\mathbf{v}_j = L\mathbf{v}_j$$.


Similarly, we want to show that $$\left(\Psi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Phi ^{\mathfrak{B}}_{\mathfrak{C}}\right)A= A$$ for all $$A \in \mathfrak{M}_{m\times n}(F)$$.
$$
\begin{align}
    \begin{split}
        \Psi^{\mathfrak{B}}_{\mathfrak{C}}\left(\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\right)\mathbf{e}_j  &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)]^{\mathfrak{B}}_{\mathfrak{C}} \mathbf{e}_j \\
        &=[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v}_j]_{\mathfrak{C}} \\
        &= A[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= A\mathbf{e}_j
    \end{split}
\end{align}
$$

Lastly, we want to show that $$\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) = \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M \circ L)$$ and $$\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{B}}(B) = \Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)$$ where $$M \in \mathcal{L}(V,W), L\in \mathcal{L}(U,V), A\in \mathfrak{M}_{m\times n}(F), B \in \mathfrak{M}_{n\times k}(F)$$.

It is suffices to show that every $j$-th column of each matrix is the same. In other words,  $$\left[\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L)\right]^j = \left[\Psi^{\mathfrak{A}}_{\mathfrak{C}}(M\circ L)\right]^j.$$

$$
\begin{align}
    \begin{split}
        \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) \mathbf{e}_j &= [M]^{\mathfrak{B}}_{\mathfrak{C}}[L]^{\mathfrak{A}}_{\mathfrak{B}} [\mathbf{u}_j]_{\mathfrak{A}} \\
        &= [M]^{\mathfrak{B}}_{\mathfrak{C}}[L\mathbf{u}_j]_{\mathfrak{B}} \\
        &= [M(L\mathbf{u}_j)]_{\mathfrak{C}} \\
        &= [(M\circ L) \mathbf{u}_j]_{\mathfrak{C}} \\
        &= [M\circ L]^{\mathfrak{A}}_{\mathfrak{C}}[\mathbf{u}_j]_{\mathfrak{A}} \\
        &= \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M \circ L) \mathbf{e}_j
    \end{split}
    \label{eq:1}
\end{align}
$$


Equation \ref{eq:1} holds for all $$j=1, \ldots, k$$. Therefore $$\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) = \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M\circ L)$$.

Let $\mathbf{u}\in U$ be given.
$$\begin{align}
    \begin{split}
        (\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)) \mathbf{u} &= \Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)(\Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\mathbf{u} ) \\
        [(\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)) \mathbf{u}]_{\mathfrak{C}} &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)(\Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\mathbf{u} )]_{\mathfrak{C}} \\
        &= A[\Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\mathbf{u}]_{\mathfrak{B}} \\
        &=AB[\mathbf{u}]_{\mathfrak{A}} \\
        &= [\Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)\mathbf{u}]_{\mathfrak{C}}
    \end{split}
\end{align}
$$

Since $$[\cdot]_{\mathfrak{C}}$$ is bijective,  $$\left(\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\right) \mathbf{u} = \Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)\mathbf{u}$$. 
$$\therefore\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{B}}(B) = \Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB).$$


$$\tag*{$\square$}$$

## Summary
- Given two vector spaces $V,W$ and corresponding bases, we can construct isomorphism between matrices and linear functions. i.e., There is a unique matrix for a given linear transformation and vice versa.
- Composition of two linear functions corresponds to matrix multiplication of the two matrices determined by the isomorphism between linear functions and matrices, and vice versa.

## Reference
- 이인석, **『**선형대수와 군**』**,서울대학교출판문화원
