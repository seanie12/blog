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

(1) linearity

$$\begin{align*}
\int_{-\infty}^\infty (\alpha f+\beta g)= \alpha \int_{-\infty}^\infty f +\beta\int_{-\infty}^\infty g.
\end{align*}
$$

(2) translation invariance

$$\begin{align*}
\int_{-\infty}^\infty f(x-\alpha)dx = \int_{-\infty}^\infty f(x)dx.
\end{align*}
$$


(3) scaling under dilations

Given any $\delta>0$,

$$
\begin{align*}
\delta\int_{-\infty}^\infty f(\delta x) dx = \int_{-\infty}^\infty f(x)dx.
\end{align*}
$$


(4) continuity

$$
\begin{align*}
\lim_{h\to 0}\int_{-\infty}^\infty \lvert f(x-h)-f(x)\rvert dx=0.
\end{align*}
$$

<*Proof*>

(1) 

Since $f,g\in\mathcal{M}(\mathbb{R})$ and 
$$
\begin{align*}
\int_{-N}^N \alpha f +\beta g = \alpha \int_{-N}^Nf + \beta \int_{-N}^Ng ,
\end{align*}
$$

$$
\begin{align*}
\lim_{N\to\infty}\left(\alpha\int_{-N}^Nf + \beta\int_{-N}^Ng \right) &=\lim_{N\to\infty}\alpha \int_{-N}^Nf+\lim_{N\to\infty}\beta\int_{-N}^Ng \\
&=\alpha\lim_{N\to\infty}\int_{-N}^Nf + \beta\lim_{N\to\infty}\int_{-N}^Ng \\
&=\alpha \int_{-\infty}^\infty f+\beta\int_{-\infty}^\infty g.
\end{align*}
$$

(2) It suffices to show that 

$$
\lim_{N\to\infty}\left(\int_{-N}^N f(x-\alpha) dx -\int_{-N}^Nf(x) dx \right) =0.
$$

With change of variables,

$$
\begin{align*}
\int_{-N}^N f(x-\alpha)-f(x)dx &= \int_{-N-\alpha}^{N-\alpha} f(x) dx - \int_{-N}^N f(x)dx \\
&= \int_{-N-\alpha}^{-N} f(x) dx + \int_{N-\alpha}^N f(x)dx. 
\end{align*}
$$

Take $N>2\alpha$. Then

$$
\begin{align*}
\left\lvert\int_{-N-\alpha}^{-N} f(x) dx + \int_{N-\alpha}^N f(x)dx\right\rvert &\leq \int_{-2N}^{-N} \lvert f(x)\rvert dx + \int_{\frac{N}{2}}^N \lvert f(x)\rvert dx \\
&\leq \int_{\frac{N}{2}\leq \lvert x\rvert \leq 2N} \lvert f(x)\rvert dx \\
&\leq  \int_{\frac{N}{2}\leq \lvert x\rvert \leq 2N} \frac{A}{x^2}dx \\
&=2A\left(-\frac{1}{2N} + \frac{2}{N}\right) \\
&=\frac{3A}{N} \to 0 \text{ as } N\to\infty.
\end{align*}
$$

(3)  With change of variables,

$$
\begin{align*}
\delta \int_{-N}^N f(\delta x) dx = \int_{-\delta N}^{\delta N} f(x)dx.
\end{align*}
$$

Thus, 

$$
\begin{align*}
\lim_{N\to\infty} \delta\int_{-N}^N f(\delta x) dx = \int_{-\infty}^\infty f(x)dx
\end{align*}
$$

(4) Given $\epsilon>0$, we want to show that there exists $H>0$ such that  if $\lvert h \rvert < H$, then

$$
\begin{align*}
\lim_{N\to\infty} \int_{-N}^N \lvert f(x-h)-f(x)\rvert dx <\epsilon.
\end{align*}
$$

Without loss of generality, we take $\lvert h \rvert\leq1$. 

Note that 

$$
\begin{align*}
\int_{\lvert x \rvert \geq N_0} \lvert f\rvert &\leq 2\int_{x  \geq N_0} \frac{A}{1+x^2}dx \\
&\leq2A\int_{x\geq N_0}\frac{dx}{x^2} \\
&=2A \lim_{M\to\infty} \int_{N_0}^M \frac{dx}{x^2} \\
&=2A \lim_{M\to\infty}\left(\frac{1}{N_0}-\frac{1}{M}\right) \\
&=\frac{2A}{N_0}.
\end{align*}
$$


Similarly, 

$$
\begin{align*}
\int_{N_0}^M \lvert f(x-h)\rvert dx &\leq \int_{ N_0}^M \frac{A}{1+(x-h)^2}dx \\
&=A\int_{N_0-h}^{M-h}\frac{dx}{1+x^2} \\
&\leq A \int_{N_0-h}^{M-h} \frac{dx}{x^2} \\
&=A\left(\frac{1}{N_0-h} -\frac{1}{M-h}\right)
\end{align*}
$$

We take $N_0$ large enough that 

$$
\begin{align*}
\int_{\lvert x \rvert \geq N_0} \lvert f\rvert \leq \frac{\epsilon}{4} \text{ and } \int_{\lvert x \rvert \geq N_0} \lvert f(x-h)\rvert dx \leq \frac{\epsilon}{4}.
\end{align*}
$$

