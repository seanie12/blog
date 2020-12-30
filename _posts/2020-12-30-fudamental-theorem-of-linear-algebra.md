
## Notation
- Define a function $[\cdot]_{\mathfrak{B}}:V \rightarrow \mathbb{R}^n$ such that $[\mathbf{v}]_{\mathfrak{B}} := (a_1, \ldots, a_n)$ where $\mathbf{v} = \sum_{i=1}^n a_i\mathbf{v}_i$ and $\mathfrak{B} = \{ \mathbf{v}_1, \ldots, \mathbf{v}_n\}$ is a basis for a vector space $V$.  It is easy to show that $[\cdot]_{\mathfrak{B}}$ is an isomorphism (bijective and linear map).

- Let $T: V \rightarrow W$ be a linear transformation where $V, W$ are vector spaces over $F$. $\mathfrak{B,C}$ are bases for vector space $V, W$, respectively. Then matrix representation of the linear transformation with respect to the bases $\mathfrak{B}=\{\mathbf{v}_1, \ldots, \mathbf{v}_n\}, \mathfrak{C}=\{ \mathbf{w}_1, \ldots, \mathbf{w}_m \}$ is defined as:
$$ [L]^\mathfrak{B}_{\mathfrak{C}} := [ [L\mathbf{v}_1]_{\mathfrak{C}} \cdots[L\mathbf{v}_n]_{\mathfrak{C}}]$$

- $\mathcal{L}(V,W)$ is a vector space of linear functions which map $V$ to $W$. In other words, for every $L\in \mathcal{L}(V,W)$, $L:V\rightarrow W$ is a linear transformation where $V,W$ are vector spaces over $F$.

-   $\mathfrak{M}_{m\times n}(F)$ is a vector space of $m\times n$ over the field $F$.
## Lemma
Let $L:V\rightarrow W$ be a linear map between vector spaces $V,W$ and $\mathfrak{B}= \{ \mathbf{v}_1, \ldots, \mathbf{v}_n\}, \mathfrak{C}= \{ \mathbf{w}_1, \ldots, \mathbf{w}_m\}$ be  bases for $V,W$. 
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

## Fundamental theorem of linear algebra
Let $U,V,W$ be vector spaces over $F$ and $\mathfrak{A,B,C}$ be bases for $U,V,W$, respectively. Define  a function $\Phi^{\mathfrak{B}}_{\mathfrak{C}}: \mathfrak{M}_{m\times n} \rightarrow \mathcal{L}(V,W)$ by $[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)]_{\mathfrak{C}} := A[\mathbf{v}]_{\mathfrak{B}}$, where $A \in \mathfrak{M}_{m\times n}(F), \mathbf{v} \in V$. Let $\Psi^{\mathfrak{B}}_{\mathfrak{C}}: \mathcal{L}(V,W) \rightarrow \mathfrak{M}_{m\times n}(F)$ be a function such that $\Psi^{\mathfrak{B}}_{\mathfrak{C}}(L) := [L]^{\mathfrak{B}}_{\mathfrak{C}}$ for all $L \in \mathcal{L}(V,W)$.
1. $\Phi^{\mathfrak{B}}_{\mathfrak{C}}, \Psi^{\mathfrak{B}}_{\mathfrak{C}}$ are isomorphism and inverse each other. i.e. $\Phi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Psi^{\mathfrak{B}}_{\mathfrak{C}} = \text{Id}$ and $\Psi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Phi^{\mathfrak{B}}_{\mathfrak{C}} = \text{Id}$.
2. $\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) = \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M \circ L)$ where $M \in \mathcal{L}(V,W)$ and $L \in \mathcal{L}(U,V)$.

<*proof*>
Let $A, B \in \mathfrak{M}_{m\times n }(F)$, $c \in F$ be given. We want to show that $\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB) = \Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B)$.  i.e. $\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB) \mathbf{v} = \{\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B) \}  \mathbf{v}$ for all $\mathbf{v} \in V$.
$$\begin{align}
\begin{split}
[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c\cdot\Phi^{\mathfrak{B}}_{\mathfrak{C}} (B) \mathbf{v} ]_{\mathfrak{C}} &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v} + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B)\mathbf{v}]_{\mathfrak{C}} \\
&= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v}]_{\mathfrak{C}} + c\cdot[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(B)\mathbf{v}]_{\mathfrak{C}} \\
&= A[\mathbf{v}]_{\mathfrak{B}} + cB[\mathbf{v}]_{\mathfrak{B}} \\
&= (A + cB)[\mathbf{v}]_{\mathfrak{B}} \\
&= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB)\mathbf{v}]_{\mathfrak{C}}
\end{split}
\end{align}$$

Since $[\cdot]_{\mathfrak{C}}$ is one-to-one correspondence, $\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A + cB) \mathbf{v} = \{\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) + c \cdot \Phi^{\mathfrak{B}}_{\mathfrak{C}}(B) \}  \mathbf{v}$ for all $\mathbf{v} \in V$. Therefore, $\Phi^{\mathfrak{B}}_{\mathfrak{C}}$ is a linear map.

