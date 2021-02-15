---
title: "Continuous functions"

categories:
  - Analysis


tags:
  - continuity
  - topological characterization

toc: true
toc_sticky: true

use_math : true
comments : true

---
## Definition 4.2.1
$f:E\to \mathbb{R}$ is continuous at $p\in E$, <br /> if $\forall \epsilon >0, \exists \delta >0$ such that $|x-p|<\delta \Rightarrow |f(x)-f(p)|<\epsilon$.

## Note
(a) $[p\in E^\prime \Rightarrow f \text{ is continuous at }p] \iff \displaystyle{\lim_{x\to p}f(x)=f(p)}$ 

(b) If $p\in E$ is an isolated point of $E$, every function $f:E\to \mathbb{R}$ is continuous at $p$.

## Remark
$f$ is continuous at $p$ <br />$\iff \epsilon >0, \exists \delta >0 \text{ s.t. }x\in N_\delta (p) \cap E \Rightarrow f(x) \in N_\epsilon (f(p))$

The continuous function maps the open set in $E$ to another open set in $\mathbb{R}.$

## Examples 4.2.2
(b) $f(x) = 0 (x\in \mathbb{Q})$ or $f(x) = x (x\not\in \mathbb{Q})$.

$f$ is continuous at $x=0$ but discontinuous at $x\neq 0$ ($\because \not\exists\displaystyle{\lim_{x\to p}f(x) \text{ for } p\neq 0)}$.

(c) $f(x) = 0 (x\in \mathbb{Q})$ or $f(x) = 1 (x\not\in \mathbb{Q}).$

$f$ is discontinuous on $\mathbb{R}$.

(e) $f(x) = 0 (x=0)$ or $f(x) = x\sin\frac{1}{x} (x\neq 0)$
<br />
$\displaystyle{\lim_{x\to 0}x\sin\frac{1}{x} = 0=f(0)}$ because $|\sin \frac{1}{x}| \leq 1$ and $\displaystyle{\lim_{x\to 0}x =0}$.

(f) $f(x) = \sin x$

Let $x,y \in \mathbb{R}$ be given.

$$
\begin{align}
\begin{split}
|f(y) - f(x)| &= |\sin y - \sin x| \\
&=2|\cos \frac{1}{2}(y+x)\sin \frac{1}{2}(y-x)| \\
&\leq 2|\sin\frac{1}{2}(y-x)| \\
&\leq 2\cdot \frac{1}{2}|y-x| \\
&=|y-x|
\end{split}
\end{align}
$$
Put $y:=p, \text{ and }\delta :=\epsilon$.  <br />Then $\forall \epsilon >0, \exists \delta >0$ s.t. $|x-p|<\delta \Rightarrow |\sin x -\sin p| \leq |x-p| <\delta =\epsilon$.

(g) $f:(0,1)\to\mathbb{R}$ defined by $f(x) =0 (x\not\in \mathbb{Q})$ or $f(x) = \frac{1}{n} (x\in \mathbb{Q}, x=\frac{m}{n} \text{ in lowest term}).$ 

<*proof*>
We want to show that $\displaystyle{\lim_{x\to p}f(x)=0}$ for all $p\in (0,1)$.

If $x\in (0,1)\setminus \mathbb{Q}, f(x)=0$. Now, suppose that $x=\frac{m}{n}$ (in lowest term). Take $n_0 \in \mathbb{N}$ such that $\frac{1}{n_0} < \epsilon$. <br /> Then there are finite numbers of rational numbers $\frac{m}{n}$ (in lowest term) with $n<n_0$. Denote these $r_1,\ldots, r_k\in \mathbb{Q}$ and 
$$
\begin{align}
\delta:=\min\{ |r_i-p|: r_i\neq p \text{ for }i=1,\ldots,k\}
\end{align}
$$
Then $\delta >0$. If $r\in \mathbb{Q}\cap(0,1)\cap N^\prime_\delta (p)$, then $r=\frac{m}{n}$ ( in lowest term) with $n\leq n_0$. <br /> $\therefore |f(x)|= \frac{1}{n} \leq \frac{1}{n_0} <\epsilon$ for $x\in \in \mathbb{Q}\cap(0,1)\cap N^\prime_\delta (p)$. <br /> $\therefore \displaystyle{\lim_{x\to p}f(x)=0}$ <br /> $\therefore f(x)$ is continuous at $p\not\in \mathbb{Q}$ but discontinuous at $p\in \mathbb{Q}$.
$$\tag*{$\square$}$$

