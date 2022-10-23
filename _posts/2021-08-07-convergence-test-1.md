---
title: "Convergence Test"

categories:
  - Analysis

tags:
  - comparison test
  - root test
  - ratio test
 

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition
Let $\\{a_n\\}$ be a sequence. Define a new sequence of $s_n := \sum_{k=1}^na_k$ for $n\geq 1$. We call the $s_n$ is the $n$-th partial sum of $\\{a_n\\}$. If the sequence of partial sums converges (say $s_n\to s$), we write $\sum_{n=1}^\infty a_n=s$ and say **the infinite series** $\sum_{n=1}^na_n$ sums to $s$.


## Theorem 7.1.1
Suppose that $\sum_{n=1}^\infty a_n = \alpha, \sum_{n=1}^\infty b_n =\beta$ where $\alpha,\beta\in\mathbb{R}$.

(a) $\sum_{n=1}^\infty c a_n = c \sum_{n=1}^\infty a_n= c\alpha$

(b) $\sum_{n=1}^\infty a_n + b_n = \sum_{n=1}^\infty a_n + \sum_{n=1}^\infty b_n=\alpha +\beta$

<*Proof*>

(a)

$$
\begin{align*}
\sum_{n=1}^\infty c a_n&= \lim_{n\to\infty} \sum_{k=1}^n c a_k \\
&= \lim_{n\to\infty}c \sum_{k=1}^n a_k \\
&=c \lim_{n\to\infty}\sum_{k=1}^n a_k \\
&= c \sum_{n=1}^\infty a_n \\
&= c\alpha
\end{align*}
$$

(b) 

$$
\begin{align*}
\sum_{n=1}^\infty a_n + b_n &= \lim_{n\to\infty}\sum_{k=1}^n a_k + b_k \\
&=\lim_{n\to\infty}\left(\sum_{k=1}^na_k + \sum_{k=1}^n b_k \right) \\
&=\sum_{n=1}^\infty a_n + \sum_{n=1}^\infty b_n \\
&=\alpha + \beta
\end{align*}
$$

$$\tag*{$\square$}$$

## Remark
If $\sum_{n=1}^\infty  a_n$ converges, then $\lim_{n\to\infty}a_n=0$.

<*Proof*>
Let $S_n = \sum_{k=1}^n a_k$ and let $L=\sum_{n=1}^\infty a_n$.
For given $\epsilon >0$, there exists $N\in\mathbb{N}$ such that $n\geq N \Rightarrow \lvert S_n - L \rvert$. Since $S_n$ converges, $S_n$ is Cauchy. Thus there exists $N_2\in \mathbb{N}$ such that $n+1>n\geq N_2 \Rightarrow \lvert S_{n+1}-S_n\rvert =\lvert a_{n+1}\rvert < 0$.

$\therefore \lim_{n\to\infty} a_n=0$ 

$$\tag*{$\square$}$$


## Theorem 7.1.2 (Comparison Test)
Let $\\{a_n\\}, \\{b_n\\},\text{and } \\{c_n\\}$ be sequences in $\mathbb{R}$. 

(1) Suppose that $\lvert a_n\rvert \leq b_n$ for all $n\geq N_0$ for some $N_0\in\mathbb{N}$. If $\sum_{n=1}^\infty b_n$ converges, then $\sum_{n=1}^\infty a_n$ converges.

(2) Suppose that $a_n \geq c_n$ for all $n\geq N_0$ for some $N_0\in\mathbb{N}$. If $\sum_{n=1}^\infty c_n$, then $\sum_{n=1}^\infty a_n$ diverges.


<*Proof*>

(1)
Let $\epsilon >0$ be given. Since $\sum_{n=1}^\infty b_n$ converges, there is $N\in\mathbb{N}$ such that $m>n\geq N_1 \Rightarrow \lvert \sum_{k=n}^m b_k\rvert < \epsilon$ .

For all $m,n$ with $m>n\geq N$, 

$$
\begin{align*}
\left\lvert \sum_{k=n}^m a_k \right\rvert &\leq \left\lvert \sum_{k=n}^m a_k\right\rvert \\
&\leq \sum_{k=n}^m \lvert a_k \rvert \\
&\leq \sum_{k=n}^m b_k \\
&< \epsilon
\end{align*}
$$

By Cauchy Criterion, $\sum_{n=1}^\infty a_n$ converges.

(2) By (1), if $\sum_{n=1}^\infty a_n$ converges, then $\sum_{n=1}^\infty c_n$ converges. Thus, if $\sum_{n=1}^\infty c_n$ diverges, $\sum_{n=1}^\infty a_n$ diverges.

## Corollary 7.1.3 (Limit Comparison Test)
Let $\\{a_n\\}$ and $\\{b_n \\}$ be positive sequences in $\mathbb{R}$.

(a) 

$$
\begin{align*}
\lim_{n\to\infty}\frac{a_n}{b_n}=L \text{ with } 0<L<\infty \Rightarrow \sum_{n=1}^\infty a_n \text{ converges if and only if } \sum_{n=1}^\infty b_n \text{ converges}.
\end{align*}
$$

