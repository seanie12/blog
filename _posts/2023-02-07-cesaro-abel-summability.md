---
title: "Cesaro and Abel Summability"

categories:
  - Fourier Analysis

tags:
  - Fejer's Theorem
  - Fejer Kernel



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition 1.1
Given a sequence $\\{c_n\\}$, let $s_n:=\sum_{k=0}^nc_k$ be the sequence of partial sums. We define $N$-th *Cesaro mean* $\sigma_N$ of the sequence $\\{s_k\\}$ (a.k.a the $N$-th Cesaro sum of the series $\sum_{k=0}^\infty c_k$) by 


  
$$
\begin{align*}
\sigma_N :=  \frac{s_0 + s_1 + \cdots + s_{N-1}}{N}
\end{align*}
$$

## Remark
If $\lim_{n\to\infty}s_n = s$, then $\lim_{n\to\infty}\sigma_n=s$.

<*Proof*>

Let $\epsilon >0$ be given.  Since $\lim_{n\to\infty}s_n=s$, there exists $N_1\in\mathbb{N}$ such that if $n>N_1$ then $\lvert s_n - s\rvert <\epsilon/2$. With triangular inequality, for $n> N_1$, we get 

$$
\begin{align*}
\lvert \sigma_n - s\vert &= \left \lvert \sum_{k=0}^{n-1} \frac{s_k}{n} - s \right\rvert \\
&\leq \frac{1}{n}\sum_{k=0}^{n-1}\lvert s_k - s\rvert \\
&= \frac{1}{n}(\lvert s_0-s\rvert + \cdots +\lvert s_{N_1-1}-s\rvert) + \frac{1}{n}(\lvert s_{N_1}-s\rvert + \cdots + \lvert s_{n-1}-s\rvert) \\
&< \frac{N_1}{n}\max_{i\in \\{0,1, \ldots, N_1-1\\}} \lvert s_i-s\rvert + \frac{n-N_1}{n}\frac{\epsilon}{2} \\
&< \frac{N_1}{n}\max_{i\in \\{0,1, \ldots, N_1-1\\}} \lvert s_i-s\rvert + \frac{\epsilon}{2} \\
\end{align*}
$$

Let $M= \max_{i\in \\{0,1, \ldots, N_1-1\\}} \lvert s_i-s\rvert\in\mathbb{R}$. By Archimedean property, there is $N_2\in\mathbb{N}$ such that $\frac{MN_1}{N_2} < \frac{\epsilon}{2}$. For $n>\max\\{N_1, N_2\\}$, we get 

$$
\begin{align*}
\lvert \sigma_n - s\rvert < \frac{\epsilon}{2} + \frac{\epsilon}{2} =\epsilon.
\end{align*}
$$
$\therefore \sigma_n \to s$ as $n\to\infty$.


$$\tag*{$\square$}$$







## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
