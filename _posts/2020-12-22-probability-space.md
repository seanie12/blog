---
title: "Probability Space"

use_math: true
---


The sample space $\Omega$ is the set of all possible outcomes of an experiment. Points in $\omega \in \Omega$ are *outcomes* or *realizations*.
A subset $A \subset \Omega$ is called a event. We will assign a real number $\mathbb{P}(A)$ to every subset $A \subset \Omega$. We call $\mathbb{P}$ a *probability measure* if the set-function $\mathbb{P}$ satisfies the following three axioms.
1. $\mathbb{P}(A) \geq 0$ for every $A \subset \Omega$
2. $\mathbb{P}(\Omega) = 1$
3. If $A_1, A_2, \ldots,$ are disjoint then
\begin{align}
\mathbb{P}( \mathop{\cup}\limits_{i=1}^\infty A_i) = \sum\limits_{i=1}^\infty \mathbb{P}(A_i)
\end{align}

However, we cannot assign probabilites to all subsets of sample space $\Omega$. We need to define what is *measurable*.

Let $\Omega$ be a sample space. We call $\mathcal{A}$ a $\sigma$-field, if the followings are satisfied.
1. $\emptyset \in \mathcal{A}$,
2. $\mathcal{A}$ is closed under the countable union. i.e., if $A_1, \ldots, A_n \in \mathcal{A}$ then $ \mathop{\cup}\limits_{i=1}^\infty A_i \in \mathcal{A}$ and
3. $A \in \mathcal{A}$ implies that $\Omega \setminus A \in \mathcal{A}$.
The sets in $\mathcal{A}$ are said to be measurable and we call $(\Omega, \mathcal{A})$ a *measurable space*. If $\mathbb{P}$ is a probability measure defined on the $\sigma$-field $\mathcal{A}$, then $(\Omega, \mathcal{A}, \mathbb{P})$ is called a probability space.


## Reference
- All of Statistics: A Concise Course in Statistical Inference
