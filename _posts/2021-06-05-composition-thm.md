---
title: "Properties of the Riemann Integral"

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

So, $$M^*_k -m^*_k \leq 2K$$.

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


## Theorem 6.2.1
Let $f,g$ be bounded real-valued functions on $[a,b]$ and $f,g,\in\mathscr{R}[a,b]$.

$(a) f+g\in\mathscr{R}[a,b]$ with $\int_a^b(f+g) = \int_a^b f+ \int_a^b g$.

$(b) cf \in \mathscr{R}[a,b]$ with $\int_a^b cf = c\int_a^b f$.

$(c) fg \in \mathscr{R}[a,b]$.

<*proof*>

$(a)$ Let 

$$
\mathscr{P} = \{x_0, \ldots, x_n\}
$$

be a partition of $[a,b]$. Then

$$
\mathscr{U}(\mathscr{P}, f+g) \leq \mathscr{U}(\mathscr{P}, f) + \mathscr{U}(\mathscr{P}, g)
$$

$\because$

$$
\begin{align}
M_i(f) &:= \sup\{f(t): t\in [x_{i-1},x_i]\} \\
M_i(g) &:=\sup\{g(t): t\in [x_{i-1},x_i]\}
\end{align}
$$

For $t\in [x_{i-1}, x_i]$, $f(t)+g(t) \leq M_i(f) + M_i(g)$. So,

$$
\sup \{f(t)+g(t): t\in [x_{i-1},x_i]\} \leq M_i(f) + M_i(g)
$$

Thus,

$$
\begin{align}
\begin{split}
\mathscr{U}(\mathscr{P}, f+g) &=\sum_{i=1}^n M_i (f+g)\Delta x_i \\
&\leq \sum_{i=1}^n M_i(f)\Delta x_i + \sum_{i=1}^n M_i (g)\Delta x_i \\
&=\mathscr{U}(\mathscr{P}, f) + \mathscr{U}(\mathscr{P}, g)
\end{split}
\end{align}
$$

Let $\epsilon >0$ be given. Since $f,g\in \mathscr{R}[a,b]$, there are partitions of $\mathscr{P}_f, \mathscr{P}_g$ of $[a,b]$, respectively such that 

$$
\begin{align}
\begin{split}
\mathscr{U}(\mathscr{P}_f, f) &<\inf_{\mathcal{Q}}\mathscr{U}(\mathcal{Q},f) +\frac{\epsilon}{2}= \overline{\int_a^b}f + \frac{\epsilon}{2} = \int_a^b f + \frac{\epsilon}{2} \\
\mathscr{U}(\mathscr{P}_g, g) &<\inf_{\mathcal{Q}}\mathscr{U}(\mathcal{Q},g) +\frac{\epsilon}{2}= \overline{\int_a^b}g + \frac{\epsilon}{2} = \int_a^b g + \frac{\epsilon}{2}
\end{split}
\end{align}
$$

Let $\mathcal{Q} = \mathscr{P}_f \cup \mathscr{P}_g$. Then $\mathcal{Q}$ is a refinement of $\mathscr{P}_f$ and $\mathscr{P}_g$, respectively.

$$
\begin{align}
\begin{split}
\overline{\int_a^b}f+g &\leq \mathscr{U}(\mathcal{Q}, f+g) \\
&\leq \mathscr{U}(\mathcal{Q},f) + \mathscr{U}(\mathcal{Q},g)\\
&=\mathscr{U}(\mathscr{P}_f, f) + \mathscr{U}(\mathscr{P}_g, g) \\
&<\int_a^bf + \int_a^bg+\epsilon
\end{split}
\end{align}
$$

So, we get

$$
\overline{\int_a^b}(f+g) \leq \int_a^b f + \int_a^b g + \epsilon.
$$

Since $\epsilon$ is arbitrary, we have

$$
\overline{\int_a^b}(f+g) \leq \int_a^b f + \int_a^b g
$$

Similarly, $\mathscr{L}(\mathscr{P}, f+g) \geq \mathscr{L}(\mathscr{P},f) + \mathscr{L}(\mathscr{P}, g)$.

$$
\begin{align}
\begin{split}
\mathscr{L}(\mathscr, f+g) &=\sum_{i=1}^n m_i (f+g) \Delta x_i\\
&\geq \sum_{i=1}^n m_i (f) \Delta x_i + \sum_{i=1}^n m_i (g) \Delta x_i\\
&=\mathscr{L}(\mathscr{P},f) + \mathscr{L}(\mathscr{P},g)
\end{split}
\end{align}
$$

Since $f\in\mathscr{R}[a,b]$, there exist partition $\mathscr{P}_f, \mathscr{P}_g$ of $[a,b]$, respectively such that 

$$
\begin{align}
\mathscr{L}(\mathscr{P}_f, f) + \frac{\epsilon}{2} &> \sup_{\mathcal{Q}}\mathscr{L}(\mathcal{Q}, f) = \underline{\int_a^b}f = \int_a^b f\\
\mathscr{L}(\mathscr{P}_g, g) + \frac{\epsilon}{2} &> \sup_{\mathcal{Q}}\mathscr{L}(\mathcal{Q}, g) = \underline{\int_a^b}g = \int_a^b g
\end{align}
$$

Let $\mathscr{S}= \mathscr{P}_f \cup \mathscr{P}_g$. Then $\mathscr{S}$ is a refinement of $\mathscr{P}_f$ and $\mathscr{P}_g$, respectively.

$$
\begin{align}
\begin{split}
\underline{\int_a^b}f+g &\geq \mathscr{L}(\mathscr{S}, f+g) + \mathscr{L}(\mathscr{S}, g) \\
&\geq \mathscr{L}(\mathscr{P}_f, f) + \mathscr{L}(\mathscr{P}_g, g)\\
&> \int_a^b f + \int_a^b g - \epsilon
\end{split}
\end{align}
$$

Since $\epsilon >0$ is arbitrary,  we get

$$
\underline{\int_a^b}f+g \geq \int_a^b f + \int_a^b g
$$

Finally, 

$$
\int_a^b f + \int_a^b g \leq \underline{\int_a^b} f+g \leq \overline{\int_a^b}f+g \leq \int_a^b f + \int_a^b g 
$$

$\therefore f+g \in\mathscr{R}[a,b]$ with

$$
\int_a^b f+g = \int_a^b f + \int_a^b g
$$

$$\tag*{$\square$}$$


## Reference
-  Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
