---
title: "Fourier Inversion Formula"

categories:
  - Fourier Analysis

tags:
  - Fourier inversion 
  - Inverse Fourier transform
  - Plancherel's theorem



toc: true
toc_sticky: true

use_math : true
comments : true

---



## Corollary

If $f\in\mathcal{S}(\mathbb{R})$, then its Fourier transform $\widehat f$ also belongs to $\mathcal{S}(\mathbb{R})$.

_Proof._

We must show that $\widehat f$ is infinitely differentiable and that every derivative is rapidly decreasing.

We will use the following identities from the [proposition in the previous post](https://seanie12.github.io/blog/fourier%20analysis/fourier-transform-1/#proposition-1): for every $g\in\mathcal{S}(\mathbb{R})$,  
$$  
\begin{aligned}  
\widehat{g'}(\xi)&=2\pi i\xi\widehat g(\xi),\  
\frac{d}{d\xi}\widehat g(\xi)&=\widehat{(-2\pi ix)g}(\xi).  
\end{aligned}  
$$

First, we verify that multiplication by a polynomial preserves the Schwartz class. **Leibniz’s product rule** states that, for smooth functions $u,v$ and any nonnegative integer $m$,  
$$  
\frac{d^m}{dx^m}[u(x)v(x)]  
=\sum_{j=0}^{m}\binom{m}{j}u^{(j)}(x)v^{(m-j)}(x).  
$$  
Applying this rule with $u(x)=x^l$ and $v(x)=f(x)$ shows that every derivative of $x^l f(x)$ is a finite linear combination of terms of the form $x^r f^{(s)}(x)$, where $r,s$ are nonnegative integers. Each term is rapidly decreasing because, for every nonnegative integer $n$,  
$$  
\sup_{x\in\mathbb{R}}|x|^n|x^r f^{(s)}(x)|  
=\sup_{x\in\mathbb{R}}|x|^{n+r}|f^{(s)}(x)|  
<\infty.  
$$  
Therefore, $x^l f(x)\in\mathcal{S}(\mathbb{R})$. Differentiation also preserves the Schwartz class, directly from its definition.

For each nonnegative integer $l$, define  
$$  
g_l(x)=(-2\pi ix)^l f(x).  
$$  
Then $g_l\in\mathcal{S}(\mathbb{R})$, so the multiplication identity gives  
$$  
\frac{d}{d\xi}\widehat{g_l}(\xi)  
=\widehat{(-2\pi ix)g_l}(\xi)  
=\widehat{g_{l+1}}(\xi).  
$$  
Starting with $g_0=f$ and applying this identity repeatedly, we obtain  
$$  
\left(\frac{d}{d\xi}\right)^l\widehat f(\xi)  
=\widehat{g_l}(\xi).  
$$  
Each $\widehat{g_l}$ is continuous by the continuity result in the previous post. Thus $\widehat f\in C^\infty(\mathbb{R})$.

Now fix arbitrary nonnegative integers $k,l$, and define  
$$  
h_{k,l}(x)  
=\frac{1}{(2\pi i)^k}  
\left(\frac{d}{dx}\right)^k  
\left[(-2\pi ix)^l f(x)\right].  
$$  
The closure properties above imply that $h_{k,l}\in\mathcal{S}(\mathbb{R})$, so it is absolutely integrable. Applying the differentiation identity $k$ times yields  
$$  
\begin{aligned}  
\widehat{h_{k,l}}(\xi)  
&=\frac{(2\pi i\xi)^k}{(2\pi i)^k}\widehat{g_l}(\xi)\  
&=\xi^k\left(\frac{d}{d\xi}\right)^l\widehat f(\xi).  
\end{aligned}  
$$  
Consequently,  
$$  
\begin{aligned}  
\left|\xi^k\left(\frac{d}{d\xi}\right)^l\widehat f(\xi)\right|  
&=\left|\int_{\mathbb{R}}h_{k,l}(x)e^{-2\pi ix\xi}dx\right|\  
&\leq\int_{\mathbb{R}}|h_{k,l}(x)|dx  
<\infty.  
\end{aligned}  
$$  
The bound is independent of $\xi$. Since $k,l$ were arbitrary, every derivative of $\widehat f$ is rapidly decreasing. Therefore, $\widehat f\in\mathcal{S}(\mathbb{R})$. $\square$


## Proposition (Multiplication formula) 

Let $f,g\in\mathcal{S}(\mathbb{R})$. Then

$$
\begin{align*}
\int_{-\infty}^\infty f(x)\hat{g}(x) dx = \int_{-\infty}^\infty \hat{f}(y) d(y) dy
\end{align*}
$$

## Remark
Recall Fubini's theorem: if $F(x,y)$ is a continuous function on $\mathbb{R}^2$ satisfying the condition

$$
\begin{align*}
\lvert F(x,y) \rvert \leq \frac{A}{(1+x^2)(1+y^2)},
\end{align*}
$$

then 

$$
\begin{align*}
\int_{-\infty}^\infty \int_{-\infty}^\infty F(x,y) dxdy = \int_{-\infty}^\infty \int_{-\infty}^\infty F(x,y) dy dx.
\end{align*}
$$

<*Proof*>

Let $F(x,y)= f(x)g(y)e^{-2\pi i xy}$. Then $F$ satisfies the decay conditions for Fubini's theorem. Applying the theorem to the function, 

$$
\begin{align*}
\int_{-\infty}^\infty f(x)\hat{g}(x) dx = \int_{-\infty}^\infty\int_{-\infty}^\infty f(x) g(y) e^{-2\pi i xy}dy dx = \int_{-\infty}^\infty\int_{-\infty}^\infty g(y) f(x) e^{-2\pi i xy} dx dy = \int_{-\infty}^\infty g(y) \hat{f}(y) dy
\end{align*}
$$

$$\tag*{$\square$}$$

## Approximation of identity
Let $f(x)=e^{-\pi x^2}$. Note that $e^{-ax^2}\in\mathcal{S}(\mathbb{R})$ for all $a>0$. We create an approximation of identitiy using dilation of Gaussian. Let 

$$
\begin{align*}
K_\delta(x)=\frac{1}{\sqrt{\delta}}f(x/\sqrt{\delta}) = \frac{1}{\sqrt{\delta}}e^{-\pi x^2/\delta}.
\end{align*}
$$

## Corollary
The Fourier transform of $K_\delta$ is

$$
\begin{align*}
\hat{K}_\delta(\xi)&= \frac{1}{\sqrt{\delta}}\sqrt{\delta}\hat{f}(\sqrt{\delta}\xi)\\
&=\hat{f}(\sqrt{\delta}\xi) \\
&=e^{-\pi\delta\xi^2}.
\end{align*}
$$

$\square$

## Theorem
$\lbrace K_\delta\rbrace_{\delta>0}$ is an approximation of the identity as $\delta \to 0$.

1. $\int_\mathbb{R} K_\delta(x)dx=1$
2. $\int_\mathbb{R} \lvert K_\delta(x)\rvert dx <M$. 
3. For every $\eta>0$, $\int_{\lvert x\rvert >\eta} \lvert K_\delta(x)\rvert dx \to 0$ as $\delta\to0$.

*Proof.*

1.

$$
\begin{align*}
\int_{-\infty}^\infty \frac{1}{\sqrt{\delta}}\exp\left(\frac{-\pi x^2}{\delta}\right)dx = \int_{-\infty}^\infty\exp(-\pi t^2)dt=1 \quad (\frac{x}{\sqrt{\delta}}=t)
\end{align*}
$$

2. Since $K_\delta(x) >0$ for all $x\in\mathbb{R}$, 

$$
\begin{align*}
\int_{-\infty}^\infty \lvert K_\delta(x)\rvert dx = \int_{-\infty}^\infty K_\delta(x) dx = 1
\end{align*}
$$

3. 

$$
\begin{align*}
\int_{\lvert x \rvert > \eta} K_\delta (x) dx = \int_{\lvert x \rvert > \eta} \frac{1}{\sqrt{\delta}}\exp\left(-\frac{-\pi x^2}{\delta}\right) dx = \int_{\lvert y\rvert > \frac{\eta}{\sqrt{\delta}}} e^{-\pi y^2}dy \to 0 \quad (\because e^{-\pi x^2} \text{ is decreasing rapidly})
\end{align*}
$$


##  Theorem (Fourier inversion formula)

  

Let $f\in\mathcal{S}(\mathbb{R})$, with Fourier transform

  

$$\widehat f(\xi)=\mathcal{F}[f](\xi)=\int_{\mathbb{R}}f(t)e^{-2\pi it\xi}dt.$$

  

Then, for every $x\in\mathbb{R}$,

  

$$f(x)=\int_{\mathbb{R}}\widehat f(\xi)e^{2\pi ix\xi}d\xi.$$

  

The integral converges absolutely because $\widehat f\in\mathcal{S}(\mathbb{R})$ and $\lvert e^{2\pi ix\xi}\rvert=1$.

  

*Proof.*

  

We first prove the formula at $x=0$, then obtain the formula at an arbitrary point by translation.

  

**Step 1: choose the Gaussian functions explicitly.**

  

Let $g(t)=e^{-\pi t^2}$. For $\delta>0$, define

  

$$\begin{aligned}G_\delta(\xi)&=g(\sqrt{\delta}\xi)=e^{-\pi\delta\xi^2},\\K_\delta(t)&=\frac{1}{\sqrt{\delta}}g\left(\frac{t}{\sqrt{\delta}}\right)=\frac{1}{\sqrt{\delta}}e^{-\pi t^2/\delta}.\end{aligned}$$

  

The Gaussian transform formula $\widehat g=g$ and the scaling identity give

  

$$\widehat{G_\delta}(t)=\frac{1}{\sqrt{\delta}}\widehat g\left(\frac{t}{\sqrt{\delta}}\right)=K_\delta(t).$$

  

Thus we have explicitly constructed a function whose Fourier transform is $K_\delta$.

  

The kernels $K_\delta$ are even and form the Gaussian approximate identity established in the [previous post](https://seanie12.github.io/blog/fourier%20analysis/fourier-transform-1/). In particular,

  

$$\lim_{\delta\to0^+}(f*K_\delta)(0)=f(0).$$

  

**Step 2: express the convolution using $\widehat f$.**

  

For each fixed $\delta>0$, the function

  

$$H_\delta(t,\xi)=f(t)G_\delta(\xi)e^{-2\pi it\xi}$$

  

is absolutely integrable on $\mathbb{R}^2$. Indeed, Tonelli's theorem gives

  

$$\begin{aligned}\iint_{\mathbb{R}^2}\lvert H_\delta(t,\xi)\rvert dt\,d\xi&=\int_{\mathbb{R}}\lvert f(t)\rvert\left[\int_{\mathbb{R}}e^{-\pi\delta\xi^2}d\xi\right]dt\\&=\frac{1}{\sqrt{\delta}}\lVert f\rVert_1<\infty.\end{aligned}$$

  

Therefore, Fubini's theorem allows us to interchange the two integrals. Using the evenness of $K_\delta$, we obtain

  

$$\begin{aligned}(f*K_\delta)(0)&=\int_{\mathbb{R}}f(t)K_\delta(-t)dt\\&=\int_{\mathbb{R}}f(t)K_\delta(t)dt\\&=\int_{\mathbb{R}}f(t)\left[\int_{\mathbb{R}}G_\delta(\xi)e^{-2\pi it\xi}d\xi\right]dt\\&=\int_{\mathbb{R}}G_\delta(\xi)\left[\int_{\mathbb{R}}f(t)e^{-2\pi it\xi}dt\right]d\xi\\&=\int_{\mathbb{R}}\widehat f(\xi)e^{-\pi\delta\xi^2}d\xi.\end{aligned}$$

  

Consequently,

  

$$f(0)=\lim_{\delta\to0^+}\int_{\mathbb{R}}\widehat f(\xi)e^{-\pi\delta\xi^2}d\xi.$$

  

**Step 3: remove the Gaussian factor.**

  

We will show that

  

$$\lim_{\delta\to0^+}\int_{\mathbb{R}}\widehat f(\xi)e^{-\pi\delta\xi^2}d\xi=\int_{\mathbb{R}}\widehat f(\xi)d\xi.$$

  

Although the Gaussian factor tends to $1$ at every fixed $\xi$, we must control the integral over the whole real line. We do this by splitting it into a bounded interval and two tails.

  

Fix $\varepsilon>0$. Since $\widehat f\in\mathcal{S}(\mathbb{R})$, it is absolutely integrable. Choose $N\geq1$ large enough that

  

$$\int_{\lvert\xi\rvert>N}\lvert\widehat f(\xi)\rvert d\xi<\frac{\varepsilon}{2}.$$

  

Also set

  

$$B_N=\int_{-N}^{N}\lvert\widehat f(\xi)\rvert d\xi<\infty.$$

  

By the triangle inequality,

  

$$\begin{aligned}&\left\lvert\int_{\mathbb{R}}\widehat f(\xi)d\xi-\int_{\mathbb{R}}\widehat f(\xi)e^{-\pi\delta\xi^2}d\xi\right\rvert\\&\quad\leq\int_{\lvert\xi\rvert>N}\lvert\widehat f(\xi)\rvert\left\lvert1-e^{-\pi\delta\xi^2}\right\rvert d\xi\\&\qquad+\int_{-N}^{N}\lvert\widehat f(\xi)\rvert\left\lvert1-e^{-\pi\delta\xi^2}\right\rvert d\xi.\end{aligned}$$

  

For the tails, observe that $0<e^{-\pi\delta\xi^2}\leq1$. Thus $0\leq1-e^{-\pi\delta\xi^2}\leq1$, and

  

$$\int_{\lvert\xi\rvert>N}\lvert\widehat f(\xi)\rvert\left\lvert1-e^{-\pi\delta\xi^2}\right\rvert d\xi\leq\int_{\lvert\xi\rvert>N}\lvert\widehat f(\xi)\rvert d\xi<\frac{\varepsilon}{2}.$$

  

On the bounded interval, the fundamental theorem of calculus gives

  

$$1-e^{-\pi\delta\xi^2}=\int_0^{\pi\delta\xi^2}e^{-s}ds.$$

  

The integrand $e^{-s}$ lies between $0$ and $1$. Its integral is therefore at most the length of the interval of integration:

  

$$0\leq1-e^{-\pi\delta\xi^2}\leq\int_0^{\pi\delta\xi^2}1ds=\pi\delta\xi^2.$$

  

If $\lvert\xi\rvert\leq N$, this gives the uniform bound

  

$$\sup_{\lvert\xi\rvert\leq N}\left\lvert1-e^{-\pi\delta\xi^2}\right\rvert\leq\pi\delta N^2\longrightarrow0\qquad(\delta\to0^+).$$

  

Thus

  

$$\begin{aligned}\int_{-N}^{N}\lvert\widehat f(\xi)\rvert\left\lvert1-e^{-\pi\delta\xi^2}\right\rvert d\xi&\leq\pi\delta N^2\int_{-N}^{N}\lvert\widehat f(\xi)\rvert d\xi\\&=\pi\delta N^2B_N.\end{aligned}$$

  

With $N$ fixed, choose

  

$$0<\delta<\frac{\varepsilon}{2\pi N^2(1+B_N)}.$$

  

The bounded-interval contribution is then less than $\varepsilon/2$. Together with the tail estimate, this makes the total error less than $\varepsilon$.

  

The order of the choices matters: first choose $N$ to control the tails, then choose $\delta$ to control the fixed bounded interval. We have proved the required convergence, and hence

  

$$f(0)=\int_{\mathbb{R}}\widehat f(\xi)d\xi.$$

  

**Step 4: extend the formula to every $x\in\mathbb{R}$.**

  

Fix any $x\in\mathbb{R}$, and define the translated function

  

$$f_x(t)=f(t+x).$$

  

Then $f_x\in\mathcal{S}(\mathbb{R})$. To check this, let $k,m$ be nonnegative integers and put $u=t+x$. We have

  

$$t^k f_x^{(m)}(t)=(u-x)^k f^{(m)}(u).$$

  

The expression on the right is bounded: expanding the polynomial $(u-x)^k$ gives a finite sum of polynomially weighted derivatives of $f$, all of which are bounded because $f$ is a Schwartz function.

  

By the [translation identity from the previous proposition](https://seanie12.github.io/blog/fourier%20analysis/fourier-transform-1/#proposition-1),

  

$$\widehat{f_x}(\xi)=\mathcal{F}[f(\cdot+x)](\xi)=e^{2\pi ix\xi}\widehat f(\xi).$$

  

Applying the formula already proved at zero to the Schwartz function $f_x$, we obtain

  

$$\begin{aligned}f(x)&=f_x(0)\\&=\int_{\mathbb{R}}\widehat{f_x}(\xi)d\xi\\&=\int_{\mathbb{R}}\widehat f(\xi)e^{2\pi ix\xi}d\xi.\end{aligned}$$

  

Since $x$ was arbitrary, the Fourier inversion formula holds for every $x\in\mathbb{R}$.

  

<div  style="text-align: right;">\(\square\)</div>

## Definition (Inverse Fourier transform)
Given $g\in\mathcal{S}(\mathbb{R})$, we define the **inverse Fourier transform**   $\check{g}$ of $g$ by

$$
\begin{align*}
\mathcal{F}^*(g)(x) = \check{g}(x) = \int_{-\infty}^\infty g(\xi) e^{2\pi ix\xi}d\xi
\end{align*}
$$


##  Theorem

  

Let $\mathcal{F}:\mathcal{S}(\mathbb{R})\to\mathcal{S}(\mathbb{R})$ be the Fourier transform, and define the inverse Fourier transform by

  

$$\mathcal{F}^{\ast}[g](y)=\int_{\mathbb{R}}g(\xi)e^{2\pi iy\xi}d\xi.$$

  

Then $\mathcal{F}^{\ast}$ maps $\mathcal{S}(\mathbb{R})$ into itself, and $\mathcal{F}$ is a bijection on the Schwartz space, with inverse $\mathcal{F}^{\ast}$.

  

*Proof.*

  

For every $g\in\mathcal{S}(\mathbb{R})$,

  

$$\mathcal{F}^{\ast}[g](y)=\mathcal{F}[g](-y)=\widehat g(-y).$$

  

Since $\widehat g\in\mathcal{S}(\mathbb{R})$ and reflection preserves the Schwartz class, $\mathcal{F}^{\ast}[g]\in\mathcal{S}(\mathbb{R})$.

  

By Fourier inversion, for every $y\in\mathbb{R}$,

  

$$\begin{aligned}(\mathcal{F}^{\ast}\circ\mathcal{F})[g](y)&=\int_{\mathbb{R}}\left[\int_{\mathbb{R}}g(t)e^{-2\pi it\xi}dt\right]e^{2\pi iy\xi}d\xi\\&=\int_{\mathbb{R}}\widehat g(\xi)e^{2\pi iy\xi}d\xi\\&=g(y).\end{aligned}$$

  

Thus $\mathcal{F}^{\ast}\circ\mathcal{F}=I$, where $I$ is the identity operator on $\mathcal{S}(\mathbb{R})$.

  

For the other composition, use the reflection identity established above and substitute $\zeta=-\xi$ in the outer integral. The substitution reverses the integration limits and gives $d\xi=-d\zeta$, so the two sign changes cancel. Hence

  

$$\begin{aligned}(\mathcal{F}\circ\mathcal{F}^{\ast})[g](y)&=\int_{\mathbb{R}}\mathcal{F}^{\ast}[g](\xi)e^{-2\pi iy\xi}d\xi\\&=\int_{\mathbb{R}}\widehat g(-\xi)e^{-2\pi iy\xi}d\xi\\&=\int_{\mathbb{R}}\widehat g(\zeta)e^{2\pi iy\zeta}d\zeta\\&=g(y),\end{aligned}$$

  

where the last equality again follows from Fourier inversion. Therefore, $\mathcal{F}\circ\mathcal{F}^{\ast}=I$.

  

The identity $\mathcal{F}^{\ast}\circ\mathcal{F}=I$ implies that $\mathcal{F}$ is injective, and $\mathcal{F}\circ\mathcal{F}^{\ast}=I$ implies that it is surjective onto $\mathcal{S}(\mathbb{R})$. Consequently, $\mathcal{F}$ is bijective and $\mathcal{F}^{-1}=\mathcal{F}^{\ast}$.

  

<div  style="text-align: right;">\(\square\)</div>


##  Definition (Inverse Fourier transform)

  

Given $g\in\mathcal{S}(\mathbb{R})$, define its **inverse Fourier transform**  $\check g$ by

  

$$\mathcal{F}^{\ast}[g](x)=\check g(x)=\int_{\mathbb{R}}g(\xi)e^{2\pi ix\xi}d\xi.$$

  

This integral converges absolutely because $g$ is absolutely integrable.

  

##  Remark (Fourier inversion and bijectivity)

  

The Fourier transform and inverse Fourier transform satisfy

  

$$\check g(x)=\widehat g(-x).$$

  

Since reflection preserves the Schwartz class, this identity shows that $\check g\in\mathcal{S}(\mathbb{R})$.

  

For every $f\in\mathcal{S}(\mathbb{R})$, Fourier inversion gives

  

$$\check{\widehat f}(x)=f(x).$$

  

The other composition also recovers $f$. Using the substitution $\zeta=-\xi$, we obtain

  

$$\begin{aligned}\widehat{\check f}(x)&=\int_{\mathbb{R}}\check f(\xi)e^{-2\pi ix\xi}d\xi\\&=\int_{\mathbb{R}}\widehat f(-\xi)e^{-2\pi ix\xi}d\xi\\&=\int_{\mathbb{R}}\widehat f(\zeta)e^{2\pi ix\zeta}d\zeta\\&=f(x).\end{aligned}$$

  

Here the substitution reverses the integration limits and gives $d\xi=-d\zeta$, so the two sign changes cancel. The last equality follows from Fourier inversion.

  

Consequently,

  

$$\mathcal{F}^{\ast}\circ\mathcal{F}=\mathcal{F}\circ\mathcal{F}^{\ast}=I.$$

  

Thus $\mathcal{F}$ is a bijection on $\mathcal{S}(\mathbb{R})$, with inverse $\mathcal{F}^{\ast}$.

  

##  Lemma (Convolution of Schwartz functions)

  

Let $u,v\in\mathcal{S}(\mathbb{R})$, and define

  

$$w(x)=(u\ast v)(x)=\int_{\mathbb{R}}u(x-t)v(t)dt.$$

  

Then $w\in\mathcal{S}(\mathbb{R})$, and

  

$$\widehat w(\xi)=\mathcal{F}[u\ast v](\xi)=\widehat u(\xi)\widehat v(\xi).$$

  

*Proof.*

  

Since every derivative of $u$ is bounded and $v$ is absolutely integrable, we may differentiate under the integral repeatedly:

  

$$w^{(m)}(x)=\int_{\mathbb{R}}u^{(m)}(x-t)v(t)dt.$$

  

For each differentiation, the difference quotients are bounded by a constant multiple of $\lvert v(t)\rvert$, using the boundedness of the next derivative of $u$. Dominated convergence therefore justifies the formula, and also gives continuity of each derivative.

  

For nonnegative integers $k,m$, expand

  

$$x^k=((x-t)+t)^k=\sum_{j=0}^k\binom{k}{j}(x-t)^jt^{k-j}.$$

  

It follows that

  

$$\begin{aligned}\sup_{x\in\mathbb{R}}\lvert x\rvert^k\lvert w^{(m)}(x)\rvert&\leq\sum_{j=0}^k\binom{k}{j}\left(\sup_{r\in\mathbb{R}}\lvert r\rvert^j\lvert u^{(m)}(r)\rvert\right)\int_{\mathbb{R}}\lvert t\rvert^{k-j}\lvert v(t)\rvert dt\\&<\infty.\end{aligned}$$

  

Every supremum and integral on the right is finite because $u,v$ are Schwartz functions. Thus every derivative of $w$ is rapidly decreasing, so $w\in\mathcal{S}(\mathbb{R})$.

  

For the Fourier-transform identity, Tonelli's theorem gives

  

$$\int_{\mathbb{R}}\int_{\mathbb{R}}\lvert u(x-t)v(t)\rvert dxdt=\lVert u\rVert_1\lVert v\rVert_1<\infty.$$

  

Hence Fubini's theorem permits us to interchange the integrals. With $s=x-t$, we obtain

  

$$\begin{aligned}\widehat w(\xi)&=\int_{\mathbb{R}}\left[\int_{\mathbb{R}}u(x-t)v(t)dt\right]e^{-2\pi ix\xi}dx\\&=\int_{\mathbb{R}}v(t)e^{-2\pi it\xi}\left[\int_{\mathbb{R}}u(s)e^{-2\pi is\xi}ds\right]dt\\&=\widehat u(\xi)\widehat v(\xi).\end{aligned}$$

  

<div  style="text-align: right;">\(\square\)</div>

  


##  Lemma (Convolution of Schwartz functions)

  

Let $u,v\in\mathcal{S}(\mathbb{R})$, and define

  

$$w(x)=(u\ast v)(x)=\int_{\mathbb{R}}u(x-t)v(t)dt.$$

  

Then $w\in\mathcal{S}(\mathbb{R})$, and

  

$$\widehat w(\xi)=\mathcal{F}[u\ast v](\xi)=\widehat u(\xi)\widehat v(\xi).$$

  

*Proof.*

  

Since every derivative of $u$ is bounded and $v$ is absolutely integrable, we may differentiate under the integral repeatedly:

  

$$w^{(m)}(x)=\int_{\mathbb{R}}u^{(m)}(x-t)v(t)dt.$$

  

For each differentiation, the difference quotients are bounded by a constant multiple of $\lvert v(t)\rvert$, using the boundedness of the next derivative of $u$. Dominated convergence therefore justifies the formula, and also gives continuity of each derivative.

  

Fix nonnegative integers $k,m$. We will first bound $\lvert x\rvert^k\lvert w^{(m)}(x)\rvert$ for each fixed $x$ by a quantity independent of $x$, then take the supremum over $x$.

  

By the triangle inequality,

  

$$\lvert x\rvert^k\lvert w^{(m)}(x)\rvert\leq\int_{\mathbb{R}}\lvert x\rvert^k\lvert u^{(m)}(x-t)\rvert\lvert v(t)\rvert dt.$$

  

Since $x=(x-t)+t$, we have $\lvert x\rvert\leq\lvert x-t\rvert+\lvert t\rvert$. Applying the binomial theorem gives

  

$$\lvert x\rvert^k\leq(\lvert x-t\rvert+\lvert t\rvert)^k=\sum_{j=0}^k\binom{k}{j}\lvert x-t\rvert^j\lvert t\rvert^{k-j}.$$

  

This splits the power of $\lvert x\rvert$ into powers of $\lvert x-t\rvert$ and $\lvert t\rvert$. Substituting the bound into the integral, we obtain

  

$$\lvert x\rvert^k\lvert w^{(m)}(x)\rvert\leq\sum_{j=0}^k\binom{k}{j}\int_{\mathbb{R}}\lvert x-t\rvert^j\lvert u^{(m)}(x-t)\rvert\lvert t\rvert^{k-j}\lvert v(t)\rvert dt.$$

  

For each $j=0,\ldots,k$, define

  

$$M_j=\sup_{r\in\mathbb{R}}\lvert r\rvert^j\lvert u^{(m)}(r)\rvert.$$

  

Each $M_j$ is finite because $u$ is a Schwartz function. For any $x,t\in\mathbb{R}$, we can substitute $r=x-t$ into the expression bounded by this supremum. Hence

  

$$\lvert x-t\rvert^j\lvert u^{(m)}(x-t)\rvert\leq M_j.$$

  

Using this bound inside each integral gives

  

$$\lvert x\rvert^k\lvert w^{(m)}(x)\rvert\leq\sum_{j=0}^k\binom{k}{j}M_j\int_{\mathbb{R}}\lvert t\rvert^{k-j}\lvert v(t)\rvert dt.$$

  

The right-hand side no longer depends on $x$, so the same bound holds for the supremum over all $x$. Substituting the definition of $M_j$, we recover

  

$$\begin{aligned}\sup_{x\in\mathbb{R}}\lvert x\rvert^k\lvert w^{(m)}(x)\rvert&\leq\sum_{j=0}^k\binom{k}{j}\left(\sup_{r\in\mathbb{R}}\lvert r\rvert^j\lvert u^{(m)}(r)\rvert\right)\int_{\mathbb{R}}\lvert t\rvert^{k-j}\lvert v(t)\rvert dt\\&<\infty.\end{aligned}$$

  

The moments of $v$ on the right are finite because polynomially weighted Schwartz functions are absolutely integrable. More explicitly, for $\lvert t\rvert\geq1$, the Schwartz condition gives

  

$$\lvert t\rvert^{k-j}\lvert v(t)\rvert\leq\frac{C_j}{\lvert t\rvert^2},\qquad C_j=\sup_{r\in\mathbb{R}}\lvert r\rvert^{k-j+2}\lvert v(r)\rvert<\infty.$$

  

The function $\lvert t\rvert^{-2}$ is integrable on these tails, and continuity gives integrability on $[-1,1]$. Thus every term in the finite sum is finite. Since $k,m$ were arbitrary, every derivative of $w$ is rapidly decreasing, so $w\in\mathcal{S}(\mathbb{R})$.

  

For the Fourier-transform identity, Tonelli's theorem gives

  

$$\int_{\mathbb{R}}\int_{\mathbb{R}}\lvert u(x-t)v(t)\rvert dxdt=\lVert u\rVert_1\lVert v\rVert_1<\infty.$$

  

Hence Fubini's theorem permits us to interchange the integrals. With $s=x-t$, we obtain

  

$$\begin{aligned}\widehat w(\xi)&=\int_{\mathbb{R}}\left[\int_{\mathbb{R}}u(x-t)v(t)dt\right]e^{-2\pi ix\xi}dx\\&=\int_{\mathbb{R}}v(t)e^{-2\pi it\xi}\left[\int_{\mathbb{R}}u(s)e^{-2\pi is\xi}ds\right]dt\\&=\widehat u(\xi)\widehat v(\xi).\end{aligned}$$

  

<div  style="text-align: right;">\(\square\)</div>

  

##  Theorem (Plancherel's identity on the Schwartz space)

  

For every $f\in\mathcal{S}(\mathbb{R})$,

  

$$\int_{\mathbb{R}}\lvert f(t)\rvert^2dt=\int_{\mathbb{R}}\lvert\widehat f(\xi)\rvert^2d\xi.$$

  

Equivalently,

  

$$\lVert f\rVert_2=\lVert\widehat f\rVert_2.$$

  

*Proof.*

  

Define the reflected conjugate of $f$ by

  

$$f^b(t)=\overline{f(-t)},$$

  

and set $h=f\ast f^b$. Reflection and complex conjugation preserve the Schwartz class, so $f^b\in\mathcal{S}(\mathbb{R})$. The convolution lemma then gives $h\in\mathcal{S}(\mathbb{R})$.

  

First, evaluate the convolution at zero. Substituting $t\mapsto-t$ in its defining integral gives

  

$$\begin{aligned}h(0)&=\int_{\mathbb{R}}f(t)f^b(-t)dt\\&=\int_{\mathbb{R}}f(t)\overline{f(t)}dt\\&=\int_{\mathbb{R}}\lvert f(t)\rvert^2dt\\&=\lVert f\rVert_2^2.\end{aligned}$$

  

Next, compute the Fourier transform of $f^b$. Substituting $s=-t$, we obtain

  

$$\begin{aligned}\mathcal{F}[f^b](\xi)&=\int_{\mathbb{R}}\overline{f(-t)}e^{-2\pi it\xi}dt\\&=\int_{\mathbb{R}}\overline{f(s)}e^{2\pi is\xi}ds\\&=\overline{\int_{\mathbb{R}}f(s)e^{-2\pi is\xi}ds}\\&=\overline{\widehat f(\xi)}.\end{aligned}$$

  

The passage to the third line uses the fact that complex conjugation commutes with an absolutely convergent integral.

  

By the convolution lemma,

  

$$\widehat h(\xi)=\widehat f(\xi)\mathcal{F}[f^b](\xi)=\widehat f(\xi)\overline{\widehat f(\xi)}=\lvert\widehat f(\xi)\rvert^2.$$

  

Finally, apply Fourier inversion to the Schwartz function $h$ at zero:

  

$$\begin{aligned}\lVert f\rVert_2^2=h(0)&=\int_{\mathbb{R}}\widehat h(\xi)d\xi\\&=\int_{\mathbb{R}}\lvert\widehat f(\xi)\rvert^2d\xi\\&=\lVert\widehat f\rVert_2^2.\end{aligned}$$

  

Taking square roots gives $\lVert f\rVert_2=\lVert\widehat f\rVert_2$.

  

<div  style="text-align: right;">\(\square\)</div>

## Reference
- Elias M. Stein and  Rami Shakarchi **『**Fourier Analysis: An Introduction**』**
- **[Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing)**
