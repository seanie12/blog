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
For $A=\{a_n\}$ and $B=\{b_n\}$ in $\ell^2(\mathbb{Z})$, we define the *inner product*

  
$$
\begin{align*}
\langle A, B\rangle =\lim_{N\to\infty}\sum_{n=-N}^Na_n \overline{b_n}
\end{align*}
$$

and $\lVert A \rVert \coloneqq \sqrt{\langle A, A \rangle}$ denote the induced norm.



$$\tag*{$\square$}$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
