---
title: "Uniform Convergence and Continuity"

categories:
  - Analysis

tags:
  - continuity
  - uniform convergence
  - Dini Theorem
toc: true
toc_sticky: true

use_math : true
comments : true

---

## Theorem 8.3.1 
Suppose $\\{f_n\\}$ is a sequence of real-valued functions that converges uniformly to a function $f$ on a subset $E$ of $\mathbb{R}$. Let $p$ be a limit point of $E$ and suppose that for each $n\in\mathbb{N}$,


$$
\begin{align*}
\lim_{x\to p}f_n(x) = A_n.
\end{align*}
$$

Then the sequence $\\{A_n\\}$ converges and 

$$
\begin{align*}
\lim_{x\to p} f(x) = \lim_{n\to\infty} A_n
\end{align*}
$$


<*Proof*>

Let $\epsilon >0$ be given. Since $f_n \rightrightarrows f$ on $E$, there is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
m,n\geq N, x\in E \Rightarrow \lvert f_n(x) - f_m(x) \rvert < \frac{\epsilon}{3}.
\end{align*}
$$

Since $f_n(x) \to A_n$ and $f_m(x) \to A_m$ as $x\to p$, there is a $\delta >0$ such that

$$
\begin{align*}
0 < \lvert x-p \rvert < \delta, x\in E \Rightarrow \lvert f_n(x) - A_n \rvert < \frac{\epsilon}{3} \text{ and } \lvert f_m(x) - A_m \rvert < \frac{\epsilon}{3}.
\end{align*}
$$

Thus,

$$
\begin{align*}
\lvert A_m - A_n\rvert &= \lvert A_m - f_m(x) + f_m(x) - f_n(x) + f_n(x) - A_n\rvert \\
&\leq \lvert A_m - f_m(x) \rvert + \lvert f_m(x) -f_n(x) \rvert + \lvert f_n(x) -A_n \rvert \\
&< \frac{\epsilon}{3} + \frac{\epsilon}{3} + \frac{\epsilon}{3} = \epsilon
\end{align*}
$$

for any $m,n \geq N$ and $x\in N^\prime_\delta (p) \cap E$.

$\therefore \\{A_n\\}$ is Cauchy sequence.

Let $A=\lim_{n\to\infty}A_n$. We want to show that $\lim_{x\to p} f(x) = A$.

Let $\epsilon >0$ be given. Since $f_n \rightrightarrows f$ on $E$, there is $N_1\in\mathbb{N}$ such that 

$$
\begin{align*}
m\geq N_1, x\in E \Rightarrow \lvert f(x) - f_m(x) \rvert < \frac{\epsilon}{3}.
\end{align*}
$$

Since $A_n \to A$, there is $N_2\in\mathbb{N}$ such that 

$$
\begin{align*}
m\geq N_2 \Rightarrow \lvert A - A_m\rvert < \frac{\epsilon}{3}.
\end{align*}
$$

Since $\lim_{x\to p} f_m(x) = A_m$, there exists $\delta>0$ such that 

$$
\begin{align*}
0<\lvert x-p \rvert < \delta \Rightarrow \lvert f_m(x) -A_m\rvert < \frac{\epsilon}{3}.
\end{align*}
$$

Put $N=\max\\{N_1, N_2\\}\in\mathbb{N}$. If $0<\lvert x - p \rvert <\delta$ and $x\in E$, then

$$
\begin{align*}
\lvert f(x) - A \rvert &\leq \lvert f(x) - f_N(x) \rvert + \lvert f_N(x) - A_N\rvert + \lvert A_N -A \rvert \\
&< \frac{\epsilon}{3} + \frac{\epsilon}{3} + \frac{\epsilon}{3}  = \epsilon.
\end{align*}
$$

$\therefore \lim_{x\to p}f(x) = A= \lim_{n\to\infty}A_n$.

$$\tag*{$\square$}$$





## Remark
The last sentence can be written as 

$$
\begin{align*}
\lim_{x\to p} \left(\lim_{n\to\infty}f_n(x) \right)= \lim_{n\to\infty}\left( \lim_{x\to p}f(x)\right)
\end{align*}
$$


## Corollary 8.3.2
(a) If $\\{f_n\\}$ is a a sequence of continuous real-valued functions on $E$, and if $\\{f_n\\}$ converges uniformly to $f$ on $E$, then $f$ is continuous on $E$.

(b) If $\\{f_n \\}$ is a sequence of continuous real-valued functions on $E$, and if $\sum_{n=1}^\infty f_n$ converges uniformly on $E$, then

$$
\begin{align*}
S(x) = \sum_{n=1}^\infty f_n(x)
\end{align*}
$$

is continuous on $E$.

<*Proof*>

(a) If $p$ is isolated point, i.e., $N_{\delta_0}(p) \cap E=\\{p\\}$ for some $\delta_0>0$, then $f$ is continuous at $p$.  If $p\in E$ is a limit point of $E$, then since $f_n$ is continuous for each $n\in\mathbb{N}$,

$$
\begin{align*}
\lim_{x\to p}f_n(x) = f_n(p).
\end{align*}
$$

Thus by the previous theorem,

$$
\begin{align*}
\lim_{x\to p} f(x) &= \lim_{x\to p}\left(\lim_{n\to\infty}f_n(x)\right) \\
&=\lim_{n\to\infty}\left(\lim_{x\to p}f_n(x) \right) \\
&= \lim_{n\to\infty}f_n(p) \\
&= f(p)
\end{align*}
$$


(b) Let 

$$
\begin{align*}
S_n(x) = \sum_{k=1}^n f_k(x).
\end{align*}
$$


Then for each $n\in\mathbb{N}$, $S_n$ is continuous on $E$. Since $\\{S_n\\}$ converges uniformly to $S$ on $E$, by part (a) $S$ is also continuous on $E$.

$$\tag*{$\square$}$$

## Theorem 8.3.5 (Dini)
Suppose $K$ is a compact subset of $\mathbb{R}$ and $\\{f_n\\}$ is a a sequence of continuous real-valued functions on $K$ satisfying the following:

(a) $\\{f_n\\}$ converges pointwise on $K$ to a continuous function $f$, and 

(b) $f_n(x) \geq f_{n+1}(x)$ for all $x\in K$ and $n\in\mathbb{N}$.

Then $\\{f_n\\}$ converges uniformly to $f$ on $K$.



$$\tag*{$\square$}$$
## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