## Theorem 4.2.3
$f,g: E\to\mathbb{R}$ is continuous at $p$.

1. $f\pm g$ is continuous at $p$.
2. $f\cdot g$ is continuous at $p$.
3. $f/g$ is continuous at $p$ $(g(x)\neq 0 \: \forall x \in E)$.

If $p$ is an isolated point of $E$, all the functions are continuous at $p$.

If $p$ is a limit point of $E$, the statements are true by Theorem 4.1.6
$$\tag*{$\square$}$$


## Theorem 4.2.4
$A,B\subset \mathbb{R}, f:A\to\mathbb{R}, g:B\to\mathbb{R}, \text{Range} f\subset B, f$ is continuous at $p$, and $g$ is continuous at $f(p)$. <br /> $\Rightarrow h=g\circ f$ is continuous at $p$.

<*proof*>
Let $\epsilon >0$ be given. Since $g$ is continuous at $f(p)$, $\exists \eta >0$ such that 
$$
\begin{align}
y\in N_\eta (f(p)) \cap B \Rightarrow g(y) \in N_\epsilon (g(f(p)))
\label{eq:1}
\end{align}
$$
Similarly, $f$ is continuous at $p, \exists \delta >0$ such that 
$$
\begin{align}
x\in N_\delta (p) \cap A \Rightarrow f(x) \in N_\eta (f(p))
\label{eq:2}
\end{align}
$$
Since $f(x)\in B$ for all $x\in A$ and by Equation $\ref{eq:1}$ and $\ref{eq:2}$,
$$
\begin{align}
\begin{split}
\forall x \in N_\delta (p) \cap A &\Rightarrow f(x) \in N_\eta (f(p)) \\
&\Rightarrow |g(f(x)) - g(f(p))| < \epsilon
\end{split}
\end{align}
$$
$\therefore h=g\circ f$ is continuous at $p$.
$$\tag*{$\square$}$$

## Theorem 4.2.6
$f:E\to\mathbb{R}$ is continuous on $E$. <br /> $\iff [\text{ For every open set }V  \Rightarrow f^{-1}(V) \text{ is open in } E.]$

<*proof*> <br />
$\Rightarrow$ Suppose that $f$ is continuous on $E$. Let $V$ be an open set and $p\in f^{-1}(V)$ be given. Then $f(p) \in V$. Since $V$ is open, there is $\epsilon >0$ s.t.  $N_{\epsilon} (f(p)) \subset V.$ Since $f$ is continuous on $E, \exists \delta >0$ s.t. 
$$
\forall x \in N_\delta (p) \Rightarrow f(x) \in N_\epsilon (f(p))
$$
Since $N_\epsilon (f(p)) \subset V, f(x)\in V$ for all $x\in N_\delta (p)\cap E$. <br /> $\therefore N_\delta (p) \cap E \subset f^{-1}(V)$.

$\Leftarrow$ Conversely, suppose that $f^{-1}(V)$ is open in $E$ for every open $V$ in $\mathbb{R}$. Let $\epsilon>0$ and $p\in E$ be given. Since every $\epsilon$ neighborhood is open,  $N_\epsilon (f(p))$ is open. <br /> By our assumption, $f^{-1}(N_\epsilon (f(p)))$ is open in $E$. So, there is a $\delta >0$ s.t. $N_\delta (p) \cap E \subset f^{-1}(N_\epsilon (f(p)))$. That is 
$$
\forall x\in N_\delta (p) \cap E \Rightarrow f(x) \in N_\epsilon (f(p)).
$$
$\therefore f$ is continuous at $p$. <br /> $\therefore f$ is continuous on $E$.
$$\tag*{$\square$}$$

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
