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

$\Leftarrow$ Suppose that for all $M\in\mathbb{R}$ and for all $n\in\mathbb{N}$, there is a $k\in\mathbb{N}$ with $k\geq n$ such that $s_k \geq M$. Then the set $E_n :=\\{s_k : k\geq n \\}$ is not bounded above and thus $a_n=\sup E_n=\infty$ for all $n\in\mathbb$.

$\therefore \limsup_{n\to\infty}s_n = \inf_{n\in\mathbb{N}}a_n=\infty$



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
\forall\epsilon >0, \exists n_0\in\mathbb{N} \text{ s.t. } n\geq n_0\Rightarrow s_n>\alpha-\epsilon \label{eq:4} \\
\forall\epsilon>0, \forall n\in\mathbb{N}, \exists k\in\mathbb{N} \text{ with } k\geq n \text{ s.t. } s_k < \alpha + \epsilon \label{eq:5}
\end{align}
$$

<*Proof*>

$\Rightarrow$ Let $\epsilon >0$ be given. Define $b_k :=\inf\\{s_n: n\geq k \\}$. Since $\liminf_{n\to\infty}=\lim_{k\to\infty}b_k=\alpha \in\mathbb{R}$, there exists $n_0\in\mathbb{N}$ such that 

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

$\Leftarrow$ Conversely, suppose that Equation $\ref{eq:4}$ and $\ref{eq:5}$ hold.

Let $\epsilon >0$ be given. By Equation $\ref{eq:4}$, there is a $n_0\in\mathbb{N}$ such that 



$$
\begin{align*}
n\geq n_0 \Rightarrow s_n > \alpha-\epsilon.
\end{align*}
$$

In other words, $\alpha-\epsilon$ is a lower bound of $\\{s_n: n\geq n_0\\}$ and thus 

$$
\begin{align*}
b_{n_0}=\inf\{s_n: n\geq n_0\}\geq \alpha-\epsilon
\end{align*}
$$

Since $\\{b_k\\}$ is monotone increasing,  $b_n\geq b_{n_0}$ for all $n\geq n_0$, i.e., $b_n \geq \alpha -\epsilon$ for $n\geq n_0$. 

Thus, $\liminf_{n\to\infty}s_n = \lim_{n\to\infty}b_n \geq \alpha-\epsilon$. Since the choice of $\epsilon >0$ is an arbitrary, $\alpha^\prime :=\liminf_{n\to\infty}s_n \geq \alpha$.

Now we want to show that $\alpha^\prime = \alpha$. Suppose that $\alpha^\prime \gneq\alpha$. Then we can take $\epsilon_0>0$ such that $\alpha^\prime -\epsilon_0 > \alpha +\epsilon_0$.

Since $\alpha^\prime = \liminf_{n\to\infty}s_n$, there exits a $n_0\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq n_0 \Rightarrow s_n > \alpha^\prime-\epsilon > \alpha+\epsilon_0,
\end{align*}
$$
which contradicts to the inequality $\ref{eq:5}$.

$\therefore \alpha=\liminf_{n\to\infty}s_n$.

$$\tag*{$\square$}$$


(b) $\liminf_{n\to\infty}s_n=-\infty$ if and only if 

$$
\begin{align}
\forall M\in\mathbb{R}, \forall n\in\mathbb{N}, \exists k\in\mathbb{N} \text{ with } k\geq n \text{ such that } s_k \leq M
\label{eq:6}
\end{align}
$$

<*Proof*>

$\Rightarrow$ Suppose that $\liminf_{n\to\infty}s_n=-\infty$. Let $b_k :=\inf \\{s_n: n\geq k\\}$. Since $\lim\inf_{n\to\infty}s_n = \sup_{k\in\mathbb{N}}b_k=-\infty$ $b_n=-\infty$ for all $n\in\mathbb{N}$. 

Since $\inf\\{s_k: k\geq n \\}=b_n$,  the set $\\{s_k: k\geq n \\}$ is not bounded below. Thus,  for any $M\in\mathbb{R}$, there is $k\in\mathbb{N}$ with $k\geq n$ such that $s_k > M$.

$\therefore$ for all $M\in\mathbb{R}$ for all $n\in\mathbb{N}$, there is $k\in\mathbb{N}$ with $k\geq n$ such that $s_k > M$.

$\Leftarrow$  Let $b_n =\inf\\{s_k: k\geq n \\}$. For all $M\in\mathbb{R},$ and for all $n\in\mathbb{N}$, 
there is $k\in\mathbb{N}$ with $k\geq n$ such that $s_k \leq M$ by the assumption $\ref{eq:6}$. It implies that the set $E_n:=\\{s_k: k\geq n \\}$  is not bounded below for all $n\in\mathbb{N}$ and thus $b_n = -\infty$ for all $n\in\mathbb{N}$.

$\therefore \liminf_{n\to\infty}=\sup_{n\in\mathbb{N}}b_n=-\infty$
 
 (c) $\liminf_{n\to\infty}s_n =\infty$ if and only if $s_n\to\infty$ as $n\to\infty$.

<*Proof*>

$\Rightarrow$ Suppose that $\liminf_{n\to\infty}s_n = \infty$. Let $b_n :=\inf \\{s_k : k\geq n\\}$. Then $s_n \geq b_n$.

Let $M>0$ be given. Since $\liminf_{n\to\infty}s_n=\lim_{n\to\infty}b_n=\infty$, there exits a $n_0\in\mathbb{N}$ such that $n\geq n_0 \Rightarrow b_n >M$. 

Since $s_n \geq b_n, s_n > M$ for all $n\geq n_0$.

$\therefore \lim_{n\to\infty}s_n = \infty$.


$\Leftarrow$ Conversely, suppose that $\lim_{n\to\infty}s_n=\infty$. Let $M>0$ be given. Then there exists $n_0\in\mathbb{N}$ such that $n\geq n_0 \Rightarrow s_n > M$. Then $M$ is a lower bound of the set $\\{s_n : n\geq n_0\\}$. Then $b_{n_0} = \inf \\{s_n: n\geq n_0\\}\geq M$.

Since $\\{b_n\\}$ is monotone increasing, $b_n \geq M$ for all $n\geq n_0$.

$\therefore \lim\inf_{n\to\infty}=\lim_{n\to\infty}b_n = \infty$.


$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
