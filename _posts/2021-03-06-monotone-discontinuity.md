---
title: "Monotone Functions and Discontinuities"

categories:
  - Analysis

tags:
  - discontinuity
  - jump discontinuity
  - montone function

toc: true
toc_sticky: true

use_math : true
comments : true

---





## Definition 4.4.1
$E\subset \mathbb{R}, f:E\to\mathbb{R}, p$ is a limit point of $E\cap (p,\infty)$. $f$ has a **right limit at $p$** if there exists a $L\in\mathbb{R}$ such that $\forall \epsilon >0, \exists \delta >0$ such that 
$$
\begin{align}
p<x<p+\delta, x\in E \Rightarrow |f(x)-L| <\epsilon
\end{align}
$$
We write 
$$
\begin{align}
f(p+) = \displaystyle{\lim_{x\to p+}f(x) = \lim_{x\to p, x> p}f(x)}.
\end{align}$$ 
Similarly, if $p$ is a  limit point of $E\cap (-\infty, p)$, the **left limit** of $f$ at $p$, if it exists, is denoted by $f(p-)$, and we write 
$$
\begin{align}
f(p-) = \lim_{x\to p}f(x) = \lim_{x\to p, x<p} f(x).
\end{align}
$$

## Remark
$$
\begin{align}
\lim_{x\to p} f(x) = L \iff f(p+), f(p-) \text{ exist and } f(p+) = f(p-) = L
\end{align}
$$
But $p\in E^\prime$ does not imply $p$ is a limit point of $E\cap (p, \infty)$ or $E\cap (-\infty, p)$. We can find an interval $I \subset E$ with $p\in I$. If $p\in \text{Int}(I)\neq \emptyset, N_{\delta_0} (p) \subset I$ for some $\delta_0 >0$.  <br />
Then for every $\delta >0, N^\prime_{\delta_0} (p) \cap N^\prime_\delta (p) \neq \emptyset$. Since $N^\prime_{\delta_0} (p) \cap (p,\infty) \neq \emptyset, N^\prime_{\delta_0} (p) \cap(I \cap (p,\infty)) \neq \emptyset.$ <br /> Thus, $p$ is a limit point of $I\cap (p,\infty)$. Similarly, $p$ is a limit point of $I\cap (-\infty,p)$. 

If $p$ is the left end point of $I$, then the right limit of $f$ at $p$ coincides with the  the limit of $f$ at $p$. Similar for $p$ is the right end point of $I$.

## Definition 4.4.2
$E\subset \mathbb{R}, f:E\to\mathbb{R}, p\in E$. The function $f$ is **right continuous  (left continuous) at $p$** <br />if $\forall \epsilon >0, \exists \delta>0$ such that 
$$
\begin{align}
p\leq x <p+\delta (p-\delta < x \leq p) \Rightarrow |f(x)-f(p) |< \epsilon.
\end{align}$$

## Definition 4.4.4 
$f$ has a **jump discontinuity** at $p$ if $f(p+), f(p-)$ exist but $f(p+) \neq f(p-)$.

## Definition 4.4.6
$f:I\to\mathbb{R}$, where $I$ is an interval. 

(a) $f$ is (monotone) **increasing** if for all $x,y\in I$ with $x<y$, then $f(x)\leq f(y)$. If $f$ is **strictly increasing** if or all $x,y\in I$ with $x<y$, then $f(x) < f(y)$.

(b) $f$ is (monotone) **decreasing** if for all $x,y\in I$ with $x<y$, then $f(x)\geq f(y)$. If $f$ is **strictly decreasing** if or all $x,y\in I$ with $x<y$, then $f(x) > f(y)$.


## Theorem 4.4.7 
$I$ is an open interval and $f:I\to\mathbb{R}$ is monotone increasing on $I$. <br />
$\Rightarrow \forall p\in I, f(p+), f(p-)$ exist and 
$$
\sup_{x<p}f(x) = f(p-) \leq f(p) \leq f(p+) = \inf_{x>p} f(x)
$$
Furthermore, if $p,q\in I$ with $p<q$, then $f(p+) \leq f(q-)$.
<*proof*>
Let $p\in I$ be given. Define 
$$
E:=\{f(x): x<p\}.
$$
Since $f$ is monotone increasing, $E$ is bounded above by $f(p)$. Since $I$ is open, there exists a $\epsilon_0 >0$ such that $N_{\epsilon_0} (p) \subset I$, i.e., there is $x\in (p-\epsilon_0, p)$. Thus $E\neq \emptyset$. By the least upper bound property, $A=\sup E$.

