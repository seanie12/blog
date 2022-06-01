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
  - root
  
  

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition (Ordered Set)
Let $S$ be a set.  An *order* on $S$ is a relation, denoted by $<$, with the following property

(1) If $x\in S$ and $y\in S$,  then only one of the statements hold true

$$
\begin{equation*}
x<y,\quad x=y, \quad y<x
\end{equation*}
$$

(2) If $x,y,z\in S$, if $x<y$ and $y<z$, then $x<z$. 

An ordered set is a set $S$ which is an order is defined.
## Definition 1.4.1
Let $S$ be an ordered set.
$E\subset S$ is bounded above if and only if $\exists \beta\in S$ such that $x\leq \beta$ for all $x\in E$. We call $\beta$ as an upper bound of $E$.

Similarly, $E$ is bounded below if and only if $\exists \beta\in S$ such that $x\geq \beta$ for all $x\in E$. We call $\beta$ as lower bound of $E$.

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
$$\tag*{$\square$}$$

## Definition 1.4.3
$\emptyset \neq E\subset \mathbb{R}$ is bounded above. $\alpha\in \mathbb{R}$ is called the **least upper bound** or **supremum** of $E$ if
1. $\alpha$ is an upper bound of $E$
2. $\beta$ is another upper bound of $E \Rightarrow \alpha \leq \beta$

We write $\alpha =\sup E$. 


## Definition 1.4.3-1
$\emptyset \neq E\subset \mathbb{R}$ is bounded below. $\alpha\in \mathbb{R}$ is called the **greatest lower bound** or **infimum** of $E$ if
1. $\alpha$ is an lower bound of $E$
2. $\beta$ is another lower bound of $E \Rightarrow \alpha \geq \beta$

We write $\alpha =\inf E$. 

## Theorem 1.4.4
$\emptyset \neq E \subset \mathbb{R}$ is bounded above. An upper bound $\alpha \in \mathbb{R}$ of $E$ is the supremum of $E$

if and only if $\forall \beta <\alpha, \exists x\in E$ s.t. $\beta < x \leq \alpha$.

<*proof*>

$\Rightarrow$
Suppose that $\alpha = \sup E$. Let $\beta <\alpha$ be given. Then $\beta$ is not an upper bound of $E$. So, there is $x\in E$ such that $\beta < x$. Since $\alpha$ is an upper bound of $E, x\leq \alpha.$ 

$\Leftarrow$
Suppose that $\forall \beta < \alpha, \exists x\in E$ such that $\beta <x \leq \alpha$. We want to show that 
$$
\begin{align}
\alpha = \sup E \iff \alpha \leq y \text{ for any }y: \text{ upper bound of }E
\end{align}
$$
Let $y$ be another upper bound of $E$. Suppose that $y <\alpha$. By our assumption, there is $x\in E$ such that $y <x\leq \alpha$. However, it implies that $y$ is not upper bound anymore, which is a contradiction.

$\therefore \alpha \leq y$

$\therefore \alpha = \sup E$
$$\tag*{$\square$}$$
### Axiom 1.4.6 (Least upper upper bound property - completeness)
Every non-empty bounded above subset of $\mathbb{R}$ has a supremum in $\mathbb{R}$.

## Theorem 
Let $S$ be an ordered set with the least upper bound property.  Then $S$ has the least upper bound property.

<*proof*>

Let $B \subset S$ be an non-empty bounded below set. Let 

$$
\begin{equation*}
L=\{y\in S\mid y\leq x, \forall x \in B \}
\end{equation*}
$$ 
be a set of lower bounds of the set $B$. Since every $x\in B$ is an upper bound of $L$, $L$ is bounded above. By the least upper bound property, there exists $\sup L \in S$. 

Now, we want to show that 
$$
\begin{equation*}
\inf B = \sup L.
\end{equation*}
$$
Let $\gamma < \sup L$ be given. Since $\gamma$ is not an upper bound of $L$ anymore, $\gamma \notin B$. By contraposition,  if $x\in B$, then $\sup L \leq x$. Thus, $\sup L$ is a lower bound of $B$. By the definition of $\sup L$, $\sup L$ is the greatest among the lower bounds of $B$.