Since $f$ is continuous, it is uniformly continuous on $[-N_0-1, N_0+1]$. Thus, we can choose $H$ such that if $h<H$,

$$
\begin{align*}
\lvert f(x-h) - f(x) \rvert < \frac{\epsilon}{4N_0} \text{ for all } \lvert x\rvert \leq N_0.
\end{align*}
$$

This implies that 

$$
\begin{align*}
\sup_{\lvert x \rvert \leq N_0}\lvert f(x-h) - f(x) \rvert < \frac{\epsilon}{4N_0}.
\end{align*}
$$

Then for any $N>N_0$, we get 

$$
\begin{align*}
\int_{-N}^N \lvert f(x-h)-f(x)\rvert dx & = \int_{-N_0}^{N_0} \lvert f(x-h)-f(x)\rvert dx + \int_{N_0 \leq \lvert x \rvert \leq N} \lvert f(x-h)-f(x)\rvert dx \\
&\leq \int_{-N_0}^{N_0} \lvert f(x-h)-f(x)\rvert dx + \int_{\lvert x \rvert \geq N_0} \lvert f \rvert +\int_{\lvert x \rvert \geq N_0} \lvert f(x-h)\rvert dx \\
&\leq \frac{\epsilon}{2} +\frac{\epsilon}{4} + \frac{\epsilon}{4} = \epsilon.
\end{align*}
$$

$$\tag*{$\square$}$$

## Definition
Given $f\in\mathcal{M}(\mathbb{R})$, we define the **Fourier transform** $\hat{f}$ of $f$ by

$$
\begin{align*}
\hat{f}(\xi) = \int_{-\infty}^\infty f(x) e^{-2\pi ix\xi}dx
\end{align*}
$$


## Definition
We call a function **rapidly decreasing* if for every $k\geq0$, we have

$$
\begin{align*}
\sup_{x\in\mathbb{R}} \lvert x \rvert^k \lvert f(x) \rvert <\infty,
\end{align*}
$$

the function *shrinks faster* than the reciprocal of any polynomial function.


## Definition 
Let $f$ be an infinitely differentiable $(\mathscr{C}^\infty)$ function. If $f$ and all of its derivatives are rapidly decreasing, we call $f$ a **Schwartz class** function and write $f\in\mathcal{S}(\mathbb{R})$.

## Proposition
Let $f\in\mathcal{S}(\mathbb{R}), h\in\mathbb{R}$, and $\delta >0$. Then 

(1) $f(x+h)\longrightarrow\hat{f}(\xi)e^{2\pi i h \xi}$ (translation becomes modulation

(2) $f(x)e^{-2\pi i xh}\longrightarrow \hat{f}(\xi+h)$

(3) $f(\delta x) \longrightarrow \delta^{-1} \hat{f}(\delta^{-1}\xi)$ (dilation)

(4) $f^\prime(x) \longrightarrow 2\pi i\xi \hat{f}(\xi)$ (differentiation becomes polynomial multiplication)

(5) $-2\pi i x f(x) \longrightarrow \frac{d}{d\xi} \hat{f}(\xi)$

<*Proof*>

(1) 

$$
\begin{align*}
\int_{-\infty}^\infty f(x+h)e^{-2\pi i x \xi} dx &= \int_{-\infty}^\infty f(x) e^{2\pi ih\xi} e^{-2\pi i x \xi} dx \text{ (by change of the variable)} \\
&=e^{2\pi i h \xi} \hat{f}(\xi)
\end{align*}
$$

(2) 

$$
\begin{align*}
\int_{-\infty}^\infty f(x) e^{-2\pi ixh} e^{-2\pi ix \xi}dx &= \int_{-\infty}^\infty  f(x) e^{-2\pi ix (h+\xi)}dx = \hat{f}(\xi+h)
\end{align*}
$$

(3) 

$$
\begin{align*}
\int_{-\infty}^\infty f(\delta x) e^{-2\pi i x \xi}dx = \int_{-\infty}^\infty \delta^{-1}f(x) e^{-2\pi i \delta^{-1} x \xi}dx = \delta^{-1} \hat{f}(\delta^{-1} \xi)
\end{align*}
$$


(4) 

$$
\begin{align*}
\int_{-N}^N f^\prime(x) e^{-2\pi ix\xi} dx &= [f(x) e^{-2\pi i x\xi}]_{-N}^N + 2\pi i \xi \int_{-N}^N f(x) e^{-2\pi i x \xi}dx \\
&\to 2\pi i \xi \hat{f}(\xi) \text{ as } N\to\infty.
\end{align*}
$$

(5) We must show that $\hat{f}$ is differentiable and find its derivative. Let $\epsilon$ be given and consider

$$
\begin{align*}
\left\lvert\frac{\hat{f}(\xi +h) -\hat{f}(\xi)}{h} - \widehat{-2\pi i x f}(\xi)\right\rvert &= \left\lvert \int_\mathbb{R} f(x) \frac{1}{h}\left( e^{-2\pi  ix(\xi +h)}-e^{-2\pi i x \xi}\right) dx+ \int_{\mathbb{R}} 2\pi ixf(x)e^{-2\pi i x \xi} dx\right\rvert \\
&= \left\lvert \int_{\mathbb{R}} f(x) e^{-2\pi i x \xi} \left( \frac{2^{-2\pi ixh}-1}{h} + 2\pi ix \right) dx\right\rvert
\end{align*}
$$
## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