(b) 

$$
\begin{align*}
\lim_{n\to\infty}\frac{a_n}{b_n}=0, \sum_{n=1}^\infty b_n \text{ converges} \Rightarrow  \sum_{n=1}^\infty a_n \text{ converges}.
\end{align*}
$$

<*Proof*>

Take $\epsilon_0:=\frac{L}{2}>0$. Then there is $k_0\in\mathbb{N}$ such that $k\geq k_0 \Rightarrow \left\lvert \frac{a_k}{b_k}-L \right\rvert <\frac{L}{2}$. In other words,

$$
\begin{equation}
0<\frac{L}{2} < \frac{a_k}{b_k} < \frac{3}{2}L
\label{eq:1}
\end{equation}
$$

$\Rightarrow$ Suppose that $\sum_{n=1}^\infty a_n <\infty$. By equation$~\ref{eq:1}$, $b_k < \frac{2}{L}a_k$ for all $k\geq k_0$. Since $\sum_{n=1}^\infty a_n < \infty$, $\sum_{n=1}^\infty b_n <\infty$ by comparison test.

$\Leftarrow$ Conversely, suppose that $\sum_{n=1}^\infty b_n < \infty$. By equation $\ref{eq:1}$, 

$$
\begin{align*}
a_k < \frac{3}{2}Lb_k
\end{align*}
$$

for all $k\geq k_0$. Since $\sum_{n=1}^\infty  b_n <\infty$, $\sum_{n=1}^\infty <\infty$ by comparison test.

(b) Suppose that $\lim_{n\to\infty}\frac{a_n}{b_n}=0$ and $\sum_{n=1}^\infty b_n <\infty$. For given $\epsilon >0$, there is $k_0\in\mathbb{N}$ such that $k\geq k_0 \Rightarrow 0<\frac{a_k}{b_k}<\epsilon$. In other words, $a_k < \epsilon b_k$ for all $k\geq k_0$. 

Since $\sum_{n=1}^\infty b_n<\infty, \sum_{n=1}^\infty a_n <\infty$ by comparison test. 

$$\tag*{$\square$}$$


## Theorem 7.1.5 (Integral Test)
Let $\\{a_n\\}$ be  decreasing sequence of nonnegative real numbers, and let $f$ be a nonnegative monotone decreasing function on $[1,\infty)$ satisfying $f(k)=a_k$ for all $k\in\mathbb{N}$. Then

$$
\begin{align*}
\sum_{k=1}^\infty a_k < \infty \iff \int_1^\infty f(x) dx < \infty.
\end{align*}
$$

<*Proof*>

Since $f$ is decreasing function on $[1,\infty)$, by Theorem 6.1.8 it is Riemann integrable on $[1,c]$ for every $c>1$. Let $n\in\mathbb{N}, n\geq 2$, and consider the partition $\mathscr{P}=\\{1,\ldots, n\\}$ of $[1,n]$. Then

$$
\begin{align*}
&\sup\{f(t): t\in [i-1,i] \} =f(i-1)=a_{i-1}\\
&\inf\{f(t): t\in [i-1,i] \} = f(i) = a_i.
\end{align*}
$$

So,

$$
\begin{align*}
\sum_{i=2}^n a_i = \mathscr{L}(\mathscr{P,f})\leq \int_1^\infty f(x) dx \leq \mathscr{U(P,f)} =\sum_{i=1}^{n-1}a_i
\end{align*}
$$

$$\tag*{$\square$}$$
## Theorem (Ratio Test)
The $\sum_{n=1}^\infty a_n$

(a) converges if $\limsup_{n\to\infty}\left\lvert \frac{a_{n+1}}{a_n}\right\rvert <1$,

(b) diverges if $\left\lvert \frac{a_{n+1}}{a_n}\right\rvert \geq 1$ for all $n\geq n_0$, where $n_0$ is some fixed number.

<*Proof*>

(a) What if $\left\lvert \frac{a_{n+1}}{a_n}\right\rvert=\alpha <1$?

$$
\begin{align*}
\lvert a_2\rvert &= \alpha \lvert a_1 \rvert \\
\lvert a_3\rvert &= \alpha^2 \lvert a_1 \rvert \\
&\:\:\:\vdots \\
\lvert a_n\rvert &= \alpha^{n-1} \lvert a_1 \rvert
\end{align*}
$$

Again, we have a geometric series.

Instead, we have $\limsup_{n\to\infty}\left\lvert\frac{a_{n+1}}{a_n}\right\rvert=\alpha <1$. Choose $\beta$ such that $\alpha <\beta <1$. By property of limsup, there is $N_0\in\mathbb{N}$ such that

$$
\begin{equation*}
n\geq N_0 \Rightarrow \left\lvert \frac{a_{n+1}}{a_n}\right\rvert < \beta < 1
\end{equation*}
$$

Thus, $\lvert a_{n+1} \rvert< \beta\lvert a_n \rvert$ for all $n\geq N_0$. It implies that

