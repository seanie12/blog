---
title: "Introduction to Fourier Series"

categories:
  - Fourier Analysis

tags:
  - Fourier Sereis


toc: true
toc_sticky: true

use_math : true
comments : true

---
## Basic Knowledge
We focus on a class of functions

(1)  Continuous functions $[0, L]$

(2) Piecewise continuous functions (only finitely many discontinuities)

(3) Riemann integrable functions 

(4) Functions on the circle (correspondence with $2\pi$ periodic functions on $\mathbb{R}$ such that $f(0)=f(2\pi)$.

## Definition 2.1
Given an integrable function $f:[a,b]\to\mathbb{C}$, we define the *Fourier series* of $f$ as 

$$
\begin{align*}
\sum_{n=-\infty}^{\infty} \hat{f}(n)e^{\frac{2\pi inx}{b-a}},
\end{align*}
$$

where 

$$
\begin{align*}
\hat{f}(n) = \frac{1}{b-a}\int_a^b f(x) e^{\frac{2\pi inx }{b-a}}
\end{align*}
$$

denotes the $n$-th *Fourier coefficient* of $f$ for $n\in\mathbb{N}$.

## Remark
One can define inner product $\langle f,g \rangle = \frac{1}{b-a}\int_a^b f(x) \bar{g}(x) dx$. Then 

$$
\begin{align*}
\hat{f}(n) = \left\langle f, \exp\left(\frac{2\pi inx}{b-a}\right) \right\rangle .
\end{align*}
$$

## Example
The Fourier series of the $2\pi$-periodic odd function defined on $[0,\pi]$ by $f(\theta) = \theta(\pi-\theta)$. For $\theta>0$ the given function is $f(\theta)=\theta(\pi+\theta)$ with its derivative $f^\prime(\theta)=\pi-2\theta$. On the other hand, $f(\theta)= \theta(\pi+\theta)$ with its derivative $f^\prime(\theta)=\pi+2\theta$ for $\theta<0$.  Then using the integration by parts,

$$
\begin{align*}
\hat{f}(n) &= \frac{1}{2\pi} \int_{-\pi}^\pi f(\theta) \exp\left( \frac{-2\pi in\theta}{2\pi} \right) \\
&=\frac{1}{2\pi}\left(\left[\frac{-f(\theta)\exp(-in\theta)}{in} \right]_{-\pi}^\pi  + \int_{-\pi}^\pi f^\prime(\theta) \frac{e^{-in\theta}}{in} d\theta \right) \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi f^\prime(\theta) \frac{e^{-in\theta}}{in} d\theta \quad (\because f(\pi)=f(-\pi)=0) \\
&=\frac{1}{2\pi}\left(\int_{-\pi}^0 (\pi+2\theta)\frac{e^{-in\theta}}{in}d\theta + \int_{0}^\pi (\pi-2\theta)\frac{e^{-in\theta}}{in}d\theta \right) \\
&=\frac{1}{2\pi}\int_{-\pi}^\pi \pi \frac{e^{-in\theta}}{in}d\theta + \frac{1}{in\pi}\left(\int_{-\pi}^0 \theta e^{-in\theta} d\theta - \int_0^\pi \theta e^{-in\theta}d\theta \right)
\end{align*}
$$

By Euler formula $e^{i\theta}=$, for all non-zero integer $k\in\mathbb{Z}\setminus \{0\}$
$$
\begin{align*}
\int_{-\pi}^\pi e^{ikx} dx &= \left[\frac{1}{ik} e^{ikx} \right]_{-\pi}^\pi  \\
&=\frac{1}{ik}(e^{ik\pi}-e^{-ik\pi}) \\
&= \frac{1}{ik}\left(\cos(k\pi)+i\sin(k\pi) - \cos(-k\pi)-i\sin(-k\pi) \right) \\
&= \frac{1}{ik}\left(\cos(k\pi) + i\sin(k\pi) -\cos(k\pi)+i\sin(k\pi) \right) \\
&=\frac{1}{ik}2i\sin(k\pi) \\
&=0.
\end{align*}
$$

Then 
$$
\begin{align*}
\frac{1}{in\pi}\int_{-\pi}^\pi \pi \frac{e^{-in\theta}}{in}d\theta &= \frac{1}{in\pi}\int_{-\pi}^\pi e^{-in\theta}d\theta \\
&=0.
\end{align*}
$$

With the change of variable $\gamma=-\theta$,
$$
\begin{align*}
\hat{f}(n) &= \frac{1}{in}\left(\int_{-\pi}^0 \theta e^{-in\theta} d\theta - \int_0^\pi \theta e^{-in\theta}d\theta \right)  \\
&= \frac{1}{in\pi}\left(-\int^\pi_0 \gamma e^{in\gamma}d\gamma -\int_{0}^\pi \gamma e^{-in\gamma}d\gamma\right) \\
&= -\frac{1}{in\pi}\left(\int_{0}^\pi \theta(e^{in\theta}+e^{-in\theta})d\theta \right).
\end{align*}
$$

Since 

$$
\begin{align*}
\int e^{in\theta} + e^{-in\theta}d\theta &= \frac{1}{in}\left( e^{in\theta}-e^{-in\theta}\right) + C \\
&=\frac{1}{in}(cos(n\theta) + i\sin(n\theta) - \cos(-n\theta)-i\sin(-n\theta)) + C \\
&= \frac{1}{in}2i\sin(n\theta) +C \\
&= \frac{2}{n}\sin(n\theta)+C,
\end{align*}
$$

we get the following equation with the integration by parts:
$$
\begin{align*}
\hat{f}(n) &= -\frac{2}{in\pi}\left(\left[\frac{\theta}{n}\sin(n\theta) \right]_0^\pi - \int_0^\pi \frac{1}{n}\sin(n\theta)d\theta\right) \\
&= \frac{2}{in^2\pi}\int_0^\pi \sin(n\theta)d\theta \\
&= \frac{2}{in^2\pi}\left[-\frac{1}{n}\cos(n\theta) \right]_0^\pi \\
&= \frac{2}{in^2\pi}\left( \frac{1-\cos(n\pi)}{n}\right) \\
&= \frac{2}{in^3\pi}(1+(-1)^{n+1}) \\
&= \frac{4}{in^3\pi}
\end{align*}
$$
for odd $n$, and $0$ otherwise.

Thus,
$$
\begin{align*}
f(\theta) \sim \sum_{k \text{ odd}}\frac{4}{ik^3\pi}e^{ikx}
\end{align*}
$$

$$\tag*{$\square$}$$

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
