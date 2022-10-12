---
title: "Moore-Penrose Pseudoinverse"

categories:
  - Linear Algebra

tags:
  - pseudo-inverse
   - linear transformation

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition
Let $V$ and $W$ be finite dimensional inner product spaces over the same field $F$ and let $T:V\to W$ be a linear transformation. Let $L:\ker T^\perp\to \text{im}T$ be linear transformation defined by $L\mathbf{x} = T\mathbf{x}$ for all $\mathbf{x}\in \ker T^\perp$. The **pseudo-inverse** ( or Moore-Penrose generalized inverse) of $T$, denoted as $T^\dagger$ is defined as the unique linear transformation from $W$ to $V$ such that

$$
\begin{align*}
T^\dagger(y) =
\begin{cases}
  L^{-1}(\mathbf{y}) &\text{ for } \mathbf{y} \in \text{im}T \\
 \mathbf{0} &\text{ for } \mathbf{y} \in \text{im} T^\perp
\end{cases}
\end{align*}
$$

## Remark
Note that $L: \ker T^\top \to \text{im}T$ is invertible since $\ker L = \\{ \mathbf{0}\\}$. The pseudo-inverse of $T$ exists if $T$ is not invertible. Furthermore if $T$ is invertible, then $T=T^\dagger$ since $\ker T^\perp=V$ and thus $L=T$. 

We can use the singular value theorem to describe the pseudo-inverse of linear transformation. Suppose that $V$ and $W$  are finite dimensional inner product spaces and $T:V\to W$ is linear transformation with rank $r$. Let $\\{\mathbf{v}_1, \ldots, \mathbf{v}_n\\}$ and $\\{\mathbf{u}_1, \ldots, \mathbf{u}_m \\}$ be bases for $V$ and $W$, respectively and let $\sigma_1\geq\sigma_2 \geq \cdots \sigma_r$ be non-zero singular values of $T$ such that 

$$
\begin{align*}
T(\mathbf{v}_i)=\begin{cases}
\sigma_i \mathbf{u}_i & \text{if } 1\leq i \leq r\\
0 & \text{if } i >r.
\end{cases}
\end{align*}
$$

Since $\dim\ker T^\perp  = \dim V - \text{rank} T = n-r$ and $T (\mathbf{v}_i)=\mathbf{0}$ for $i>r$,  

$$
\begin{align*}
\{\mathbf{v}_{r+1}, \ldots, \mathbf{v}_n\}
\end{align*}
$$ 

is a basis for $\ker T$.  On the other hand, since $\mathbf{v}_i \perp \mathbf{v}_j$ for all $1\leq i \leq r$ and $r<j \leq n$, $\\{\mathbf{v}_1, \ldots, \mathbf{v}_r\\}$ is linearly independent subset of $\ker T^\perp$. 

Since  $V= \ker T \bigoplus \ker T^\perp$, $\dim \ker T^\perp = \dim V - \dim \ker T^\perp=n - (n-r) =r$. Thus $\\{\mathbf{v}_1\ldots, \mathbf{v}_r\\}$ is a basis for $\ker T^\perp$.

Similarly, we can show that  

$$
\begin{align*}
\{\mathbf{u}_{1}, \ldots, \mathbf{u}_r \}
\end{align*}
$$ 

is a basis for $\text{im} T$ and $\\{\mathbf{u}_{r+1}, \ldots, \mathbf{u}_m \\}$ is a basis for $\text{im}T^\perp$.


Then 
$$
\begin{align*}
\{\mathbf{v}_1, \ldots, \mathbf{v}_r \}
\end{align*}
$$ 

is a basis for $\ker T^\perp$ and 

$$
\begin{align*}
\{\mathbf{v}_{r+1},\ldots, \mathbf{v}_n \}
\end{align*}
$$ 

is a basis for $\ker T$.  Since 


Let $L$ be the restriction of $T$ to $\ker T^\perp$ as in the definition of the pseudo-inverse. Then $L^{-1}(\mathbf{u}_i)=\frac{1}{\sigma_i}\mathbf{v}_i$ for $1 \leq i \leq r$. Therefore, 

$$
\begin{align*}
T^\dagger (\mathbf{u}_i) = \begin{cases}
\frac{1}{\sigma_i} \mathbf{v}_i &\text{ if } 1 \leq i \leq r \\
\mathbf{0} &\text{ if } r< i  < m.
\end{cases}
\end{align*}
$$

## Definition (Pseudo-inverse of a Matrix)
Let $A$ be an $m\times n$ matrix of rank $r$. Then there exists a unique $n\times m$ matrix $B$ such that $L^\dagger_A: F^m\to F^n$ is equal to $L_B$. We call $B$ the pseudo-inverse of $A$ and denote it by $B=A^\dagger$.

