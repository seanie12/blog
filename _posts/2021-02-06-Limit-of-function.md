---
title: "Limit of function"

categories:
  - Analysis

tags:
  - limit of function
  - epsilon-delta
  - bounded
  
  

toc: true
toc_sticky: true

use_math : true
comments : true

---


## 4.1.1 Definition
$E \subset \mathbb{R}, f: E \rightarrow \mathbb{R}$: a function, $p \in E^\prime$.
$f$ has a **limit at p** if there exists $L\in \mathbb{R}$ such that $\forall \epsilon >0, \exists \delta >0$ s.t.
$$
\begin{align}
0 <|x-p|<\delta \:(\forall x \in E) \Rightarrow |f(x)-L| < \epsilon.
\end{align}$$
We write $\displaystyle{\lim_{x\to p}f(x) = L}$.


## Remark
- The definition does not consider the case when $x=p$.
- Why should $p$ be a limit point? 
  We want to guarantee the existence of  $x\in N^\prime_\delta (x) \cap E$.      Since every deleted neighborhood of $p$ contains infinitely many points of $E$,     there is such $x$ for every $\delta >0.$
 - $\displaystyle{\lim_{x\to p}f(x) \neq L} \iff \forall L \in \mathbb{R}, \exists \epsilon >0$ such that $\forall \delta >0, \exists x\in E$ 
   such that $0<|x-p|<\delta \text{ and } |f(x) - L| \geq \epsilon .$

## Examples 4.1.2
(a) $\displaystyle{\lim_{x\to p}c = c}$

$\because \forall \epsilon>0, \forall \delta >0, $
$0<|x-p|<\delta \Rightarrow |c-c| <\epsilon$

(b) $\displaystyle{\lim_{x\to p}x = p}$

$\because \forall \epsilon >0, \exists \delta >0$ such that 
$0<|x-p|<\delta \Rightarrow |x-p|<\epsilon$.  Take $\delta :=\epsilon$. 
Then, $0<|x-p|<\delta \Rightarrow |x-p|<\delta=\epsilon$.

(c) $\displaystyle{\lim_{x\to p}x^2 = p^2}$

<*proof*>
Let $\epsilon >0$ be given. We want to show that the existence of $\delta >0$ such that $0<|x-p|<\delta \Rightarrow |x^2-p^2| <\epsilon.$
Now we factorize $|x^2-p^2| = |x+p|\cdot |x-p|$. 
If $0<\delta \leq 1$,

$$
\begin{align}
\begin{split}
|x|-|p| \leq |x-p| &\leq \delta \\
|x| &< |p| + \delta \\
&\leq |p| + 1 \\
\end{split}
\end{align}
$$
Similarly, we can bound $|x+p|$ with triangular inequality,
$$
\begin{align}
\begin{split}
|x+p| &\leq |x| + |p| \\
&< 2|p| + \delta \\
&\leq 2|p| + 1
\end{split}
\end{align}
$$
Now, we take $\delta := \min (\frac{\epsilon}{2|p|+1}, 1)$. Then, 
$$
\begin{align}
|x+p||x-p| < (2|p|+1)\frac{\epsilon}{2|p|+1} = \epsilon
\end{align}
$$ 
$\therefore \displaystyle{\lim_{x\to p}}x^2 = p^2.$
 $$\tag*{$\square$}$$

(e) $f(x) = 1 \text{ if } x \in \mathbb{Q}, f(x) = 0 \text{ if } x \not\in \mathbb{Q}.$

$\displaystyle{\lim_{x\to p}f(x)}$ does not exist for every $p$.

<*proof*>
Let $L \in \mathbb{R}$ be given. Take $\epsilon := \max (|L-1|, |L|)$.
Then for any $\delta >0$, we can take $x \in \mathbb{Q}$ such that $0<|x-p| <\delta$ by the density of rational number. 
Thus $|f(x) - L| = |L-1| \leq \epsilon$.

Similarly, $\forall \delta >0$, we can take $x\in \mathbb{R}\setminus \mathbb{Q}$ such that $0<|x-p| <\delta$ by the density of irrational number. 
Thus, $|f(x) - L| = |L| \leq \epsilon$.
 $$\tag*{$\square$}$$

