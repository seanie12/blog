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
$E$ is a subset of $\mathbb{R}$. $p\in E$ is an *interior point* of $E$ if  there is $epsilon >0$ such that $N_{\epsilon} (p) \subset E$.
$$\text{Int}(E) := \{\text{all interior points of } E\} \subset E$$

### Example
1. $E=[1,2)$, $\text{int}(E) = (1,2]$.
2. $E =\mathbb{R} \setminus \mathbb{Q}$, $\text{Int}(E) = \emptyset$.


## Definition 3.1.3
(a) $O \subset \mathbb{R}$ is *open* if $\text{Int}(O) = O.$
(b) $F \subset \mathbb{R}$ is *closed* if $F^c = \mathbb{R}\setminus F$ is open.

