---
title: "Monotone Sequences"

categories:
  - Analysis


tags:
  - monotone sequence
  - monotone convergence theorem
  - nested interval property
 

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 2.3.1
A sequence $$\{a_n\}$$ is said to be <br /> (a) **monotone increasing** if $a_n \leq a_{n+1}$ for all $n\in\mathbb{N}$ <br /> (b) **monotone decreasing** if $a_n \geq a_{n+1}$ for all $n\in\mathbb{N}$ <br /> **monotone** if it is either monotone increasing or monotone decreasing

## Theorem 2.3.2 (Monotone Convergence Theorem)
If a sequence $$\{a_n\}$$ is monotone and bounded, then it converges.

<*proof*>
Suppose that $$\{a_n\}$$ is bounded and monotone increasing. Put
$$
\begin{align}
E:=\{a_n:n\in\mathbb{N}\} \neq \emptyset
\end{align}
$$
Then $E$ is bounded above and nonempty set. By the least upper bound property, we have $\alpha=\sup E$. Now, we want to show that 
$$
\begin{align}
\lim_{n\to\infty}a_n = \alpha
\end{align}
$$
Let $\epsilon >0$ be given. Then there exists $n_0\in\mathbb{N}$ s.t. $\alpha-\epsilon <a_{n_0}\leq \alpha$. Since $$\{a_n\}$$ is increasing, $a_n\geq a_{n_0}$ for all $n\geq n_0$. Thus, if $n\geq n_0$, then
$$
\begin{align}
\alpha-\epsilon < a_n \leq \alpha<\alpha+\epsilon
\end{align}
$$
$\therefore \displaystyle{\lim_{n\to\infty}a_n=\alpha}$
$$\tag*{$\square$}$$

## Corollary 2.3.3
Let $$\{I_n\}$$ be a sequence of closed and bounded intervals with $I_n\supset I_{n+1}$ for all $n\in\mathbb{N}$. <br /> $\Rightarrow \cap_{n=1}^\infty I_n\neq\emptyset$

<*proof*>
Let $I_n = [a_n, b_n]$. Since $I_n \supset I_{n+m}$ for all $m\geq 0$,
$$
\begin{align}
a_n \leq a_{n+m} \leq b_{n+m} \leq b_m
\end{align}
$$
Thus, $a_n \leq b_m$ for all $m\in\mathbb{N}$. Since $$\{a_n\}$$ is monotone increasing, by the monotone convergence theorem, we know that $$\{a_n\}$$ converges to  $$a=\sup\{a_n: n\in\mathbb{N}\}$$. Now, note that $a\leq b_m$ for all $m\in\mathbb{N}$. So, we have $a\in I_m$ for all $m\in\mathbb{N}$.

$\therefore a\in \cap_{n=1}^\infty I_m$
$$\tag*{$\square$}$$

## Examples 2.3.5
$e:= \displaystyle{\lim_{n\to\infty}}(1+\frac{1}{n})^n$

<*proof*>
Define $t_n:= (1+\frac{1}{n})^n$. Then, 
$$
\begin{align}
\begin{split}
 (1+\frac{1}{n})^n&=1 + {n \choose 1}\frac{1}{n} + {n \choose 2}\frac{1}{n^2} + \cdots {n \choose n-1}\frac{1}{n^{n-1}} + {n \choose n}\frac{1}{n^n} \\
&= 1 + 1 + \frac{n(n-1)}{2}\frac{1}{n^2}+\cdots + \frac{n(n-1)\cdots 2\cdot1}{1\cdot2\cdots n}\frac{1}{n^n}
 \end{split}
 \end{align}
$$
$(k+1)^{th}$ term of $t_n$ is
$$
\begin{align}
\frac{n(n-1)\cdots (n-k+1)}{1\cdot 2\cdots k}\frac{1}{n^k}=\frac{1}{k!}(1-\frac{1}{n})\cdots (1-\frac{k-1}{n})
\end{align}
$$
Then $t_{n+1}$ is  
$$
\begin{align}
(1+\frac{1}{n+1})^{n+1} =1 + 1 + \frac{(n+1)n}{2}\frac{1}{(n+1)^2} + \cdots \frac{(n+1)n\cdots 1}{1\cdot 2\cdots (n+1)}\frac{1}{(n+1)^{n+1}}
\end{align}
$$
$(k+1)^{th}$ term of $t_{n+1}$ is
$$
\begin{align}
\frac{1}{k!}(1-\frac{1}{n+1})\cdots (1-\frac{k-1}{n+1})
\end{align}
$$
Since $(k+1)^{th}$ of $t_n$ is less than that of $t_{n+1}$ for all $k$, we have $t_n<t_{n+1}$ for all $n\in\mathbb{N}$. Moreover,
$$
\begin{align}
\begin{split}
(1+\frac{1}{n})^n &=1 + 1 + \frac{n(n-1)}{2}\frac{1}{n^2}+\cdots + \frac{n(n-1)\cdots 2\cdot1}{1\cdot2\cdots n}\frac{1}{n^n}\\
&<1+1 + \frac{1}{2!} + \cdots  + \frac{1}{n!} \\
&\leq 1 = 1 +\frac{1}{2} +\frac{1}{2^2} + \cdots + \frac{1}{2^{n-1}} \\
&=1+\frac{1-(\frac{1}{2})^n}{1-\frac{1}{2}} \\
&\leq 3
\end{split}
\end{align}
$$
By the monotone convergence theorem, $$\{t_n\}$$ converges.
$$\tag*{$\square$}$$

## Definition 2.3.6
$$
\begin{align}
\lim_{n\to\infty}a_n =\infty &\iff \forall M>0, \exists N\in\mathbb{N} \text{ s.t. } n\geq N \Rightarrow a_n > M \\
\lim_{n\to\infty}a_n =-\infty &\iff \forall M<0, \exists N\in\mathbb{N} \text{ s.t. } n\geq N \Rightarrow a_n < M \\
\end{align}
$$

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
Now, $n_k \geq k$. So, if $k\geq N$, then $n_k\geq k \geq N$.

$\therefore |p_{n_k}-p|<\epsilon$

$\therefore \displaystyle{\lim_{k\to\infty}}p_{n_k}=p$
$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
