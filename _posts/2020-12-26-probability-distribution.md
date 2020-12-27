---
title: "Distribution Function"

categories:
  - Statistics

tags:
  - random variable
  - distribution function
  - density function
  - mass function

use_math : true
---

## Distribution Function
Let $X$ be a random variable on $(\mathbb{R}, \mathcal{B}(\mathbb{R}), \mu)$. The distribution function (cumulative distribution function) of $X$ is defined as 

$$F(x) := \mu((-\infty, x]) = \mathbb{P}(X^{-1}((-\infty,x])) = \mathbb{P}(X \leq x) $$

## Probability density function
If $F(x)$ can be written as 
$$F(x) = \int_{-\infty}^x f(x) dx$$
$f(x)$ is called the density or probability density function of $X$ with respect to Lebesgue measure.

## Probability mass function
Let $(\Omega, \mathcal{A}, \mathbb{P})$ be a probability space and $(B, \mathcal{B})$  be a measurable space whose underlying $\sigma$-field is discrete. If $X:\Omega \rightarrow B$ is discrete provided its preimage is discrete, the probability mass function $f_X$ is defined as follows:
$$f_X(x_i) := \mathbb{P}(X=x_i) = \mathbb{P}(\{\omega\in\Omega: X(\omega) = x_i \})$$

## $\sigma$-finite measure
Let $(E, \mathcal{E}, \mu)$ be a measurable space. $\mu$ is said to be $\sigma$-finite if $E$ can be covered with  at most countable many measurable sets with finite measure. 
$$\cup_{n\in \mathbb{N}} A_n = E \text{ and } \mu(A_n) < \infty \text{ for all } n\in \mathbb{N} $$ 

One of examples is Lebesgue measure. Consider Lebesgue measure on $\mathbb{R}$. It is $\sigma$-finite. For all integer $k$, define an interval $I_k := [k, k+1)$. Then $\mathbb{R} = \cup_{k\in\mathbb{Z}} I_k$ since the set of integers $\mathbb{Z}$ is countable.

## Absolute continuity
Let $\mu$ and $\nu$ be a measure on a measurable space $(E, \mathcal{E})$. $\mu$ is said to be absolute continuous with respect to $\nu$ if for any $A \in \mathcal{E}$,

$$ \nu(A) = 0 \Longrightarrow  \mu(A) = 0$$
and denote $\mu \ll \nu$.

## Counting measure
Let $(E, \Sigma)$ be a measurable space where the $\sigma$-field $\Sigma$ is the power set of $E$. Then we define counting measure $\mu: \Sigma \rightarrow [0, +\infty]$ for all $A \in \Sigma$ as follows:
$$\mu(A)  = \begin{cases} |A|  \quad \text{ if } A \text{ is finite}\\
+\infty \quad\text{otherwise} \end{cases}$$


## Radon-Nikodym derivate
Let $\mu$ and $\nu$ be two measures on measurable space $(E, \mathcal{E})$ and assume $\nu$ is $\sigma$-finite. If $\mu \ll \nu$, there exists a unique nonnegative measurable function $f:E \rightarrow [0,\infty)$ satisfying
$$ \mu(A) = \int_A f(x) \nu(dx) \text{ for all }A \in \mathcal{E}$$
The function $f$ is called the *Radon-Nikodym* derivative of $\mu$ with respect to $\nu$ and denoted as $\frac{d\mu}{d\nu}$.

## Summary
- The pdf of $\mathbb{R}$-valued random variable is the Radon-Nikodym derivate of the cdf with respect to the Lebesgue measure.
- The pmf of a discrete random variable is the Radon-Nikodym derivative of the distribution with respect to the counting measure.
- In general, the density of a random variable on a measure space with Borel sets is the Radon-Nikodym derivative of the distribution $\mu$ with respect to the reference measure $\nu$.

## Reference
- [Note for Bayesian Machine Learning AI701](https://www.overleaf.com/project/5f3a04409a8fe0000159412a)
