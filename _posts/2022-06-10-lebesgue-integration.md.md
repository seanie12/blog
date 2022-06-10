---
title: "Lebesgue Integration"

categories:
  - Measure Theory 


tags:
  - Lebesgue integral
  - Lebesgue monotone convergence theorem


toc: true
toc_sticky: true

use_math : true
comments : true

---

## Proposition 8.2.6
Let $\Omega$ be a measurable set, and let $f: \Omega\rightarrow [0,\infty]$ and $g: \Omega\rightarrow [0,\infty]$ be non-negative measurable functions.

(a) We have $0\leq \int_\Omega f\leq \infty$. Furthermore, we have $\int_\Omega f = 0$ if and only if $f(x)=0$ for almost every $x\in\Omega$.

(b) For any positive number $c$, we have $\int_\Omega cf = c\int_\Omega f$.

(c) If $f(x)\leq g(x)$ for almost every $x\in\Omega$, then $\int_\Omega f = \int_\Omega g$.

(d) If $f(x)=g(x)$ for almost every $x\in\Omega$, then $\int_\Omega f = \int_\Omega g$.

(e) If $\Omega^\prime \subseteq \Omega$ is a measurable, then $\int_{\Omega^\prime}f = \int_{\Omega}f\chi_{\Omega^\prime}\leq \int_{\Omega}f$.


## Lemma 1
If $A_1\subseteq A_2\subseteq A_3\subseteq\cdots$ is a sequence of measurable sets, then we have 

$$
\begin{align*}
m\left(\bigcup_{j=1}^\infty A_j \right)=\lim_{j\to \infty}m(A_j).
\end{align*}
$$

<*proof*>
Define $A_0:= \emptyset$ and $B_i := A_i \setminus A_{i-1}$. Since $A_i$ is measurable, $A^c_i$ is also measurable. Thus, $A_i\setminus A_{i-1}=A_i\cap A^c_{i-1}$ is measurable.
$$
\biguplus_{i=1}^\infty B_i= \bigcup_{i=1}^{\infty}A_i.
$$

Since $B_i$'s are disjoint measurable sets,
$$
\begin{align*}
m\left(\biguplus_{i=1}^\infty B_i\right)&=\sum_{i=1}^\infty m\left( B_i \right) \\
&=\lim_{n\to\infty}\sum_{i=1}^nm(B_i) \\
&=\lim_{n\to\infty}m(A_n)-m(A_0) \\
&=\lim_{n\to\infty}m(A_n)
\end{align*}
$$
## Theorem 8.2.9
Let $\Omega$ be a measurable subset of $\mathbb{R}^n$, and let $(f_n)_{n=1}^\infty$ be a sequence of non-negative measurable functions from $\Omega$ to $\mathbb{R}$ which are increasing in the sense that 

$$
\begin{align*}
0\leq f_1(x)\leq f_2(x)\leq f_3(x)\leq \cdots \text{ for all }x\in \Omega.
\end{align*}
$$

Then we have

$$
\begin{equation}
0\leq \int_\Omega f_1 \leq \int_\Omega f_2 \leq \int_\Omega f_3\leq \cdots
\end{equation}
\label{eq:1}
$$

and

$$
\begin{equation}
\int_\Omega \sup_n f_n=\sup_n \int_\Omega f_n.
\end{equation}
$$

By Proposition 8.2.6(c), it is clear to show the inequality $\ref{eq:1}$.  For the second conclusion, we want to show that 

$$
\begin{align*}
\int_\Omega \sup_n f_n \geq \sup_n\int_\Omega f_n \text{ and } \int_\Omega \sup_n f_n \leq \sup_n\int_\Omega f_n.
\end{align*}
$$

<*proof*>
Since $\sup_m f_m \geq f_n$  for every $n$, we have 

$$
\begin{align*}
\int_\Omega \sup_m f_m \geq \int_\Omega f_n
\end{align*}
$$

for all $n\in\mathbb{N}$.

Taking supremum for $n$, we obtain

$$
\begin{align*}
\int_\Omega \sup_m f_m \geq \sup_n \int_\Omega f_n.
\end{align*}
$$

Now, we have to show that 

$$
\begin{align*}
\int_\Omega \sup_m f_m \leq \sup_n \int_\Omega f_n.
\end{align*}
$$

It suffices to show that 

$$
\begin{align*}
\int_\Omega s \leq \sup_n \int_\Omega f_n
\end{align*}
$$
for all simple non-negative functions such that $0\leq s \leq \sup_m f_m$ since 