Now we want to show that $A = f(p-)$. <br /> Let $\epsilon >0$ be given. Then there is $x_i \in I$ with $x_0 <p$ s.t. $A-\epsilon < f(x_0) \leq A$. For $x_0 < x< p,$
$$
\begin{align}
A-\epsilon< f(x_0) \leq f(x) \leq A < A < A+\epsilon
\end{align}
$$
$\therefore |f(x)-A| < \epsilon$ for all $x_0<x<p$. <br /> $\therefore f(p-) = A$

Similarly, $$S:=\{f(x): x<p \}$$. Since $f$ is monotone increasing, $S$ is bounded below by $f(p)$. Since $I$ is open, there is $\epsilon_0>0$ such that $N_{\epsilon_0} (p) \subset I$, i.e. there is $x\in (p, p+\epsilon_0)$. Thus, $S\neq \emptyset$. By the least upper bound property, $B=\inf S$.

Now we want to show that $B=f(p+)$. <br /> Let $\epsilon >0$ be given. There is $x_0 \in I$ with $x_0 >p$ such that $B\leq f(x_0) < B +\epsilon$. For $p<x<x_0$,
$$
\begin{align}
B-\epsilon < B \leq f(x) \leq f(x_0) < B+\epsilon
\end{align}
$$
$\therefore |f(x) - B| < \epsilon$ for all $x\in I$ with $p<x<x_0$. <br /> $\therefore f(p+) = B$

$\therefore \displaystyle{\sup_{x<p} f(x) = f(p+) \leq f(p) \leq f(p-) = \inf_{x>p} f(x)}$

Furthermore, for $p,q\in I$ with $p<q$,
$$
\begin{align}
f(p+) = \inf_{x<p} f(x) \leq \inf_{p<x<q} f(x) \leq \sup_{p<x<q} f(x) \leq \sup_{x<q} f(x) = f(q-)
\end{align}
$$
$\therefore f(p+) \leq f(q-)$
$$\tag*{$\square$}$$

## Definition 4.4.9
The **unit jump function** $I:\mathbb{R}\to\mathbb{R}$ defined by 
$$
I(x) = \begin{cases}0 \quad (x<0)\\
1\quad (x\geq 0)
\end{cases}
$$
Then $$I_a (x) := I(x-a) = \begin{cases}
0 \quad (x<a)\\
1\quad (x\geq a)
\end{cases}
$$
## Cauchy Criterion
Suppose that $\sum_{k=1}^\infty a_k$ converges, where $a_k\in\mathbb{R}$ for all $k=1,2,\ldots$. Since $s_n= \sum_{k=1}^n a_k$ is convergent sequence in $\mathbb{R}$, it  is Cauchy sequence. So for all $\epsilon >0 \exists N\in\mathbb{N}$ such that,
$$
\begin{align}
m>n\leq N \Rightarrow \left|\sum_{k=1}^m a_k -\sum_{k=1}^n a_k\right|=\left|\sum_{k=n+1}^m a_k \right| < \epsilon.
\end{align}
$$
So, for all $\epsilon >0 \exists N\in\mathbb{N}$ such that,
$$
\begin{align}
m\leq N \Rightarrow \left|\sum_{k=N+1}^m a_k \right| < \epsilon.
\end{align}
$$
Then the sequence $b_m:= \sum_{k=N+1}^m a_k$ converges. So, for all $\epsilon >0 \exists N\in\mathbb{N}$ such that,
$$
\begin{align}
\left|\sum_{k=N+1}^\infty a_k \right| < \epsilon.
\end{align}
$$

## Theorem 4.4.10
Let $a,b\in \mathbb{R}$ and let $$\{x_n\}$$ be a countable subset of $(a,b)$ and let $$\{c_n\}_{n=1}^\infty$$ be s sequence such that $\sum_{n=1}^\infty c_n < +\infty$. <br /> Then there is a monotone increasing function on $[a,b]$ such that 

(a) $f(a)=0, f(b) = \sum_{n=1}^\infty c_n$

(b) $f$ is continuous on $[a,b] \setminus \{x_n:n\in\mathbb{N}\}$

(c) $f(x_n+) = f(x_n)$, i.e. $f$ is right continuous at each $x_n$.

(d) $f$ is discontinuous at $x_n$ for all $n\in\mathbb{N}$ and $f(x_n+) -f(x_n-)=c_n$

<*proof*>
Define $f(x):=\sum_{k=1}^\infty c_k I(x-x_k)$. <br /> Since $0\leq c_k I(x-x_k)\leq c_k$, $s_n (x) :=\sum_{k=1}^n c_k I (x-x_k) \leq \sum_{k=1}^n c_k$. <br /> Since $\sum_{k=1}^\infty c_k < +\infty$, $$\{s_n (x)\}$$ is bounded above. Since $s_n (x)$ is monotone increasing sequence, $s_n (x)$ converges.

