---
title: "Set and Function"

categories:
  - Analysis


tags:
  - set
  - function
  
  

toc: true
toc_sticky: true

use_math : true
comments : true

---

## Lemma 1.1.0 (De Morgan's law)
(1) $(\cup_{i\in I} A_i)^c = \cap_{i\in I}A^c_i$
(2) $(\cap_{i\in I}A_i)^c = \cup_{i\in I}A^c_i$

<*proof*>

**(a)**
$$
\begin{align}
\begin{split}
w\in (\cup_{i\in I} A_i)^c &\iff w \not\in \cup_{i\in I} A_i \\
&\iff w \not\in A_i \text{ for all } i \in I \\
&\iff w\in A^c_i \text{ for all } i \in I \\
&\iff w \in  \cap_{i\in I}A^c_i
\end{split}
\end{align}
$$

**(b)**
$$
\begin{align}
\begin{split}
w \in (\cap_{i\in I}A_i)^c &\iff w\not\in \cap_{i\in I} A_i \\
&\iff w \in A^c_i \text{ for some }i \in I\\
&\iff w \in \cup_{i\in I}A^c_i
\end{split}
\end{align}
$$
$$\tag*{$\square$}$$
## Theorem 1.1.1
(a) $A\cap (B\cup C) = (A\cap B) \cup (A\cap C)$

(b) $A\cup (B\cap C) = (A\cup B) \cap (A\cup C)$

(c) $C\setminus (A\cap B) = (C\setminus A) \cup (C\setminus B)$

<*proof*>

**(a)** Let $x \in A\cap(B\cup C)$ be given. That is $x\in A$ and $x\in B\cup C$.

If $x\in A$ and $x\in B$, $x\in A\cap B$. So, $x\in (A\cap B)\cup(A\cap C).$

If $x\in A$ and $x\in C$, then $x\in A\cap C$. Thus, $x\in (A\cap B)\cup (A\cap C).$

$\therefore A\cap (B\cup C) \subset (A\cap B)\cup (A\cap C).$

Conversely, let $x\in (A\cap B)\cup (A\cap C)$ be given.  Then, $x\in A\cap B$ or $x\in A\cap C$. 
If $x\in A\cap B$, then $x\in A$ and $x\in B$. Since $B\subset (B\cup C)$,  $x\in B\cup C$. Clearly, $x \in A$. Thus, $x\in A$ and $x\in B\cup C.$

If $x\in A\cap C,$ then $x\in A$ and $x\in C.$ Since $C\subset (B\cup C), x\in (B\cup C).$ So, $x\in A$ and $x \in B\cup C.$

$\therefore A\cap (B\cup C) = (A\cap B)\cup (A\cap C)$ by the double inclusion.

**(b)**  Let $x\in A\cup (B\cap C)$ be given. That is $x\in A$ or $x\in B\cap C.$
Suppose $x \in A$. Since $A \subset (A\cup B)$ and $A\subset (A\cup C)$, $x\in (A\cup B)$ and $x\in (A\cup C)$.

Otherwise, $x\in B\cap C$. Since $(B\cap C) \subset B \subset (A\cup B), x\in A\cup B.$ Similarly, $x\in A\cup C$ because $(B\cap C) \subset C \subset (A\cup C)$.
$\therefore x\in (A\cup B)\cap  (A\cup C)$.

Conversely, let $x\in (A\cup B)\cap (A\cup C)$ be given. 
Since $A \subset (A\cup B)$ and $A \subset (A\cup C), A\subset (A\cup B)\cap (A\cup C).$ 
So, if $x\in A, x\in A\cup(B\cap C).$ 

Otherwise, $x\in (B\setminus A)\cap (C\setminus A)$ because $x \in (A\cup B) \cap (A\cup C).$ Then it implies that $x\in B$ and $x\in C$ because $(B\setminus A)\subset B$ and $(C\setminus A)\subset C$.
$\therefore x\in A\cup (B\cap C)$.

$\therefore A\cup (B\cap C) = (A\cup B) \cap (A\cup C).$

**(c)**
$$
\begin{align}
\begin{split}
C\setminus (A\cup B) &= C\cap (A\cup B)^c \\
&=C\cap (A^c\cap B^c) \\
&=(C\cap A^c)\cap (C\cap B^c) \\
&=(C\setminus A)\cap (C\setminus B)
\end{split}
\end{align}
$$
The second equality holds by de Morgan's law and the third equality holds by (b).

**(d)**
$$
\begin{align}
\begin{split}
C\setminus (A\cap B) &= C\cap (A\cap B)^c \\
&=C \cap (A^c \cup B^c) \\
&=(C\cap A^c)\cup (C\cap B^c) \\
&=(C\setminus A)\cup (C\setminus B)
\end{split}
\end{align}
$$
The second equality holds by de Morgan's law and the third equality holds by (a).
$$\tag*{$\square$}$$

## Reference
- Manfred Stoll,  **『**Introduction to Real Analysis**』**, Pearson
