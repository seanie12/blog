---
title: "Riemann Integral"

categories:
  - Analysis

tags:
  - Riemann Integral
  - Composition Theorem


toc: true
toc_sticky: true

use_math : true
comments : true

---


## Theorem 6.1.9
Let $f:[a,b]\to\mathbb{R}$ be a bounded real valued Riemann integrable function with $Range f \subset [c,d]$. Let $\varphi:[c,d]\to\mathbb{R}$ be a continuous function on $[c,d]$.  Then

$$
\varphi\circ f \in \mathscr{R}[a,b]
$$

<*proof*>
Let $\epsilon >0$ be given. Since $\varphi$ is continuous on $[c,d]$, $\varphi$ is uniformly continuous on $[c,d]$. Let 

$$
K:=\sup \{ |\varphi(t)|: t\in [c,d]\}
$$

and let 

$$
\epsilon^\prime := \frac{\epsilon}{b-a+2K}.
$$

Since $\varphi$ is uniformly continuous on $[c,d]$, there exists $0<\delta<\epsilon^\prime$ such that 

$$
|s-t|<\delta \text{ with } s,t\in[c,d] \Rightarrow |\varphi(s)-\varphi(t)|<\epsilon^\prime.
$$

Since $f\in\mathscr{R}[a,b]$, there is a partition 

$$
\mathscr{P}=\{x_0, \ldots, x_n\} \text{ of } [a,b] \text{ such that } \mathscr{U}(\mathscr{P},f) - \mathscr{L}(\mathscr{P},f) < \delta^2.
$$

Now we want to show that $\mathscr{U}(\mathscr{P}, \varphi\circ f) - \mathscr{L}(\mathscr{P},\varphi\circ f) < \epsilon$. We write

$$
\begin{align}
\begin{split}
m_k &= \inf \{ f(t): t\in [x_{k-1}, x_k]\}\\
M_k &=\sup \{f(t):t\in [x_{k-1}, x_k]\} \\
m^*_k &= \inf \{ (\varphi\circ f)(t): t\in[x_{k-1},x_k]\} \\
M^*_k &= \sup \{ (\varphi\circ f)(t): t\in[x_{k-1},x_k]\} 
\end{split}
\end{align}
$$

Let 

$$
\begin{align}
\begin{split}
A&:=\{k: M_k - m_k <\delta\}\\
B &:=\{k: M_k - m_k \geq \delta \}
\end{split}
\end{align}
$$

If $k\in A$, then

$$
\left|\varphi(f(s))-\varphi(f(t)) \right| < \epsilon^\prime
$$

for all $s,t\in [x_{k-1}, x_k]$.  For $k\in A$,

$$
\begin{align}
\begin{split}
M^*_k - m^*_k &=\sup\{\varphi(f(t)): t \in [x_{k-1}, x_k]\}  - \inf\{\varphi(f(t)): t \in [x_{k-1}, x_k]\} \\
&=\sup \{\varphi(f(t)): t \in [x_{k-1}, x_k]\} + \sup \{-\varphi(f(t)): t \in [x_{k-1}, x_k]\} \\
&=\sup\{\varphi(f(t))-\varphi(f(s)): t,s \in [x_{k-1}, x_k]\} \\
&\leq \sup\{\left|\varphi(f(t))-\varphi(f(s))\right|: t,s\in [x_{k-1},x_k]\}\\
&\leq \epsilon^\prime
\end{split}
\end{align}
$$

If $k\in B$, 

$$
\begin{align}
\begin{split}
M^*_k &=\sup\{\varphi(f(t)): t\in [x_{k-1},x_k]\} \\
&\leq \sup \{|\varphi(f(t))|: t\in [x_{k-1},x_k]\} \\
&\leq \sup \{|\varphi(f(t))|: t\in [c,d]\} \\
&=K
\end{split}
\end{align}
$$

Similarly,

$$
\begin{align}
\begin{split}
-m^*_k &= \sup\{-\varphi(f(t)): t\in [x_{k-1},x_k]\}\\
&\leq \sup\{ |\varphi(f(t)): t\in [x_{k-1},x_k]\}\\
&\leq \sup \{|\varphi(f(t))|: t\in [c,d]\} \\
&=K
\end{split}
\end{align}
$$

So, $M^*_k -m^*_k \leq 2K$.

Now,
$$
\begin{align}
\begin{split}
\mathscr{U}(\mathscr{P}, \varphi\circ f) - \mathscr{L}(\mathscr{P},\varphi\circ f) &= \sum_{i=1}^n (M^*_i- m^*_i)\Delta x_i \\
&=\sum_{k\in A}(M^*_k- m^*_k)\Delta x_k + \sum_{k\in B}(M^*_k- m^*_k)\Delta x_k \\
&\leq \epsilon^\prime \sum_{k\in A}\Delta x_k + 2K\sum_{k\in B} \Delta x_k \\
&< \epsilon^\prime (b-a) + 2K \sum_{k\in B} \Delta x_k
\end{split}
\end{align}
$$

Then we need to derive the upper bound of sum of $\Delta x_k$ with the condition $f \in\mathscr{R}[a,b]$ and $M_k - m_k \geq \delta$ for $k\in B$. 

Since $M_k - m_k \geq \delta$ for $k\in B$, $\frac{M_k-m_k}{\delta} \geq 1$.

$$
\begin{align}
\begin{split}
\sum_{k\in B} \Delta x_k &\leq \sum_{k\in B} \frac{M_k-m_k}{\delta}\Delta x_k \\
&\leq \frac{1}{\delta}\sum_{i=1}^n(M_i-m_i)\Delta x_i\\
&=\frac{1}{\delta}\left(\mathscr{U}(\mathscr{P},f) - \mathscr{L}(\mathscr{P},f) \right) \\
&< \delta \\
&< \epsilon^\prime
\end{split}
\end{align}
$$

Combining the equation $(6)$ and $(7)$,  we get 

$$
\begin{align}
\begin{split}
\mathscr{U}(\mathscr{P}, \varphi\circ f) - \mathscr{L}(\mathscr{P}, \varphi\circ f) &< \epsilon^\prime (b-a) + 2K \epsilon^\prime\\
&=\epsilon^\prime (b-a+2K)\\
&=\epsilon
\end{split}
\end{align}
$$

$\therefore \varphi\circ f \in \mathscr{R}[a,b]$.
$$\tag*{$\square$}$$


## Reference
-  Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
