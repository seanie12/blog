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


(d) 

$$
\begin{align}
f(x) &=\left| x \right| \\
f^\prime (x) &= \begin{cases} 1 \quad &(x>0) \\
-1 \quad &(x<0)
\end{cases}
\end{align}$$


(f) $$\begin{align}f(x) = \begin{cases} x\sin \frac{1}{x} \quad &(x\neq 0) \\
-1 \quad &(x=0)
\end{cases}
\end{align}$$

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

<*proof*>
$$\begin{align}
\begin{split}
\lim_{h\to0} \frac{(f+g)(x+h)-(f+g)(x)}{h} &= \frac{f(x+h)-f(x)+g(x+h)-g(x)}{h}\\
&= \frac{f(x+h)-f(x)}{h} + \frac{g(x+h)-g(x)}{h} \\
&= f^\prime(x) + g^\prime(x)
\end{split}
\end{align}
$$
By Theorem 5.1.4, since $f$ is differentiable at $x$, 

$$\lim_{h\to0}f(x+h)=f(x)$$.

$$
\begin{align}
\begin{split}
(fg)^\prime(x) &= \lim_{h\to 0} \frac{(fg)(x+h)-(fg)(x)}{h} \\
&= \lim_{h\to0}f(x+h)\lim_{h\to 0}\left(\frac{g(x+h)-g(x)}{h} \right)\\
&\quad +g(x)\lim_{h\to0}\left(\frac{f(x+h)-f(x)}{h} \right) \\
&=f(x)g^\prime(x) + g(x)f^\prime(x)
\end{split}
\end{align}
$$
Since $g(x) \neq 0$ and $g$ is continuous at $x$, Take $\epsilon = |g(x)|/2$. Then there exists a $\delta >0$ such that for all $k$ with $\left| k-x \right| <\delta \Rightarrow \left| g(k)-g(x) \right| < \epsilon=|g(x)|/2$.  Put $h=k-x$.  <br />Then for all $h$ with $\left| h \right| <\delta, \left|g(x+h) -g(x) \right| < \left| g(x)\right| / 2$.  Either $g(x) >0$ or $g(x)<0$, $g(x+h)\neq 0$ with $|h|<\delta$.

$$
\begin{align}
\begin{split}
\left(\frac{1}{g} \right)^\prime &= \lim_{h\to0} \frac{\frac{1}{g(x+h)}-\frac{1}{g(x)}}{h} \\
&=-\lim_{h\to0}\left(\frac{g(x+h)-g(x)}{h} \right) \lim_{h\to0}\frac{1}{g(x)g(x+h)} \\
&=\frac{-g^\prime(x)}{g^2(x)}
\end{split}
\end{align}
$$
Then $(f\cdot \frac{1}{g})^\prime =  \frac{f^\prime(x)g(x) - f(x)g^\prime(x)}{\{g(x)\}^2}$
$$\tag*{$\square$}$$

## Theorem 5.1.6 (Chain Rule)
$f$ is differentiable at $x$ and $g$ is differentiable at $f(x)$. Then $(g\circ f)^\prime (x) = g^\prime(f(x))\cdot f^\prime(x)$

$Q(t) = \frac{f(t)-f(x)}{t-x} \Rightarrow Q(t) \rightarrow f^\prime(x)$ as $t\rightarrow x$.  

Let $u(t) = Q(t)- f^\prime(x)$. Then $u(t) \rightarrow 0$ as $t\rightarrow x$. So, $f(t)-f(x)=(t-x)(u(t)+f^\prime(x))$.

<*proof*>
$y=f(x)$
$$
\begin{align}
\begin{split}
f(t)-f(x) &= (t-x)(f^\prime(x) + u(t)) \\
g(s)-g(y) &=(s-y)(g^\prime(y) + v(s)) \\
\end{split}
\end{align}
$$
where $u(t) \rightarrow 0$ as $t\rightarrow x$, $v(s)\rightarrow 0$ as $s\rightarrow y$. <br /> Let $s=f(t)$ and $h=g\circ f$.
$$
\begin{align}
\begin{split}
h(t)-h(x) &= g(f(t)) - g(f(x))\\
&=g(s) - g(y)\\
&=(s-y)(g^\prime(y) + v(s)\\
&=(f(t)-f(x))(g^\prime(y) + v(s)) \\
&=(t-x)(f^\prime(x) + u(t))(g^\prime(y) + v(s)) \\
\frac{h(t)-h(x)}{t-x} &=(f^\prime(x) + u(t))(g^\prime(y)+v(s)) \\
\lim_{t\to x}\frac{h(t)-h(x)}{t-x} &= g^\prime(f(x))f^\prime(x)
\end{split}
\end{align}
$$
$\therefore h^\prime(x) = g^\prime(f(x))f^\prime(x)$.
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
