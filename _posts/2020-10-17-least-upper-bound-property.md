---
title: "Least Upper Bound Property"

categories:
  - Analysis


tags:
  - supremum
  - infimum
  - completeness
  - Archimedean property
  - dense
  
  

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 1.4.1
$E\subset \mathbb{R}$ is bounded above if and only if $\exists \beta\in \mathbb{R}$ such that $x\leq \beta$ for all $x\in E$. We call $\beta$ as an upper bound of $E$.

Similarly, $E$ is bounded below if and only if $\exists \beta\in\mathbb{R}$ such that $x\geq \beta$ for all $x\in E$. We call $\beta$ as lower bound of $E$.

$E$ is bounded if and only if $E$ is bounded below and above.

## Examples 1.4.2
1. $\mathbb{N}$ is bounded below because 1 is a lower bound, but not bounded above.
2. Define a set $E$ as follows:
$$
\begin{align}
E:=\{r\in \mathbb{Q}: r>0, r^2 <2\}
\end{align}
$$

  $E$ is bounded but $E$ has no maximum.
  $\because \forall p\in E,$ define $q:= p+ \frac{2-p^2}{p+2} = \frac{2p+2}{p+2}.$
  $$
  \begin{align}
\begin{split}
  q^2- 2 &= (\frac{2p+2}{p+2})^2 -2\\
  &=\frac{4p^2+8p+4-2p^2-8p-8}{(p+2)^2} \\
  &=\frac{2(p^2-2)}{(p+2)^2} <0
  \end{split}
  \end{align}
  $$
  $\therefore q\in \mathbb{Q}, q>p, q^2 <2$
  $\therefore q\in E$ but $q>p$
  $\therefore E$ has no maximum  


## Definition 1.2.1 
Let $A,B$ be subsets of $\mathbb{R}$. $f:A\to B$ is a function if 
$$
\begin{align}\forall x\in A, \exists ! y\in B \text{ such that } y=f(x).
\end{align}$$

## Definition 1.2.2
$f: A\to B$ is a function.
$$
\begin{align}
\begin{split}
f \text{ is injective } &\iff [f(x_1)=f(x_2) \Rightarrow x_1 = x_2 ]\\
&\iff \forall y \in f(A), \exists ! x\in A \text{ s.t. } y= f(x) 
\end{split}
\end{align}
$$

## Definition 1.2.3
$f: A\to B$ is a function.
$$
\begin{align}
\begin{split}
f \text{ is surjective } &\iff f(A) = B\\
&\iff \forall y \in B, \exists  x\in A \text{ s.t. } y= f(x) 
\end{split}
\end{align}
$$

## Definition 1.2.4
$f: A\to B$ is a function. If $f$ is bijective if and only if the function is injective and surjective. 

## Theorem 1.2.5
$f:A\to B$ is a function and $A_1, A_2 \subset A$.

(a) $f(A_1\cup A_2) = f(A_1) \cup f(A_2)$

(b) $f(A_1 \cap A_2) \subset f(A_1)\cap f(A_2)$ 

(c) $f$ is injective $\Rightarrow f(A_1) \cap f(A_2) \subset f(A_1 \cap A_2)$ 

<*proof*>

**(a)**
Let $y \in f(A_1 \cup A_2)$ be given. Then $y= f(x)$ for some $x\in A_1 \cup A_2.$ So $y=f(x)$ for some $x\in A_1$, which is equivalent to $y\in f(A_1)$, or $y=f(x)$ for some $x\in A_2$, which is equivalent to $y\in f(A_2)$.

$\therefore y\in f(A_1) \cup f(A_2)$

Conversely, let $y\in f(A_1) \cup f(A_2)$ be given. If $y\in f(A_1)$, then $y=f(x)$ for some $x\in A_1$. Since $A_1\subset (A_1\cup A_2), x\in A_1\cup A_2$. 

$\therefore f(x) \in f(A_1\cup A_2)$.

If $y\in f(A_2)$, then $y=f(x)$ for some $x\in A_2$. Since $A_2\subset (A_1\cup A_2), x\in A_1\cup A_2$. 

$\therefore f(x) \in f(A_1\cup A_2)$.

$\therefore f(A_1\cup A_2) = f(A_1) \cup f(A_2)$

**(b)**
Let $y\in f(A_1\cap A_2)$ be given. Then $y=f(x)$ for some $x\in A_1$ and $x\in A_2$. Thus, $y=f(x) \in f(A_1)$ and $y=f(x) \in f(A_2)$.

$\therefore f(A_1 \cap A_2) \subset f(A_1) \cap f(A_2).$

**(c)**
Let $y\in f(A_1)\cap f(A_2)$ be given. Then for the same $y, y=f(x_1)$ for some $x_1 \in A_1$ or $y=f(x_2)$ for some $x_2 \in A_2$. 

