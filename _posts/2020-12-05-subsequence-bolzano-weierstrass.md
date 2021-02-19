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
<br />
Assume that $p>1$. Take $\epsilon_0 := |p-1|$. Then $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$.
<br />
Assume that $p=\frac{1}{n}$. Take $\epsilon_0 :=\left|\frac{1}{n}-\frac{1}{n+1}\right|$. Then, $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$
<br />
Assume that $p\neq \frac{1}{n}, \text{ and } p\in (0,1)$. For this $p$, we can find $n\in\mathbb{N}$ such that $\frac{1}{n+1} < p < \frac{1}{n}$. If we take $$
\begin{align}
\epsilon_0 = \min\{\left|p-\frac{1}{n+1}\right|,\left|p-\frac{1}{n}\right| \}
\end{align}
$$, then $N^\prime_{\epsilon_0} (p)\cap E=\emptyset$.
<br />
Finally assume $p=0$. Let $\epsilon >0$ be given. Then, take $N\in\mathbb{N}$ such that $\frac{1}{N} < \epsilon$ by Archimedean property. In other words,
$$
\begin{align}
\frac{1}{N} \in (-\epsilon,\epsilon) \setminus \{0\} = N^\prime_\epsilon (0).
\end{align}
$$
That is $\frac{1}{N}\in N^\prime_\epsilon (0) \cap E$. <br /> $\therefore N^\prime_\epsilon (0)\neq \emptyset$. <br /> $\therefore 0$  is a limit point of $E$.
$$\tag*{$\square$}$$

(b) $$E:=\{a_n:n\in\mathbb{N}\}, \lim_{n\to\infty}a_n =L.$$ $L$ is not a limit point of $E$.

<*proof*>
Since $a_n\to L$ as $n\to\infty$, for any $\epsilon >0$, there exists $N\in\mathbb{N}$ s.t. $n\geq N \Rightarrow \left|a_n-L\right|<\epsilon$. In other words, $a_n \in (L-\epsilon, L+\epsilon)$ for all $n\geq N$, but we cannot guarantee that $a_n \neq L$. <br /> For example, if $a_n=L$ for all $n\in\mathbb{N}$, then $a_n\not\in N^\prime_\epsilon (L)$. 

$\therefore N^\prime_\epsilon (L) \cap E =\emptyset$ <br />
$\therefore L$  is not a limit point
$$\tag*{$\square$}$$

(c) $$E:=\{a_n:n\in\mathbb{N}\}, \lim_{n\to\infty}a_n =\infty.$$ Then there is no limit point of $E$.
Let $p\in\mathbb{R}$ be given. Since $a_n\to\infty$ as $n\to\infty$, for all $M>0, N\in\mathbb{N}$ such that $a_n > M$. Take $M_0 >0$ with $M_0 > p$ and define
$$
\begin{align}
\epsilon_0 := \min\{|p-M_0|, |a_i-p|: a_i\neq p, a_i <M_0 \}
\end{align}
$$
Then $\epsilon_0 >0$ and $N^\prime_{\epsilon_0} (p) \cap E =\emptyset$.

(d) $E:=[0,1]\cap \mathbb{Q}$. Find all the limit points of $E$. 

<*proof*>
Let $q\in [0,1]$ and $\epsilon >0$ be given. Since the rational number is dense in real number, there exists $r\in\mathbb{Q}$ such that $q-\epsilon <r <q+\epsilon$. Definitely $r\in E$.

$\therefore N^\prime_\epsilon (q) \cap E \neq \emptyset$.

$\therefore q \in [0,1]$ is a limit point of $E$.

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
