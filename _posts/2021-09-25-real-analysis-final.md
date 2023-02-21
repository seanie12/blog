---
title: "Ascoli-Azrela and Stone-Weirstrass Theorem"

categories:
  - Analysis

tags:
  - Ascoli-Azrela Theorem
  - Stone-Weirstrass Theorem
  - Analytic function

 
toc: true
toc_sticky: true

use_math : true
comments : true

---

## Theorem (Ascoli-Azrela)
Let $\\{f_n\\}$ be a sequence of functions defined on a set $K$. If $K$ is compact, $\\{f_n\\}$ is pointwise bounded on $K$, $\\{f_n\\}$ is equicontinuous then

(a) $\\{f_n\\}$ is uniformly bounded on $K$

(b) $\\{f_n\\}$ has a uniformly convergence subsequence.


<*Proof*>

(a) Fix an $\epsilon>0$. By equicontinuity, there is a $\delta>0$ such that

$$
\begin{align*}
d(x,y) < \delta \Rightarrow d(f_n(x), f_n(y)) <\epsilon
\end{align*}
$$

for all $x,y \in K$ and for all $n\in\mathbb{N}$. Now cover the set $K$ with $\\{N_\delta (x): x\in K\\}$. Since $K$ is compact, there is a finite sub-cover $\\{N_\delta(x_1), \ldots, N_\delta(x_n)\\}$. Since $\\{f_n\\}$ is pointwise bounded, for each $x_i$, there is $M_i>0$ such that 

$$
\begin{align*}
\lvert f_n(x_i) \rvert \leq M_i
\end{align*}
$$

for all $n\in\mathbb{N}$. Now let $M :=\max\\{M_1, \ldots, M_n\\}+\epsilon$. For any $x\in K$, choose $x_i$ such that $x\in N_\delta(x_i)$, i.e., $d(x, x_i) <\delta$. Then

$$
\begin{align*}
\lvert f_n(x) \rvert &= \lvert f_n(x) - f_n(x_i)+  f_n(x_i) \rvert \\
&\leq \lvert f_n(x) - f_n(x_i)\rvert + \lvert f_n(x_i) \rvert \\
&< \epsilon + M_i \\
&\leq M
\end{align*}
$$


