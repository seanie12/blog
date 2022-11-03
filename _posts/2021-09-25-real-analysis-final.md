---
title: "Equicontinuous Families of Functions"

categories:
  - Analysis

tags:
  - Ascoli-Azrela Theorem
  - Stone-Weirstrass Theorem

 
toc: true
toc_sticky: true

use_math : true
comments : true

---

## Theorem (Ascoli-Azrela)
Let $\\{f_n\\}$ be a sequence of functions defined on a set $K$. If $K$ is compact, $\\{f_n\\}$ is pointwise bounded on $K$, $\\{f_n\\}$ is equicontinuous then

(a) $\\{f_n\\}$ is uniformly bounded on $K$

(b) $\\{f_n\\}$ has a uniformly convergence subsequence.


<*Proof*>

(a) Fix an $\epsilon>0$. By equicontinuity, there is a $\delta>0$ such that

$$
\begin{align*}
d(x,y) < \delta \Rightarrow d(f_n(x), f_n(y)) <\epsilon
\end{align*}
$$

for all $x,y \in K$ and for all $n\in\mathbb{N}$. Now cover the set $K$ with $\\{N_\delta (x): x\in K\\}$. Since $K$ is compact, there is a finite sub-cover $\\{N_\delta(x_1), \ldots, N_\delta(x_n)\\}$. Since $\\{f_n\\}$ is pointwise bounded, for each $x_i$, there is $M_i>0$ such that 

$$
\begin{align*}
\lvert f_n(x_i) \rvert \leq M_i
\end{align*}
$$

for all $n\in\mathbb{N}$. Now let $M :=\max\\{M_1, \ldots, M_n\\}+\epsilon$. For any $x\in K$, choose $x_i$ such that $x\in N_\delta(x_i)$, i.e., $d(x, x_i) <\delta$. Then

$$
\begin{align*}
\lvert f_n(x) \rvert &= \lvert f_n(x) - f_n(x_i)+  f_n(x_i) \rvert \\
&\leq \lvert f_n(x) - f_n(x_i)\rvert + \lvert f_n(x_i) \rvert \\
&< \epsilon + M_i \\
&\leq M
\end{align*}
$$


(b) Exercise) If $K$ is compact metric space, then there is countable dense subset $E \subset K$, i.e., $K=E\cup E^\prime$. By previous [Theorem](https://seanie12.github.io/blog/analysis/equicontinuity/#theorem-723), there exists a subsequence $\\{f_{n_k}\\}$ pointwise converges on $E$.

We want to show that $\\{f_{n_k}\\}$ is uniformly convergent subsequence. 

Let $\epsilon >0$ be given.  By equicontinuity, there exists a $\delta>0$ such that 


$$
\begin{align*}
d(x,y) < \delta \Rightarrow d(f_{n_k}(x) - f_{n_k}(x)) < \epsilon
\end{align*}
$$

for all $k\in\mathbb{N}$. Cover $E$ with $\\{N_\delta (e): e\in E\\}$. Since $E$ is dense, it also covers $K$. By compactness of $K$, there exists a finite sub-cover $\\{N_\delta (e_1), \ldots, N_\delta (e_p)\\}$ of $K$. Since $$\\{f_{n_k\\}$ converges pointwise on $E$, for each $e_i$, there exists $N\in\mathbb{N}$ such that 

$$
\begin{align*}
k,l > N_i \Rightarrow \lvert f_{n_k}(e_i) - f_{n_l}(e_i)\rvert <\epsilon.
\end{align*}
$$

Let $N=\max\\{N_1, \ldots, N_p\\}$ and let  $x\in K$ be given. Choose $e_i$ such that $x\in N_\delta(e_i)$. Then, if $k,l >N$

$$
\begin{align*}
\lvert f_{n_k}(x) - f_{n_l}(x) \rvert &\leq \lvert f_{n_k}(x) - f_{n_k}(e_i)\rvert + \lvert f_{n_k}(e_i) - f_{n_l}(e_i)\rvert + \lvert f_{n_l}(e_i)-f_{n_l}(x) \rvert \\
&<3\epsilon.
\end{align*}
$$

$\therefore \\{f_{n_k}\\}$ converges uniformly on $K$ by Cauchy criterion.

$$\tag*{$\square$}$$




## Reference
- Walter Rudin, **『**Principles of Mathematical Analysis**』**