$$\tag*{$\square$}$$


## Definition 1.4.9
If $E$ is not bounded above, define $\sup E:= \infty$.

If $E$ is not bounded below, define $\inf E:= -\infty$.

$\sup \emptyset := -\infty, \inf \emptyset := \infty$.

## Definition 1.4.11
$J\subset \mathbb{R}$ is an interval if 
$$
\begin{align}
\forall x,y \in J \text{ with }x<y, \exists t\in J \text{ s.t. } x<t<y.
\end{align}
$$ 
Note that $\emptyset$ and singleton set are also intervals.

## Theorem 1.5.1 (Archimedean Property)
$x,y\in \mathbb{R}, x>0 \Rightarrow \exists n\in \mathbb{N}$ such that $nx >y$.

<*proof*>

If $y\leq 0$, take $n=1$.

Assume that $y>0$. Define a set $A$ as follows:
$$
\begin{align}
A:=\{nx: n\in \mathbb{N}\} \neq \emptyset
\end{align}
$$
Suppose that $nx\leq y$ for all $n\in\mathbb{N}$. In other words, $y$ is an upper bound of $A$. By the least upper bound property, there is $\alpha = \sup A \in \mathbb{R}$. Now, since $x>0, \alpha-x < \alpha.$ It implies that $\alpha-x$ is not an upper bound of $A$ anymore. 

So, there is $m\in\mathbb{N}$ such that $\alpha -x < mx \in A$, i.e., $\alpha <(m+1)x \in A$. Thus, $\alpha$ is not an upper bound of $A$, which contradicts to our assumption.

$\therefore \exists n\in \mathbb{N}$ such that $nx > y$.

$$\tag*{$\square$}$$

## Remark
By Archimedean property, for any $\epsilon > 0$, there is $n_0 \in \mathbb{N}$ such that $\frac{1}{n_0}<\epsilon$. 

Then for any $n\geq n_0, \frac{1}{n}\leq \frac{1}{n_0}< \epsilon$.

## Theorem 1.5.2 (Density of $\mathbb{Q}$ in $\mathbb{R}$)
$\forall x,y \in \mathbb{R}, x<y \Rightarrow \exists r\in \mathbb{Q}$ such that $x<r<y$.

(1) <*proof*>

Since $y-x>0$, there is $n\in\mathbb{N}$ s.t. $n(y-x) >1$ by Archimedean property. Define a set $A$ as follows:
$$
\begin{align}
A :=\{k\in \mathbb{N}: k >nx\}
\end{align}
$$
By Archimedean property, $A\neq \emptyset.$ By the well-ordering principle, we can take the smallest element $m =\min A\in \mathbb{N}$. Then $m-1 \leq nx <m$. 

$\Rightarrow nx < m \leq 1+nx < ny$, i.e. $nx < m < ny$.

$\therefore x<\frac{m}{n} < y$.

(2) <*proof*>

Since $y-x>0$, there exists $n\in\mathbb{N}$ such that $n(y-x) >1$ by Archimedean property. Similarly there exists $m_1, m_2\in\mathbb{N}$ such that

$$
\begin{align*}
m_1 \cdot 1 &> nx\\
m_2 \cdot 1 &> -nx
\end{align*}
$$
So, $-m_2 < nx < m_1$. Let define a set 

$$
\begin{equation*}
A = \{k\in\mathbb{Z}\mid nx < k \leq m_1\}.
\end{equation*}
$$

Since the $A$ is finite, we can take a minimum of it, denoted as $m=\min A$. Then $m-1 \leq nx$ and $nx < m$. Combining all together,  we get

$$
\begin{equation*}
nx < m \leq nx+1<ny.
\end{equation*}
$$ 

Thus, 

$$
\begin{equation*}
x < \frac{m}{n} < y.
\end{equation*}
$$

$$\tag*{$\square$}$$


## Lemma
Let $0<a<b$ be given. Then $b^n - a^n<(b-a)nb^{n-1}$ for any $n\in \mathbb{N}$ with $n>1$.

