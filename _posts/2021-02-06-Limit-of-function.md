---
title: "Limit of function"

categories:
  - Analysis

tags:
  - limit of function
  - epsilon-delta
  
  

toc: true
toc_sticky: true

use_math : true
comments : true

---


## 4.1.1 Definition
$E \subset \mathbb{R}, f: E \rightarrow \mathbb{R}$: a function, $p \in E^\prime$.

$f$ has a **limit at p** if there exists $L\in \mathbb{R}$ such that $\forall \epsilon >0, \exists \delta >0 (\forall x \in E)$ s.t. $0 <|x-p|<\delta \Rightarrow |f(x)-L| < \epsilon.$

We write $\displaystyle{\lim_{x\to p}f(x) = L}$.


## Remark
- The definition does not consider the case when $x=p$.
- Why should $p$ be a limit point? 
  We want to guarantee the existence of  $x\in N^\prime_\delta (x) \cap E$.      Since every deleted neighborhood of $p$ contains infinitely many points of $E$,     there is such $x$ for every $\delta >0.$
 - $\displaystyle{\lim_{x\to p}f(x) \neq L} \iff \forall L \in \mathbb{R}, \exists \epsilon >0$ such that $\forall \delta >0, \exists x\in E$ such that $0<|x-p|<\delta \Rightarrow |f(x) - L| \geq \epsilon .$

## Examples 4.1.2
(a) $\displaystyle{\lim_{x\to p}c = c}$

$\because \forall \epsilon>0, \forall \delta >0, 0<|x-p|<\delta \Rightarrow |c-c| <\epsilon$

(b) $\displaystyle{\lim_{x\to p}x = p}$

$\because \forall \epsilon >0, \exists \delta >0$ such that $0<|x-p|<\delta \Rightarrow |x-p|<\epsilon$. Take $\delta :=\epsilon$. Then, $0<|x-p|<\delta \Rightarrow |x-p|<\delta=\epsilon$.

(c) $\displaystyle{\lim_{x\to p}x^2 = p^2}$

<*proof*>
Let $\epsilon >0$ be given. We want to show that the existence of $\delta >0$ such that $0<|x-p|<\delta \Rightarrow |x^2-p^2| <\epsilon.$
Now we factorize $|x^2-p^2| = |x+p|\cdot |x-p|$. If $0<\delta \leq 1$,
$$
\begin{align}
\begin{split}
|x|-|p| \leq |x-p| &\leq \delta \\
|x| &< |p| + \delta \\
&\leq |p| + 1 \\
\end{split}
\end{align}
$$
Similarly, we can bound $|x+p|$ with triangular inequality,
$$
\begin{align}
\begin{split}
|x+p| &\leq |x| + |p| \\
&< 2|p| + \delta \\
\&leq 2|p| + 1
\end{split}
\end{align}
$$
Now, we take $\delta := \min (\frac{\epsilon}{2|p|+1}, 1)$. Then 
$$
|x+p||x-p| < (2|p|+1)\frac{\epsilon}{2|p|+1} = \epsilon
$$ 
$\therefore \displaystyle{\lim_{x\to p}}x^2 = p^2.$
 $$\tag*{$\square$}$$
