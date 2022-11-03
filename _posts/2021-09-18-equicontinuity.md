---
title: "Equicontinuous Families of Functions"

categories:
  - Analysis

tags:
  - boundedness
  - equicontinuous 

 
toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 7.19
Let $\\{f_n\\}$ be a sequence of functions defined on a set $E$. We say that $\\{f_n\\}$ is **pointwise bounded** on $E$ if the sequence $\\{f_n(x)\\}$ is bounded for every $x\in E$, that is, if there exists a finite valued function $\phi: E\to\mathbb{R}$ such that

$$
\begin{align*}
\lvert f_n(x) \rvert < \phi(x) \quad (x\in E, n\in\mathbb{N}).
\end{align*}
$$

We say that $\\{f_n\\}$ is **uniformly bounded** on $E$ if there exists a number $M$ such that

$$
\begin{align*}
\lvert f_n(x) \rvert < M \quad (x\in E, n\in\mathbb{N}).
\end{align*}
$$

## Remark
Even if $\\{f_n\\}$ is a uniformly bounded sequence of continuous functions on a compact set $E$, there need not exist a subsequence which converges pointwise on $E$.

Let $f_n(x) = \sin (nx), x\in [0,2\pi], n\in\mathbb{N}$. Suppose that there exists a sequence $\\{n_k\\}$ such that $\\{\sin(n_kx)\\}$ converges for every $x\in [0,2\pi]$. In that case we must have

$$
\begin{align*}
\lim_{k\to\infty}(\sin(n_kx)-\sin(n_{k+1}x))=0 \quad (0\leq x \leq 2\pi),
\end{align*}
$$

which implies that 


