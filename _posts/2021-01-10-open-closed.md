---
title: "Open and closed set"

categories:
  - Analysis

tags:
  - open set
  - closed set
  - derived set
  - closure

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Definition 3.1.1
$E$ is a subset of $\mathbb{R}$. $p\in E$ is an *interior point* of $E$ if  there is $\epsilon >0$ such that $N_{\epsilon} (p) \subset E$.
$$\text{Int}(E) := \{\text{all interior points of } E\} \subset E$$

## Example 3.1.2
1. $E=[1,2)$, $\text{int}(E) = (1,2)$.
2. $E =\mathbb{R} \setminus \mathbb{Q}$, $\text{Int}(E) = \emptyset$.


## Definition 3.1.3
- $O \subset \mathbb{R}$ is *open* if $\text{Int}(O) = O.$
- $F \subset \mathbb{R}$ is *closed* if $F^c = \mathbb{R}\setminus F$ is open.

## Examples 3.1.4
(a) $\mathbb{R}$ is open and closed set. It is one of axioms in topology.

(b) Every $\epsilon$-neighborhood is open. (basis in topology)

<*proof*>
We want to show that $N_\epsilon (p)$ is open for every $p \in \mathbb{R}$.  Let $q \in N_\epsilon (p)$ be given. Define $\delta >0$ such that
$$\delta := \min\{ |p-q|, \epsilon - |p-q|\}.$$
For every $x \in N_\delta (q)$,
$$
\begin{align}
\begin{split}
|x-p| &\leq |x-q| + |p-q| \\
&< \delta + |p-q| \\
&\leq \epsilon-|p-q| + |p-q|\\
&=\epsilon
\end{split}
\end{align}
$$
$\therefore N_\delta (q) \subset N_\epsilon (p)$. i.e. $N_\epsilon (p)$ is open.
$$\tag*{$\square$}$$

## Theorem 3.1.6 
(a) $$\{O_\alpha \}_{\alpha \in \Lambda}: \text{ a family of open sets}\Rightarrow \cup_{\alpha \in \Lambda}O_\alpha \text{ is open.}  $$

(b) $$\{O_1, \ldots, O_n \}: \text{ a finite collection of open sets} \Rightarrow \cap_{i=1}^n O_i \text{ is open}.$$

<*proof*>
(a) Let $p\in \cup_{\alpha \in \Lambda}$ be given. Then $p \in O_\alpha$ for some $\alpha \in \Lambda.$ Since $O_\alpha$ is open, there exists $\epsilon>0$ such that $N_\epsilon (p) \subset O_\alpha.$ Since $O_\alpha \subset \cup_{\alpha \in \Lambda}, N_\epsilon (p) \subset O_\alpha \subset \cup_{\alpha \in \Lambda}O_\alpha.$

$\therefore p\in \text{Int}(\cup_{\alpha \in \Lambda}O_\alpha)$, i.e. $\cup_{\alpha \in \Lambda}$ is open.
$$\tag*{$\square$}$$

(b) Let $p \in \cap_{i=1}^nO_i$ be given. Then $p\in O_i$ for all $i=1, \ldots,n$. Since $O_i$ is open, there exists $\epsilon_i >0$ such that $N_{\epsilon_i}(p) \subset O_i$ for all $i=1,\ldots,n.$ Take $$\epsilon := \min\{\epsilon_1, \ldots, \epsilon_n \}.$$ Then $N_\epsilon (p) \subset N_{\epsilon_i} \subset O_i.$

$\therefore p\in \text{Int}(\cap_{i=1}^n O_i)$, i.e. $\cup_{i=1}^n O_i$ is open.
$$\tag*{$\square$}$$

## Theorem 3.1.7
(a) $$\{F_\alpha \}_{\alpha \in \Lambda} \text{ is a family of closed sets} \Rightarrow \cap_{\alpha \in \Lambda}F_\alpha \text{ is closed}.$$

(b)$$\{F_1, \ldots, F_n\} \text{ is a collection of closed sets} \Rightarrow \cup_{i=1}^n F_i \text{ is closed}.$$

<*proof*>
(a) Since $F^c$ is open for all $\alpha \in \Lambda$, $\cup_{\alpha \in \Lambda}$ is open, by de Morgan's law and Theorem 3.1.6.

$\therefore \cap_{\alpha \in \Lambda}F$ is closed.
$$\tag*{$\square$}$$

(b) Since $F^c$ is open for all $i=1, \ldots, n, \cap_{i=1}^n F^c_i =(\cup_{i=1}^nF_i)^c$ is open. 

$\therefore \cup_{i=1}^nF_i$ is open.

## Examples
- Intersection of infinite collection of open sets.
  Define a sequence of interval $I_n := (1-\frac{1}{n}, 1+\frac{1}{n}).$ Then $$\cap_{n=1}^\infty I_n=\{1\}$$, which is closed but not open set.