(b) Exercise) If $K$ is compact metric space, then there is countable dense subset $E \subset K$, i.e., $K=E\cup E^\prime$. By previous [Theorem](https://seanie12.github.io/blog/analysis/equicontinuity/#theorem-723), there exists a subsequence $\\{f_{n_k}\\}$ pointwise converges on $E$.

We want to show that $\\{f_{n_k}\\}$ is uniformly convergent subsequence. 

Let $\epsilon >0$ be given.  By equicontinuity, there exists a $\delta>0$ such that 


$$
\begin{align*}
d(x,y) < \delta \Rightarrow d(f_{n_k}(x) - f_{n_k}(x)) < \epsilon
\end{align*}
$$

for all $k\in\mathbb{N}$. Cover $E$ with $\\{N_\delta (e): e\in E\\}$. Since $E$ is dense, it also covers $K$. By compactness of $K$, there exists a finite sub-cover $\\{N_\delta (e_1), \ldots, N_\delta (e_p)\\}$ of $K$. Since $\\{f_{n_k}\\}$ converges pointwise on $E$, for each $e_i$, there exists $N\in\mathbb{N}$ such that 

$$
\begin{align*}
k,l > N_i \Rightarrow \lvert f_{n_k}(e_i) - f_{n_l}(e_i)\rvert <\epsilon.
\end{align*}
$$

Let $N=\max\\{N_1, \ldots, N_p\\}$ and let  $x\in K$ be given. Choose $e_i$ such that $x\in N_\delta(e_i)$. Then, if $k,l >N$

$$
\begin{align*}
\lvert f_{n_k}(x) - f_{n_l}(x) \rvert &\leq \lvert f_{n_k}(x) - f_{n_k}(e_i)\rvert + \lvert f_{n_k}(e_i) - f_{n_l}(e_i)\rvert + \lvert f_{n_l}(e_i)-f_{n_l}(x) \rvert \\
&<3\epsilon.
\end{align*}
$$

$\therefore \\{f_{n_k}\\}$ converges uniformly on $K$ by Cauchy criterion.

$$\tag*{$\square$}$$


## Theorem (Stone-Weierstrass)
Given any function $f\in\mathscr{C}[a,b]$, there exists a sequence $\\{P_n\\}$ of polynomials that converges uniformly to $f$ on $[a,b]$. In other words, the space polynomial of $[a,b]$ is dense in $\mathscr{C}[a,b]$ with respect to supnorm metric.

<*Proof*>

Without loss of generality, assume $[a,b]$ is $[0,1]$ , $f(0)=f(1)=0$, and think $f(x)=0$ for all $x\in \mathbb{R}\setminus [a,b]$. Since $[a,b]$ is closed and bounded, $[a,b]$ is compact. Thus $f$ is uniformly continuous on $[a,b]$ and also  on $\mathbb{R}$.

We will create an **approximation of the identity**. Let 

$$
\begin{align*}
Q_n(x) = c_n(1-x^2)^n
\end{align*}
$$
on $[-1,1]$, where

$$
\begin{align*}
c_n = \frac{1}{\int_{-1}^1 Q_n(x)dx}.
\end{align*}
$$

Observe that $\int_{-1}^1 Q_n(x)dx=1$ and for any $\delta\in (0,1)$ $Q_n$ converges uniformly to $0$ on $\delta \leq \lvert x \rvert \leq 1$. 

$f(x)= (1-x^2)^n, g(x) = 1-nx^2$ on $[0,1]$. $f(0)=g(0)=1,\text{and } f(1)=g(1)=0$. Since

$$
\begin{align*}
f^\prime(x) = n(1-x^2)^n(-2x) \geq -2nx = g^\prime(x), \forall x \in [0,1]
\end{align*}
$$

$f(x) \geq g(x)$ for all $x\in [0,1]$.

Since 

$$
\begin{align*}
\int_{-1}^1 (1-x^2)^n dx &= 2\int_0^1(1-x^2)^n dx\\
&\geq 2\int_0^{1/\sqrt{n}}(1-x^2)^ndx \\
&\geq 2\int_0^{1/\sqrt{n}}(1-nx^2)dx \quad (\because (1-x^2)^n \geq 1-nx^2 \text{ on } [0,1]) \\
&=\frac{4}{3\sqrt{n}} \\
&> \frac{1}{\sqrt{n}}
\end{align*}
$$




Thus $c_n <\sqrt{n}$. Then 

$$
\begin{align*}
Q_n(x) < \sqrt{n}(1-x^2)^n \leq \sqrt{n}(1-\delta^2)^n.
\end{align*}
$$

By L'Hôpital's rule

$$
\begin{align*}
\lim_{n\to\infty}\sqrt{n}(1-\delta^2)^n = \lim_{n\to\infty} \frac{\sqrt{n}}{r^n} = \lim_{n\to\infty}\frac{1}{2\sqrt{n}r^{n-1}}=0,
\end{align*}
$$ 

where $r=(1-\delta^2)^{-n}>1$.



Thus, $Q_n$ converges uniformly to $0$ on $\delta \leq \lvert x \rvert \leq 1$. Define 

$$
\begin{align*}
P_n(x) = \int_{-1}^1 f(x+t)Q_n(t) dt.
\end{align*}
$$

Intuitively, if $n\to\infty$ $Q_n(t)$ becomes dirac-delta, i.e., $\int_{-1}^1Q_n(t) dt =1$ but $Q_n(t)=\mathbf{1}\\{t=0\\}$. Since

$$
\begin{align*}
P_n(x) &= \int_{-1}^1 f(x+t)Q_n(t)dt \\
&= \int_{-x}^{1-x}f(x+t)Q_n(t) dt \quad (\because 0\leq x+t \leq 1 \Rightarrow -x \leq t \leq 1-x) \\
&=\int_0^1 f(t) Q_n(t-x)dt \quad (\because \text{change of variable})\\
&=\int_0^1 f(t) c_n(1-(t-x)^2)^n dt
\end{align*}
$$


Now we want to show that $P_n \to f$ uniformly. Let $\epsilon >0$ be given.  Since $f \in \mathscr{C}[0,1]$, it is bounded, i.e., there is $M>0$ such that $\lvert f(x) \rvert < 0$ for all $x\in [0,1]$. Moreover, since $f$ is uniformly continuous on $[0,1]$, we can choose $\delta >0$ such that 

$$
\begin{align*}
\lvert t \rvert <\delta \Rightarrow \lvert f(x+t) -f(x) \rvert <\frac{\epsilon}{2}.
\end{align*}
$$

Lastly, $Q_n\to 0$ uniformly on $\delta \leq \lvert x \rvert \leq 1$, 

$$
\begin{align*}
\lim_{n\to\infty}\int_{\delta \leq \lvert t\rvert \leq 1}Q_n(t) &= \int_{\delta \leq \lvert t \rvert \leq 1}\lim_{n\to\infty}Q_n(t)dt \\
&=\int_{\delta \leq \lvert t \rvert \leq 1} 0dt =0.
\end{align*}
$$

Then, we can choose $N\in\mathbb{N}$ such that 

$$
\begin{align*}
n\geq N\Rightarrow \int_{\delta \leq \lvert t \rvert \leq 1} Q_n(t) dt < \frac{\epsilon}{4M}.
\end{align*}
$$

$$
\begin{align*}
\lvert P_n(x) - f(x) \rvert &=\left\lvert \int_{-1}^1f(x+t)Q_n(t) dt - f(x) \right\rvert \\
&=\left\lvert \int_{-1}^1f(x+t)Q_n(t) dt - f(x)\int_{-1}^1Q_n(t)dt \right\rvert \\
&=\left\lvert \int_{-1}^1(f(x+t)-f(x)Q_n(t) dt \right\rvert \\ 
&\leq \int_{-1}^1\left\lvert f(x+t)-f(x)\right\rvert Q_n(t)dt \\
&\leq \int_{\lvert t\rvert \leq \delta}\left\lvert f(x+t)-f(x)\right\rvert Q_n(t)dt + \int_{\delta \leq \lvert t\rvert \leq 1}\left\lvert f(x+t)-f(x)\right\rvert Q_n(t)dt \\
&\leq \frac{\epsilon}{2}\int_{\lvert t\rvert \leq \delta}Q_n(t)dt + 2M\int_{\delta \lvert t \rvert \leq 1}Q_n(t) dt \\
&\leq \frac{\epsilon}{2}\int_{-1 \leq t \leq 1}Q_n(t)dt + 2M\int_{\delta \leq \lvert t \rvert \leq 1}Q_n(t) dt \\
&< \frac{\epsilon}{2} + 2M\frac{\epsilon}{4M}\\
&=\epsilon
\end{align*}
$$

$$\tag*{$\square$}$$


## Definition (Analytic Function)
Any function $f$ that has a **power series expansion**, i.e., can be expressed in the form of 

$$
\begin{align*}
f(x) = \sum_{n=0}^\infty c_n x^n
\end{align*}
$$

or

$$
\begin{align*}
f(x) = \sum_{n=0}^\infty c_n(x-a)^n, \quad a \in \mathbb{R}
\end{align*}
$$


is called analytic function.


## Remark
Any such power series has a radius of convergence $R$, obtained via [root test](https://seanie12.github.io/blog/analysis/convergence-test-1/#theorem-718-root-test),

$$
\begin{align*}
\limsup_{n\to\infty}\sqrt[n]{\lvert c_n x^n \rvert} <1 \Rightarrow \sum_{n=0}^\infty c_n x^n \text{ converges.}
\end{align*}
$$

In other words,  convergence radius $R=1/\sqrt[n]{c_n}$.

## Lemma
$\lim_{n\to\infty}\sqrt[n]{n}=1$

<*Proof*>

Let $\sqrt[n]{n}:=1+\delta$. By binomial theorem,

$$
\begin{align*}
n&=(1+\delta_n)^n\\
&=1 + n\delta_n + {n \choose 2 } \delta^2_n + \cdots +  \delta^n_n.\\
\end{align*}
$$

Thus $n > n(n-1)/2 \delta^2_n$, i.e., 

$$
\begin{align*}
0 < \delta_n < \sqrt{\frac{2}{n-1}}.
\end{align*}
$$

$\therefore \lim_{n\to\infty}\sqrt[n]{n}=1$.


$$\tag*{$\square$}$$
## Theorem
Suppose $f(x) = \sum c_n x^n$ converges in $(-R, R)$. Then 

i) $\sum c_n x^n$ converges uniformly in $[-R+\epsilon, R-\epsilon]$ for any $\epsilon >0$.

ii) $f$ is continuous and differentiable on $(-R,R)$ and $f^\prime(x) = \sum_{n=1}^\infty n c_n x^{n-1}$.

<*Proof*>

Use [Weierstrass M-test](https://seanie12.github.io/blog/analysis/pointwise-uniform-convergence/#theorem-827-weierstrass-m-test). If $x\in [-R+\epsilon, R-\epsilon]$, then $\lvert x\rvert \leq R-\epsilon$, which implies that $\lvert c_n x^n \rvert \leq \lvert c_n (R-\epsilon)^n\rvert$. Since every power series converges absolutely in the interior of convergence by the root test, $\sum c_n x^n$ converges uniformly by Weierstrass M-test.

Now consider $\sum_{n=1}^\infty n c_n x^{n-1}$. By Lemma,

$$
\begin{align*}
\limsup_{n\to\infty}\sqrt[n]{\lvert n c_n x^{n-1}\rvert}= \limsup_{n\to\infty}\sqrt[n]{\lvert c_n\rvert}\lvert x_n\rvert <1.
\end{align*}
$$

Thus, $\sum_{n=1}^\infty n c_n x^{n-1}$ has the same radius of convergence, which implies that $\sigma_N=\sum_{n=1}^N n c_n x^{n-1}$ converges uniformly on $[-R+\epsilon, R-\epsilon]$. So by the [previous theorem](https://seanie12.github.io/blog/analysis/uniform-convergence-integration/#theorem-851),  

$$
\begin{align*}
\frac{d}{dx}\lim_{N\to\infty}\sum_{n=0}^N c_n x^n=\lim_{N\to\infty}\frac{d}{dx}\left(\sum_{n=0}^Nc_nx^n\right)=\lim_{N\to\infty}\sigma_N.
\end{align*}
$$

$$\tag*{$\square$}$$

## Reference
- Walter Rudin, **『**Principles of Mathematical Analysis**』**
