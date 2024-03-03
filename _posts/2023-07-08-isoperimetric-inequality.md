---
title: "Fourier series and the isoperimetric inequality"

categories:
  - Fourier Analysis

tags:
  - Curve
  - Isoperimetric Inequality





toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 1.1
A $\mathscr{C}^1$ mapping 

$$
\begin{align*}
\gamma: [a,b] \to \mathbb{R}^2,
\end{align*}
$$

such that $\gamma^\prime(s)\neq 0$, is called a **parameterized curve**. We call the image of $\gamma$ a **curve** (denoted by $\Gamma$). If $\gamma$ is 1-1, we call $\Gamma$ simple if $\gamma(a) = \gamma(b)$ we call $\Gamma$ closed.



## Definition 1.2 
We define the **length** of the curve $\Gamma$, parameterized by $\gamma(s)= (x(s), y(s))$ by

$$
\begin{align*}
\ell = \int^b_a \lVert \gamma^\prime(s) \rVert ds = \int^b_a (x^\prime(s)^2 + y^\prime(s)^2)^{1/2} ds
\end{align*}
$$



## Definition 1.3
Let $s: [c,d] \to [a,b]$ be a bijective and $\mathscr{C}^1$ mapping. Then we call 


$$
\begin{align*}
\eta(t) := \gamma \circ s (t)
\end{align*}
$$
a **re-parameterization** of $\Gamma$. If, further, 

$$
\begin{align*}
\lVert \eta^\prime(t) \rVert = 1 \text{ for all } t \in [c,d]
\end{align*}
$$

we call $\eta$ the **arclength parameterization** of $\Gamma$.


## Remark
The length of the curve $\gamma: [a,b]\to \mathbb{R}^2$ is independent of parameterization.

By the change of variable, 
$$
\begin{align*}
\int_a^b \lVert \gamma^\prime(s) \rVert ds = \int^d_c \lvert s^\prime(t) \rvert \rVert  \gamma^\prime(s(t))\lVert  dt =
\int^d_c\lVert \eta^\prime(t)\rVert dt
\end{align*}
$$


## Lemma 1
Let $\gamma: [a,b] \to \mathbb{R}^2$ be a $\mathscr{C}^1$ parametric curve. Now define a function $t: [a,b] \to [0,\ell]$ by 

$$
\begin{align*}
t(s)= \int_a^s \lVert \gamma^\prime (x)\lVert dx,
\end{align*}
$$

where $\ell = \int_a^b \lVert \gamma^\prime (x)\lVert dx$. Then $t(s)$ is a bijective function and $\eta(t) := (\gamma \circ s) (t)$ is an arclength parameterization, where $s(t)$ is the inverse of $t(s)$.

<*Proof*>

First, we want to show that $t(s)$ is bijective function. Suppose that $s_1, s_2 \in [a,b]$ are given , where $s_1 < s_2$. Then

$$
\begin{align*}
\int_a^{s_2} \lVert \gamma^{\prime}(x)\rVert dx - \int_a^{s_1} \lVert \gamma^{\prime}(x)\rVert dx = \int_{s_1}^{s_2} \lVert \gamma^{\prime}(x)\rVert dx \neq 0.
\end{align*}
$$ 

