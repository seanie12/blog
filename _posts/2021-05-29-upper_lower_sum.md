---
title: "Riemann Integral"

categories:
  - Analysis

tags:
  - Integration
  - Riemann Integral
  - upper sum
  - lower sum


toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition (upper sum, lower sum)
Let $[a,b]$ with $a<b$ be a closed and bounded interval in $\mathbb{R}$. By a partition of $\mathscr{P}$ of $[a,b]$ we mean a finite set of points 


$$
\begin{align}
\mathscr{P}=\{x_0, x_1,\ldots, x_n\} \text{ such that }
a = x_0 < x_1 < \cdots < x_n =b.
\end{align}
$$

There is no requirement that the points $x_i$ be equally spaced. For each $i=1,2,\ldots,n$, set

$$
\begin{align}
\Delta x_i = x_i - x_{i-1}
\end{align}
$$

which is equal to the length of the interval $[x_{i-1}, x_i]$.

Suppose that $f$ is bounded real valued function on $[a,b]$. Given a partition 

$$
\begin{align}
\mathscr{P}=\{x_0, x_1, \ldots x_n\}
\end{align}
$$ 

of $[a,b]$, for each $i=1,\ldots,n$, let 

$$
\begin{align}
\begin{split}
m_i &= \inf\{f(t): t\in [x_{i-1},x_i]\} \\
M_i &= \sup\{f(t):t\in [x_{i-1},x_i]\}
\end{split}
\end{align}
$$

Since $f$ is bounded, by the least upper bound property, $m_i, M_i$ are real value. If $f$ is continuous function on $[a,b]$, then by Corollary 4.2.9 for each $i$  there exist point s $t_i, s_i \in [x_{i-1},x_i]$ such that $M_i = f(t_i), m_i = f(s_i)$.

The **upper sum** $\mathscr{U}(\mathscr{P},f)$ for the partition $\mathscr{P}$ and function $f$ is defined by

$$
\begin{align}
\mathscr{U}(\mathscr{P}, f) = \sum_{i=1}^n M_i \Delta x_i
\end{align}
$$

Similarly, the **lower sum** $\mathscr{L}(\mathscr{P},f)$ is defined by

$$
\begin{align}
\mathscr{L}(\mathscr{P}, f) = \sum_{i=1}^n m_i \Delta x_i
\end{align}
$$

Since $m_i \leq M_i$ for all $i=1,\ldots, n$, we always have

$$
\begin{align}
\mathscr{L}(\mathscr{P},f) \leq \mathscr{U}(\mathscr{P},f)
\end{align}
$$


## Definition 6.1.1
Let $f$ be a bounded real-valued function on the closed and bounded interval $[a,b]$. The **upper** and **lower** integrals of $f$, denoted $\overline{\int_a^b}f$ and $\underline{\int_a^b}f$ respectively, are defined by

$$
\begin{align}
\begin{split}
\overline{\int_a^b}f &=\inf\{\mathscr{U}(\mathscr{P},f): \mathscr{P}\text{ is a partition of } [a,b]\} \\
\underline{\int_a^b}f &=\sup\{\mathscr{L}(\mathscr{P},f):\mathscr{P}\text{ is a partition of } [a,b]\}
\end{split}
\end{align}
$$


## Definition 6.1.2
A partition of $$\mathscr{P}^{*}$$ of $$[a,b]$$ is a **refinement** of $$\mathscr{P}$$ if $$\mathscr{P}\subset \mathscr{P}^*$$.


## Remark
A refinement of a given partition $\mathscr{P}$ is obtained by adding additional points to $\mathscr{P}$. If $\mathscr{P}_1$ and $\mathscr{P}_2$ are two partitions of $[a,b]$, then $\mathscr{P}_1\cup\mathscr{P}_2$ is a refinement of both $\mathscr{P}_1$ and $\mathscr{P}_2$.

## Lemma 6.1.3
If $\mathscr{P}^*$ is a refinement of $\mathscr{P}$, then 

$$
\begin{align}
\mathscr{L}(\mathscr{P}, f) \leq \mathscr{L}(\mathscr{P}^*, f) \leq \mathscr{U}(\mathscr{P}^*,f )\leq \mathscr{U}(\mathscr{P},f)
\end{align}
$$

<*proof*>
Suppose 

$$
\begin{align}
\mathscr{P}=\{x_0, x_1, \ldots, x_n\}, \mathscr{P}^* = \mathscr{P}\cup \{x^*\}
\end{align}
$$ 

