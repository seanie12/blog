---
title: "Riemann Integral"

categories:
  - Analysis

tags:
  - Integration
  - Riemann Integral



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition (upper sum, lower sum)
Let $[a,b]$ with $a<b$ be a closed and bounded interval in $\mathbb{R}$. By a partition of $\mathscr{P}$ of $[a,b]$ we mean a finite set of points 

$$\mathscr{P}=\{x_0, x_1,\ldots, x_n\} \text{ such that }
a = x_0 < x_1 < \cdots < x_n =b.
$$

There is no requirement that the points $x_i$ be equally spaced. For each $i=1,2,\ldots,n$, set

$$
\Delta x_i = x_i - x_{i-1}
$$

which is equal to the length of the interval $[x_{i-1}, x_i]$.

Suppose that $f$ is bounded real valued function on $[a,b]$. Given a partition 

$$\mathscr{P}=\{x_0, x_1, \ldots x_n\}$$ 

of $[a,b]$, for each $i=1,\ldots,n$, let 

$$
m_i = \inf\{f(t): t\in [x_{i-1},x_i]\} \\
M_i = \sup\{f(t):t\in [x_{i-1},x_i]\}
$$

Since $f$ is bounded, by the least upper bound property, $m_i, M_i$ are real value. If $f$ is continuous function on $[a,b]$, then by Corollary 4.2.9 for each $i$  there exist point s $t_i, s_i \in [x_{i-1},x_i]$ such that $M_i = f(t_i), m_i = f(s_i)$.

The **upper sum** $\mathscr{U}(\mathscr{P},f)$ for the partition $\mathscr{P}$ and function $f$ is defined by

$$
\mathscr{U}(\mathscr{P}, f) = \sum_{i=1}^n M_i \Delta x_i
$$

Similarly, the **lower sum** $\mathscr{L}(\mathscr{P},f)$ is defined by

$$
\mathscr{L}(\mathscr{P}, f) = \sum_{i=1}^n m_i \Delta x_i
$$

Since $m_i \leq M_i$ for all $i=1,\ldots, n$, we always have

$$
\mathscr{L}(\mathscr{P},f) \leq \mathscr{U}(\mathscr{P},f)
$$


## Definition 6.1.1
Let $f$ be a bounded real-valued function on the closed and bounded interval $[a,b]$. The **upper** and **lower** integrals of $f$, denoted $\overline{\int_a^b}f$ and $\underline{\int_a^b}f$ respectively, are defined by

$$
\overline{\int_a^b}f =\inf\{\mathscr{U}(\mathscr{P},f): \mathscr{P}\text{ is a partition of } [a,b]\} \\
\underline{\int_a^b}f =\sup\{\mathscr{L}(\mathscr{P},f):\mathscr{P}\text{ is a partition of } [a,b]\}
$$

## Definition 6.1.2
A partition of $\mathscr{P}^{*}$ of $[a,b]$ is a **refinement** of $\mathscr{P}$ if $\mathscr{P}\subset \mathscr{P}^*$.

## Remark
A refinement of a given partition $\mathscr{P}$ is obtained by adding additional points to $\mathscr{P}$. If $\mathscr{P}_1$ and $\mathscr{P}_2$ are two partitions of $[a,b]$, then $\mathscr{P}_1\cup\mathscr{P}_2$ is a refinement of both $\mathscr{P}_1$ and $\mathscr{P}_2$.

## Lemma 6.1.3
If $\mathscr{P}^*$ is a refinement of $\mathscr{P}$, then 

$$
\mathscr{L}(\mathscr{P}, f) \leq \mathscr{L}(\mathscr{P}^*, f) \leq \mathscr{U}(\mathscr{P}^*,f )\leq \mathscr{U}(\mathscr{P},f)
$$

<*proof*>
Suppose $$\mathscr{P}=\{x_0, x_1, \ldots, x_n\}$$ and $$\mathscr{P}^* = \mathscr{P}\cup \{x^*\}$$, where $x^*\neq x_j$ for any $j=0,1,\ldots,n$. Then there exists an index $k$ such that $x_{k-1} < x^* <x_{k}$. Let 

$$
M^1_k = \sup\{f(t):t\in [x_{k-1}, x_k]\}\\
M^2_k = \sup\{f(t): t\in [x_{k-1},x_k]\}
$$

$$\tag*{$\square$}$$



## Reference

[1] Oslen, Lars, A New Proof of darboux’s Theorem, The American Mathematical Society, Vol. 111, No. 8(Oct., 2004), pp. 713-715.

[2] Bhandari, Mukta Bahadur. “Another Proof of Darboux's Theorem.” _arXiv: History and Overview_ (2016): n. pag.

[3] Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
