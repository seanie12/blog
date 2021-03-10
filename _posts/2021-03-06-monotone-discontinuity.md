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

$$\tag*{$\square$}$$



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
Similarly, if $p$ is a  limit point of $E\cap (-\infty, p)$, the **left limit** of $f$ at $p$, if it exists, is denoted by $f(p-), and we write 
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

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
