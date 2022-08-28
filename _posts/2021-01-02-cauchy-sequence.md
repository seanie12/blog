---
title: "Cauchy Sequence"

categories:
  - Analysis

tags:
  - Cauchy Sequence
  - completeness

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition
Let $$\{p_n\}_{n=1}^\infty$$ be a sequence in $\mathbb{R}$. The sequence is a **Cauchy sequence** if $\forall \epsilon >0, \exists N\in \mathbb{N}$ such that
$$
\begin{align}
n,m > N \Rightarrow |p_n - p_m| < \epsilon.
\end{align}$$

## Theorem1
- Every convergent sequence is a Cauchy sequence.
- Every Cauchy sequence is bounded.

<*proof*>
Let $$\{ p_n\}$$ be a convergent sequence such that $p_n \rightarrow p \text{ as } n\rightarrow \infty$. Let $$\epsilon >0$$ be given. There exists $N\in \mathbb{N}$ such that 
$$
\begin{align}n\geq N \Rightarrow |p_n -p| <\frac{\epsilon}{2}
\end{align}
$$ 
By triangular inequality, for $n,m \geq N$
$$\begin{align}
\begin{split}
|p_n - p_m| &\leq |p_n - p| + |p_m -p|\\
&< \frac{\epsilon}{2} + \frac{\epsilon}{2} \\
&= \epsilon
\end{split}
\end{align}$$ 

$$\therefore \{p_n\}$$ is a Cauchy sequence.

- Let $$\{p_n\}$$ be a Cauchy sequence. There exists $N \in \mathbb{N}$ such that 
$$
\begin{align}
n\geq N \Rightarrow |p_n - p_m| < 1.
\end{align}$$ 
That is $|p_n|-|p_m| \leq |p_n -p_m| < 1.$ Thus, $|p_n| < 1 + |p_m| \text{ for } n \geq N.$
$$
\begin{align}
M :=\max\{|p_1|, \ldots, |p_{N-1}|, |p_N|+1\}
\end{align}$$

$$\therefore |p_n| \leq M \text{ for all } n\in\mathbb{N}.$$ 

$$\tag*{$\square$}$$

## Theorem2
$$\{p_n\}_{n=1}^\infty$$ be a Cauchy sequence having convergent subsequence. Then the sequence $$\{p_n\}$$ converges.

<*proof*>
Let $$\{p_{n_k}\}$$ be a convergent subsequence of $$\{p_n\} \text{ such that } p_{n_k} \rightarrow p \text{ as } k\rightarrow \infty.$$ Let $$\epsilon >0$$ be given. <br /> Since $$\{p_n\}$$ is a Cauchy sequence, there exists $$n_0 \in \mathbb{N}  \text{ such that } n,m \geq n_0 \Rightarrow |p_n -p_m| <\frac{\epsilon}{2}.$$ <br /> Since $$\{p_{n_k}\}$$ is a convergent subsequence, there is $$k_0 \in \mathbb{N} \text{ such that } k\geq k_0 \Rightarrow |p_{n_k} - p| < \frac{\epsilon}{2}.$$ <br /> Put $$N :=\{n_0, k_0\}$$. If $$n\geq N$$,
$$
\begin{align}
\begin{split}
|p_n -p| &= |p_n-p_N +p_N -p|\\
&\leq |p_n-p_N| + |p_N - p| \\
&< \frac{\epsilon}{2} +  \frac{\epsilon}{2} = \epsilon
\end{split}
\end{align}
$$

$$\therefore \lim_{n\to \infty} p_n = p$$

$$\tag*{$\square$}$$

## Theorem 3
Every Cauchy sequence converges in $\mathbb{R}$.

<*proof*>
Let $$\{p_n\}$$ be a Cauchy sequence. Then $$\{p_n\}$$ is bounded. By Bolzano-Weierstrass theorem, $$\{p_n\}$$ has a convergent subsequence. By the theorem2, $$\{p_n\}$$ converges.
$$\tag*{$\square$}$$

## Remark
We say that $\mathbb{R}$ is complete because theorem2 holds. In general, if $(X,d)$ is metric space, then we say that $$(X,d)$$ is complete if every Cauchy sequence in $X$ converges in $X$.

## Theorem 4
If every Cauchy sequence in $\mathbb{R}$ converges, then every nonempty subsuet of $\mathbb{R}$ that is bounded above has a supremum.

<*proof*>

Let $$A$$ be a bounded nonempty subset of $$\mathbb{R}$$. If $$\lvert A\rvert$$ is finite, it is trivial case. Otherwise, suppose that $$\lvert A\rvert$$ is infinite. Let $$b_1$$ be an upper bound of $$A$$. Then, there is $$a_1 \in A$$ such that $$a_1 < b_1$$. Define $$m_1 :=\frac{a_1+b_1}{2}.$$ If $$m_1$$ is an upper bound of $$A$$, put $$b_2 :=m_1$$ and $$a_2 :=a_1$$. Otherwise, $$a_2 := m_1, b_2 :=b1.$$ Repeat this process: If $$m_n:=\frac{a_n+b_n}{2}$$ is an upper bound of $$A$$, put $$b_{n+1} := m_n, a_{n+1} := a_n.$$ Otherwise, $$b_{n+1} := b_n, a_{n+1} :=m_n$$. 

Then $$\{a_n\}, \{b_n\}$$ are bounded and monotone increasing and decreasing sequence, respectively. By monotone convergence theorem, 

