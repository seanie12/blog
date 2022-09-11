---
title: "Limit Superior and Inferior of a Sequence"

categories:
  - Analysis


tags:
  - limit superior
  - limit inferior
 

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 2.5.1
Let $\\{s_n\\}$ be a sequence in $\mathbb{R}$. The **limit superior** of $\\{s_n\\}$, denoted as $\limsup_{n\to\infty}s_n$,  is defined as

$$
\begin{align*}
\limsup_{n\to\infty}s_n:=\lim_{k\to\infty}b_k:=\inf_{k\in\mathbb{N}}\sup\{s_n: n\geq k \} \in \mathbb{R} \cup\{ \pm \infty\}
\end{align*}
$$

The **limit inferior** of $\\{s_n\\}$, denoted as $\liminf_{n\to\infty}s_n$, defined as 

$$
\begin{align*}
\liminf_{n\to\infty}s_n:=\lim_{k\to\infty}a_k :=\sup_{k\in\mathbb{N}}\inf\{s_n: n\geq k\} \in \mathbb{R} \cup\{ \pm \infty\}
\end{align*}
$$

## Theorem 2.5.3 
Let $\\{s_n\\}$  be a sequence in $\mathbb{R}$.

(a) $\beta=\limsup_{n\to\infty}s_n$  is a real number if and only if

$$
\begin{align}
\forall \epsilon >0, \exists n_0\in\mathbb{N} \text{ such that } n\geq n_0 \Rightarrow s_n < \beta +\epsilon \label{eq:1} \\
\forall \epsilon >0, \forall n\in\mathbb{N}, \exists k\in\mathbb{N} \text{ with } k\geq n \text{ such that } s_k > \beta-\epsilon \label{eq:2}
\end{align}
$$

(b) $\limsup_{n\to\infty}s_n=\infty$ if and only if 

$$
\begin{align}
\forall M\in\mathbb{R}, \forall n\in\mathbb{R}, \exists k\in\mathbb{N} \text{ with } k\geq n \text { such that } s_k\geq M
\end{align}
$$

(c) $\limsup_{n\to\infty}s_n = -\infty$ if and only if $\lim_{n\to\infty}s_n =-\infty$


<*Proof*>

$\Rightarrow$ Let $\beta= \limsup_{n\to\infty}s_n \in \mathbb{R}$ and let $a_k = \sup_{n\geq k} s_n$. Since $\lim_{k\to\infty}a_k=\beta$, there exists a $n_0\in\mathbb{N}$ such that

$$
\begin{align*}
n\geq n_0 \Rightarrow a_n < \beta + \epsilon.
\end{align*}
$$

Since $a_{n_0}=\sup\\{s_k: k\geq n_0 \\}$, 

$$
\begin{align*}
n\geq n_0 \Rightarrow s_n \leq a_{n_0}<\beta + \epsilon.
\end{align*}
$$

On the other hand, since the sequence $\\{a_k \\}$ is decreasing, $a_n \geq \beta$ for all $n\in\mathbb{N}$. That is 


$$
\begin{align*}
\sup\{s_k: k\geq n\}=a_n\geq \beta > \beta-\epsilon.
\end{align*}
$$

Therefore for each $n\in\mathbb{N}$, there is $k\in\mathbb{N}$ with $k\geq n$ such that $s_k > \beta-\epsilon$.

$\Leftarrow$ Conversely, suppose that Equation $\ref{eq:1}$ and $\ref{eq:2}$ hold.

Let $\epsilon >0$ be given. By Equation $\ref{eq:1}$, there exists a $n_0\in\mathbb{N}$ such that $n\geq n_0 \Rightarrow s_n < \beta + \epsilon$. Since $\beta+\epsilon$ is an upper bound of $\\{s_n: n\geq n_0 \\}$,  

$$
\begin{align*}
a_{n_0}=\sup\{s_n: n\geq n_0 \} \leq \beta+\epsilon.
\end{align*}
$$

Since the sequence $\\{ a_n \\}$ is decreasing, 

$$
\begin{align*}
a_n \leq a_{n_0} \leq \beta +\epsilon \text{ if } n\geq n_0.
\end{align*}
$$

Thus,

$$
\begin{align*}
\limsup_{n\to\infty}s_n=\lim_{n\to\infty}a_n \leq \beta+\epsilon.
\end{align*}
$$

Let $\beta^\prime := \limsup_{n\to\infty}s_n$. Since the choice of $\epsilon$ is an arbitrary, $\beta^\prime \leq \beta$. Now we want to show that $\beta^\prime = \beta$.

Suppose that $\beta^\prime \lneq \beta$. Then we take $\epsilon_0 > 0$ such that 

$$
\begin{align*}
\beta^\prime + \epsilon < \beta -\epsilon_0
\end{align*}
$$

For an instance, $\epsilon_0 := (\beta-\beta^\prime) / 3$. Since $\limsup_{n\to\infty}s_n=\beta^\prime\in\mathbb{R}$, there exits $n_0\in\mathbb{N}$ such that

