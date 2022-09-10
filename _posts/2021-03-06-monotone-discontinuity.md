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
\begin{align*}
p<x<p+\delta, x\in E \Rightarrow |f(x)-L| <\epsilon
\end{align*}
$$

We write 

$$
\begin{align*}
f(p+) = \displaystyle{\lim_{x\to p+}f(x) = \lim_{x\to p, x> p}f(x)}.
\end{align*}
$$ 

Similarly, if $p$ is a  limit point of $E\cap (-\infty, p)$, the **left limit** of $f$ at $p$, if it exists, is denoted by $f(p-)$, and we write 

$$
\begin{align*}
f(p-) = \lim_{x\to p}f(x) = \lim_{x\to p, x<p} f(x).
\end{align*}
$$

## Remark
If any interval $I$ with Int$(I)\neq \emptyset$ and $f:I\to\mathbb{R}$, then $f$ has a limit point at $p\in\text{Int}(I)$,

$$
\begin{align*}
\lim_{x\to p} f(x) = L \iff f(p+), f(p-) \text{ exist and } f(p+) = f(p-) = L
\end{align*}
$$

Since $p\in E^\prime$ does not imply $p$ is a limit point of $E\cap (p, \infty)$ or $E\cap (-\infty, p)$, we need the set $E$ to be interval $I$ with $\text{Int}(I)\neq\emptyset$ and $p\in\text{Int}(I)$.

<*Proof*>

$\Rightarrow$ Suppose that $f$ has a limit at $p\in\text{Int}(I)$. Since $p\in\text{Int}(I)$, there exists $\epsilon>0$ such that $(p-\epsilon, p+\epsilon)\subset I$. Moreover, for every $\delta >0, N^\prime(p)_\delta \cap \text{I}\neq\emptyset$ since $p$ is a limit point of $I$. Then, $N^\prime_\delta (p) \cap (p, p+\epsilon)\neq\emptyset$, which implies that $N^\prime_\delta(p)\cap (p, \infty)\neq \emptyset$.

$\therefore p$ is a limit point of $I\cap (p,\infty)$.

Similarly, we can show that $p$ is also a limit point of $I\cap (-\infty, p)$.

$\Leftarrow$ It is trivial case.

$$\tag*{$\square$}$$

If $p$ is the left end point of $I$, then the right limit of $f$ at $p$ coincides with the  the limit of $f$ at $p$. Similar for $p$ is the right end point of $I$.
