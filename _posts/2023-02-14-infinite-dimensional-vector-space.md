---
title: "Fourier Series in the Language of Infinite Dimensional Vector Space"

categories:
  - Fourier Analysis

tags:
  - Hilbert Space
  - Best Approximation Lemma
  - Infinite dimensional vector space



toc: true
toc_sticky: true

use_math : true
comments : true

---


## Preliminaries
Let $\\{a_n: n \in\mathbb{Z}\\}$ denote a sequence of complex numbers. We define $\ell_2$ norm of $\\{a_n\\}$ by 


$$
\begin{align*}
\lVert \{a_n \}_{n\in\mathbb{Z}} \rVert_{\ell_2} = \sum_{n\in\mathbb{Z}}\lvert a_n \rvert^2
\end{align*}
$$

and let $\ell^2(\mathbb{Z})$ denote the vector space of all sequences whose $\ell_2$ norm is finite.

## Definition 1.2
For $A=\\{a_n\\}$ and $B=\\{b_n\\}$ in $\ell^2(\mathbb{Z})$, we define the *inner product*

  
$$
\begin{align*}
\langle A, B\rangle =\lim_{N\to\infty}\sum_{n=-N}^Na_n \overline{b_n}
\end{align*}
$$

and $\lVert A \rVert := \sqrt{\langle A, A \rangle}$ denote the induced norm.


## Remark
Is $\ell_2(\mathbb{Z})$ closed under addition?

<*Proof*>

Let $(\mathbb{C}^n, +, \cdot)$ be vector space over $\mathbb{C}$ and define inner product $\langle (a_1,\ldots, a_n), (b_1, \ldots, b_n)\rangle = \sum_{i=1}^n a_i \overline{b_i}$. We define norm $\lVert \mathbf{x}\rVert = \sqrt{\langle \mathbf{x}, \mathbf{x}\rangle}$. Let $\mathbf{x}= (a_1, \ldots, a_n)$ and $\mathbf{y}=(b_1, \ldots, b_n)$.

$$
\begin{align*}
\lVert \mathbf{x}+\mathbf{y}\rVert^2 &= \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + \langle \mathbf{x},\mathbf{y}\rangle + \overline{\langle \mathbf{x}, \mathbf{y}\rangle} \\
&= \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + 2\text{Re}\langle \mathbf{x},\mathbf{y}\rangle  \\
&\leq \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + 2 \lvert \langle \mathbf{x}, \mathbf{y}\rangle \rvert \\
&\leq \lVert \mathbf{x}\rVert^2 + \lVert \mathbf{y}\rVert^2 + 2 \lVert \mathbf{x}\rVert^2 \lVert \mathbf{y}\rVert^2 \\
&\leq \left( \lVert \mathbf{x} \rVert + \lVert \mathbf{y}\rVert\right)^2.
\end{align*}
$$

It implies that $\lVert \mathbf{x}+\mathbf{y}\rVert \leq \lVert \mathbf{x}\rVert + \lVert \mathbf{y}\rVert$.

Thus, for all $N\in\mathbb{N}$,

$$
\begin{align*}
\sqrt{\sum_{n=-N}^N \lvert a_n+b_n\rvert^2} &\leq \sqrt{\sum_{n=-N}^N \lvert a_n\rvert^2}+ \sqrt{\sum_{n=-N}^N \lvert b_n\rvert^2} \\
&\leq \lim_{N\to\infty}\sqrt{\sum_{n=-N}^N \lvert a_n\rvert^2}+ \lim_{N\to\infty}\sqrt{\sum_{n=-N}^N \lvert b_n\rvert^2} \\
&<\infty
\end{align*}
$$


$$\tag*{$\square$}$$
## Definition 1.3 
An inner product space with strictly positive definite inner product, which is complete with respect to the induced metric, is called a *Hilbert space*.

Since all the sequences are monotone increasing and bounded, $\lVert A +B \rVert \in \mathbb{R}$. Thus, $\ell_2(\mathbb{Z})$ is closed under the addition.





## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
