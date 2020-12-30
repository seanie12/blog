---

title: "Probability Space"

categories:

  - Statistics

tags:

  - probability space

  

use_math: true
toc: true

---

  

  

The sample space $\Omega$ is the set of all possible outcomes of an experiment. Points in $\omega \in \Omega$ are *outcomes* or *realizations*.

A subset $A \subset \Omega$ is called a event. We will assign a real number $\mathbb{P}(A)$ to every subset $A \subset \Omega$. We call $\mathbb{P}$ a *probability measure* if the set-function $\mathbb{P}$ satisfies the following three axioms.

1. $\mathbb{P}(A) \geq 0$ for every $A \subset \Omega$

2. $\mathbb{P}(\Omega) = 1$

3. If $A_1, A_2, \ldots,$ are disjoint then

  

$$ \mathbb{P}( \mathop{\cup}\limits_{i=1}^\infty A_i) = \sum\limits_{i=1}^\infty \mathbb{P}(A_i) $$

  

  

However, we cannot assign probabilites to all subsets of sample space $\Omega$. We need to define what is *measurable*.

  

Let $\Omega$ be a sample space. We call $\mathcal{A}$ a $\sigma$-field, if the followings are satisfied.

1. $\emptyset \in \mathcal{A}$,

2. $\mathcal{A}$ is closed under the countable union. i.e., if $A_1, \ldots, A_n \in \mathcal{A}$ then $ \mathop{\cup}\limits_{i=1}^\infty A_i \in \mathcal{A}$ and

3. $A \in \mathcal{A}$ implies that $\Omega \setminus A \in \mathcal{A}$.

The sets in $\mathcal{A}$ are said to be measurable and we call $(\Omega, \mathcal{A})$ a *measurable space*. If $\mathbb{P}$ is a probability measure defined on the $\sigma$-field $\mathcal{A}$, then $(\Omega, \mathcal{A}, \mathbb{P})$ is called a probability space.

  

  

  

## Properties of probability

1. $\mathbb{P}(\emptyset) = 0$ and $0 \leq \mathbb{P}(A) \leq 1$ for all $A \in \mathcal{A}$

2. If $A \subset B$, then $\mathbb{P}(A) \leq \mathbb{P}(B)$

3. $\mathbb{P}(A_1 \cup A_2) = \mathbb{P}(A_1) + \mathbb{P}(A_2) - \mathbb{P}(A_1 \cap A_2)$

  

<*proof*>

1. Let $\Omega$ be a sample space. $\Omega = \cup_{i=1}^\infty A_i$ where $A_1 := \Omega$ and $A_j := \emptyset$ for $j \geq 2$.

$$\begin{align}
\begin{split}
\mathbb{P}(\Omega) &=\mathbb{P}( \cup_{i=1}^\infty A_i) \\
&= \sum_{i=1}^\infty \mathbb{P}(A_i) \\
&= \mathbb{P}(A_1) + \sum_{i=2}^\infty \mathbb{P}(A_i) \\
&= \mathbb{P}(\Omega) + \sum_{i=2}^\infty \mathbb{P}(A_i)  \\
\end{split}
\end{align}$$

By the cancellation law, $\sum_{i=2}^\infty \mathbb{P}(A_i) =0$. Since $\mathbb{P}(A) \geq 0$ for all $A \in \mathcal{A}$, $\mathbb{P}(A_j) = \mathbb{P}(\emptyset) = 0$ for $j \geq 2$.

$1= \mathbb{P}(\Omega) = \mathbb{P}(A) + \mathbb{P}(A^c)$. Thus, $\mathbb{P}(A^c) = 1 -\mathbb{P}(A) \geq 0$.

$\therefore 0 \leq \mathbb{P}(A) \leq 1$


  
  

2.  Suppose that $A\subset B$, where $A, B \in \mathcal{A}$. Since $B = A \cup (B\setminus A)$,  $\mathbb{P}(B) = \mathbb{P}(A) + \mathbb{P}(B\setminus A) \geq \mathbb{P}(A)$.


  

3. Since $A_1 \cup A_2  = (A_1 \setminus A_2) \cup (A_1 \cap A_2) \cup (A_2\setminus A_1)$,

$$\begin{align}
\begin{split}
\mathbb{P}(A_1 \cup A_2) &= \mathbb{P}(A_1 \setminus A_2) + \mathbb{P}(A_1 \cap A_2) + \mathbb{P}(A_2\setminus A_1) \\
&= \mathbb{P}(A_1 \setminus A_2) + \mathbb{P}(A_1\cap A_2) + \mathbb{P}(A_2 \setminus A_1) + \mathbb{P}(A_1 \cap A_2) - \mathbb{P}(A_1 \cap A_2) \\
&= \mathbb{P}(A_1) + \mathbb{P}(A_2) - \mathbb{P}(A_1 \cap A_2)
\end{split}
\end{align}$$

  

$$\tag*{$\square$}$$

## Reference

- All of Statistics: A Concise Course in Statistical Inference
