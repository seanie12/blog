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
If the result is false, then $y$ is an upper bound of $A$. By the least upper bound property, we can get $\alpha = \sup A$. Now, since $x>0, \alpha-x < \alpha.$ It implies that $\alpha-x$ is not an upper bound of $A$ anymore. 

So, there is $m\in\mathbb{N}$ such that $\alpha -x < mx \in A$, i.e. $\alpha <(m+1)x \in A$. Thus, $\alpha$ is not an upper bound of $A$, which contradicts to our assumption.

$\therefore \exists n\in \mathbb{N}$ such that $nx > y$.

$$\tag*{$\square$}$$

## Remark
By Archimedean property, for any $\epsilon > 0$, there is $n_0 \in \mathbb{N}$ such that $\frac{1}{n_0}<\epsilon$. 

Then for any $n\geq n_0, \frac{1}{n}\leq \frac{1}{n_0}< \epsilon$.

## Theorem 1.5.2 (Density of $\mathbb{Q}$ in $\mathbb{R}$)
$\forall x,y \in \mathbb{R}, x<y \Rightarrow \exists r\in \mathbb{Q}$ such that $x<r<y$.

<*proof*>
Assume that $x\geq0$. Since $y-x>0$, there is $n\in\mathbb{N}$ s.t. $n(y-x) >1$ by Archimedean property. Define a set $A$ as follows:
$$
\begin{align}
A :=\{k\in \mathbb{N}: k >nx\}
\end{align}
$$
By Archimedean property, $A\neq \emptyset.$ By the well-ordering principle, we can take the smallest element $m \in \mathbb{N}$ such that $m-1 \leq nx <m$. 

$\Rightarrow nx < m \leq 1+nx < ny$, i.e. $nx < m < ny$.

$\therefore x<\frac{m}{n} < y$.

If $x < 0$ and $y>0$, then the result is obvious. 

Finally if $x<y<0$, then by the preceding calculations there exists $r\in\mathbb{Q}$ such that $-y< r < -x$, i.e. $x<-r<y$.

$$\tag*{$\square$}$$
## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
