---
title: "Continuous functions"

categories:
  - Analysis


tags:
  - compact
  - min-max value theorem
  - intermediate value theorem

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Lemma 1

Let $f:X\to Y$ be a function and let $A\subset X, B\subset Y$. Then,
$$
\begin{align}
\begin{split}
f^{-1}(f(A)) &\supset A \\
f(f^{-1}(B)) &\subset B
\end{split}
\end{align}
\label{set}
$$

<*proof*>

Let $x \in A$ be given. Then $f(x)\in f(A)$. Since f^{-1}(f(A)) = \{x\in X: f(x)\in A \}, $x\inf^{-1}(f(A))$.

$\therefore f^{-1}(f(A)) \supset A$.

Now, let $y\in f(f^{-1}(B))$ be given. Then $y=f(x_0)$ for some $x_0 \in f^{-1}(B)$. Since $x_0 \in f^{-1}(B), y= f(x_0)\in B$.  <br />$\therefore f(f^{-1}(B))\subset B$
$$\tag*{$\square$}$$

## Theorem 4.2.8
Let $K$ is a compact set and let $f:K\to \mathbb{R}$ be a continuous function on $K$. Then $f(K)$ is compact set.

<*proof*>
Let $$\{V_\alpha\}_{\alpha \in \Lambda}$$ be an open cover of $f(K)$. Since $f$ is continuous on $K, f^{-1}(V_\alpha)$ is open in $K$ for all $\alpha \in \Lambda$. Then there exists an open set $U_\alpha$ in $\mathbb{R}$ such that $f^{-1}(V_\alpha) = U_\alpha \cap K$. 

Now we want to show that $K\subset \cup_{\alpha\in \Lambda} U_\alpha$.
$$
\begin{align}
\begin{split}
p\in K &\Rightarrow f(p) \in f(K) \\
&\Rightarrow f(p) \in \cup_{\alpha \in \Lambda}U_\alpha\\
&\Rightarrow f(p) \in U_\alpha \text{ for some } \alpha \in \Lambda \\
&\Rightarrow p\in f^{-1}(V_\alpha) = U_\alpha \cap K \subset U_\alpha
\end{split}
\end{align}
$$
So, $$\{U_\alpha \}_{\alpha \in \Lambda}$$ is an open cover of $K$. Since $K$ is compact, there are $\alpha_1,\ldots, \alpha_n \in \Lambda$ such that $K\subset \cup_{i=1}^n U_{\alpha_i}$. In other words,
$$
\begin{align}
\begin{split}
K&\subset (\cup_{i=1}^n U_{\alpha_i}) \cap K \\
&=\cup_{i=1}^n(U_{\alpha_i}\cap K) \\
&= \cup_{i=1}^n f^{-1}(V_{\alpha_i})
\end{split}
\end{align}
$$
Thus, $f(K)\subset f(\cup_{i=1}^n f^{-1}(V_{\alpha_i}))=\cup_{i=1}^n f(f^{-1}(V_{\alpha_i}))$. Since $f(f^{-1}(V_{\alpha_i})) \subset V_{\alpha_i}$ by Eq.\label{set}, $\cup_{i=1}^n f(f^{-1}(V_{\alpha_i})) \subset \cup_{i=1}^n V_{\alpha_i}$. 

$\therefore f(K)$ is compact.

$$\tag*{$\square$}$$

## Lemma 2
Let $A$ be a closed set. Then $\sup A \in A$.

<*proof*>
For any $n\in \mathbb{N}$, there is $x_n \in A$ such that $\sup A -1/n \leq x_n \leq \sup A$. If there is $n_0\in\mathbb{N}$ such that $x_{n_0} = \sup A$, then $\sup A \in A$. <br />
 Suppose that $x_n \neq \sup A$ for all $n\in\mathbb{N}$.  Then $\sup A \in A^\prime$. Since $A$ is closed, $A^\prime \subset A$. 

$\therefore \sup A \in A$.
$$\tag*{$\square$}$$
## Corollary 4.2.9
Let $K$ be a compact subset of $\mathbb{R}$ and let $f:K\to\mathbb{R}$ be a continuous function. Then there exists $p,q \in K$ such that 
$$
\begin{align}
f(q) \leq f(x) \leq f(p) \text{ for all }x\in K
\end{align}
$$

<*proof*>
By the above theorem, $f(K)$ is compact. By the Heine-Borel-Bolzano-Weierstrass theorem, $f(K)$ is closed and bounded. Let
$$
\begin{align}
M:= \sup \{f(x): x\in K\}
\end{align}
$$
Since $f(K)$ is bounded, $M < +\infty$. Since $f(K)$ is closed, $M\in f(K)$. So, there is $p\in K$ such that $f(p) = M$, i.e. $f(x) \leq f(p)$ for all $x\in K$. Similarly for $$m=\inf\{f(x):x\in K\}$$.

$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