(f) $f(x) = 0 \text{ if } x \in \mathbb{Q}$ or $f(x) = x \text{ if } x \in \mathbb{R}\setminus \mathbb{Q}$.
$\displaystyle{\lim_{x\to 0} f(x)=0}$ and $\displaystyle{\lim_{x\to p} f(x)}$ does not exist for $\forall p\neq0.$

Let $\epsilon >0$ be given. Since $|f(x)| \leq |x| <\delta$, take $\delta := \epsilon$. Then $|f(x) < \epsilon$.
$\therefore \displaystyle{\lim_{x\to 0} f(x) = 0}$. 
$$\tag*{$\square$}$$
## Theorem 4.1.3
$E \subset \mathbb{R}, f: E\rightarrow \mathbb{R}, p \in E^\prime$.
$$
\begin{align}
\begin{split}
\lim_{x\to p}f(x) = L \iff &\lim_{n\to\infty} f(p_n) = L \\
&\text{for all seq } (p_n) \text{ with } p_n \rightarrow p \text{ as } n\rightarrow \infty \\
&\text{and } p_n \neq p
\end{split}
\end{align}
$$

<*proof*>
$\Rightarrow$ Suppose that $\displaystyle{\lim_{x\to p}f(x)=L}$. Let $\epsilon >0 $ be given.
Since $\displaystyle{\lim_{x\to p}f(x)=L}$, there is $\delta >0$, such that 
$0<|x-p| <\delta \Rightarrow |f(x)-L| <\epsilon.$
Since $p$ is a limit point, there exists a sequence $(p_n)$ with $p_n \rightarrow p$ as $n\rightarrow \infty$ 
and $p_n \neq p$. Let $(p_n)$ be any sequence satisfying such condition.
Since $p_n \rightarrow p$ as $n\rightarrow \infty$, there exists $N\in \mathbb{N}$ such that 
$n\geq N \Rightarrow 0<|p_n -p| <\delta (\because p_n \neq p)$. <br />
$\therefore |f(p_n) - L | <\epsilon$, i.e. $\displaystyle{\lim_{n\to\infty}f(p_n) = L}.$

$\Leftarrow$ Suppose that $\displaystyle{\lim_{x\to p} f(x) \neq L}.$
$\exists \epsilon >0$ such that $\forall \delta >0, \exists x \in E$, $0<|x-p|<\delta \text{ and } |f(x)-L| \geq \epsilon$.
Take $\delta := \frac{1}{n}$. Then there exists $p_n \in E$ such that 
$$
\begin{align}
0< |p_n-p|<\frac{1}{n} \text{ but } |f(p_n) - L | \geq \epsilon
\end{align}
$$
which contradicts to the assumption that $\displaystyle{\lim_{n\to\infty}f(p_n)=L}.$

$\therefore \displaystyle{\lim_{x\to p}f(x)=L}.$
 $$\tag*{$\square$}$$
## Corollary 4.1.4
$[f(x) \rightarrow L_1$ and $f(x) \rightarrow L_2$ as $x\rightarrow p] \Rightarrow [L_1 = L_2]$.

<*proof*>
By the previous theorem, for any seq. $(p_n)$ with $p_n \rightarrow p$ as $n\rightarrow \infty$ and $p_n \neq p$
$\Rightarrow \displaystyle{\lim_{n\to\infty}f(p_n)} = L_1 \text{ and } \displaystyle{\lim_{n\to\infty}f(p_n) = L_2}.$
Since the limit of sequence is unique, $L_1 = L_2$.
 $$\tag*{$\square$}$$

## Examples 4.1.5
(a) $E = (0, \infty), f(x) = \sin \frac{1}{x}$
If we take a sequence $p_n = \frac{(2n+1)\pi}{2}$, then $\sin \frac{1}{p_n} = (-1)^n$.

$\therefore \displaystyle{\lim_{x\to p}f(x)}$ does not exist for every $p \in \mathbb{R}$.

(b) $f(x) = 0 \text{ if } x \in \mathbb{Q}$ or $f(x) = x \text{ if } x \not\in \mathbb{Q}$.

