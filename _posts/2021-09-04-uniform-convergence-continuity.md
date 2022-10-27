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


<*Proof*>
We want to show that for every $\epsilon>0$, there exists $N\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N, x\in K \Rightarrow \lvert f_n(x) - f(x)\rvert < \epsilon.
\end{align*}
$$

Observe that it suffices to show that there exists $N\in\mathbb{N}$ such that 

$$
\begin{align*}
f_N(x) - f(x) < \epsilon
\end{align*}
$$

for all $x\in K$ since $\\{f_n(x)\\}$ is monotone decreasing for all $x\in K$. Let $g = f_n - f$ and let $K_n=\\{x\in K: g(x) \geq \epsilon\\}$ for each $n\in \mathbb{N}$. We want to show that $K_N=\emptyset$ for some $N\in\mathbb{N}$.

First, $K_n$ is closed set for all $n\in\mathbb{N}$. Let $p\in K^\prime_n$ be given. Then there is a sequence $\\{x_k\\}_{k=1}^\infty$ such that $x_k\to p$ with $x_k\neq p$ for all $k\in\mathbb{N}$.

Since $g_n$ is continuous and $g_n(x_k)\geq \epsilon$ for all $k\in\mathbb{N}$,

$$
\begin{align*}
g_n(p) = g_n\left(\lim_{k\to\infty}(x_k)\right) = \lim_{k\to\infty}\left(g_n(x_k)\right) \geq \epsilon.
\end{align*}
$$

$\because$ Suppose that $g_n(p) < \epsilon$. Let $\epsilon_0= \epsilon-g_n(p)$. Since $g_n(x_k)\to g(p)$ as $p\to\infty$, there exists $N\in\mathbb{N}$ such that 

$$
\begin{align*}
k\geq N \Rightarrow \lvert g_n(x_k) -g(p) \rvert < \epsilon_0.
\end{align*}
$$

However,

$$
\begin{align*}
\lvert g_n(x_k) - g_n(p) \rvert &= g_n(x_k) - g_n(p) \\
&\geq \epsilon-g_n(p) \\
&=\epsilon_0,
\end{align*}
$$

which is a contradiction. Thus, $g_n(p) \geq \epsilon$, i.e., $p\in K_n$.

$\therefore K_n$ is closed.

Alternatively, we can show $K_n$ is closed by using the topological characterization of continuous function.  Since $[\epsilon, \infty)^c = (-\infty, \epsilon)$ is open, $[\epsilon, \infty)$ is closed. Since $K_n=g^{-1}\left([\epsilon, \infty)\right)$ and $g$ is continuous, $K_n$ is closed.


Since $K_n$ is closed and $K_n \subset K$, $K_n$ is compact and $K_n\supset K_{n+1} (\because g_n(x) \geq g_{n+1}(x)).$

Now we want to show that $\bigcap_{n=1}^\infty K_n=\emptyset$. Suppose that $\bigcap_{n=1}^\infty K_n\neq \emptyset$ and let $x_0 \in \bigcap_{n=1}^\infty K_n$ be given.  In other words, 

$$
\begin{align*}
g_n(x_0) \geq \epsilon \text{ for all } n \in \mathbb{N}.
\end{align*}
$$

Since $g_n(x_0) \to 0$ as $n\to\infty$, for the given $\epsilon$, there is $N\in\mathbb{N}$ such that 


$$
\begin{align*}
n\geq N\Rightarrow \lvert g_n(x_0)\rvert <\epsilon,
\end{align*}
$$

which is a contradiction to the assumption that $\lvert g_n(x_0)\rvert$ for all $n\in\mathbb{N}$. 

$\therefore \bigcap_{n=1}^\infty K_n\neq \emptyset$.

By [Theorem 3.2.7](https://seanie12.github.io/blog/analysis/compact/#theorem-327), there is a $K_{n_0}=\emptyset$ for some $n_0\in\mathbb{N}$. That is if $n\geq n_0$, then 

$$
\begin{align*}
g_n(x) < \epsilon
\end{align*}
$$

for all $x\in K$.

$\therefore g_n \rightrightarrows 0$ on $K$, i.e., $f_n\rightrightarrows f$ on $K$.

$$\tag*{$\square$}$$


## The Space $\mathscr{C}[a,b]$
$\mathscr{C}[a,b]$ is the set of all continuous real-valued functions on $[a,b]$. For $f,g\in \mathscr{C}[a,b]$ and $c\in\mathbb{R}$,  we can define binary operation and scalar multiplication as follows:

(a) $(f+g)(x) := f(x) + g(x)$

(b) $(cf)(x) :=c\cdot f(x)$

Then $(\mathscr{C}[a,b], +, \cdot)$ is $\mathbb{R}$-vector space.

## Definition 8.3.7
For each $f\in \mathscr{C}[a,b]$, set 

$$
\begin{align*}
\lVert f\rVert_u=\sup\{\lvert f(x)\rvert: x\in [a,b] \}.
\end{align*}
$$

The quantity $\lVert f\rVert_u$ is called the **uniform norm** of $f$ on $[a,b]$.


## Theorem 8.3.8
A sequence $\\{f_n\\}$ in $\mathscr{C}[a,b]$ converges uniformly to $f\in\mathscr{C}[a,b]$ if and only if given $\epsilon>0$, there exists $n_0\in\mathbb{N}$ such that $\lVert f-f_n\rVert_u < \epsilon$ for all $n\geq n_0$. 

<*Proof*>

Since 

$$
\begin{align*}
\lVert f_n - f\rVert_u = \sup\{\lvert f_n(x) - f(x)\rvert: x\in [a,b]\},
\end{align*}
$$

by [Theorem 8.2.5](https://seanie12.github.io/blog/analysis/pointwise-uniform-convergence/#theorem-825),  we are done.

$$\tag*{$\square $}$$

## Theorem 8.3.11
The metric space $(\mathscr{C}[a,b], \lVert \cdot \rVert_u)$ is complete.

<*Proof*>

Let $\\{f_n\\}$ be a Cauchy sequence in $\mathscr{C}[a,b]$. Given $\epsilon>0$ there is $N\in\mathbb{N}$ such that 

$$\begin{align*}
m,n \geq N \Rightarrow \lVert f_n - f_m \rVert_u < \epsilon. 
\end{align*}
$$

By the definition of uniform norm,

$$\begin{align*}
\lvert f_n(x) - f_m(x) \rvert \leq \sup_{x\in [a,b]}\{\lvert f_n(x) - f_m(x)\rvert\}=\lVert f_n -f_m\rVert_u
\end{align*}
$$

for all $x\in [a,b]$.

By Cauchy criterion, $\\{f_n\\}$ converges uniformly to $f$. Since $f_n$ is continuous for all $n\in\mathbb{N}$, by [Corollary 8.3.2](https://seanie12.github.io/blog/analysis/uniform-convergence-continuity/#corollary-832) $f$ is continuous on $[a,b]$, i.e., $f\in\mathscr{C}[a,b]$.

Since $f_n \rightrightarrows f$, $f\stackrel{\lVert \cdot \rVert_u}{\to}f$ by [Theorem 8.3.8](https://seanie12.github.io/blog/analysis/uniform-convergence-continuity/#corollary-838).

$\therefore (\mathscr{C}[a,b], \lVert \cdot \rVert_u)$ is complete.


$$\tag*{$\square$}$$

## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