## Theorem
Let $A$ be an $m\times n$ matrix of rank $r$ with a singular value decomposition $A =U\Sigma V^*$ and non-zero singular values $\sigma_1\geq \sigma_2\geq \cdots \geq\sigma_r$.  Let $\Sigma^\dagger$ be the $m\times n$ matrix defined by

$$
\begin{align*}
\Sigma^\dagger_{ij} = \begin{cases}
\frac{1}{\sigma_i} &\text{ if } i=j \leq r \\
0 & \text{otherwise}.
\end{cases}
\end{align*}
$$ 

Then $A^\dagger = V \Sigma^\dagger U^*$.

<*Proof*>

Let $\beta =\\{\mathbf{v}_1, \ldots, \mathbf{v}_n \\}$ be an orthonormal basis for $F^n$ with $V = [\mathbf{v_1}\cdots \mathbf{v}_n]\in \mathbb{R}^{n\times n}$ and let $\gamma =\\{ \mathbf{u}_1, \ldots, \mathbf{u}_m\\}$ be an orthonormal basis for $F^m$ with $U=[\mathbf{u}\cdots \mathbf{u}]\in\mathbb{R}^{m\times m}$. Let $\mathcal{E}$ and $\mathcal{F}$ be standard bases for $F^n$ and $F^m$, respectively.

Then by the fundamental theorem of linear algebra, the following equations hold.

$$
\begin{align}
A^\dagger  &= [L^\dagger_A]^\mathcal{F}_\mathcal{E} \\
&= [Id_V\circ L^\dagger_A\circ Id_W]^\mathcal{F}_\mathcal{E} \\
&=[Id_V]_\mathcal{E}^\beta [L_A^\dagger]^\gamma_\beta[Id_W]_\gamma^\mathcal{F} \\
&=[Id_V]_\mathcal{E}^\beta [L_A^\dagger]^\gamma_\beta([Id_W]^\gamma_\mathcal{F})^{-1} \\
&=V\Sigma^\dagger U^{-1} \\
&=V\Sigma^\dagger U^{*} 
\end{align}
$$

$$\tag*{$\square$}$$


## Lemma
Let $V$ and $W$ be finite-dimensional inner product spaces and let $T:V\to W$ be linear. Then

(a) $T^\dagger T$ is  the orthogonal projection of $V$ onto $\ker T^\perp$.

(b) $T T^\dagger$ is the orthogonal projection of $W$ onto $\text{im} T$.


<*Proof*>

We define $L: \ker T^\perp \to \text{im} T$ by $L(\mathbf{x}) = T(\mathbf{x})$  for all $\mathbf{x}\in\ker T^\perp$.

(a)  If $\mathbf{x}\in\ker T^\perp$, then $T^\dagger T (\mathbf{x})=L^{-1} (L(\mathbf{x}))= \mathbf{x}$. If $\mathbf{x}\in \ker T$,  then $T^\dagger T(\mathbf{x})=T^\dagger(\mathbf{0})=\mathbf{0}$. 

$\therefore T^\dagger T$ is orthogonal projection of $V$ onto $\ker T^\perp$.

(b) If $\mathbf{y} \in \text{im}T$, then $TT^\dagger(\mathbf{y})=T(L^{-1}(y))= L(L^{-1}(\mathbf{y}))=\mathbf{y}$. On the other hand, if $\mathbf{y} \in \text{im}T^\perp$, then $TT^\dagger(\mathbf{y})=T(\mathbf{0})=\mathbf{0}$.

$\therefore TT^\dagger$ is orthogonal projection of $W$ onto $\text{im} T$.


$$\tag*{$\square$}$$

## Theorem

Consider the system of linear equations $A\mathbf{x}=\mathbf{b}$, where $A$ is an $m \times n$ matrix and $\mathbf{b}\in F^m$. If $\mathbf{z} = A^\dagger \mathbf{b}$, then $\mathbf{z}$ has the following properties.

(a) If $A\mathbf{x}=\mathbf{b}$ is consistent, then $\mathbf{z}$ is the unique solution to the system having minimum norm. That is $\mathbf{z}$ is a solution to the system and if $\mathbf{y}$ is any solution to the system, then $\lVert \mathbf{z}  \rVert \leq \lVert \mathbf{y} \rVert$  with equality if and only if $\mathbf{y}=\mathbf{z}$.

(b) If $A\mathbf{x}=\mathbf{b}$ is inconsistent, then $\mathbf{z}$ is the unique best approximation to  a solution having minimum norm. That is $\lVert A\mathbf{z}-\mathbf{b} \rVert \leq \lVert A\mathbf{y}-\mathbf{b}\rVert$ for any $\mathbf{y}\in F^m$ with equality if and only if $A\mathbf{z}=A\mathbf{y}$. Furthermore, if $A\mathbf{z}=A\mathbf{y}$, then $\lVert \mathbf{z} \rVert \leq \lVert \mathbf{y} \rVert$ with equality if and only if $\mathbf{y}=\mathbf{z}$.

