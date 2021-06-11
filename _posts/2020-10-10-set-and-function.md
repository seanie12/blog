---
title: "Differentiation"

categories:
  - Analysis

tags:
  - differentiation
  - derivative


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
\begin{align*}
\begin{split}
f^{\prime} (p) = \lim_{x\to p} \frac{x^{n}- p^n}{x-p} &= \lim_{x\to p} \frac{(x-p)(x^{n-1}+px^{n-2}+\cdots + p^{n-1})}{x-p} \\
&=\lim_{x\to p} (x^{n-1} + px^{n-2} + \cdots + p^{n-1}) \\
&=np^{n-1}
\end{split}
\end{align*}
$$
$\therefore f^\prime(x) = nx^{n-1}$

(b) $f(x)=\sqrt{x}$

$$
\begin{align*}
\begin{split}
\lim_{h\to0}\frac{\sqrt{p+h}-\sqrt{p}}{h} &= \lim_{h\to0} \frac{1}{h} \times \frac{h}{\sqrt{p+h}+\sqrt{p}} = \frac{1}{2\sqrt{p}}
\end{split}
\end{align*}
$$

$$\tag*{$\square$}$$


## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
