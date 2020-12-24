---
title: "Random Variable"

use_math: true
---



## Measurable function
Let $(E, \mathcal{E})$ and $(F, \mathcal{F})$ be measurable spaces where  $E,F,$ are sets and $\mathcal{E}$ and $\mathcal{F}$ are $\sigma$-field on $E$ and $F$, respectively. Then a function $f$ is measurable function if every pre-image of $B \in \mathcal{F}$ is measurable.

\begin{equation}  f^{-1}(B) \coloneqq \{ x \in E: f(x) \in B\}  \in \mathcal{E}\end{equation}

## Random variable
Let $(\Omega, \mathcal{A}, \mathbb{P})$  and $(E, \mathcal{E})$ be a probability space and measurable space, respectively.  A $\mathcal{A}/\mathcal{E}$ measurable function $X$ is a  *random variable*, satisfying the following:

\begin{equation}X^{-1}(B) = \{ \omega \in \Omega: X(\omega) \in B \} \in \mathcal{A}  \text{, for evey } B \in \mathcal{E}.\end{equation}

If we set $E  \coloneqq \mathbb{R}$, we take $\mathcal{E}$ to be the smallest $\sigma$-field, that contains   all the open subsets, which is called the *Borel $\sigma$-field*. 

## Distribution
Let $X$ be a random variable on measurable space $(E, \mathcal{E})$. The distribution of $X$ is defined as 

\begin{equation}\mu(A) \coloneqq  \mathbb{P}(X \in A) \coloneqq \mathbb{P}(X^{-1}(A))  = \mathbb{P}(\{ \omega \in \Omega: X(\omega)\in A\}).\end{equation}

The probability space $(\Omega, \mathcal{A}, \mathbb{P})$ is often called background probability space and the measure space $(E, \mathcal{E}, \mu)$ is called the *induced probability space*.
