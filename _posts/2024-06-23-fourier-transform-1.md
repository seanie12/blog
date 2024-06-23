---
title: "Fourier Transform"

categories:
  - Fourier Analysis

tags:
  - moderate decrease
  - fourier transform



toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition
We define (if the limit exists)

$$
\begin{align*}
\int_{-\infty}^\infty f(x)dx = \lim_{N\to\infty} \int_{-N}^N f(x)dx
\end{align*}
$$

## Defintion
Let $f:\mathbb{R}\to\mathbb{C}$ be continuous. If there exists $A>0$ such that 

$$
\begin{align*}
\lvert f(x)\rvert \leq \frac{A}{1+x^2}
\end{align*}
$$

for all $x\in\mathbb{R}$, then we say $f$ is of **moderate decrease** and denote by $\mathcal{M}(\mathbb{R})$ the vector space of such functions.

## Exercise
Whenever $f\in\mathcal{M}(\mathbb{R})$, its limit 

$$
\begin{align*}
\int_{-\infty}^\infty f(x)dx = \lim_{N\to\infty}\int_{-N}^Nf(x)dx
\end{align*}
$$

always exists. 

<*Proof*>

For each $N\in\mathbb{N}$, define the integral $I_N=\int_{-N}^Nf(x)dx$. It is well-defined since $f$ is continuous. It suffices to show that $\\{I_N\\}$ is a Cauchy sequence. Let $M,N\in\mathbb{N}$ with $M>N$ be given. Then

$$
\begin{align*}
\lvert I_M - I_N\rvert &\leq \left\lvert \int_{N\leq \lvert x \rvert \leq M} f(x) dx\right\rvert \\
&\leq A \int_{N\leq \lvert x \rvert \leq M} \frac{dx}{1+x^2} \\
&\leq A \int_{N\leq \lvert x \rvert \leq M} \frac{dx}{x^2} \\
&=2A\left(\frac{1}{N}-\frac{1}{M}\right) \\
&\leq \frac{2A}{N}
\end{align*}
$$

which goes to $0$ as $N\to\infty$.
$$\tag*{$\square$}$$

## Proposition (Properties of the improper integral)
Let $f,g\in\mathcal{M}(\mathbb{R})$, and $\alpha,\beta\in\mathbb{C}$. Then

1. linearity

$$\begin{align*}
\int_{-\infty}^\infty (\alpha f+\beta g)= \alpha \int_{-\infty}^\infty f +\beta\int_{-\infty}^\infty g.
\end{align*}
$$

2. translation invariance

$$\begin{align*}
\int_{-\infty}^\infty f(x-\alpha)dx = \int_{-\infty}^\infty f(x)dx.
\end{align*}
$$


3. scaling under dilations

Given any $\delta>0$,

$$
\begin{align*}
\delta\int_{-\infty}^\infty f(\delta x) dx = \int_{-\infty}^\infty f(x)dx.
\end{align*}
$$


4. Continuity

$$
\begin{align*}
\lim_{h\to 0}\int_{-\infty}^\infty \lvert f(x-h)-f(x)\rvert dx=0.
\end{align*}
$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
