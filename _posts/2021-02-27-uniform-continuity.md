---
title: "Uniform Continuity"

categories:
  - Analysis

tags:
  - uniform continuity
  - Lipschitz continuity
  - jump discontinuity
toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 4.3.1 
Let $E$ be a subset of $\mathbb{R}$ and let $f:E\to\mathbb{R}$ be a function. <br /> The function $f$ is **uniformly continuous** on $E$ if <br /> $\forall \epsilon >0, \exists \delta >0$ such that 
$$
\begin{align}
|x-y|<\delta \text{ for all }x,y\in E \Rightarrow |f(x)-f(y)|<\epsilon.
\end{align}$$


## Examples 4.3.2
(a) $E\subset \mathbb{R}$ is bounded and $f(x) = x^2 \Rightarrow f$ is uniformly continuous on $E$.

<*proof*>
Since $E$ is bounded, there is $C>0$ such that $|x|\leq C$ for all $x\in E$. <br /> Let $\epsilon >0$ be given. Then, if $x,y \in E$,
$$
\begin{align}
\begin{split}
|f(x)-f(y)| = |x^2 - y^2| &= |x+y|\cdot |x-y| \\
&\leq (|x|+|y|)\cdot |x-y| \\
&\leq 2C \cdot |x-y|
\end{split}
\end{align}
$$
Take $\delta := \epsilon / 2 >0$. If $|x-y| <\delta$ for all $x,y\in E$, then 
$$
\begin{align}
|f(x)-f(y)| \leq 2C|x-y| < 2C \cdot \frac{\epsilon}{2C} = \epsilon
\end{align}
$$
$$\tag*{$\square$}$$

(b) $f(x) = \sin x$ is uniformly continuous.

<*proof*>
$$
\begin{align}
\begin{split}
|f(x) - f(y) | &= | 2\cos(\frac{x+y}{2})\sin(\frac{x-y}{2}) \\
&\leq 2|\sin(\frac{x-y}{2}) | \\
&\leq |x-y|
\end{split}
\end{align}
$$
Take $\delta :=\epsilon$, then we are done.
$$\tag*{$\square$}$$

(c) $f(x) = \frac{1}{x}$.  If $E = (0,\infty)$, then $f$ is not uniformly continuous on $E$. But if $E=[a,\infty] \text{for all }a>0$, $f$ is uniformly continuous on $E$.

<*proof*>
Let $E=(0,\infty)$ and suppose that $f$ is uniformly continuous on $E$. Taking $\epsilon=1$, there exists a $\delta >0$ such that 
$$
\begin{align}
\text{for all } x,y \in E \text{ with } |x-y|<\delta \Rightarrow \left|\frac{1}{x}-\frac{1}{y}\right| < 1
\end{align}
$$
Choose $n_0 \in \mathbb{N}$ such that $\frac{1}{n_0}<\delta$ by Archimedean property and set a sequence $x_n = \frac{1}{n}$. Then
$$
\begin{align}
|x_n-x_{n+1}| = \frac{1}{n}-\frac{1}{n+1} = \frac{1}{n} \leq \frac{1}{n_0} < \delta
\end{align}
$$
whenever $n\geq n_0$. But $|f(x_n) -f(x_{n+1}) | = |n - (n+1)|=1$, which is a contradiction. 

$\therefore f$ is not uniformly continuous on $E$.

Now, let $E=[a,\infty)$ with $a>0$ and $\epsilon >0$ be given. For $x,y \in E$,
$$
\begin{align}
|f(x)-f(y) | = \left|\frac{1}{x}-\frac{1}{y} \right| = \left|\frac{x-y}{xy} \right| = \frac{1}{a^2}|x-y|
\end{align}
$$
Take $\delta := a^2\epsilon >0$. If $|x-y| <\delta$ for all $x,y\in E$, then
$$
\begin{align}
|f(x) - f(y) | \leq \frac{1}{a^2}|x-y| < \frac{1}{a^2}\cdot a^2\epsilon
\end{align}
$$
$\therefore f$ is uniformly continuous on $E$.
$$\tag*{$\square$}$$

## Definition (Lipschitz continuity)
Let $E\subset \mathbb{R}$ and let $f:E\to \mathbb{R}$ be a function satisfying a **Lipschitz condition**  <br /> if there is a $M>0$ such that
$$
\begin{align}
x,y\in E \Rightarrow |f(x)- f(y)| \leq M |x-y|
\end{align}
$$

## Theorem 4.3.3
Let $f:E\to\mathbb{R}$ be a function satisfying Lipschitz condition on $E$. Then $f$ is uniformly continuous on $E$.

<*proof*>
Since $f$ is Lipschitz function, there is a $M>0$ such that 
$$
x,y \in E \Rightarrow |f(x)-f(y)| < M|x-y|
$$
Let $\epsilon >0$ be given. Take $\delta := \epsilon / M$. Then for $x,y\in E$,
$$
|f(x)-f(y)| \leq M|x-y| < M\cdot\frac{\epsilon}{M} = \epsilon
$$
$\therefore f$ is uniformly continuous on $E$.
$$\tag*{$\square$}$$

## Theorem 4.3.4
Let $K\subset\mathbb{R}$ be a compact set and let $f:K\to\mathbb{R}$ be a continuous function on $K$. Then $f$ is uniformly continuous on $K$. 

<*proof*>
Let $\epsilon >0$ be given. Since $f$ is continuous on $K$, for every $p\in K$, there is a $\delta_p >0$ such that 
$$
\begin{align}
|x-p|<2\delta_p \Rightarrow |f(x)-f(p)| <\frac{\epsilon}{2} 
\end{align}
$$
Now, $$\{N_{\delta_p} (p): p\in K\}$$ is an open cover of $K$. Since $K$ is compact, there are $p_1,\ldots, p_n \in K$ such that 
$$
\begin{align}
K \subset \cup_{i=1}^n N_{\delta_{p_i}} (p_i)
\end{align}
$$
Take $$\delta :=\min\{\delta_{p_1},\ldots, \delta_{p_n}\} >0$$. Suppose that $x,y\in K$with $|x-y|<\delta$. Then $x\in N_{\delta_{p_i}} (p_i)$ for some $i=1,\ldots, n$. That is $|x-y|<\delta \leq \delta_{p_i}$. So, $x,y\in N_{2\delta_{p_i}}(p_i)$. Thus,
$$
\begin{align}
|f(x) - f(y)| \leq |f(x) - f(p_i)| + |f(y)-f(p_i)| < \frac{\epsilon}{2} +\frac{\epsilon}{2} =\epsilon
\end{align}
$$
$\therefore f$ is uniformly continuous on $K$.
$$\tag*{$\square$}$$

## Example
$A\subset \mathbb{R}$. Define $$d(p,A) :=\inf\{|p-x|:x\in A\}$$. Then,
$$
\begin{align}
|d(x, A) - d(y, A)| \leq |x-y|
\end{align}
$$
So, $d(\cdot, A)$ is Lipschitz function.

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

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