$$
\begin{align*}
\lim_{n\to\infty} a_n &= a \\
\lim_{n\to\infty} b_n &= b
\end{align*}
$$


Let $$\epsilon>0$$ be given. Since $$|b_n-a_n| = \frac{b_1 -a_1}{2^{n-1}}$$, $$|b_n -a_n| < \epsilon \text{ if } n \geq N \text{ with } N\in \mathbb{N} \text{ such that }\frac{b_1-a_1}{2^{N-1}} < \epsilon.$$ Therefore, $$\lim_{n\to\infty}(b_n-a_n) =0.$$ i.e. $$\{b_n -a_n\}$$ is a Cauchy sequence, by theorem 1. 

Suppose $m\geq n$. Then $$|a_m - a_n|\leq |b_n - a_n| < \epsilon \text{ for } n\geq N \text{ s.t. } \frac{b_1-a_1}{2^{N-1}} < \epsilon.$$ Similarly, $$|b_m-b_n|\leq |a_n-b_n| < \epsilon.$$ Thus, $$\{a_n\}, \{b_n\}$$ are Cauchy sequence. 

$$\therefore b=\lim_{n\to\infty}b_n = \lim_{n\to\infty}(b_n-a_n) + \lim_{n\to\infty}a_n = \lim_{n\to\infty}a_n=a.$$ 

Now, we want to show that $$\lim_{n\to\infty}b_n =b$$ is the supremum of $A$. Since $b_n$ is an upper bound of $A$, $\forall x \in A, x\leq b_n \text{ for all }n\in\mathbb{N}.$ We claim that $$\lim_{n\to\infty}b_n \geq x \text{ for all } x\in A.$$Suppose $$\lim_{n\to\infty}b_n < x.$$ Take $$\epsilon_0 := x- b >0$$. Since $$b_n \rightarrow b \text{ as } n \rightarrow \infty$$, there is $$n_0 \in \mathbb{N} \text{ such that } n\geq n_0 \Rightarrow b-\epsilon_0 < b_n < b+\epsilon_0 = x$$, which implies that $$b_n <x \text{ for } n\geq N.$$ It contradicts to the assumption. Therefore, $$\lim_{n\to\infty}b_n \geq x.$$ i.e. $b$ is an upper bound of $A$. 

Lastly, we want to show that $b$ is the least upper bound of $A$. Suppose that there is another upper bound $M$ of $A$ such that $M<b=a.$ Since $a_n \leq M \text{ for all } n\in \mathbb{N}$, $$\lim_{n\to\infty}a_n = a \leq M.$$ Moreover, $a_n \leq a \text{ for all } n \in \mathbb{N}$. Therefore $$a_n\leq a \leq M < b$$, but it contradicts to the assumption that $a=b.$

$$\therefore b=\sup A.$$

$$\tag*{$\square$}$$


## Definition

Let $E$ be a subset of metric space $X$. We define diameter of the set $E$ as 

$$
\begin{align*}
\text{diam}E= \sup \{d(p,q)\mid p,q\in E \} 
\end{align*}
$$

## Remark
Suppose that $(p_n)^\infty_{n=1}$ is a sequence. Let $$E_N := \{ p_N, p_{N+1},\ldots \}$$. Then the sequence $$(p_n)_{n=1}^\infty$$ is a Cauchy sequence if and only if $$\displaystyle{\lim_{N\to\infty}\text{diam}E_N}=0$$

Given any $\epsilon >0$, there is $M\in\mathbb{N}$ such that $N\geq M \Rightarrow \text{diam}E_N=\sup_{n,m \geq M} d(p_n, p_m)<\epsilon$, which is equivalent to say that the sequence is Cauchy.

## Theorem
Let $E$ be a subset of metric space $X$. Then diam$\overline{E} = E$.

<*Proof*>
Pick any $p,q\in E$. For any $\epsilon >0$, there are $p^\prime, q^\prime\in E$ such that 

$$
\begin{align*}
d(p,p^\prime) < \frac{\epsilon}{2}, \quad d(q,q^\prime) < \frac{\epsilon}{2} 
\end{align*}
$$

If $p\in E^\prime$, there is $p^\prime \in N^\prime_{\frac{\epsilon}{2}}(p)\cap E\neq \emptyset$. Otherwise we can take $p^\prime :=p$.

With triangular inequality,

$$
\begin{align*}
d(p,q) &\leq  d(p, p^\prime) + d(p^\prime, q) \\
&\leq d(p,p^\prime) + d(q^\prime, q) + d(p^\prime, q^\prime) \\
&\leq d(p^\prime,q^\prime) + \epsilon
\end{align*}
$$

By the definition of diameter of $E$, 

$$
\begin{align*}
d(p,q) \leq d(p^\prime, q^\prime) + \epsilon \leq \text{diam}E + \epsilon
\end{align*}
$$

Since $\text{diam}\overline{E}$ is the least upper bound of $$\{d(p,q)\mid p,q\in \overline{E}\}$$, $d(p,q) \leq \text{diam}\overline{E}\leq \text{diam}E + \epsilon$. Since the choice of $\epsilon$ is arbitrary, $\text{diam}\overline{E} \leq \text{diam} E$. It is trivial that $\text{diam}\overline{E} \geq \text{diam}E$.

$\therefore \text{diam}\overline{E} = \text{diam}E$.

$$\tag*{$\square$}$$