On the other hand, we want to show that $\Psi^{\mathfrak{B}}_{\mathfrak{C}}$ is a linear transformation. In other words, we want to show that $\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M + cL) = \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) + c \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L)$ where $M, L \in \mathcal{L}(V,W)$ and $c \in F$. However, it suffices to show that  $\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M + cL) \mathbf{e}_j= (\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) + c \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L))\mathbf{e}_j$ for $j=1, \ldots,n$ where $\mathbf{v}_j \in \mathbb{R}^n$ is a standard basis for $\mathbb{R}^n$ and only the $\text{j}^{\text{th}}$ component is 1 and zero for the others.
 
\begin{align}
    \begin{split}
        \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M+L) \mathbf{e}_j & = \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M+L)[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= [M+L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= [(M+L)\mathbf{v}_j]_{\mathfrak{C}} \\
        &= [M\mathbf{v}_j + L\mathbf{v}_j]_{\mathfrak{C}} \\
        &= [M\mathbf{v}_j]_{\mathfrak{C}} + [L\mathbf{v}_j]_{\mathfrak{C}} \\
        &= [M]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} + [L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= \Psi^{\mathfrak{B}}_{\mathfrak{C}}(M)\mathbf{e}_j + \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L) \mathbf{e}_j \\
        &= (\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) + \Psi^{\mathfrak{B}}_{\mathfrak{C}}(L))\mathbf{e}_j
    \end{split}
\end{align}



Now, we want to show that $(\Phi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Psi^{\mathfrak{B}}_{\mathfrak{C}})L = L$ for every $L \in \mathcal{L}(V,W)$.
$(\Phi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Psi^{\mathfrak{B}}_{\mathfrak{C}})L = \Phi^{\mathfrak{B}}_{\mathfrak{C}}(\Psi^{\mathfrak{B}}_{\mathfrak{C}}(L)) = \Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})$.
By the linear extension theorem, it suffices to show that $\Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})\mathbf{v}_j = L\mathbf{v}_j$ for all $j=1,\ldots, n$.  Since $[\Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})\mathbf{v}_j ]_{\mathfrak{C}} = [L]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} = [L\mathbf{v}_j]_{\mathfrak{C}}$ and $[\cdot]_{\mathfrak{C}}$ is bijective, $\Phi^{\mathfrak{B}}_{\mathfrak{C}}([L]^{\mathfrak{B}}_{\mathfrak{C}})\mathbf{v}_j = L\mathbf{v}_j$.


Similarly, we want to show that $(\Psi^{\mathfrak{B}}_{\mathfrak{C}} \circ \Phi ^{\mathfrak{B}}_{\mathfrak{C}})A= A$ for all $A \in \mathfrak{M}_{m\times n}(F)$.

\begin{align}
    \begin{split}
        \Psi^{\mathfrak{B}}_{\mathfrak{C}}(\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A))\mathbf{e}_j  &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)]^{\mathfrak{B}}_{\mathfrak{C}} \mathbf{e}_j \\
        &=[\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)]^{\mathfrak{B}}_{\mathfrak{C}}[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\mathbf{v}_j]_{\mathfrak{C}} \\
        &= A[\mathbf{v}_j]_{\mathfrak{B}} \\
        &= A\mathbf{e}_j
    \end{split}
\end{align}

Lastly, we want to show that $\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) = \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M \circ L)$ and $\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{C}}(B) = \Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)$ where $M \in \mathcal{L}(V,W), L\in \mathcal{L}(U,V), A\in \mathfrak{M}_{m\times n}(F), B \in \mathfrak{M}_{n\times k}(F)$.

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


Equation \ref{eq:1} holds for all $j=1, \ldots, k$. Therefore $\Psi^{\mathfrak{B}}_{\mathfrak{C}}(M) \cdot \Psi^{\mathfrak{A}}_{\mathfrak{B}}(L) = \Psi^{\mathfrak{A}}_{\mathfrak{C}}(M\circ L)$.

$$\begin{align}
    \begin{split}
        \{\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{C}}(B)\} \mathbf{u} &= \Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\{\Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\mathbf{u} \} \\
        [\{\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{C}}(B)\} \mathbf{u}]_{\mathfrak{C}} &= [\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A)\{\Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\mathbf{u} \}]_{\mathfrak{C}} \\
        &= A[\Phi^{\mathfrak{A}}_{\mathfrak{B}}(B)\mathbf{u}]_{\mathfrak{B}} \\
        &=AB[\mathbf{u}]_{\mathfrak{A}} \\
        &= [\Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)\mathbf{u}]_{\mathfrak{C}}
    \end{split}
\end{align}
$$

Since $[\cdot]_{\mathfrak{C}}$ is bijective,  $\{\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{C}}(B)\} \mathbf{u} = \Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)\mathbf{u}$ for all $\mathbf{u} \in U$. Therefore $\Phi^{\mathfrak{B}}_{\mathfrak{C}}(A) \circ \Phi^{\mathfrak{A}}_{\mathfrak{C}}(B) = \Phi^{\mathfrak{A}}_{\mathfrak{C}}(AB)$.
$$\tag*{$\square$}$$

 