$$
\begin{align*}
\sup_{s\in S}\int_\Omega s = \int_\Omega \sup_m f_m \quad \text{ where } S=\{s:\text{ simple function}\mid 0\leq s(x)\leq\sup_mf_m(x), \forall x \in \Omega \}
\end{align*}
$$

Fix $s\in S$. We want to show that 

$$
\begin{align*}
(1-\epsilon)\int_\Omega s \leq \sup_n\int_\Omega f_n
\end{align*}
$$

for every $0<\epsilon<1$. Now Fix $\epsilon$. Since $s\in S$, we have

$$
\begin{align*}
s(x) \leq \sup_nf_n(x)
\end{align*}
$$

for every $x\in\Omega$. Since $0<\epsilon<1, (1-\epsilon)s(x)<s(x)$. For every $x\in\Omega$, then $(1-\epsilon)s(x)$ cannot be an upper bound of $$\{ f_n(x)\mid n\in\mathbb{N}\} $$. Hence, for every $x\in\Omega$, there exists $N:= N_x\in\mathbb{N}$ such that 

$$
\begin{align*}
f_{N}(x)\geq (1-\epsilon)s(x).
\end{align*}
$$

Since the $f_n$ increasing, it implies that $f_n(x)\geq (1-\epsilon)s(x)$ for all $n\geq N$. Thus, if we define the set $E_n$ by

$$
\begin{align*}
E_n:= \{ x\in\Omega\mid f_n(x) \geq (1-\epsilon)s(x)\}
\end{align*}
$$

then we have $E_1\subset E_2\subset E_3\subset \cdots$ and $\bigcup_{n=1}^\infty E_n=\Omega$.

By Proposition 8.2.6,
$$
\begin{align}
(1-\epsilon)\int_{E_n}s
\stackrel{\text{(b)}}{=} \int_{E_n}(1-\epsilon)s \stackrel{\text{(c)}}{\leq}\int_{E_n}f_n\stackrel{(e)}{\leq} \int_\Omega f_n.
\label{ineq}
\end{align} 
$$

Now it suffices to show that 

$$
\begin{align*}
\sup_n \int_{E_n} s= \int_\Omega s.
\end{align*}
$$

Since $s$ is a simple function, we may write $s=\sum_{i=1}^kc_i\chi_{F_i}$ for some measurable $F_i\subset \Omega$ and $c_i >0$.

Since 
$$
\begin{align*}
\int_\Omega s = \sum_{i=1}^kc_i m(F_i)
\end{align*}
$$
and by Proposition 8.2.6(d),

$$
\begin{align*}
\int_{E_n}s&=\int_\Omega \chi_{E_n}s \\
&=\int_\Omega\chi_{E_n}\sum_{i=1}^kc_i\chi_{F_i}\\
&=\int_\Omega \sum_{i=1}^kc_i\chi_{F_i}\chi_{E_n}\\
&= \int_\Omega \sum_{i=1}^kc_i\chi_{F_i\cap E_n} \\
&=\sum_{i=1}^kc_im(F_i\cap E_n)
\end{align*}
$$

Now, it suffices to show that 
$$
\begin{align*}
\sup_n\sum_{i=1}^kc_im(F_i\cap E_n)=  \int_\Omega s.
\end{align*}
$$
Since $m(F_i\cap E_n)$ is increasing sequence with respect to $n$ and $(F_i\cap E_1)\subset (F_i\cap E_2)\subset (F_i\cap E_3)\subset \cdots$ for each $i$,

$$
\begin{align}
\begin{split}
\sup_n\sum_{i=1}^kc_im(F_i\cap E_n)&=\lim_{n\to\infty}\sum_{i=1}^kc_im(F_i\cap E_n)\\
&=\sum_{i=1}^kc_i\lim_{n\to\infty}m(F_i\cap E_n)\\
&=\sum_{i=1}^kc_i m\left(\lim_{n\to\infty}F_i\cap E_n\right) \: (\text{By Lemma1})\\
&=\sum_{i=1}^kc_im(F_i\cap \Omega) \\
&=\sum_{i=1}^kc_im(F_i) \\
&=\int_\Omega s
\end{split}
\label{eq:final}
\end{align}
$$

The inequality $\ref{ineq}$, we get $\int_{E_n}s \leq \int_\Omega f_n$ as $\epsilon \to 0$. Combining it with Equation $\ref{eq:final}$,

$$
\int_\Omega s = \sup_n\int_{E_n}s\leq \sup_n \int_\Omega f_n
$$

for all $s\in S$.
$$\tag*{$\square$}$$
## Reference
- Terrance Tao,  **『**Introduction to Real Analysis**』**, Pearson