$$
\begin{align*}
\lvert a_{N_0+1}\rvert &< \beta \lvert a_{N_0}\rvert \\
\lvert a_{N_0+2}\rvert &< \beta^2 \lvert a_{N_0}\rvert \\
&\:\:\:\vdots \\
\lvert a_{N_0+k}\rvert &< \beta^{k} \lvert a_{N_0}\rvert
\end{align*}
$$

for all $k\in\mathbb{N}$. By comparison test, $\sum_{n=1}^\infty a_n$  converges.


(b) Suppose that $\lvert a_{n+1} \rvert \geq\lvert a_n \rvert$ for all $n\geq N_0\in\mathbb{N}$. Then $\lim_{n\to\infty}a_n \neq 0$. 

$\therefore \sum_{n=1}^\infty a_n$ diverges by $n-$th term test.

$$\tag*{$\square$}$$


## Theorem 7.1.8 (Root Test)
Given $\sum_{n=1}^\infty a_n$, put $\alpha = \limsup_{n\to\infty}\sqrt[n]{\lvert a_n \rvert}$. Then

(a) if $\alpha <1, \sum_{n=1}^\infty a_n$ converges;

(b) if $\alpha >1, \sum_{n=1}^\infty a_n$ diverges;

(c) if $\alpha=1$, the test gives no information. E.g., $\lim_{n\to\infty} \sqrt[n]{\frac{1}{n}}=1$ but $\sum_{n=1}^\infty \frac{1}{n}=\infty$.

<*Proof*>

Ideas: What if we had $\sqrt[n]{\lvert a_n \rvert}=\alpha$? We don't have that, but we have something close. $\limsup_{n\to\infty}\sqrt[n]{\lvert a_n \rvert}=\alpha$ which is **close enough**.

(a) Choose $\beta$ such that $\alpha < \beta <1$. By property of $\limsup$, there is $N_0\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N_0 \Rightarrow \sqrt[n]{\lvert a_n \rvert} < \beta \Rightarrow \lvert a_n \rvert < \beta^n
\end{align*}
$$

Since $\beta <1$, $\sum_{n=1}^\infty \beta^n$ converges. Thus, by comparison test $\sum_{n=1}^\infty a_n$ converges.

(b) Say $\alpha >1$. Since limsup is one of subsequential limits of $\\{\sqrt[n]{\lvert a_n\rvert}\\}$, there is some subsequence 


$$
\begin{align*}
\sqrt[n_k]{\lvert a_{n_k}} \to \alpha >1 \text{ as } n\to\infty.
\end{align*}
$$

Take $\epsilon >0$ such that $\alpha -\epsilon >1$. Then there is $K\in\mathbb{N}$ such that 

$$
\begin{align*}
k\geq K \Rightarrow 1<\alpha -\epsilon < \sqrt[n_k]{\lvert a_{n_k}\rvert} < \alpha + \epsilon,
\end{align*}
$$

which implies that $\lvert a_{n_k}\rvert >1$ for all $k\in \mathbb{K}$. So, $\lim_{n\to\infty}a_n\neq 0$.

$\therefore \sum_{n=1}^\infty a_n$ diverges by $n$-th term test.

$$\tag*{$\square$} $$


## Theorem 7.1.10
Let $\\{a_n\\}$ be a sequence of positive numbers. Then

$$
\begin{align*}
\liminf_{n\to\infty}\frac{a_{n+1}}{a_n} \leq \liminf_{n\to\infty}\sqrt[n]{a_n} \leq \limsup_{n\to\infty}\sqrt[n]{a_n}\leq \limsup_{n\to\infty}\frac{a_{n+1}}{a_n}.
\end{align*}
$$

<*Proof*>

Let $R=\limsup_{n\to\infty}\frac{a_{n+1}}{a_n}$. If $R=\infty$, we are done. Suppose that $R\in\mathbb{R}$. Let $\epsilon >0$ be given and let $\beta = \epsilon+R$. By the property of $\limsup$, there exist $n_0\in \mathbb{N}$ such that 

$$
\begin{align*}
n\geq n_0 \Rightarrow \frac{a_{n+1}}{a_n}\leq \beta.
\end{align*}
$$

Then $a_{n_0+k} < \beta^k a_{n_0}$ for all $k\in\mathbb{N}$, i.e., $\sqrt[k]{a_{n_0+k} }\leq \beta \sqrt[k]{ a_{n_0}}.$ Since $\limsup_{n\to\infty}\beta\sqrt[n]{a_{n_0}}=\lim_{n\to\infty}\beta\sqrt[n]{a_{n_0}}=\beta$ by [Theorem 2.2.6](https://seanie12.github.io/blog/analysis/sequence/#theorem-226), $\limsup_{n\to\infty}\sqrt[n]{a_n}\leq \beta.$ Since $\epsilon >0$ is arbitrary, we have $\limsup_{n\to\infty}\sqrt[n]{a_n} \leq R$.

$$\tag*{$\square$}$$
## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**
