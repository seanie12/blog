---
title: "Differentiation"

categories:
  - Analysis

tags:
  - differentiation
  - derivative
  - chain rule


toc: true
toc_sticky: true

use_math : true
comments : true

---





## Definition 5.1.1
Let $I\subset \mathbb{R}$ be an interval and let $f:I\rightarrow\mathbb{R}$ be a function. Fix a $p\in I$. <br /> The **derivative of $f$ at $p$** is defined by

$$
f^\prime(p) := \lim_{x\to p} \frac{f(x)-f(p)}{x-p}
$$

provided that the limit exists. If $f^\prime(p)$ can be defined at the point $p\in I$, the $f$ is called **differentiable at $p$**.

## Remark
If $p$ is an interior point of $I$, then $p+h\in I$ for sufficiently small $h$. Then we can say

$$
f^\prime(p) = \lim_{x\to p}\frac{f(x)-f(p)}{x-p} = \lim_{h\to 0}\frac{f(p+h)-f(p)}{h}
$$

## Definition 5.1.2
In the same setting, if $p\in I$ with $I\cap (p,\infty) \neq \emptyset$, then the **right derivative of $f$ at $p$** is defined by

$$
f^\prime_{+}(p) := \lim_{h\to 0^+} \frac{f(p+h)-f(p)}{h}
$$

provided that the limit exists.

## Examples 5.1.3
(a) $f(x) = x^n$

$$
\begin{align}
\begin{split}
f^{\prime} (p) = \lim_{x\to p} \frac{x^{n}- p^n}{x-p} &= \lim_{x\to p} \frac{(x-p)(x^{n-1}+px^{n-2}+\cdots + p^{n-1})}{x-p} \\
&=\lim_{x\to p} (x^{n-1} + px^{n-2} + \cdots + p^{n-1}) \\
&=np^{n-1}
\end{split}
\end{align}
$$
$\therefore f^\prime(x) = nx^{n-1}$

$$\tag*{$\square$}$$

(b) $f(x)=\sqrt{x}$

$$
\begin{align}
\begin{split}
\lim_{h\to0}\frac{\sqrt{p+h}-\sqrt{p}}{h} &= \lim_{h\to0} \frac{1}{h} \times \frac{h}{\sqrt{p+h}+\sqrt{p}} = \frac{1}{2\sqrt{p}}
\end{split}
\end{align}
$$

$\therefore f^\prime(x) = \frac{1}{2\sqrt{x}}$
$$\tag*{$\square$}$$

(c) $f(x)=\sin x$

$$
\begin{align}
\begin{split}
\lim_{h\to 0} \frac{\sin (x+h) - \sin x}{h} &= \lim_{h\to 0}\frac{\sin x \cos h + \cos x \sin h - \sin x}{h} \\
&=\lim_{h\to0} \frac{\sin x(\cos h -1)}{h} + \frac{\cos x \sin h}{h} \\
&= \cos x
\end{split}
\end{align}
$$
$$\tag*{$\square$}$$

(d) $f(x) =\left|x \right|$

$f^\prime (x) = \begin{cases} 1 \quad &(x>0) \\
-1 \quad &(x<0)
\end{cases}
$

(f) $f(x) = \begin{cases} x\sin \frac{1}{x} \quad &(x\neq 0) \\
-1 \quad &(x=0)
\end{cases}$

For $x\neq 0$, 
$$
\begin{align}
\begin{split}
f^\prime (x) &= \sin\frac{1}{x} + x\cos \frac{1}{x} \cdot (-\frac{1}{x^2}) \\ 
&= \sin \frac{1}{x} - \frac{1}{x}\cos  \frac{1}{x}
\end{split}
\end{align}
$$

For $x=0$,
$$
\begin{align}
\begin{split}
\lim_{h\to 0} &\frac{h\sin \frac{1}{h}}{h}=\lim_{h\to 0} \sin \frac{1}{h}
\end{split}
\end{align}
$$
The limit does not exist. <br />
$\therefore f$ is not differentiable at $x=0$.

(g) $$f(x) = \begin{cases} x^2 \sin \frac{1}{x} \quad &(x\neq 0) \\
0 \quad &(x=0)
\end{cases}
$$
For $x\neq 0, f^\prime (x) = 2x \sin \frac{1}{x} - \cos \frac{1}{x}$. 

For $x=0$,
$$
\lim_{h\to 0} \frac{h^2 \sin \frac{1}{h}}{h} = \lim_{h\to 0} h\sin \frac{1}{h} = 0
$$
$\therefore f^\prime(0) = 0$, but $f^\prime$ is not continuous.

## Theorem 5.1.4
If $f:I\rightarrow \mathbb{R}$ is differentiable at $p$, then $f$ is continuous at $p$.

<*proof*>
For $t\neq p$,

$$
f(t) - f(p) = \frac{f(t)-f(p)}{t-p}(t-p)
$$
Since 

$$
\lim_{t\to p}\frac{f(t)-f(p)}{t-p}
$$
exists and equal to $f^\prime (p)$,

$$
\begin{align}
\begin{split}
\lim_{t\to p}(f(t)-f(p)) & = \lim_{t\to p}\frac{f(t)-f(p)}{t-p} \lim_{t\to p}(t-p) \\
&= f^\prime(p)\cdot 0 \\
&=0
\end{split}
\end{align}
$$
Therefore, $\lim_{t\to p}f(t) = f(p)$ and thus $f$ is continuous at $p$. In the above, if $p$ is an endpoint of the interval $I$, then the limits are either the right or left limit at $p$, whichever is appropriate.
$$\tag*{$\square$}$$

## Remark
Let $p_1, \ldots p_n$ be points. Construct $f$ that is continuous but not differentiable at $p_1,\ldots, p_n$.

$$
f(x) = \sum_{k=1}^n\left|x-p_k\right|
$$

## Theorem 5.1.5
$f,g$ are differentiable at $x\in I$. Then $f+g, fg, f/g$ are all differentiable at $x\in I$ and

$$
\begin{align}
\begin{split}
(f+g)^\prime (x) &= f^\prime (x) + g^\prime (x)\\
(fg)^\prime (x) &= f^\prime (x)g(x) + f(x)g^\prime(x) \\
(f/g)^\prime (x) &= \frac{f^\prime(x)g(x) - f(x)g^\prime(x)}{\{g(x)\}^2}
\end{split}
\end{align}
$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
