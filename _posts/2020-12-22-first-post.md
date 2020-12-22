---
title: "Probability Space"

use_math: true
---

\newtheorem{Thm}{Theorem}[section]
\newtheorem{Cor}{Corollary}[Thm]
\newtheorem{Lem}[Thm]{Lemma}
\newtheorem{Def}{Definition}[section]

\begin{Def}
Let $\Omega$ be a sample space. We call a class $\mathcal{A}$ $\sigma$-field if the followings are satisfied.
\begin{enumerate}
\item $\emptyset \in \mathcal{A}$,
\item $\mathcal{A} is closed under the countable union. i.e., if $A_1, \ldots, A_n \in \mathcal{A}$ then $\cup_{i=1}^\infty A_i \in \mathcal{A}$ and
\item $A \in \mathcal{A}$ implies that $\Omega \setminus A \in \mathcal{A}$.
\end{enumerate}
The sets $\mathcal{A}$ are said to be measurable and we call $(\Omega, \mathcal{A})$ a \textbf{measurable space}.
\end{Def}
This formula $f(x) = x^2$ is an example.


\begin{align}
\lim_{x\to 0}{\frac{e^x-1}{2x}}
\overset{\left[\frac{0}{0}\right]}{\underset{\mathrm{H}}{=}}
\lim_{x\to 0}{\frac{e^x}{2}}={\frac{1}{2}}
\end{align}