where $$x^*\neq x_j$$ for any $$j=0,1,\ldots,n$$. Then there exists an index $$k$$ such that $$x_{k-1} < x^* <x_{k}$$. Let 

$$
\begin{align}
\begin{split}
M^1_k &= \sup\{f(t):t\in [x_{k-1}, x_k]\}\\
M^2_k &= \sup\{f(t): t\in [x_{k-1},x_k]\}
\end{split}
\end{align}
$$

Since $f(t) \leq M_k$ for all $t\in [x_{k-1},x_k]$, we have that $f(t)\leq M_k$ for all $$t\in[x_{k-1},x^*]$$ and also for all $$t\in [x^*, x_k]$$. Thus both $$M^1_k$$ and $$M^2_k$$ are less than or equal to $$M_k$$. Now

$$
\begin{align}
\mathscr{U}(\mathscr{P},f)=\sum_{j=1}^{k-1}M_j \Delta x_j + M^1_k(x^*-x_{k-1}) + M^2_k(x_k-x^*)  + \sum_{j=k+1}^n M_j \Delta x_j
\end{align}
$$

But

$$
\begin{align}
\begin{split}
M^1_k(x^* - x_{k-1}) + M^2_k(x_k-x^*) &\leq M_k (x^* - x_{k-1}) + M_k(x_k-x^*) \\
&=M_k \Delta x_k
\end{split}
\end{align}
$$

Therefore,
$$\mathscr{U}(\mathscr{P}^*, f) \leq \mathscr{U}(\mathscr{P}, f)$$

The proof for the lower sum is similar. If $\mathscr{P}^*$ contains $k$ more points than $\mathscr{P}$, we need only repeat the above argument $k$ times to obtain the result.
$$\tag*{$\square$}$$

## Theorem 6.1.4
Let $f$ be a bounded real-valued function on $[a,b]$. Then

$$
\underline{\int_a^b}f \leq \overline{\int_a^b}f.
$$

<*proof*>

Given any two partitions $\mathscr{P}, \mathcal{Q}$ of $[a,b]$.
Since $\mathscr{P}\cup\mathcal{Q}$ is both refinement of $\mathscr{P}$ and $\mathcal{Q}$, respectively,

$$
\begin{align}
\mathscr{L}(\mathscr{P},f) \leq \mathscr{L}(\mathscr{P}\cup\mathcal{Q},f) \leq \mathscr{U}(\mathscr{P}\cup\mathcal{Q},f) \leq \mathscr{U}(\mathcal{Q},f) 
\end{align}
$$ 

by lemma 6.1.3. Thus $\mathscr{L}(\mathscr{P}, f) \leq \mathscr{U}(\mathcal{Q},f)$ for any partitions $\mathscr{P}, \mathcal{Q}$. Hence

$$
\begin{align}
\underline{\int_a^b}f = \sup_{\mathscr{P}} \mathscr{L}(\mathscr{P},f) \leq \mathscr{U}(\mathcal{Q},f)
\end{align}
$$

for any partition $\mathcal{Q}$. Now taking the infimum over $\mathcal{Q}$,

$$
\begin{align}
\overline{\int_a^b}f= \inf_{\mathcal{Q}}\mathscr{L}(\mathcal{Q},f) \geq \underline{\int_a^b} f
\end{align}
$$

$\therefore \underline{\int_a^b}f \leq \overline{\int_a^b}f$


## Definition 6.1.5
Let $f$ be a bounded real-valued function on the closed and bounded interval $[a,b]$. If

$$
\begin{align}
\underline{\int_a^b}f = \overline{\int_a^b}f
\end{align}
$$

then $f$ is said to be **Riemann integrable** or **integrable** on $[a,b]$. The common value is denoted by

$$
\begin{align}
\int_a^b f \quad \text{or } \int_a^b f(x) dx,
\end{align}
$$

and is called the **Riemann Integrable** or **Integrable** of $f$ over $[a,b]$. We denote by $\mathscr{R}[a,b]$ the set of *Riemann integrable functions* on $[a,b]$. In addition if $f\in\mathscr{R}[a,b]$, we define

$$
\int_b^a f :=-\int_a^bf.
$$
$$\tag*{$\square$}$$

If $f:[a,b]\to\mathbb{R}$ satisfies $m\leq f(t) \leq M$ for all $t\in [a,b]$, then 


$$
m(b-a) \leq \underline{\int_a^b} f \leq \overline{\int_a^b}f \leq M(b-a).
$$

If, in addition, $f\in \mathscr{R}[a,b]$, then

$$
m(b-a) \leq \int_a^b f \leq M(b-a)
$$
## Reference
-  Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