For $x<y, I(x-x_k) \leq I(y-x_k)$ for all $k=1,2,\ldots$. So, 
$$
f(x) = \sum_{k=1}^\infty c_k I (x-x_k) \leq \sum_{k=1}^\infty I(y-x_k) = f(y)
$$
Thus, $f(x) is monotone increasing function.

(a) Since $x_k > a$ for all $k\in\mathbb{N}$, $I(a-x_k)=0$. <br />$\therefore f(a) = \sum_{k=1}^\infty c_k f(a-x_k)=0$. <br /> Since $x_k <b$ for all $k\in\mathbb{N}$, $I(b-a_k)=1$. <br /> $\therefore f(b) = \sum_{k=1}^\infty c_k f(b-x_k) = \sum_{k=1}^\infty c_k$.

(b) $$E:=\{x_n:n\in\mathbb{N}\}$$. Let $p\in [a,b]\setminus E$.
1. $p\not\in E^\prime$.
  There is a $\delta>0$ such that $N_\delta (p) \cap E =\emptyset$. For $x\in N_\delta (p), I(x-x_k)=I(p-x_k)$ for all $k\in\mathbb{N}$. So,
  $$
  \begin{align}
  \begin{split}
  f(x) &= \sum_{k=1}^\infty c_k I(x-x_k)\\
  &=\sum_{k=1}^\infty c_k I(p-x_k) 
  \end{split}
  \end{align}
  $$
2. $p\in E^\prime$
  Let $\epsilon >0$ be given. Since $\sum_{k=1}^\infty c_k$ converges, there exists a $N\in\mathbb{N}$ such that 
  $$
  \begin{align}
  \sum_{k=N+1}^\infty c_k <\epsilon
  \end{align}
  $$
  by Cauchy criterion. Choose a $\delta \in\mathbb{R}$ such that 
  $$
  \begin{align}
  0<\delta < \min\{|p-x_k|: k=1,2,\ldots, N\} 
  \end{align}
  $$
  Then $x_k\not\in (p-\delta, p+\delta)$ for $k=1,\ldots, N$. If $x_k\in N_\delta (p) \cap E$, then $k>N$. <br /> Suppose that $p<x<p+\delta$. Then $I(x-x_k) = I(p-x_k)$ for $k=1,\ldots, N$. <br /> Furthermore, for any $p<x, 0\leq I(x-x_k) - I(p-x_k)\leq 1$ for all $k\in\mathbb{N}$.
  Therefore, if $p<x<p+\delta$
  $$
  \begin{align}
  \begin{split}
  f(x) - f(p) &= \sum_{k=N+1}^\infty c_k(I(x-x_k)-I(p-x_k))\\
  &\leq \sum_{k=N+1}^\infty c_k \\
  &< \epsilon
  \end{split}
  \end{align}
  $$
  $\therefore \left|f(x)-f(p)\right|<\epsilon$ for all $p<x<p+\delta$. < br/> $\therefore f$ is right continuous at $p$.
  Similarly, suppose that $p-\delta < x < p$. <br />Then $I(x-x_k) = I(p-x_k)$ for $k=1,\ldots, N$. Furthermore, for any $x<p, 0\leq I(p-x_k)-I(x-x_k) \leq 1$
  $$
  \begin{align}
  \begin{split}
    f(p) - f(x) &= \sum_{k=N+1}^\infty c_k(I(p-x_k)-I(x-x_k))\\
   &\leq \sum_{k=N+1}^\infty c_k \\
   &< \epsilon
   \end{split}
  \end{align}
  $$
  $\therefore f$ is left continuous at $p$. <br /> $\therefore f$ is continuous at $p$.

(c) We want to show that $f(x_n+)=f(x_n)$ <br /> Fix an $x_n\in E$. 
1. $x_n\not\in E^\prime$.
  There is a $\delta >0$ such that $N^\prime_\delta (x_n) \cap E = \emptyset$, i.e. $(x_n, x_n+\delta) \cap E = \emptyset$. <br /> For $y\in (x_n, x_n+\delta), I(y-x_k) = I(x_n-x_k)$ for all $k\in\mathbb{N}$. <br /> $\therefore f(y) = f(x_n)$ for all $y\in (x_n, x_n+\delta)$ <br /> $\therefore f$ is right continuous at $x_n$.
2. $x_n \in E^\prime$.   
  
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