<*proof*>

$$
\begin{align*}
b^n - a^n &= (b-a)(b^{n-1}+ab^{n-2}+\cdots + a^{n-2}b+a^{n-1})\\
&<(b-a)(b^{n-1}+b^{n-1} + \cdots + b^{n-1} + b^{n-1}) \\
&=(b-a)nb^{n-1}
\end{align*}
$$

The first inequality holds since $0<a<b \Rightarrow 0<a^k <b^k$ for any $k\in\mathbb{N}$.
$$\tag*{$\square$}$$

## Theorem 
Let $x\in\mathbb{R}$ with $x>0$ be given. Then there exists a unique $y\in\mathbb{R}$ such that $y^n = x$ and $y>0$.

<*proof*>

Define a set 

$$
\begin{equation*}
A = \{a\in\mathbb{R} \mid a> 0, a^n < x \}.
\end{equation*}
$$

If $t = \frac{x}{x+1}$, then $0<t<1$ and $t<x$. Since $0<t<1$, $0<t^n<t<x$. Thus $t\in A$, i.e., $A\neq \emptyset$. Suppose that $t>x+1$. Since $t>1$, $t^n>t>x$, i.e., $t\notin A$.  By contraposition, $t\in A \Rightarrow t\leq x+1$, i.e., $A$ is not bounded above. By the least upper bound property, there is $y=\sup A\in\mathbb{R}$. We want to show that $y^n = x$ by contradiction.

(1) Suppose that $y^n < x$.  We want to find $h>0$ such that $(y+h)^n < x$. If there is such $h$, then $y+h\in A$, but $y<y+h$, which contradicts to the assumption that $y=\sup A$ which should be greater than or equal to $y+h$.

We  want to find $h>0$ such that $(y+h)^n < x$. It is equivalent to $(y+h)^n - y^n < x -y^n$. By Lemma, we get

$$
\begin{equation}
(y+h)^n - y^n < h^nn(y+h)^{n-1}.
\end{equation}
\label{eq:7}
$$  

Instead, we find $h>0$ such that $h^nn(y+h)^{n-1}<y-x^n$. Moreover, if $0<h<1$, we get the following inequality

$$
\begin{align}
0<h < \frac{x-y^n}{n(y+1)^{n-1}} < \frac{x-y^n}{n(y+h)^{n-1}}.
\label{eq:8}
\end{align}
$$

By the density of $\mathbb{Q}$, we can find such $h$.

Now, let $h\in (0,1)$ such that 

$$
\begin{equation*}
0<h < \frac{x-y^n}{n(y+1)^{n-1}}. 
\end{equation*}
$$

By Equation $\ref{eq:7}$ and $\ref{eq:8}$, 

$$
\begin{equation*}
(y+h)^n - y^n < nh(y+h)^{n-1}< x-y^n.
\end{equation*}
$$

That is $(y+h)^n < x$, i.e., $y+h\in A$ and $y+h >y=\sup A$. It is a contradiction to the assumption.

 
(2) Let $y=\sup A$ and  suppose that $y^n >x$. Let $h\in (0,y)$ such that 

$$
\begin{equation}
0<h<\frac{y^n-x}{ny^{n-1}}.
\label{eq:9}
\end{equation}
$$

By Lemma and Equation  $\ref{eq:9}$,

$$
\begin{align*}
y^n-(y-h)^n < hn(y-h)^{n-1} < y^n-x.
\end{align*}
$$

That is $(y-h)^n >x$ and $t<y-h$ for all $t\in A$. In other words, $y-h$ is an upper bound of $A$ but less than $y=\sup A$, which is a contradiction.

(3) Uniqueness. Let $y_1, y_2 >0$ such that $y^n_1 = y^n_2=x$. Suppose that $y_1 > y_2$. Then $y^n_1 > y^n_2$, which is a contradiction. Thus, $y_1= y_2$.
$$\tag*{$\square$}$$

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**.
- Walter Rudin, **『**The Principles of Mathematical Analysis**』**.