Let $p \in \mathbb{R}$ and $p\neq 0$.
$\exists (p_n) \subset \mathbb{Q}$ s.t. $p_n \to p$ as $n\to\infty$ and $p_n \neq p$.
$\exists (q_n) \subset \mathbb{R}\setminus\mathbb{Q}$ s.t. $q_n \to p$ as $n\to\infty$ and $q_n \neq p$.
$(\because$ For every $n\in \mathbb{N}$, take $p_n \in \mathbb{Q}$ or $q_n \in \mathbb{R}\setminus \mathbb{Q}$  $p_n, q_n \in (p, p+\frac{1}{n})$.
By the density of rational/irrational numbers, we can construct such sequences.)
$$
\begin{align}
\begin{split}
0<|p_n -p| <\delta &\Rightarrow f(p_n) = 0 \to 0 \\
0< |q_n -p| <\delta &\Rightarrow f(q_n) =q_n \to 0
\end{split}
\end{align}
$$
Since $q_n \to p$ and $q_n \to 0$, $p=0$. But it is contradiction.
 $$\tag*{$\square$}$$

## Theorem 4.1.6
$E\subset \mathbb{R}, f,g: E \rightarrow \mathbb{R}, p\in E^\prime$
$\displaystyle{\lim_{x\to p}f(x)=A, \lim_{x\to p}g(x) = B}$.

(a) $\displaystyle{\lim_{x\to p}(f(x) + g(x))} = A+B$

(b) $\displaystyle{\lim_{x\to p}(f(x) \cdot g(x))} = A\cdot B$

(c) $\displaystyle{\lim_{x\to p}\frac{f(x)}{ g(x)}} = \frac{A}{B}$

<*proof*>
(a) Since $f(x) \to A$ as $x\to p$ and $g(x)\to B$ as $x\to p$.
Let $(p_n)$ be a sequence with $p_n \to p$ as $n\to \infty$ and $p_n \neq p$.
Thus,
$$
\begin{align}
\lim_{n\to\infty}f(p_n)=A, \lim_{n\to\infty}g(p_n)=B
\end{align}$$
$\therefore \displaystyle{\lim_{n\to\infty}(f(p_n) + g(p_n)) = A+B}$

$\therefore \displaystyle{\lim_{x\to p}(f(x) + g(x))= A + B}$
$$\tag*{$\square$}$$

(b) Similarly, we can prove it.

(c) It is enough to show that $\displaystyle{\lim_{x\to p}\frac{1}{g(x)}} = \frac{1}{B}$

<*proof*>
Since $\displaystyle{\lim_{x\to p}g(x) = B}$,
$$
\begin{align}
\exists \delta_1 >0 \text{ s.t. } 0<|x-p|<\delta_1 \Rightarrow |g(x) - B| <\epsilon
\end{align}
$$
Take $\epsilon := \frac{|B|}{2}$. Then,
$$
\begin{align}
|B| - |g(x)| \leq |g(x) - B| < \frac{|B|}{2}
\end{align}
$$
$\therefore |g(x)| > \frac{|B|}{2}$ for  $0<|x-p|<\delta_1$.

Let $(p_n)$ be a sequence with $p_n \to p$ as $n\to \infty$ and $p_n \neq p$.
Then there is $N \in \mathbb{N}$ such that
$$
\begin{align}n\geq N \Rightarrow 0<|p_n -p| <\delta_1.
\end{align}$$

So, $g(p_n)\to B$ as $n\to \infty$. i.e. $\frac{1}{g(p_n)} \to \frac{1}{B}$ as $n\to \infty$.

$\therefore \displaystyle{\lim_{n\to\infty}\frac{1}{g(p_n)}=\frac{1}{B}}.$

$\therefore \displaystyle{\lim_{x\to p}\frac{1}{g(x)}=\frac{1}{B}}.$


## Definition 4.1.7
$f:E\to \mathbb{R}$ is **bounded** if $\exists M\in \mathbb{R}$ such that $|f(x)| \leq M$ for all $x\in E$.

