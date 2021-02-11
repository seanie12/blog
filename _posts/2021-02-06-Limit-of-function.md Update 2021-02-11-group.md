---
title: "Group and Ring"

categories:
  - Group
  - Ring

tags:
  - quotient group
  - normal subgroup
  - quotient ring
  - well-defined binary operation
  
  

toc: true
toc_sticky: true

use_math : true
comments : true

---


## Definition 1
$\cdot: G\times G \to G$ is binary operation where we write $x\cdot y =xy$ for $x,y\in G$. 
$(G,\cdot)$ is group if it satisfies the followings
(a) For all $x,y,z \in G$, $(x\cdot y)\cdot z = x\cdot (y\cdot z)$.
(b) $\exists e \in G$, such that $x\cdot e = e\cdot x = x$, for all $x\in G$.
(c) For every $x \in G$, $\exists \hat{x} \in G$ such that $x \hat{x} = \hat{x}x = e$.

## Definition 2
Let $(G,\cdot)$ is a group. $H \subset G$ is a **subgroup** satisfying the three requirements of group as described in Definition 1. We write $(H,\cdot) \leq (G,\cdot)$.

## Definition 3
Let  $(G,\cdot)$ is a group and $(H,\cdot) \leq G$. $H$ is normal subgroup if $g^{-1}hg\in H$ for all $g \in G, h \in H$. We write $H \trianglelefteq G$.