<*Proof*>

(a) Let $T = L_A$. Suppose that $A\mathbf{x}= \mathbf{b}$ is consistent and let $\mathbf{z}=A^\dagger\mathbf{b}$. Since $\mathbf{b} \in \text{im} T$, 

$$
\begin{align*}
A\mathbf{z}=AA^\dagger\mathbf{b}=TT^\dagger(\mathbf{b})=\mathbf{b}
\end{align*}
$$

by the previous lemma. Thus $\mathbf{z}$ is a solution to the system. Now suppose that $\mathbf{y}$ is a solution to the system. Then

$$
\begin{align*}
T^\dagger T(\mathbf{y}) = A^\dagger A\mathbf{y}=A^\dagger \mathbf{b}=\mathbf{z},
\end{align*}
$$

that is $\mathbf{z}$ is orthogonal projection of $\mathbf{y}$ onto $\ker T^\perp$. Since $F^n=\ker T \bigoplus\ker T^\perp, \mathbf{y}=\mathbf{x}+\mathbf{z}$ for some $\mathbf{x}\in\ker T$.  

 Since $\langle \mathbf{x}, \mathbf{z}\rangle = 0$,

$$
\begin{align*}
\lVert \mathbf{y} \rVert^2 &= \lVert \mathbf{x+z} \rVert^2 \\
&= \langle \mathbf{x}, \mathbf{x} \rangle+ \langle \mathbf{z}, \mathbf{z}\rangle + \langle \mathbf{x}, \mathbf{z} \rangle + \langle \mathbf{z}, \mathbf{x} \rangle \\
&=  \langle \mathbf{x}, \mathbf{x} \rangle+ \langle \mathbf{z}, \mathbf{z}\rangle \\
& = \lVert \mathbf{x} \rVert^2 + \lVert \mathbf{z} \rVert^2 \\
&\geq  \lVert \mathbf{z} \rVert^2
\end{align*}
$$
$\therefore \lVert \mathbf{z} \rVert\leq \lVert \mathbf{y}\rVert$ for all solution $\mathbf{y}\in F^n$.

(b) Suppose that $A\mathbf{x}=\mathbf{b}$ is inconsistent.  By the previous lemma, 

$$
\begin{align*}
A\mathbf{z}= AA^\dagger \mathbf{b} = TT^\dagger(\mathbf{b}).
\end{align*}
$$

Thus $A\mathbf{z}$ is the orthogonal projection of $\mathbf{b}$ onto $\text{im} T$, which is $A\mathbf{z}$ is the best approximation to $\mathbf{b}$. Thus, $\lVert A\mathbf{z}-\mathbf{b}\rVert \leq \lVert A\mathbf{y} -\mathbf{b}\rVert$ for all $\mathbf{y}\in F^m$.

Finally, suppose that $\mathbf{y}\in F^n$ is any vector such that $A\mathbf{z}=A\mathbf{y} = \mathbf{c}$. 

With singular value decomposition of $A$, we can write $A=U\Sigma V^*$ and $A^\dagger = V\Sigma U^*$. Thus

$$
\begin{align}
\begin{split}
A^\dagger A A^\dagger &=  (V\Sigma^\dagger U^*)( U\Sigma V^*)(V\Sigma^\dagger U^*) \\
&=V\Sigma^\dagger \Sigma \Sigma^\dagger U^* \\
&=V\begin{pmatrix}
I_r & 0 \\
0 & 0
\end{pmatrix} \Sigma^\dagger U^* \\
&=V\Sigma^\dagger U^* \\
&=A^\dagger
\end{split}
\label{eq:1}
\end{align}
$$

Then by Equation$\ref{eq:1}$,

$$
\begin{align*}
A^\dagger \mathbf{c}=A^\dagger A\mathbf{z}=A^\dagger AA^\dagger \mathbf{b} = A^\dagger\mathbf{b}=\mathbf{z}.
\end{align*}
$$

Since $\mathbf{z}=A^\dagger\mathbf{c}$, we can apply the part (a) to the linear system $A\mathbf{x}=\mathbf{c}$, which is consistent. Thus $\lVert \mathbf{z} \rVert \leq \lVert \mathbf{y}\rVert$  with equality if and only if $\mathbf{y}=\mathbf{z}$.

$$\tag*{$\square$}$$


## Reference
- Stephen Friedberg, Arnold Insel, and Lawrence Spence **『**Linear Algebra**』**
