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

Let $x \in A$ be given. Then $f(x)\in f(A)$. Since $$f^{-1}(f(A)) = \{x\in X: f(x)\in A \}$$, $x\inf^{-1}(f(A))$.

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
Thus, $f(K)\subset f(\cup_{i=1}^n f^{-1}(V_{\alpha_i}))=\cup_{i=1}^n f(f^{-1}(V_{\alpha_i}))$. Since $f(f^{-1}(V_{\alpha_i})) \subset V_{\alpha_i}$ by Eq.\ref{set}, $\cup_{i=1}^n f(f^{-1}(V_{\alpha_i})) \subset \cup_{i=1}^n V_{\alpha_i}$. 

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


## Theorem 4.2.11 (Intermediate Value Theorem)
Let $f: [a,b]\to\mathbb{R}$ be a continuous function with $f(a) < f(b)$. <br /> If $\gamma \in\mathbb{R}$ s.t. $f(a)<\gamma <f(b)$, then there is $c\in (a,b)$ s.t. $f(c) =\gamma$. 

<*proof*>
Let 
$$
\begin{align}
A :=\{x\in [a,b]: f(x)\leq \gamma \}
\end{align}
$$
Then $A \neq \emptyset$ and is bounded above by $b$. By the least upper bound property, there is a supremum $c=\sup A$. Then $c\leq b$. 

Now, we want to show that $f(c) = \gamma$. Since $c=\sup A$, $c\in A$ or $c\in A^\prime$. If $c\in A$, then $f(c)\leq \gamma$.

Suppose that $c\in A^\prime$. Then there exists $$\{x_n\}\subset A$$ such that $x_n\to c$ as $n\to\infty$ with $x_n\neq c$. Since $x_n \in A, f(x_n)\leq \gamma$ for all $n\in \mathbb{N}$. Since $f$ is continuous and $c$ is a limit point of $[a,b],$
$$
\begin{align}
f(c) = \lim_{n\to\infty}f(x_n) \leq \gamma
\end{align}
$$
Thus, $f(c) \leq \gamma$.

Suppose that $f(c) \lneq \gamma$. Take 
$$
\begin{align}
\epsilon_0 := \frac{1}{2}(\gamma -f(c)) > 0
\end{align}
$$
Since $f$ is continuous at $c$, there is $\delta >0$ such that 
$$
\begin{align}
x_n \in N_\delta (c) \cap [a,b] \Rightarrow f(x) -\epsilon_0 < f(x) < f(c) + \epsilon_0
\end{align}
$$
Since $f(c) \lneq \gamma, c\neq b$. Then $(c,b]\cap N_\delta (c) \neq \emptyset$. If $x\in (c,b]$ with $c<x<c+\delta$, then 
$$
\begin{align}
\begin{split}
f(x) < f(c) + \epsilon_0 &= f(c) + \frac{1}{2}(\gamma - f(c)) \\
&=\frac{1}{2}(\gamma + f(c)) \\
&<\gamma
\end{split}
\end{align}
$$
Since $x >c =\sup A, x \not\in  A$ That is $f(x) > \gamma$. But it is a contradiction because $c$ is supremum of $A$.

$\therefore f(c) = \gamma$

$$\tag*{$\square$}$$

## Corollary 4.2.12
Let $I \subset \mathbb{R}$ be an interval and let $f:I\to \mathbb{R}$ be a continuous function. Then $f(I)$ is an interval.

<*proof*>
Let $s,t \in f(I)$ with $s<t$ such that $f(a) = s, f(b) = t$. <br /> Let $s <\gamma <t$ be given. If $a<b$, then since $f$ is continuous on $I$, by the intermediate value theorem there exists $c\in (a,b)$ such that $f(c) = \gamma$. <br /> $\therefore \gamma \in f(I)$ <br /> A similar argument also holds if $a>b$.

$$\tag*{$\square$}$$

## Corollary 4.2.13
For every $\gamma >0$ and for every $n\in\mathbb{N}$, there exists a unique $y>0$ such that $y^n = \gamma$.

<*proof*>
Let $f(x) := x^n$. Since $f$ is continuous on $\mathbb{R}$, it is also continuous on $[0,\gamma+1]$. Since $(\gamma +1)^n > \gamma, 0<\gamma <(\gamma+1)^n$. By the mean value theorem, there exists $y\in\mathbb{R}$ such that $f(y) = y^n=\gamma$. 

Now we want to show the uniqueness of $y$. Suppose that $y^n_1 = y^n_2=\gamma$. Then,
 $$
 (y^n_1 -y^n_2 )= (y_1 - y_2)(y^{n-1}_1 + y^{n-2}_1y_2 + \cdots + y_1y^{n-1}_2)=0 
 $$
 Since $y_1, y_2 >0, y_1 = y_2$.

## Corollary 4.2.14
If $f:[0,1]\to[0,1]$ is continuous, then there is $y\in [0,1]$ such that $f(y) = y$.

<*proof*>
Let $g(x) := f(x) = x$. Then $g(0) = f(0) \geq 0$, $g(1) = f(1)-1 \leq 0$.  <br /> If $g(0) =0$ or $g(1) =0$, then $f(0) =0$ or $f(1)=1$.

Suppose that $g(0) \neq 0$ and $g(1) \neq 0$. Since $f$ is continuous, by the mean value theorem, there is $y \in \mathbb{R}$ such that $g(y)=0 (\because g(1) < 0 < g(0) )$. 

$\therefore \exists y\in\mathbb{R}$ such that $f(y) = y$.

$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
