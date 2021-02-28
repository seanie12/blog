title: "Continuous function-2"

categories:
  - Analysis


tags:
  - compact
  - min-max theorem
  - intermediate value theorem
 

toc: true
toc_sticky: true

use_math : true
comments : true

## Lemma

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
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