$$
\begin{align*}
n\geq n_0 \Rightarrow s_n<\beta^\prime +\epsilon < \beta-\epsilon_0
\end{align*}
$$

by Equation $\ref{eq:1}$, which contradicts to Equation $\ref{eq:2}$.

$\therefore \beta=\beta^\prime$.



(b) $\Rightarrow$ Suppose that $\limsup_{n\to\infty}s_n = \infty$. Let $a_k = \sup_{n\geq k}s_n$. Since $\\{a_n \\}$ is decreasing sequence, $a_n=\infty$ for all $n\in\mathbb{N}$. Since $a_n = \sup \\{s_k : k\geq n \\}$, the set $\\{s_k : k\geq n \\}$ is not bounded above. 

$\therefore$ For all $M\in\mathbb{R},$ there is $k\in\mathbb{N}$ with $k\geq n$ such that $s_k > M$.

$\Leftarrow$ Suppose that for all $M\in\mathbb{R}$ and for all $n\in\mathbb{N}$, there is a $k\in\mathbb{N}$ with $k\geq n$ such that $s_k \geq M$. Assume that $a_n=\sup \\{ s_k: k\geq n\\}=\alpha$ is a real number. Then 

$$
\begin{align}
s_k\leq \alpha \text{ for all } k\geq n.
\label{eq:3}
\end{align}
$$

Now take $M:=\alpha+1$. Then by the assumption, there is $k\in\mathbb{N}$ with $k\geq n$ such that 

$$
\begin{align*}
s_k \geq \alpha +1 > \alpha.
\end{align*}
$$

But it  contradicts to the inequality $\ref{eq:3}$.

$\therefore \limsup_{n\to\infty}s_n=\infty$.

(c) $\Rightarrow$ Suppose that $\limsup_{n\to\infty}s_n = -\infty$. Let $a_n=\sup\\{ s_k: k\geq n\\}$. 

Let $M<0$ be given. Since $a_n\to -\infty$ as $n\to\infty$, there exists $n_0\in\mathbb{N}$ such that  $n\geq n_0 \Rightarrow a_n \leq M.$ Since $s_n\leq a_n, s_n \leq a_n <M$ for all $n\geq n_0$.

$\therefore \limsup_{n\to\infty}s_n = -\infty$.

$\Leftarrow$ Suppose that $\lim_{n\to\infty}s_n = -\infty$. Let $M<0$ be given. Then there is $n_0\in\mathbb{N}$ such that $n\geq n_0\Rightarrow s_n \leq M$.

Since $a_{n_0}$ is the least upper bound of $\\{ s_n: n\geq n_0\\}, a_{n_0}\leq M$ and $s_n \leq M$ for all $n\geq n_0$,

$$
\begin{align*}
s_n \leq a_{n_0} \leq M \text{ for all } n\geq n_0.
\end{align*}
$$

Since $\\{ a_n \\}$ is monotone decreasing, $n\geq n_0 \Rightarrow a_n \leq a_{n_0}\leq M$.

$\therefore \limsup_{n\to\infty}s_n = \lim_{n\to\infty}a_n = -\infty$.

$$\tag*{$\square$}$$

## Theorem 2.5.4
Let $\\{s_n\\}$ be a sequence in $\mathbb{R}$.

(a) $\liminf_{n\to\infty}s_n=\alpha\in\mathbb{R}$ if and only if 


$$
\begin{align}
\forall\epsilon >0, \exists n_0\in\mathbb{N} \text{ s.t. } n\geq n_0\Rightarrow s_n>\alpha-\epsilon \labe{eq:4} \\
\forall\epsilon>0, \forall n\in\mathbb{N}, \exists k\in\mathbb{N} \text{ with } k\geq n \text{ s.t. } s_k < \alpha + \epsilon \label{eq:5}
\end{align}
$$

<*Proof*>

Let $\epsilon >0$ be given. Define $b_k :=\inf\\{s_n: n\geq k \\}$. Since $\liminf_{n\to\infty}=\lim_{k\to\infty}b_k=\alpha \in\mathbb{R}$, there exists $n_0\in\mathbb{N}$ such that 

$$
\begin{align*}
k\geq n_0 \Rightarrow b_k > \alpha-\epsilon
\end{align*}
$$

Since $b_k$ is infimum of $\\{ s_n: n\geq k\\}$, 

$$
\begin{align*}
s_n\geq b_k > \alpha-\epsilon \text{ for all } n \geq k \geq n_0.
\end{align*}
$$

$\therefore s_n > \alpha- \epsilon$ for $n\geq n_0$.

On the other hand, $\\{b_k \\}$ is increasing sequence, 

$$
\begin{align*}
\inf\{s_k: k\geq n\}=b_n \leq \alpha < \alpha + \epsilon.
\end{align*}
$$

Since $\alpha$ is the greatest lower bound of $\\{b_n: n=1,2,\ldots \\}, \alpha+\epsilon$ is not a lower bound anymore.

$\therefore s_k < \alpha +\epsilon$ for some $k\geq n$.

$$\tag*{$\square$}$$



## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
