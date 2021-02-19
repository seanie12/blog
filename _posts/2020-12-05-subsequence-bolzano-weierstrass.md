---
title: "Subsequences and Bolzano-Weierstrass Theorem"

categories:
  - Analysis


tags:
  - limit point
  - isolated point
  - Bolzano-Weierstrass Theorem
  - 
 

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 2.4.1 
Let $$\{p_n\}$$ be a sequence and let $$\{n_k\}$$ be strictly increasing sequence, i.e. $n_1 < n_2 <n_3 < \cdots$. We call $$\{p_{n_k}\}_{k=1}^\infty$$ a subsequence of $$\{p_n\}$$.

## Theorem 2.4.3 
Let $$\{p_n\}$$ be a convergent sequence with $\displaystyle{\lim_{n\to\infty}p_n=p}$. Then for all subsequences of $$\{p_n\}$$ converges to $p$.

<*proof*>
Let $\epsilon >0$ be given and let $$\{p_{n_k}\}$$ be a subsequence of $$\{p_n\}$$. Since $p_n\to p$ as $n\to\infty$, there exists $N\in\mathbb{N}$ such that $$
\begin{align}
n\geq N \Rightarrow |p_n-p| <\epsilon
\end{align}
$$
Now, $n_k \geq k$. So, if $k\geq N$, then $n_k\geq k \geq N$.  <br />$\therefore |p_{n_k}-p|<\epsilon$ <br />$\therefore \displaystyle{\lim_{k\to\infty}}p_{n_k}=p$
$$\tag*{$\square$}$$

## Definition 2.4.5
Let $E$ be a subset of $\mathbb{R}$

(a) $p\in\mathbb{R}$ is a **limit point** of $E$ if $N^\prime_\epsilon (p) \cap E\neq \emptyset$ for all $\epsilon >0$, where $$N^\prime_\epsilon (p):= N_\epsilon (p) \setminus \{p \}$$ is a deleted $\epsilon$-neighborhood of $p$.

(b) $p\in \mathbb{R}$ is an **isolated point** of $E$ if $p$ is not a limit point of $E$.

## Examples 2.4.6
(a) $$E =\{\frac{1}{n}: n\in\mathbb{N}\}$$

Assume  $p<0$.  Take $\epsilon_0 := \frac{\left|p\right|}{2}$. Then $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$

Assume that $p>1$. Take $\epsilon_0 := |p-1|$. Then $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$.

Assume that $p=\frac{1}{n}$. Take $\epsilon_0 :=\left|\frac{1}{n}-\frac{1}{n+1}\right|$. Then, $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$

Assume that $p\neq \frac{1}{n}, \text{ and } p\in (0,1)$. For this $p$, we can find $n\in\mathbb{N}$ such that $\frac{1}{n+1} < p < \frac{1}{n}$. If we take $$\epsilon_0 = \min\{\left|p-\frac{1}{n+1}\right|,\left|p-\frac{1}{n}\right| \}$$, then $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$.

Finally assume $p=0$. Let $\epsilon >0$ be given. Then, take $N\in\mathbb{N}$ such that $\frac{1}{N} < \epsilon$ by Archimedean property. In other words,
$$
\begin{align}
\frac{1}{N} \in (-\epsilon,\epsilon) \setminus \{0\} = N^\prime_\epsilon (0).
\end{align}
$$
That is $\frac{1}{N}\in N^\prime_\epsilon (0) \cap E$. <br /> $\therefore N^\prime_\epsilon (0)\neq \emptyset$. <br /> $\therefore 0$  is a limit point of $E$.
$$\tag*{$\square$}$$

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