## Theorem 4.1.8
$f:E\to\mathbb{R}, p\in E^\prime, g:E\to\mathbb{R}$ is bounded and $\displaystyle{\lim_{x\to p}f(x)} = 0$.

$\Rightarrow \displaystyle{\lim_{x\to p}f(x)g(x)} = 0$

<*proof*>
Let $\epsilon >0$ be given. Since $f(x)\to 0$ as $x\to p$, there exist $\delta >0$ such that $|f(x)|<\epsilon$, whenever $0<|x-p|<\delta, x\in E$. Since $g$ is bounded, there is a constant $M$ such that $|g(x)|\leq M$ for all $x\in E$.

If $0<|x-p|<\delta, x\in E$, then $|f(x)g(x)| = |f(x)| |g(x)| < \epsilon$.
<br />$\therefore \displaystyle{\lim_{x\to p}f(x)g(x)}$
$$\tag*{$\square$}$$

## Theorem 4.1.9
$f,g,h: E\to \mathbb{R}, p\in E^\prime$

Suppose that $g(x)\leq f(x)\leq h(x)$ for all $x\in E$. 

If $\displaystyle{\lim_{x\to p}g(x)=L=\lim_{x\to p}h(x)}$, then $\displaystyle{\lim_{x\to p}f(x)=L}$.

<*proof*>
Let $\epsilon >0$ be given. Since $\displaystyle{\lim_{x\to p}g(x) = L = \lim_{x\to p}h(x)}$, there exists $\delta >0$ such that $0<|x-p|<\delta, x\in E \Rightarrow L-\epsilon < g(x), h(x)<L +\epsilon$.

Since $g(x)\leq f(x) \leq h(x)$ for all $x\in E$, we have 
$$
\begin{align}
L-\epsilon < g(x) \leq <f(x) \leq h(x) <L+\epsilon
\end{align}
$$
if $0<|x-p|<\delta, x\in E$, i.e. $\displaystyle{\lim_{x\to p}f(x) =L}.$
$$\tag*{$\square$}$$

## Examples 4.1.10
$p(x):= a_n x^n + a_{n-1}x^{n-1} + \cdots + a_1 x + a_0$, where $a_n \neq 0$. We call it polynomial function of degree $n$.

$$
\lim_{x\to c} p(x) = a_n c^n + \cdots + a_0 = p(c)
$$

## Definition 4.1.11
$f$ is real-valued function such that $\text{Dom}f \cap (a,\infty)\neq \emptyset$ for all $a\in \mathbb{R}$. <br />
The function $f$ has a **limit at $\infty$** if $\exists L\in \mathbb{R}$ such that $$\forall \epsilon >0, \exists M\in \mathbb{R} \text{ s.t. } x\in \text{Dom}f \cap (M,\infty)\neq \emptyset \Rightarrow |f(x)-L|<\epsilon.$$ <br />
We write $\displaystyle{\lim_{x\to\infty}f(x)=L}.$


## Examples 4.1.12
(a) $f(x)= \frac{\sin x}{x}$ for all $x\in (0,\infty)$.

Since, $|\sin x|\leq 1$, $|f(x)|\leq \frac{1}{x}$ for all $x\in (0,\infty)$. Let $\epsilon >0$ be given. Take $M :=\frac{1}{\epsilon}$. If $x>\frac{1}{\epsilon}$, then $\frac{1}{x} <\epsilon$.
$$
|f(x)| \leq \frac{1}{x} < \epsilon, \text{ for all }x > \frac{1}{\epsilon}=M
$$
<br />
$\therefore \displaystyle{\lim_{x\to\infty}\frac{\sin x}{x}=0}$

(b) $f(x) = x\sin \pi x$

Put $p_n :=(n+\frac{1}{2})$. Then $\sin \pi (p_n) = \sin(\frac{2n+1}{2})\pi = (-1)^n,$ i.e. $f(p_n) = (n+\frac{1}{2})\cdot (-1)^n.$  <br /> Since $\displaystyle{\lim_{x\to\infty}f(p_n)}$ does not exist, $\displaystyle{\lim_{x\to\infty}f(x)}$ does not exist.


## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