$$
\begin{align*}
\lim_{k\to\infty}(\sin (n_kx)-\sin(n_{k+1}x)^2=0 \quad (0\leq x \leq 2\pi).
\end{align*}
$$

By Lebesque dominated convergence theorem,


$$
\begin{align*}
\lim_{k\to\infty}\int_0^{2\pi}\left( \sin(n_kx)-\sin(n_{k+1}x)\right)^2 = \int_0^{2\pi}\lim_{k\to\infty} \left(\sin(n_kx)-\sin(n_{k+1}x) \right)^2 =0.
\end{align*}
$$

However

$$
\begin{align*}
\int_0^{2\pi}(\sin (n_kx)-\sin(n_{k+1}x))^2=2\pi,
\end{align*}
$$

which is a contradiction.

$$\tag*{$\square$}$$


## Theorem 7.23
If $\\{f_n\\}$ is a pointwise bounded sequence of complex functions on a countable set $E$, then $\\{f_n\\}$ has a subsequence $\\{f_{n_k}\\}$ such that $\\{f_{n_k}(x)\\}$ converges for every $x\in E$.


Note that if $E=\\{x_1, x_2\\}$, by [Bolzano-Weierstrass Theorem](https://seanie12.github.io/blog/analysis/subsequence-bolzano-weierstrass/#theorem-2410-bolzano-weierstrass-theorem) we can get a convergent subsequence $\\{f_{n_k}(x_1)\\}$ on $x_1$. Then consider the sequence 

$$
\begin{align*}
\{f_{n_k}(x_2)\}_{k=1}^\infty.
\end{align*}
$$

Again by [Bolzano-Weierstrass Theorem](https://seanie12.github.io/blog/analysis/subsequence-bolzano-weierstrass/#theorem-2410-bolzano-weierstrass-theorem), we can choose a convergent subsequence $\\{f_{n_{k_l}}(x_2)\\}$ on $x_2$.  

$\therefore $\\{f_{n_{k_l}}\\}$ converges on $E=\\{x_1, x_2\\}$.

<*Proof*>

Let $E=\\{x_i\\}$. Since 
$$
\begin{align*}
\{f_n(x_1)\}_{n=1}^\infty
\end{align*}
$$ 

is bounded, there is a convergent subsequence 

$$
\begin{align*}
\{f_{n_k}(x_1)\}_{k=1}^\infty.
\end{align*}
$$

We denote $\\{f_{n_k}\\}$, which converges to $\lim_{k\to\infty}f_{n_k}(x_1)$ by $\\{f_{1,k}\\}$.

Iterate the following procedure. Since $\\{f_{1,n}(x_2)\\}$ is bounded, there is a convergent subsequence $\\{f_{1, {n_k}}(x_2)\\}_{k=1}^\infty$. Notate $f_{2,k}=f_{1,n_k}$. Now we consider sequences $S_1, S_2, S_3,\ldots$, which represent by the array


$$
\begin{align*}
&S_1: \: f_{1,1} \quad f_{1,2} \quad f_{1,3} \quad f_{1,4} \quad \cdots \\
&S_2: \: f_{2,1} \quad f_{2,2} \quad f_{2,3} \quad f_{2,4} \quad \cdots \\
&S_3: \:f_{3,1} \quad f_{3,2} \quad f_{3,3} \quad f_{3,4} \quad \cdots \\
\end{align*}
$$

and which have the following properties:

(1) Each row is a subsequence of the earlier row

(2)  $n$-th row converges on $\\{x_1, \ldots, x_n\\}$.

(3) $k$-th element of the $n$-th row occurs in the greater or than equal to $k$-th place in the previous row.

The sequence $S=\\{f_{n,n}\\}$ (except possibly its first $n-1$ terms) is a subsequence of $S_n$ for all $n\in\mathbb{N}$. Hence (2) implies that $\\{f_{n,n}(x_i)\\}$ converges as $n\to\infty$, for every $x_i\in E$.

Specifically, let $x_i$ be given and let $\epsilon >0$ be given. Then 

$$
\begin{align*}
\{f_{n,n}\}_{n=i}^\infty
\end{align*}
$$

 is a subsequence of $S_i=\\{f_{i,n}\\}$. Since $S_i$ converges pointwise on $\\{x_1, \ldots, x_i\\}$, there is $N_1\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N_1 \Rightarrow \lvert f_{i,n}(x_i) - \lim_{k\to\infty}f_{i,k}(x_i)\rvert < \epsilon.
\end{align*}
$$

 Since $\\{f_{n,n}(x_i)\\}$ is a subsequence of 
 
$$
\begin{align*}
\{f_{i,n}(x_i)\}_{n=1}^\infty
\end{align*}
$$,  

$$
\begin{align*}
n\geq N:=\max\{i, N_1\}\Rightarrow \lvert f_{n,n}(x_i) - \lim_{k\to\infty} f_{i,k}(x_i) \rvert <\epsilon.
\end{align*}
$$

$\therefore \\{f_{n,n}(x_i)\\}$ converges on $x_i$.

$$\tag*{$\square$}$$

## Definition 7.22
A family $\mathscr{F}$ of complex functions $f$ defined on a set $E$ in a metric space $X$ to be **equicontinuous** on $E$ if for every $\epsilon>0$ there exists a $\delta>0$ such that 

$$
\begin{align*}
d(x,y) <\delta , x,y\in E\Rightarrow \lvert f(x) - f(y) \rvert <\epsilon \text{ for all }f\in\mathscr{F}.
\end{align*}
$$

## Remark
IS every finite collection of uniformly continuous functions are equicontinuous? Yes.

Let $\\{f_n\\}_{n=1}^k$ is a collection of uniformly continuous functions. Let $\epsilon > 0$ be given. Then for each $f_n\in\mathscr{F}$, there is a $\delta_n>0$ such that 

$$
\begin{align*}
d(x,y) < \delta_n \Rightarrow \lvert f_n(x) - f_n(y)\rvert <\epsilon.
\end{align*}
$$

Take $\delta =\min\\{\delta_1, \ldots, \delta_k\\}$. Then $\mathscr{F}$ is equicontinuous.

## Theorem 7.24
If $K$ is a compact metric space, if $\\{f_n\\}$ is a sequence of continuous functions on $K$, and if $\\{f_n\\}$ converges uniformly on $K$, then  $$\\{f_n\\}$ is equicontinuous.

<*Proof*> 

Let $\epsilon >0$ be given. By uniform convergence, there is $N\in\mathbb{N}$ such that 

$$
\begin{align*}
n > N \Rightarrow \lvert f_n(x) - f_N(x) \rvert < \frac{\epsilon}{3}
\end{align*}
$$

for all $x\in K$. Since $f_n$ is continuous on the compact set $K$, all $f_n$ are uniformly continuous  on $K$ by [Theorem 4.3.4](https://seanie12.github.io/blog/analysis/uniform-continuity/#theorem-434). By previous remark $\\{f_1, \ldots, f_N\\}$ is equicontinuous. Thus, there exists $\delta>0$ such that 

$$
\begin{align*}
d(x,y) <\delta \Rightarrow \lvert f_i(x) - f(y) \rvert <\frac{\epsilon}{3}
\end{align*}
$$

for all $i=1,\ldots, N$.

For $n> N$, if $d(x,y)<\delta$, then

$$
\begin{align*}
\lvert f_n(x) -f_n(y)\rvert &\leq \lvert f_n(x) - f_N(x) \rvert + \lvert f_N(x) - f_N(y) \rvert + \lvert f_N(y) - f_n(y)\rvert  \\
&< \frac{\epsilon}{3} + \frac{\epsilon}{3} + \frac{\epsilon}{3}\\
&=\epsilon.
\end{align*}
$$
 
$$\tag*{$\square$}$$

## Reference
- Walter Rudin, **『**Principles of Mathematical Analysis**』**
