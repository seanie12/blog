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

## Theorem 3.1.13
$U \subset \mathbb{R}$ is open $\Rightarrow$ $$\exists \{I_n\}$$: a finite or countable family of pairwise disjoint union of open intervals such that $U=\cup_n I_n.$

<*proof*>
Let $x \in U$ be given. Since $U$ is open, there is $\epsilon >0$ such that $(x-\epsilon, x+\epsilon) \subset U.$ Define $$A := \{t: t>x \text{ and } [x,t) \subset U\}, B:=\{s: s<x \text{ and } (s,x] \subset U\} .$$ Put $r_x := \sup A, l_x := \sup B$. We claim that $I_x= (l_x, r_x)\subset U$ and for $x,y \in U, I_x = I_y$ or $I_x \cap I_y =\emptyset.$ Suppose that $(l_x, r_x) \not\subset U.$ Without loss of generality, assume that $[x, r_x) \not\subset U,$ i.e. $r_x - \delta \not\in U$ with $x<r_x-\delta$ for some $\delta>0.$ Since $r_x = \sup A$, there exists $t_0$ such that $r_x\delta < x \leq r_x,$ i.e. $[x, r_x-\delta] \subset [x, r_x) \subset U$. It contradicts to the assumption that $r_x -\delta \not\in U$. 

$\therefore [x, r_x) \subset U.$
Similarly, we can show that $(l_x, x] \subset U.$

$\therefore $I_x = (l_x, r_x) \subset U.$

Now