Since $f$is bijective, $x_1=x_2=x\in A_1\cap A_2$, i.e. $y=f(x)$ for some $x\in A_1\cap A_2$.

$\therefore y\in f(A_1 \cap A_2)$

$$\tag*{$\square$}$$

## Theorem 1.2.6
$f:A\to B$ is a function, $B_1,B_2 \subset B$.

(a) $f^{-1}(B_1\cup B_2) = f^{-1}(B_1)\cup f^{-1}(B_2)$
(b) $f^{-1}(B_1\cap B_2) = f^{-1}(B_1)\cap f^{-1}(B_2)$

where $f^{-1}(B_1)$  is preimage defined as follows:
$$
\begin{align}
f^{-1}(B_1) := \{ x\in A| f(x)\in B_2 \}
\end{align}
$$

<*proof*>

(a) 
$$
\begin{align}
\begin{split}
f^{-1}(B_1\cup B_2) &= \{x\in A: f(x) \in B_1\cup B_2 \} \\
&=\{x\in A: f(x)\in B_1 \text{ or } f(x)\in B_2 \} \\
&=\{x\in A: x\in f^{-1}(B_1) \text{ or } x\in f^{-1}(B_2)\} \\
&=\{x\in A: x\in f^{-1}(B_1) \cup f^{-1}(B_2) \}
\end{split}
\end{align}
$$

(b)
$$
\begin{align}
\begin{split}
f^{-1}(B_1\cap B_2) &= \{x\in A: f(x)\in B_1\cap B_2\}\\
&=\{x\in A: f(x)\in B_1 \text{ and } f(x)\in B_2 \} \\
&= \{x\in A: x\in f^{-1}(B_1) \text{ and } x\in f^{-1}(B_2) \} \\
&=\{x\in A: x\in f^{-1}(B_1)\cap f^{-1}(B_2) \}
\end{split}
\end{align}
$$
$$\tag*{$\square$}$$

## Remark (Well-ordering principle)
Every nonempty subset of $\mathbb{N}$ has a smallest element.

## Theorem 1.3.1 
For each $n\in \mathbb{N}$, let $p(n)$ be a statement about $n$.
If

(a) $p(1)$ is true, and

(b) $p(k)$ is true $\Rightarrow p(k+1)$ is true

then $p(n)$ is true for all $n\in \mathbb{N}$.

<*proof*>
Suppose that $p(n)$ is false for some $n\in\mathbb{N}$. If we set
$$
\begin{align}
A:=\{k\in \mathbb{N}: p(k) \text{ is false} \}
\end{align}
$$ 
then $A$ is a nonempty subset of $\mathbb{N}.$ By the well-ordering principle, there is the smallest element $k_0 \in A, k_0 \geq 2$. Since $k_0$ is the smallest element of $A$, $p(k_0 -1)$ is true. By our assumption, however, $p(k_0)$ is also true, which is a contradiction.

$\therefore p(n)$ is true for all $n\in\mathbb{N}$.
$$\tag*{$\square$}$$

## Examples 1.3.3
(a) $p(n) = r+r^2+\cdots + r^{n-1} +r^n=\frac{r(1-r^n)}{1-r}$, where $r\neq 1$.

(b) (Bernoulli's inequality): $p(n): h >-1, (1+h)^n \geq 1+ nh$.

<*proof*>

(a) For $n=1$, $p(1) = r = \frac{r(1-r)}{1-r}$. Assume that the statement holds true for $n=k-1$.  
$$
\begin{align}
\begin{split}
p(k) &= 1+ r^2 + \cdots + r^{k-1} + r^{k} \\
&=p(k-1) + r^k \\
&=\frac{r(1-r^{k-1})}{1-r} + r^k \\
&=\frac{r(1-r^{k-1})+ r^k(1-r)}{1-r} \\
&=\frac{r-r^k+r^k-r^{k+1}}{1-r}  \\
&=\frac{r-r^{k+1}}{1-r}  \\
&=\frac{r(1-r^{k})}{1-r}
\end{split}
\end{align}
$$
Thus, $p(k)$ holds. 

$\therefore$ By the mathematical induction $p(n)$ is always true. 

(b) For $n=1$, the left hand side is $(1+h)^1 = 1+h$ and the right hand side is $1+1\cdot h=1+h$.

Assume that $p(k) = (1+h)^k \geq 1+k\cdot h$ is true.
$$
\begin{align}
\begin{split}
(1+h)^{k+1} &= (1+h)(1+h)^k \\
&\geq (1+kh)(1+h) \\
&=1+h+kh+kh^2 \\
&\geq 1+(k+1)h
\end{split}
\end{align}
$$
Thus, $p(k+1)$ holds.

$\therefore$ By the mathematical induction, $p(n)$ is always true.

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