- Intersection of infinite collection of open sets.
  Define a sequence of interval $I_n :=(0, 1-\frac{1}{n}).$ Then $\cup_{i=n}^\infty I_n = (0, 1]$, which is not open nor closed set.

- Union of infinite collection of closed sets.
  Define a sequence of intervals $I_n :=[\frac{1}{n}, 2-\frac{1}{n}].$ Then $\cup_{n=1}^\infty I_n=(0,2)$, which is open but not closed set.

- Union of infinite collection of closed sets.
  Define a sequence of intervals $I_n :=[0, 2-\frac{1}{n}].$ Then $\cup_{n=1}^\infty I_n=[0,2)$, which is not open nor not closed set.


## Theorem 3.1.9
$F$ is a subset of $\mathbb{R}$. $F$ is closed set if and only if $F$ contains all the limit points of $F$.

<*proof*>
$\Rightarrow$ Suppose that $F$ is closed set, i.e. $F^c$ is open set. Let $p \in F^c$ be given. Then there exists $\epsilon >0$ such that $N_\epsilon (p) \subset F^c$, i.e. $N_\epsilon (p) \cap F = \emptyset$, which implies $N^\prime_\epsilon (p) \cap F = \emptyset$ because $p \in F^c.$ 
$\therefore p \text{ is not a limit point of } F, \text{i.e. }F \text{ contains all its the limit points.}$

$\Leftarrow$ Suppose that $F$ contains all limit points of $F.$ Let $p \in F^c$ be given. Since $p$ is not a limit point of $F$, there is $\epsilon>0$ such that $N^\prime_\epsilon (p) \cap F = \emptyset.$ Since $p \in F^c, N_\epsilon (p) \cap F=\emptyset.$ It implies that $N_\epsilon (p) \subset F^c$.
$\therefore p\in \text{Int}(F^c), \text{i.e. } F^c \text{ is open.}$

$\therefore F$ is closed.

$$\tag*{$\square$}$$

## Definition 3.1.10
$E$ is a subset of $\mathbb{R}.$
$$E^\prime :=\{\text{all limit points of }E \}$$ is called the *derived set* of $E$. 
$$\overline{E} := E \cup E^\prime$$ is the *closure* of $E$.

## Theorem 3.1.11
$E \subset \mathbb{R}$

(a) $\overline{E}$ is closed

(b) $\overline{E} = E \iff E$ is closed

(c) $\overline{E}$ is the smallest closed set containing $E$, i.e. $F$ is closed and $E\subset F \Rightarrow \overline{E} \subset F.$

<*proof*>
(a) Let $p \in \overline{E^c}$ be given. Then $p \notin E$ and $p$ is not a limit point of $E$. There is $\epsilon >0$ such that $N^\prime_\epsilon (p) \cap E = \emptyset.$ Since $p \notin E, N_\epsilon (p) \cap E = \emptyset.$ 

Now, we want to show that $N_\epsilon (p) \cap E^\prime = \emptyset.$  <br /> Suppose that $N_\epsilon (p) \cap E^\prime\neq \emptyset.$ Let $q \in N_\epsilon \cap E^\prime$ be given. Since $q$ is a limit point of $E$, we can take $\delta >0$ such that 
$$
\begin{align}
N^\prime_\delta (q) \cap E \neq \emptyset \text{ and } N_\delta \subset N_\epsilon (p).
\end{align}
$$ 
Such $\delta$ exists because $N_\epsilon (p)$ is an open set. Since $N_\delta (q) \subset N_\epsilon (p), N_\epsilon (p) \cap E \neq \emptyset.$ <br /> But it is a contradiction because $N_\epsilon (p) \cap E = \emptyset$.

$\therefore N_\epsilon (p) \cap E^\prime = \emptyset$

$\therefore \overline{E^c}$ is open, i.e. $\overline{E}$ is closed.

(b) $\Rightarrow$ Suppose that $\overline{E} = E$. Then $E^\prime\subset E$. Since $E$ contains all its limits points, $E$ is closed by Theorem 3.1.9.
$\Leftarrow$ Suppose that $E$ is closed. By Theorem 3.1.9, $E^\prime\subset E$.

$\therefore \overline{E} = E \cup E^\prime = E.$

(c) Let $F$ be a closed set and $E$ is a subset of $F$. Since $E \subset F$ and $F$ is closed, $E^\prime\subset F^\prime \subset F.$

$\therefore \overline{E} \subset F.$

$$\tag*{$\square$}$$

## Definition 3.1.12
$D$ is a subset of $\mathbb{R}$. $D$ is dense in $\mathbb{R}$ if $\overline{D} = \mathbb{R}$. For an instance, $\mathbb{Q}$ is dense in $\mathbb{R}$.




## Reference
- Manfred Stoll, **『**Introduction to Real Analysis**』**, Pearson