Thus, $t(s)$ is 1-1.  Now suppose that $y\in [0,\ell]$ be given and define $F(x)$ to be anti-derivative of $\lVert \gamma^{\prime}(x)\rVert$. Since $t(s)$ is continuous function, we can apply the [Intermediate Value Theorem](https://seanie12.github.io/blog/analysis/continous-function-2/#theorem-4211-intermediate-value-theorem), where $g$ is continuous on $[a,b]$, then for any $c between $g(a)$ and $g(b)$$, there exists at least one $t \in [a,b]$ such that $g(t)=c$.  Thus, $ t(s)$ is onto. 

For the length of re-parmeterized curve $\eta(t)$,

$$
\begin{align*}
\lVert \eta^\prime(t) \rVert = \lvert s^\prime(t) \rvert \cdot \lVert \gamma^\prime (s(t)) \rVert &=\frac{1}{\lvert t^\prime(s(t))\rvert} \lVert \gamma^\prime (s(t))\rVert = \lVert \gamma^\prime (s(t))\rVert^{-1} \lVert \gamma^\prime(s(t))\rVert =1,
\end{align*}
$$

$\therefore \eta(t)$ is an arclength parameterization.

$$\tag*{$\square$}$$

## Theorem 2.1
Let $\Gamma \subset \mathbb{R}^2$ be a simple closed curve. Let $\ell$ denote the length of $\Gamma, A$ the area of its enclosed region. Then


$$
\begin{align*}
A \leq \frac{\ell^2}{2\pi},
\end{align*}
$$

with equality if and only if $\Gamma$ is a circle. 

<*Proof*>
Observe that we can rescale the problem by a factor of $\delta>0$. Consider the mappling of the plane $\mathbb{R}^2$ to $\mathbb{R}^2$ where $(x,y)\mapsto (\delta x, \delta y).$ Then the length $\ell$ is scaled to $\delta \ell$ and its area $A$ is rescaled to $\delta^2 A$. But the inequality does not change

$$
\begin{align*}
\delta^2 A \leq \frac{\delta ^2\ell^2}{2\pi} \iff A \leq \frac{\ell^2}{2\pi}.
\end{align*}
$$

By taking $\delta = 2\pi / \ell$, if suffices to prove that if $\ell=2\pi$ then $A \leq \pi$, with equality only if $\Gamma$ is a circle. Note that any curve admits a parameterization by arc	length by Lemma 1. Then, after a possible additional translation,  we can consider a parameterization $\gamma(s)=(x(s), y(s))$ of $\Gamma$ by arc-length defined on $[0,\ell]=[0,2\pi]$. Then 

$$
\begin{align*}
\frac{1}{2\pi} \int_0^{2\pi} x^\prime(s)^2 + y^\prime(s)^2 ds &=1 \\
\lVert x^\prime \rVert^2_{L^2}  + \lVert y^\prime \rVert^2_{L^2} &=1
\end{align*}
$$

$x(s)$ and $y(s)$ are $2\pi$ periodic  functions, and have Fourier coefficients $\\{a_n\\}$ and $\\{b_n\\}$, respectively. Their derivatives have coefficients $\\{ina_n\\}$ and $\\{inb_n\\}$, respectively. 

Using [Parseval's identity](https://seanie12.github.io/blog/fourier%20analysis/L2-recovery/#corollary-12-parsevals-identity) on the above, we get 

$$
\begin{align*}
1 &=\lVert \{ina_n\}\rVert^2_{\ell^2} + \lVert \{inb_n\}\rVert^2_{\ell_2} \\
&=\sum_{n=-\infty}^\infty  ina_n (-in\overline{a}_n) +\sum_{n=-\infty}^\infty inb_n(-in\overline{b}_n) \\ &= \sum_{n=-\infty}^\infty \lvert n\rvert^2(\lvert a_n\rvert^2 + \lvert b_n \rvert^2) 
\end{align*}
$$ 


Now, the area is by definition

$$
\begin{align*}
A = \frac{1}{2} 2\pi \left\lvert \frac{1}{2\pi}\int_a^b x(s) y^\prime(s) - y(s)x^\prime(s) ds\right\rvert
\end{align*}
$$

Using Parseval Again,  we get

$$
\begin{align*}
A &= \pi \left\lvert \sum_{n\in\mathbb{Z}} a_n(-in\overline{b}_n) - b_n(-in\overline{a}_n) \right\rvert \\
&\leq \pi \sum_{n\in\mathbb{Z}} \lvert n \rvert \lvert a_n\overline{b}_n-\overline{a}_nb_n \rvert 
\end{align*}
$$

Since 

$$
\begin{align}
\lvert a_n \overline{b}_n - \overline{a}_n b_n \rvert  \leq \lvert a_n\overline{b}_n\rvert + \lvert \overline{a}_n b_n\rvert = 2\lvert a_n b_n\rvert \leq \lvert a_n \rvert^2 + \lvert b_n \rvert^2,
\label{eq:5}
\end{align}
$$

we bound the area 

$$
\begin{align}
A &\leq \pi \sum_{n\in\mathbb{Z}} \lvert n \rvert \lvert a_n\overline{b}_n-\overline{a}_nb_n \rvert  \label{eq:6}\\
&\leq \pi\sum_{n\in\mathbb{Z}} \lvert n \rvert^2 (\lvert a_n \rvert^2+ \lvert b_n \rvert^2) =\pi \label{eq:7}.
\end{align}
$$

Equality in $\eqref{eq:6}$ and $\eqref{eq:7}$ could only occur if we have no terms $\lvert n \rvert\geq 2$. Moreover $x(s)$ and $y(s)$ are differentiable and real-valued functions and thus 




$$
\begin{align*}
x(s) &= a_{-1}e^{-is} + a_0 + a_1 e^{is} \\
y(s) &= b_{-1}e^{-is} + b_0 + b_1e^{is}.
\end{align*}
$$

by [Theorem](https://seanie12.github.io/blog/fourier%20analysis/L2-recovery/#theorem-21).

Since $x(s)$ and $y(s)$ are real-valued functions, 

$$
\begin{align*}
\overline{a}_{-n} &= \overline{\frac{1}{2\pi}\int_0^{2\pi} x(s) e^{-ins}ds} 
= \frac{1}{2\pi}\int_0^{2\pi} x(s) e^{ins}ds = a_n \\
\overline{b}_{-n} &= \overline{\frac{1}{2\pi}\int_0^{2\pi} y(s) e^{-ins}ds} 
= \frac{1}{2\pi}\int_0^{2\pi} y(s) e^{ins}ds = b_n.
\end{align*}
$$

Equation $\ref{eq:7}$ implies that $2(\lvert a_1 \rvert^2 + \lvert b_1 \rvert^2)=1$.

Now by $\ref{eq:5}$, equality hold only if 

$$
\begin{align*}
\lvert a_1 \overline{b}_1 - \overline{a}_1 b_1 \rvert =  2\lvert a_1 b_1\rvert =\lvert a_1 \rvert^2 + \lvert b_1 \rvert^2 = \frac{1}{2}
\end{align*}
$$

and thus, since. $(\lvert a_n \rvert - \lvert b_n \rvert)^2=0$ implies $\lvert a_n \rvert = \lvert b_n \rvert$, $\lvert a_1 \rvert = \lvert b_1 \rvert = 1/2$. So we get

$$
\begin{align*}
a_1= \frac{1}{2}e^{i\alpha} \quad \text{and } b_1 = \frac{1}{2}e^{i\beta}
\end{align*}
$$ 

for some $\alpha, \beta \in \mathbb{R}$. Since $1 = 2\lvert a_1 \overline{b}_1 - \overline{a}_1 b_1\rvert$, 

$$
\begin{align*}
\left\lvert \frac{1}{2} \left(e^{i(\alpha-\beta)} - e^{-i(\alpha-\beta)} \right)\right\rvert = 1,
\end{align*}
$$

i.e., $\lvert \sin(\alpha-\beta)\rvert=1$. So, $\alpha-\beta = k\pi/2$ for some $k\in\mathbb{Z}$. Putting all the pieces together, 

$$
\begin{align*}
x(s) &= \frac{1}{2}e^{-i\alpha}e^{-is} + a_0 + \frac{1}{2}e^{i\alpha}e^{is} = a_0 + \cos(\alpha+s) \\
y(s)&= \frac{1}{2}e^{-i\beta}e^{-is} + a_0 + \frac{1}{2}e^{i\beta}e^{is} = b_0 + \cos(\beta+s)  \\
&=b_0+ \cos(\alpha - \frac{k\pi}{2} +s) \\
&=b_0 \: \pm \sin(\alpha+s).
\end{align*}
$$

$\therefore \Gamma$ is a circle.

$$\tag*{$\square$}$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
