---
title: "Fourier Transform"
categories:
  - Fourier Analysis
tags:
  - moderate decrease
  - Fourier transform
  - rapidly decreasing
toc: true
toc_sticky: true
use_math: true
comments: true
---

## Definition

For a continuous function $f:\mathbb{R}\to\mathbb{C}$, define

$$
\int_{\mathbb{R}}f(x)dx:=\lim_{a\to\infty}\int_{-a}^{0}f(x)dx+\lim_{b\to\infty}\int_{0}^{b}f(x)dx,
$$

provided both limits exist. Here, $a$ and $b$ tend to infinity independently.

When this integral exists, it also equals the symmetric limit

$$
\int_{\mathbb{R}}f(x)dx=\lim_{R\to\infty}\int_{-R}^{R}f(x)dx.
$$

The converse requires care. A symmetric limit alone is called a **Cauchy principal value** and need not give an improper integral. For example,

$$
\int_{-R}^{R}x\,dx=0,
$$

but the integrals over the positive and negative half-lines do not converge separately. The decay assumptions below will guarantee absolute convergence, so this distinction will cause no difficulty for the functions we study.

## Definition

A continuous function $f:\mathbb{R}\to\mathbb{C}$ is of **moderate decrease** if there is a constant $A>0$ such that

$$
\lvert f(x)\rvert\leq\frac{A}{1+x^2}
$$

for every $x\in\mathbb{R}$. Write $\mathcal{M}(\mathbb{R})$ for the vector space of these functions. The denominator controls both regions: it stays positive near the origin and behaves like $x^2$ far away.

## Exercise

Every $f\in\mathcal{M}(\mathbb{R})$ is absolutely integrable. In particular, its improper integral exists.

*Proof.*

Suppose $f\in\mathcal{M}(\mathbb{R})$. Since

$$
\int_{-R}^{R}\lvert f(x)\rvert dx\leq A\int_{-R}^{R}\frac{dx}{1+x^2}=2A\arctan R\leq A\pi,
$$

the integrals of $\lvert f\rvert$ on each half-line are increasing and bounded. Thus

$$
\lVert f\rVert_1:=\int_{\mathbb{R}}\lvert f(x)\rvert dx\leq A\pi.
$$

This is **absolute integrability**. It also guarantees convergence of the integral of $f$: differences of truncated integrals are bounded by integrals of $\lvert f\rvert$ over their tails, which tend to zero.

More explicitly, for every $R>0$,

$$
\begin{aligned}
\int_{\lvert x\rvert>R}\lvert f(x)\rvert dx
&\leq A\int_{\lvert x\rvert>R}\frac{dx}{x^2}\\
&=2A\int_R^\infty\frac{dx}{x^2}=\frac{2A}{R}.
\end{aligned}
$$

Here and below, an integral over $\lvert x\rvert>R$ means the sum of the two tail integrals. This estimate tells us exactly how a large interval captures almost all of the integral. For example,

$$
\left\lvert\int_{\mathbb{R}}f(x)dx-\int_{-R}^{R}f(x)dx\right\rvert\leq\frac{2A}{R}.
$$

<div style="text-align: right;">\(\square\)</div>

## Proposition (Properties of the improper integral)

Let $f,g\in\mathcal{M}(\mathbb{R})$, $\alpha,\beta\in\mathbb{C}$, $a\in\mathbb{R}$, and $\delta>0$. Then

(1) Linearity:

$$
\int_{\mathbb{R}}(\alpha f+\beta g)=\alpha\int_{\mathbb{R}}f+\beta\int_{\mathbb{R}}g.
$$

(2) Translation invariance:

$$
\int_{\mathbb{R}}f(x-a)dx=\int_{\mathbb{R}}f(x)dx.
$$

(3) Scaling under dilations:

$$
\delta\int_{\mathbb{R}}f(\delta x)dx=\int_{\mathbb{R}}f(x)dx.
$$

(4) Continuity under translation:

$$
\lim_{h\to0}\int_{\mathbb{R}}\lvert f(x-h)-f(x)\rvert dx=0.
$$

*Proof.*

(1) Linearity.

For $\alpha,\beta\in\mathbb{C}$,

$$
\int_{\mathbb{R}}\bigl(\alpha f(x)+\beta g(x)\bigr)dx=\alpha\int_{\mathbb{R}}f(x)dx+\beta\int_{\mathbb{R}}g(x)dx.
$$

Indeed, if $f$ and $g$ have decay constants $A_f$ and $A_g$, then

$$
\lvert\alpha f(x)+\beta g(x)\rvert\leq\frac{\lvert\alpha\rvert A_f+\lvert\beta\rvert A_g}{1+x^2}.
$$

Thus the sum is also of moderate decrease. Apply linearity on $[-R,R]$ and take $R\to\infty$; every integral involved converges absolutely.

(2) Translation invariance.

Let $f:\mathbb{R}\to\mathbb{C}$ be continuous and suppose that

$$
\lvert f(x)\rvert\leq\frac{A}{1+x^2}
$$

for some $A>0$ and every $x\in\mathbb{R}$. We prove that, for every real shift $a$,

$$
\int_{\mathbb{R}}f(x-a)dx=\int_{\mathbb{R}}f(x)dx.
$$

*Proof.*

First, $f$ is absolutely integrable because

$$
\int_{\mathbb{R}}\lvert f(u)\rvert du\leq A\int_{\mathbb{R}}\frac{du}{1+u^2}=A\pi<\infty.
$$

Write $I=\int_{\mathbb{R}}f(u)du$.

For a finite $R$, the substitution $u=x-a$ gives

$$
\int_{-R}^{R}f(x-a)dx=\int_{-R-a}^{R-a}f(u)du.
$$

We are now integrating the same function over a shifted interval. As $R$ increases, its left endpoint tends to $-\infty$ and its right endpoint tends to $+\infty$. Thus the interval still captures more and more of the whole integral.

To make this precise, the difference from $I$ consists of the two missing tails:

$$
I-\int_{-R-a}^{R-a}f(u)du=\int_{-\infty}^{-R-a}f(u)du+\int_{R-a}^{\infty}f(u)du.
$$

If $R>\lvert a\rvert$, then

$$
-R-a\leq-(R-\lvert a\rvert),\qquad R-a\geq R-\lvert a\rvert.
$$

In other words, the shifted interval contains $[-(R-\lvert a\rvert),R-\lvert a\rvert]$. Every missing point therefore satisfies $\lvert u\rvert>R-\lvert a\rvert$. By the triangle inequality and the decay assumption,

$$
\begin{aligned}
\left\lvert I-\int_{-R}^{R}f(x-a)dx\right\rvert
&\leq\int_{\lvert u\rvert>R-\lvert a\rvert}\lvert f(u)\rvert du\\
&\leq A\int_{\lvert u\rvert>R-\lvert a\rvert}\frac{du}{u^2}\\
&=2A\int_{R-\lvert a\rvert}^{\infty}\frac{du}{u^2}\\
&=\frac{2A}{R-\lvert a\rvert}\longrightarrow0.
\end{aligned}
$$

Here $a$ is fixed, so $R-\lvert a\rvert\to\infty$. This shows that the symmetric integrals of the shifted function approach $I$.

Finally, its ordinary improper integral also exists. Applying the same substitution to the absolute value gives

$$
\int_{-R}^{R}\lvert f(x-a)\rvert dx=\int_{-R-a}^{R-a}\lvert f(u)\rvert du\leq A\pi.
$$

The integrals of $\lvert f(x-a)\rvert$ on each half-line are increasing and bounded above by $A\pi$, so both converge. Thus $f(x-a)$ is absolutely integrable, and its improper integral equals its symmetric limit. Therefore,

$$
\int_{\mathbb{R}}f(x-a)dx=\lim_{R\to\infty}\int_{-R}^{R}f(x-a)dx=I=\int_{\mathbb{R}}f(x)dx.
$$

<div style="text-align: right;">\(\square\)</div>

(3) Scaling under dilations.

For $\delta>0$,

$$
\int_{\mathbb{R}}f(\delta x)dx=\frac{1}{\delta}\int_{\mathbb{R}}f(u)du.
$$

The scaled function is of moderate decrease because

$$
\lvert f(\delta x)\rvert\leq\frac{A}{1+\delta^2x^2}\leq\frac{A\max\lbrace 1,\delta^{-2}\rbrace}{1+x^2}.
$$

On a finite interval, the substitution $u=\delta x$ gives

$$
\int_{-R}^{R}f(\delta x)dx=\frac{1}{\delta}\int_{-\delta R}^{\delta R}f(u)du.
$$

Let $R\to\infty$. The factor $1/\delta$ compensates for compressing the graph horizontally by a factor of $\delta$.

(4) Continuity under translation in the integral.

We claim that

$$
\lim_{h\to0}\int_{\mathbb{R}}\lvert f(x-h)-f(x)\rvert dx=0.
$$

Pointwise continuity says that the integrand tends to zero for each fixed $x$. To control its integral over an infinite interval, we split the real line into a bounded interval and two tails.

The split is at $R$ in the original variable $x$:

$$
\begin{aligned}
\int_{\mathbb{R}}\lvert f(x-h)-f(x)\rvert dx
&=\int_{-R}^{R}\lvert f(x-h)-f(x)\rvert dx\\
&\quad+\int_{\lvert x\rvert>R}\lvert f(x-h)-f(x)\rvert dx.
\end{aligned}
$$

In particular, the region $R-1\leq\lvert x\rvert\leq R$ belongs to the first integral and is controlled by Step 2. No region is omitted.

**Step 1: control both tails uniformly for small translations.**

Restrict to $\lvert h\rvert\leq1$ and choose $R>1$. If $\lvert x\rvert>R$, then the reverse triangle inequality gives

$$
\lvert x-h\rvert\geq\lvert x\rvert-\lvert h\rvert>R-1.
$$

Thus, after substituting $u=x-h$,

$$
\begin{aligned}
\int_{\lvert x\rvert>R}\lvert f(x-h)\rvert dx
&\leq\int_{\lvert u\rvert>R-1}\lvert f(u)\rvert du\\
&\leq\frac{2A}{R-1}.
\end{aligned}
$$

Here $R-1$ is a cutoff for the new variable $u=x-h$. The substitution sends the original tail $\lvert x\rvert>R$ to the region $\lvert u+h\rvert>R$, which is contained in $\lvert u\rvert>R-1$. We enlarge the region of integration to obtain an upper bound for the nonnegative integrand. This does not change the original split at $\lvert x\rvert=R$.

Together with the unshifted tail estimate, this gives

$$
\begin{aligned}
\int_{\lvert x\rvert>R}\lvert f(x-h)-f(x)\rvert dx
&\leq\frac{2A}{R-1}+\frac{2A}{R}\\
&\leq\frac{4A}{R-1}.
\end{aligned}
$$

The bound does not depend on the particular $h$ as long as $\lvert h\rvert\leq1$. The condition $R>1$ simply ensures that $R-1$ is positive: a shift of at most $1$ can bring a point at most $1$ unit closer to the origin.

Given $\varepsilon>0$, choose

$$
R>1+\frac{8A}{\varepsilon}.
$$

The tail contribution is then less than $\varepsilon/2$.

**Step 2: control the bounded interval by uniform continuity.**

For $\lvert x\rvert\leq R$ and $\lvert h\rvert\leq1$, both $x$ and $x-h$ belong to $[-R-1,R+1]$. Since $f$ is continuous on this closed bounded interval, it is uniformly continuous there. Therefore, there is an $\eta>0$ such that

$$
u,v\in[-R-1,R+1],\quad\lvert u-v\rvert<\eta
\Longrightarrow\lvert f(u)-f(v)\rvert<\frac{\varepsilon}{4R}.
$$

If $\lvert h\rvert<\min\lbrace 1,\eta\rbrace$, then

$$
\begin{aligned}
\int_{-R}^{R}\lvert f(x-h)-f(x)\rvert dx
&\leq2R\sup_{\lvert x\rvert\leq R}\lvert f(x-h)-f(x)\rvert\\
&\leq\frac{\varepsilon}{2}.
\end{aligned}
$$

Combining the two regions gives a total smaller than $\varepsilon$. The order matters: **first choose $R$ to control the tails, then choose $h$ to control the fixed bounded interval.**

<div style="text-align: right;">\(\square\)</div>

## Definition

For $f\in\mathcal{M}(\mathbb{R})$, define its **Fourier transform** by

$$
\widehat f(\xi)=\int_{\mathbb{R}}f(x)e^{-2\pi ix\xi}dx,\qquad\xi\in\mathbb{R}.
$$

Euler's formula gives

$$
e^{-2\pi ix\xi}=\cos(2\pi x\xi)-i\sin(2\pi x\xi).
$$

For fixed $\xi$, this factor oscillates as $x$ varies. Its absolute value is always $1$, so multiplying by it does not affect absolute integrability:

$$
\int_{\mathbb{R}}\lvert f(x)e^{-2\pi ix\xi}\rvert dx=\lVert f\rVert_1<\infty.
$$

In particular, the Fourier transform is well-defined and bounded:

$$
\lvert\widehat f(\xi)\rvert\leq\lVert f\rVert_1
\qquad\text{for every }\xi\in\mathbb{R}.
$$

## Remark

We will repeatedly use

$$
\lvert e^{iu}-1\rvert\leq\lvert u\rvert
\qquad(u\in\mathbb{R}).
$$

Geometrically, $1=(1,0)$ and $e^{iu}=(\cos u,\sin u)$ lie on the unit circle. For a complex number $a+ib$, its absolute value is $\sqrt{a^2+b^2}$. Therefore, subtracting the two endpoints and taking the absolute value gives their straight-line distance:

$$
\lvert e^{iu}-1\rvert
=\lvert(\cos u-1)+i\sin u\rvert
=\sqrt{(\cos u-1)^2+\sin^2u}.
$$

Traveling along the unit circle through an angle $u$ radians covers a distance $\lvert u\rvert$, since arc length equals radius times the absolute angle and the radius is $1$. The straight segment between the endpoints cannot be longer than this circular path, so $\lvert e^{iu}-1\rvert\leq\lvert u\rvert$.

Move the slider below to compare the two lengths. Positive angles travel counterclockwise, and negative angles travel clockwise. Try $u=2\pi$: the circular path makes one full turn of length $2\pi$, but its endpoint returns to $1$, so the straight-line distance is zero. For angles larger in magnitude than $2\pi$, the circular path length counts every full turn.

<div id="unit-circle-distance">
  <style>
    #unit-circle-distance {
      --uc-fg: currentColor;
      --uc-muted: color-mix(in srgb, currentColor 9%, transparent);
      --uc-line: color-mix(in srgb, currentColor 25%, transparent);
      --uc-secondary: color-mix(in srgb, currentColor 65%, transparent);
      --uc-chord: #1875d1;
      --uc-path: #c46c09;
      margin: 1.5em 0; font-family: inherit; font-size: 1rem;
    }
    #unit-circle-distance *, #unit-circle-distance *::before,
    #unit-circle-distance *::after { box-sizing: border-box; }
    #unit-circle-distance h3 { margin: 0 0 1em; font-size: 1.1em; }
    #unit-circle-distance output { display: inline; color: inherit; }
    #unit-circle-distance .form-range { display: block; width: 100%; margin: 0; min-height: 32px; accent-color: var(--uc-chord); }
    #unit-circle-distance .btn { display: inline-block; margin: 0; padding: .45em .7em; min-height: 44px; border: 1px solid var(--uc-line); border-radius: 5px; background: var(--uc-muted); color: inherit; font: inherit; font-size: .9em; cursor: pointer; }
    #unit-circle-distance .btn:hover { background: color-mix(in srgb, currentColor 16%, transparent); }
    #unit-circle-distance .btn:focus-visible, #unit-circle-distance input:focus-visible { outline: 2px solid var(--uc-chord); outline-offset: 3px; }
    #unit-circle-distance .tabular-nums { font-variant-numeric: tabular-nums; }
    #unit-circle-distance .text-small { font-size: .875em; }
    #unit-circle-distance .geometry { margin: 0; overflow: visible; }
    #unit-circle-distance .measure-heading { flex-wrap: wrap; }
    #unit-circle-distance .measure-name { min-width: 0; }
    @media (prefers-color-scheme: dark) {
      #unit-circle-distance { --uc-chord: #60a5fa; --uc-path: #fbbf24; }
    }

    #unit-circle-distance { color: var(--uc-fg); }
    #unit-circle-distance .angle-control { display: grid; gap: 8px; }
    #unit-circle-distance .angle-heading { display: flex; justify-content: space-between; gap: 12px; flex-wrap: wrap; }
    #unit-circle-distance .presets { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 8px; }
    #unit-circle-distance .geometry { width: 100%; display: block; }
    #unit-circle-distance .geometry text { fill: var(--uc-fg); }
    #unit-circle-distance .measure { margin-top: 16px; }
    #unit-circle-distance .measure-heading { display: flex; align-items: center; justify-content: space-between; gap: 12px; }
    #unit-circle-distance .measure-name { display: flex; align-items: center; gap: 8px; }
    #unit-circle-distance .swatch { display: inline-block; width: 22px; height: 3px; flex-shrink: 0; }
    #unit-circle-distance .track { height: 10px; background: var(--uc-muted); margin-top: 7px; overflow: hidden; }
    #unit-circle-distance .bar { height: 100%; }
    #unit-circle-distance .turn-status { margin-top: 14px; }
  </style>
  <h3>Chord and circular path</h3>
  <div class="angle-control">
    <div class="angle-heading">
      <label for="uc-angle">Angle u</label>
      <output id="uc-angle-value" for="uc-angle" class="tabular-nums">2.094 rad</output>
    </div>
    <input id="uc-angle" class="form-range" type="range" min="-12.566370614359172" max="12.566370614359172" step="any" value="2.0943951023931953" aria-label="Angle u in radians">
  </div>
  <div class="presets" aria-label="Example angles">
    <button type="button" class="btn" data-angle="1.5707963267948966">u = π/2</button>
    <button type="button" class="btn" data-angle="3.141592653589793">u = π</button>
    <button type="button" class="btn" data-angle="6.283185307179586">u = 2π</button>
    <button type="button" class="btn" data-angle="7.853981633974483">u = 5π/2</button>
  </div>
  <noscript><p>The straight segment joins 1 to eⁱᵘ. Its length is |eⁱᵘ − 1|; the circular path has length |u|. Enable JavaScript to move the endpoint.</p></noscript>
  <svg class="geometry" role="img" aria-label="Unit circle with a straight chord and a circular path joining 1 to e to the power i u"></svg>
  <div class="measure">
    <div class="measure-heading">
      <span class="measure-name"><span class="swatch" style="background: var(--uc-chord);"></span>Straight distance |eⁱᵘ − 1|</span>
      <output class="tabular-nums" id="uc-chord-value">1.732</output>
    </div>
    <div class="track" aria-hidden="true"><div id="uc-chord-bar" class="bar" style="background: var(--uc-chord); width: 13.78%;"></div></div>
  </div>
  <div class="measure">
    <div class="measure-heading">
      <span class="measure-name"><span class="swatch" style="background: var(--uc-path);"></span>Circular path length |u|</span>
      <output class="tabular-nums" id="uc-arc-value">2.094</output>
    </div>
    <div class="track" aria-hidden="true"><div id="uc-arc-bar" class="bar" style="background: var(--uc-path); width: 16.67%;"></div></div>
  </div>
  <div id="uc-turns" class="turn-status text-small" aria-live="polite">0 full turns · 2.094 rad counterclockwise</div>
  <script>
    (function () {
      const root = document.getElementById('unit-circle-distance');
      const input = root.querySelector('#uc-angle');
      const svg = root.querySelector('.geometry');
      const tau = 2 * Math.PI;
      const ns = 'http://www.w3.org/2000/svg';
      function el(tag, attrs, text) {
        const node = document.createElementNS(ns, tag);
        for (const key in attrs) node.setAttribute(key, attrs[key]);
        if (text !== undefined) node.textContent = text;
        svg.appendChild(node);
        return node;
      }
      function draw() {
        const u = Number(input.value);
        const a = Math.abs(u);
        const chord = 2 * Math.abs(Math.sin(u / 2));
        const width = Math.max(280, root.getBoundingClientRect().width);
        const height = Math.min(365, width + 35);
        const cx = width / 2, cy = height / 2;
        const r = Math.min((width - 112) / 2, (height - 80) / 2);
        const px = t => cx + r * Math.cos(t);
        const py = t => cy - r * Math.sin(t);
        svg.setAttribute('viewBox', '0 0 ' + width + ' ' + height);
        svg.replaceChildren();
        el('title', {}, 'Straight distance versus distance traveled on the unit circle');
        el('desc', {}, 'Angle ' + u.toFixed(3) + ' radians. Straight distance ' + chord.toFixed(3) + '. Circular path length ' + a.toFixed(3) + '.');
        el('line', {x1: cx-r-24, y1: cy, x2: cx+r+24, y2: cy, stroke: 'var(--uc-line)', 'stroke-width': 1});
        el('line', {x1: cx, y1: cy-r-24, x2: cx, y2: cy+r+24, stroke: 'var(--uc-line)', 'stroke-width': 1});
        el('circle', {cx, cy, r, fill: 'none', stroke: 'var(--uc-line)', 'stroke-width': 1.5});
        el('line', {x1: cx, y1: cy, x2: px(u), y2: py(u), stroke: 'var(--uc-secondary)', 'stroke-width': 1, 'stroke-dasharray': '4 5'});
        el('text', {x: cx+9, y: cy+19, 'font-size': 12}, '0');
        el('text', {x: cx+r+26, y: cy-10, 'text-anchor': 'end', 'font-size': 12}, 'Re');
        el('text', {x: cx+9, y: cy-r-19, 'font-size': 12}, 'Im');
        // Multiple complete turns follow the same geometric circle.
        const count = Math.max(1, Math.ceil(a / 0.035));
        let path = '';
        for (let k=0; k<=count; k++) {
          const t = u*k/count;
          path += (k ? ' L ' : 'M ') + px(t).toFixed(3) + ' ' + py(t).toFixed(3);
        }
        el('path', {d: path, fill: 'none', stroke: 'var(--uc-path)', 'stroke-width': 4, 'stroke-linecap': 'round'});
        if (a > 0.12) {
          const t = u - Math.sign(u)*Math.min(0.25, a*0.15);
          const x = px(t), y = py(t);
          const dx = -Math.sin(t)*Math.sign(u), dy = -Math.cos(t)*Math.sign(u);
          el('path', {d: 'M '+(x-9*dx-5*dy)+' '+(y-9*dy+5*dx)+' L '+x+' '+y+' L '+(x-9*dx+5*dy)+' '+(y-9*dy-5*dx), fill: 'none', stroke: 'var(--uc-path)', 'stroke-width': 2.5});
        }
        el('line', {x1: px(0), y1: py(0), x2: px(u), y2: py(u), stroke: 'var(--uc-chord)', 'stroke-width': 3});
        el('circle', {cx: px(0), cy: py(0), r: 5, fill: 'var(--uc-fg)'});
        el('circle', {cx: px(u), cy: py(u), r: 5, fill: 'var(--uc-chord)'});
        const overlap = chord < 0.14;
        el('text', {x: px(0)+12, y: py(0)+22, 'font-size': 14}, '1');
        const cos = Math.cos(u), sin = Math.sin(u);
        el('text', {
          x: overlap ? px(u)-14 : px(u)+(cos>0.25 ? 13 : cos<-.25 ? -13 : 0),
          y: overlap ? py(u)-16 : py(u)+(sin>=0 ? -15 : 24),
          'text-anchor': overlap ? 'end' : cos>.25 ? 'start' : cos<-.25 ? 'end' : 'middle',
          'font-size': 14
        }, 'eⁱᵘ');
        root.querySelector('#uc-angle-value').textContent = u.toFixed(3) + ' rad (' + (u/Math.PI).toFixed(2) + 'π)';
        root.querySelector('#uc-chord-value').textContent = chord.toFixed(3);
        root.querySelector('#uc-arc-value').textContent = a.toFixed(3);
        root.querySelector('#uc-chord-bar').style.width = (100*chord/(4*Math.PI))+'%';
        root.querySelector('#uc-arc-bar').style.width = (100*a/(4*Math.PI))+'%';
        const turns = Math.floor((a+1e-10)/tau);
        const remainder = Math.max(0, a-turns*tau);
        root.querySelector('#uc-turns').textContent = turns + ' full ' + (turns===1 ? 'turn' : 'turns') + ' · ' + remainder.toFixed(3) + ' rad' + (a<1e-10 ? '' : u>0 ? ' counterclockwise' : ' clockwise');
      }
      input.addEventListener('input', draw);
      root.querySelectorAll('[data-angle]').forEach(button => button.addEventListener('click', () => {
        input.value = button.getAttribute('data-angle');
        draw();
      }));
      new ResizeObserver(draw).observe(root);
      draw();
    })();
  </script>
</div>


Here is an algebraic derivation. By the fundamental theorem of calculus,

$$
e^{iu}-1=\int_0^1\frac{d}{dt}e^{itu}dt=iu\int_0^1e^{itu}dt.
$$

Taking absolute values and using $\lvert e^{itu}\rvert=1$ gives

$$
\lvert e^{iu}-1\rvert\leq\lvert u\rvert\int_0^1 1\,dt=\lvert u\rvert.
$$

The same bound can be recognized from

$$
\lvert e^{iu}-1\rvert=2\lvert\sin(u/2)\rvert\leq\lvert u\rvert.
$$

The useful general idea is that **a difference can be bounded by integrating the derivative**.

## Proposition

The Fourier transform of a function in $\mathcal{M}(\mathbb{R})$ is uniformly continuous.

*Proof.*

For any $\xi,h\in\mathbb{R}$,

$$
\widehat f(\xi+h)-\widehat f(\xi)=\int_{\mathbb{R}}f(x)e^{-2\pi ix\xi}\bigl(e^{-2\pi ixh}-1\bigr)dx.
$$

On $\lvert x\rvert\leq R$, use the exponential bound:

$$
\lvert e^{-2\pi ixh}-1\rvert\leq2\pi\lvert x\rvert\lvert h\rvert\leq2\pi R\lvert h\rvert.
$$

On $\lvert x\rvert>R$, use the triangle inequality:

$$
\lvert e^{-2\pi ixh}-1\rvert\leq2.
$$

Consequently,

$$
\lvert\widehat f(\xi+h)-\widehat f(\xi)\rvert
\leq2\pi R\lvert h\rvert\lVert f\rVert_1
+2\int_{\lvert x\rvert>R}\lvert f(x)\rvert dx.
$$

Given $\varepsilon>0$, first choose $R\geq1$ so that the tail integral is less than $\varepsilon/4$. Then choose

$$
\lvert h\rvert<\frac{\varepsilon}{4\pi R(1+\lVert f\rVert_1)}.
$$

Both terms together are less than $\varepsilon$. Since the bound is independent of $\xi$, this proves that $\widehat f$ is **uniformly continuous** on $\mathbb{R}$.

<div style="text-align: right;">\(\square\)</div>

## Definition

A continuous function $f:\mathbb{R}\to\mathbb{C}$ is **rapidly decreasing** if, for every integer $k\geq0$,

$$
\sup_{x\in\mathbb{R}}\lvert x\rvert^k\lvert f(x)\rvert<\infty.
$$

For $k=0$, the weight is understood to be $1$. This condition says that we can multiply $f$ by any fixed power of $\lvert x\rvert$ and still obtain a bounded function.

It also implies that $\lvert x\rvert^k\lvert f(x)\rvert\to0$ as $\lvert x\rvert\to\infty$. Indeed, the condition for $k+1$ gives a constant $C_{k+1}$ such that

$$
\lvert x\rvert^k\lvert f(x)\rvert\leq\frac{C_{k+1}}{\lvert x\rvert}
\qquad(\lvert x\rvert\geq1).
$$

Rapid decrease implies moderate decrease. If

$$
B_0=\sup_x\lvert f(x)\rvert,\qquad B_2=\sup_x\lvert x\rvert^2\lvert f(x)\rvert,
$$

then

$$
(1+x^2)\lvert f(x)\rvert\leq B_0+B_2.
$$

More generally, every polynomially weighted function $x^mf(x)$ is rapidly decreasing, since its $k$th weighted bound is one of the bounds for $f$. In particular,

$$
\int_{\mathbb{R}}\lvert x\rvert^m\lvert f(x)\rvert dx<\infty
\qquad(m=0,1,2,\ldots).
$$

## Definition

An infinitely differentiable function $f$ belongs to the **Schwartz class** $\mathcal{S}(\mathbb{R})$ if every derivative is rapidly decreasing. Equivalently,

$$
\sup_{x\in\mathbb{R}}\lvert x\rvert^k\lvert f^{(m)}(x)\rvert<\infty
\qquad\text{for all integers }k,m\geq0.
$$

Thus $f$, its derivatives, and their polynomially weighted versions are absolutely integrable. These bounds justify the operations used below.

## Proposition

Let $f\in\mathcal{S}(\mathbb{R})$, $h\in\mathbb{R}$, and $\delta>0$. With the Fourier convention above, the following identities hold for every $\xi\in\mathbb{R}$:

$$\begin{aligned}\mathcal{F}[f(\cdot+h)](\xi)&=e^{2\pi ih\xi}\widehat f(\xi),\\\mathcal{F}[f(\cdot)e^{-2\pi ih(\cdot)}](\xi)&=\widehat f(\xi+h),\\\mathcal{F}[f(\delta\cdot)](\xi)&=\delta^{-1}\widehat f(\xi/\delta),\\\mathcal{F}[f^{\prime}](\xi)&=2\pi i\xi\widehat f(\xi),\\\mathcal{F}[-2\pi i(\cdot)f(\cdot)](\xi)&=\frac{d}{d\xi}\widehat f(\xi).\end{aligned}$$

Here, $\mathcal{F}[g]=\widehat g$, and the dot denotes the input variable. For example,

$$\mathcal{F}[(\cdot)f(\cdot)](\xi)=\int_{\mathbb{R}}xf(x)e^{-2\pi ix\xi}dx.$$

Thus $\mathcal{F}[-2\pi i(\cdot)f(\cdot)]$ denotes the Fourier transform of the function $x\mapsto-2\pi ix f(x)$.

The first three identities follow from changes of variables or combining exponentials. The last two describe how the Fourier transform relates differentiation and multiplication. In particular, $\mathcal{F}[f^{\prime}]$ is the Fourier transform of the derivative of $f$, whereas $\frac{d}{d\xi}\widehat f$ is the derivative of the Fourier transform of $f$.

*Proof.*

**(1) Translation becomes modulation.**

Set $u=x+h$, so $x=u-h$. Then

$$\begin{aligned}\mathcal{F}[f(\cdot+h)](\xi)&=\int_{\mathbb{R}}f(x+h)e^{-2\pi ix\xi}dx\\&=\int_{\mathbb{R}}f(u)e^{-2\pi i(u-h)\xi}du\\&=e^{2\pi ih\xi}\int_{\mathbb{R}}f(u)e^{-2\pi iu\xi}du\\&=e^{2\pi ih\xi}\widehat f(\xi).\end{aligned}$$

A shift in the original function introduces a phase factor in its Fourier transform. Absolute convergence justifies the substitution on the whole real line.

**(2) Modulation becomes translation.**

Multiplying two exponentials adds their exponents:

$$\begin{aligned}\mathcal{F}[f(\cdot)e^{-2\pi ih(\cdot)}](\xi)&=\int_{\mathbb{R}}f(x)e^{-2\pi ixh}e^{-2\pi ix\xi}dx\\&=\int_{\mathbb{R}}f(x)e^{-2\pi ix(\xi+h)}dx\\&=\widehat f(\xi+h).\end{aligned}$$

Thus multiplying $f$ by an oscillation shifts the frequency argument of its transform.

**(3) Dilation reverses the frequency scale.**

Set $u=\delta x$, so $dx=du/\delta$. Then

$$\begin{aligned}\mathcal{F}[f(\delta\cdot)](\xi)&=\int_{\mathbb{R}}f(\delta x)e^{-2\pi ix\xi}dx\\&=\frac{1}{\delta}\int_{\mathbb{R}}f(u)e^{-2\pi iu(\xi/\delta)}du\\&=\frac{1}{\delta}\widehat f(\xi/\delta).\end{aligned}$$

If $\delta>1$, the original function is compressed horizontally. Its transform is stretched horizontally, with a compensating factor $1/\delta$.

**(4) Differentiation becomes multiplication.**

For a finite $R>0$, integration by parts gives

$$\begin{aligned}\int_{-R}^{R}f^{\prime}(x)e^{-2\pi ix\xi}dx&=\left[f(x)e^{-2\pi ix\xi}\right]_{-R}^{R}\\&\quad+2\pi i\xi\int_{-R}^{R}f(x)e^{-2\pi ix\xi}dx.\end{aligned}$$

Since $f$ is rapidly decreasing, $f(R)$ and $f(-R)$ tend to zero. More precisely,

$$\left\lvert\left[f(x)e^{-2\pi ix\xi}\right]_{-R}^{R}\right\rvert\leq\lvert f(R)\rvert+\lvert f(-R)\rvert\longrightarrow0.$$

Both $f$ and $f^{\prime}$ are absolutely integrable, so taking $R\to\infty$ yields

$$\mathcal{F}[f^{\prime}](\xi)=2\pi i\xi\widehat f(\xi).$$

The factor $2\pi i\xi$ comes from differentiating the exponential during integration by parts.

**(5) Multiplication becomes differentiation.**

We now prove

$$\begin{aligned}\frac{d}{d\xi}\widehat f(\xi)&=\mathcal{F}[-2\pi i(\cdot)f(\cdot)](\xi)\\&=-2\pi i\mathcal{F}[(\cdot)f(\cdot)](\xi)\\&=\int_{\mathbb{R}}(-2\pi ix)f(x)e^{-2\pi ix\xi}dx.\end{aligned}$$

Formally, this is what we obtain by differentiating $e^{-2\pi ix\xi}$ with respect to $\xi$ inside the integral. We justify this interchange directly by showing that the difference quotient approaches the claimed derivative.

**Step 1: isolate the error.**

For a nonzero increment $h$, define

$$R_h(x):=\frac{e^{-2\pi ixh}-1+2\pi ixh}{h}=\frac{e^{-2\pi ixh}-1}{h}+2\pi ix.$$

Linearity of absolutely convergent integrals gives

$$\begin{aligned}&\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}+2\pi i\mathcal{F}[(\cdot)f(\cdot)](\xi)\\&\qquad=\int_{\mathbb{R}}f(x)e^{-2\pi ix\xi}R_h(x)dx.\end{aligned}$$

Therefore,

$$\begin{aligned}&\left\lvert\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}+2\pi i\mathcal{F}[(\cdot)f(\cdot)](\xi)\right\rvert\\&\qquad\leq\int_{\mathbb{R}}\lvert f(x)\rvert\lvert R_h(x)\rvert dx.\end{aligned}$$

Our task is to show that the integral on the right tends to zero as $h\to0$.

**Step 2: predict the useful bound from cancellation.**

For fixed $x$, Taylor expansion suggests why the error is small:

$$e^{-2\pi ixh}=1-2\pi ixh+\frac{(-2\pi ixh)^2}{2}+\cdots.$$

Subtracting $1$ and adding $2\pi ixh$ cancels the constant and linear terms. The numerator of $R_h(x)$ therefore begins with a term proportional to $x^2h^2$. Dividing by $h$ suggests a bound proportional to $x^2\lvert h\rvert$.

This calculation helps us discover the estimate. We next prove an explicit inequality valid for every real $x$ and every nonzero $h$.

**Step 3: derive the explicit bound.**

Apply the fundamental theorem of calculus in the parameter $t$:

$$e^{-2\pi ixh}-1=-2\pi ixh\int_0^1e^{-2\pi ixht}dt.$$

After dividing by $h$ and adding $2\pi ix$, we obtain

$$R_h(x)=2\pi ix\int_0^1\bigl(1-e^{-2\pi ixht}\bigr)dt.$$

Using the previously established inequality $\lvert1-e^{iu}\rvert\leq\lvert u\rvert$, we get

$$\begin{aligned}\lvert R_h(x)\rvert&\leq2\pi\lvert x\rvert\int_0^1\lvert1-e^{-2\pi ixht}\rvert dt\\&\leq2\pi\lvert x\rvert\int_0^1 2\pi\lvert x\rvert\lvert h\rvert t\,dt\\&=2\pi^2x^2\lvert h\rvert.\end{aligned}$$

In particular, on a fixed interval $[-R,R]$,

$$\sup_{\lvert x\rvert\leq R}\lvert R_h(x)\rvert\leq2\pi^2R^2\lvert h\rvert\longrightarrow0\qquad(h\to0).$$

The bound controls every $x$ in the interval with the same choice of $h$, so the convergence is uniform on that interval.

**Step 4: obtain a bound for the tails that is independent of $h$.**

For every real $x$ and every nonzero $h$,

$$\begin{aligned}\lvert R_h(x)\rvert&\leq\frac{\lvert e^{-2\pi ixh}-1\rvert}{\lvert h\rvert}+2\pi\lvert x\rvert\\&\leq2\pi\lvert x\rvert+2\pi\lvert x\rvert\\&=4\pi\lvert x\rvert.\end{aligned}$$

This bound is independent of $h$. After multiplication by $\lvert f(x)\rvert$, it involves only the integrable function $\lvert x\rvert\lvert f(x)\rvert$, which lets us control the tails uniformly in $h$.

**Step 5: combine the bounds and choose the parameters.**

Splitting at $R\geq1$ gives

$$\begin{aligned}\int_{\mathbb{R}}\lvert f(x)\rvert\lvert R_h(x)\rvert dx&=\int_{-R}^{R}\lvert f(x)\rvert\lvert R_h(x)\rvert dx\\&\quad+\int_{\lvert x\rvert>R}\lvert f(x)\rvert\lvert R_h(x)\rvert dx\\&\leq2\pi^2R^2\lvert h\rvert\int_{-R}^{R}\lvert f(x)\rvert dx\\&\quad+4\pi\int_{\lvert x\rvert>R}\lvert x\rvert\lvert f(x)\rvert dx\\&\leq2\pi^2R^2\lvert h\rvert\lVert f\rVert_1\\&\quad+4\pi\int_{\lvert x\rvert>R}\lvert x\rvert\lvert f(x)\rvert dx.\end{aligned}$$

Given $\varepsilon>0$, first choose $R\geq1$ large enough that

$$\int_{\lvert x\rvert>R}\lvert x\rvert\lvert f(x)\rvert dx<\frac{\varepsilon}{8\pi}.$$

Such an $R$ exists because $xf(x)$ is absolutely integrable. The tail contribution is then less than $\varepsilon/2$, independently of $h$.

With this $R$ fixed, choose

$$0<\lvert h\rvert<\frac{\varepsilon}{4\pi^2R^2(1+\lVert f\rVert_1)}.$$

The contribution from $[-R,R]$ is then less than $\varepsilon/2$. Hence

$$\int_{\mathbb{R}}\lvert f(x)\rvert\lvert R_h(x)\rvert dx<\varepsilon.$$

Combining this with Step 1 shows that

$$\lim_{h\to0}\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}=-2\pi i\mathcal{F}[(\cdot)f(\cdot)](\xi)=\mathcal{F}[-2\pi i(\cdot)f(\cdot)](\xi).$$

This proves the fifth identity. Since every estimate is independent of $\xi$, the difference quotients in fact converge uniformly in $\xi$.

**A useful shortcut for Schwartz functions.**

Since $x^2f(x)$ is absolutely integrable, we can also integrate the estimate from Step 3 over the whole line:

$$\begin{aligned}&\left\lvert\frac{\widehat f(\xi+h)-\widehat f(\xi)}{h}+2\pi i\mathcal{F}[(\cdot)f(\cdot)](\xi)\right\rvert\\&\qquad\leq2\pi^2\lvert h\rvert\int_{\mathbb{R}}x^2\lvert f(x)\rvert dx\longrightarrow0\qquad(h\to0).\end{aligned}$$

Thus, for Schwartz functions, this single estimate also completes the proof. The longer argument above requires only continuity and absolute integrability of $f$ and $xf$, and explains the same division into a bounded interval and tails used elsewhere in this post.

<div style="text-align: right;">\(\square\)</div>



## Corollary

For $\delta>0$, define

$$
K_\delta(x)=\delta^{-1/2}g(x/\sqrt{\delta})=\frac{1}{\sqrt{\delta}}e^{-\pi x^2/\delta}, \quad g(x)=e^{-\pi x^2}.
$$

As $\delta$ decreases, the kernel becomes narrower and taller. Its horizontal scale is $\sqrt{\delta}$, and the factor $1/\sqrt{\delta}$ keeps its total integral equal to $1$.

*Proof.*

The dilation identity gives

$$
\begin{aligned}
\widehat{K_\delta}(\xi)
&=\delta^{-1/2}\frac{1}{\delta^{-1/2}}\widehat g\bigl(\xi/\delta^{-1/2}\bigr)\\
&=\widehat g(\sqrt{\delta}\xi)\\
&=e^{-\pi\delta\xi^2}.
\end{aligned}
$$

<div style="text-align: right;">\(\square\)</div>

## Theorem

The Gaussian kernels $\lbrace K_\delta\rbrace_{\delta>0}$ form an approximate identity as $\delta\to0^+$.

A family of absolutely integrable kernels $\lbrace K_\delta\rbrace_{\delta>0}$ is an **approximate identity** as $\delta\to0^+$ if:

1. Each kernel has total integral $1$.
2. There is a constant $C$, independent of $\delta$, such that $\int_{\mathbb{R}}\lvert K_\delta(x)\rvert dx\leq C$.
3. For every fixed $\eta>0$, the absolute mass outside $[-\eta,\eta]$ tends to zero.

The first property preserves constants when averaging. The second controls the total size of the averaging weights. The third says that those weights become concentrated near the origin.

*Proof.*

We verify all three properties for the Gaussian kernels.

**Total integral.** Substitute $u=x/\sqrt{\delta}$, so $dx=\sqrt{\delta}du$:

$$
\begin{aligned}
\int_{\mathbb{R}}K_\delta(x)dx
&=\int_{\mathbb{R}}\frac{1}{\sqrt{\delta}}e^{-\pi x^2/\delta}dx\\
&=\int_{\mathbb{R}}e^{-\pi u^2}du=1.
\end{aligned}
$$

**Uniform bound on the absolute integral.** Since $K_\delta(x)>0$,

$$
\int_{\mathbb{R}}\lvert K_\delta(x)\rvert dx=\int_{\mathbb{R}}K_\delta(x)dx=1.
$$

Thus we may take $C=1$ for every $\delta>0$.

**Concentration near the origin.** For any fixed $\eta>0$, the same substitution gives

$$
\int_{\lvert x\rvert>\eta}K_\delta(x)dx=\int_{\lvert u\rvert>\eta/\sqrt{\delta}}e^{-\pi u^2}du.
$$

The threshold $\eta/\sqrt{\delta}$ tends to infinity as $\delta\to0^+$. We are therefore integrating over tails farther and farther from the origin, so the integral tends to zero.

There is also an explicit bound. For $L>0$, symmetry and $u/L\geq1$ when $u\geq L$ give

$$
\begin{aligned}
\int_{\lvert u\rvert>L}e^{-\pi u^2}du
&=2\int_L^\infty e^{-\pi u^2}du\\
&\leq\frac{2}{L}\int_L^\infty ue^{-\pi u^2}du\\
&=\frac{e^{-\pi L^2}}{\pi L}.
\end{aligned}
$$

Setting $L=\eta/\sqrt{\delta}$ yields

$$
\int_{\lvert x\rvert>\eta}K_\delta(x)dx
\leq\frac{\sqrt{\delta}}{\pi\eta}e^{-\pi\eta^2/\delta}\longrightarrow0.
$$

This proves that the Gaussian kernels form an approximate identity.

<div style="text-align: right;">\(\square\)</div>

## Definition

For $f,g\in\mathcal{S}(\mathbb{R})$, define their **convolution** by

$$
(f*g)(x)=\int_{\mathbb{R}}f(x-t)g(t)dt.
$$

For each fixed $x$, this integral converges absolutely, because $f$ is bounded and $g$ is absolutely integrable:

$$
\int_{\mathbb{R}}\lvert f(x-t)g(t)\rvert dt\leq\lVert f\rVert_\infty\lVert g\rVert_1<\infty,
$$

where $\lVert f\rVert_\infty=\sup_{x\in\mathbb{R}}\lvert f(x)\rvert$.

In particular, $(f*K_\delta)(x)$ is a weighted average of values of $f$ near $x$. As $K_\delta$ concentrates near $t=0$, the values being averaged should approach $f(x)$.

## Corollary

For every $f\in\mathcal{S}(\mathbb{R})$,

$$\lim_{\delta\to0^+}\sup_{x\in\mathbb{R}}\lvert(f*K_\delta)(x)-f(x)\rvert=0.$$

*Proof.*

We first show that $f$ is uniformly continuous on the whole real line. We then split the convolution error into nearby and distant contributions: nearby function values are close to $f(x)$, and the Gaussian kernel assigns little total weight to distant values.

**Step 1: prove uniform continuity using decay and compactness.**

Since $f$ is a Schwartz function, the definition of rapid decrease with $k=1$ gives a finite constant

$$C:=\sup_{x\in\mathbb{R}}\lvert x\rvert\lvert f(x)\rvert<\infty.$$

Thus, for $x\neq0$,

$$\lvert f(x)\rvert\leq\frac{C}{\lvert x\rvert}.$$

The constant $C$ depends only on $f$, not on $x$. The bound tends to zero as $\lvert x\rvert\to\infty$, so it gives an explicit way to make $f(x)$ small. Given $\varepsilon>0$, choose

$$N=1+\frac{4C}{\varepsilon}.$$

Then, whenever $\lvert x\rvert>N$,

$$\lvert f(x)\rvert\leq\frac{C}{\lvert x\rvert}\leq\frac{C}{N}<\frac{\varepsilon}{4}.$$

We use $\varepsilon/4$ because we will add two such bounds. Making each function value smaller than $\varepsilon/4$ makes their sum smaller than $\varepsilon/2$.

If both $x$ and $y$ lie outside $[-N,N]$, the triangle inequality gives

$$\lvert f(x)-f(y)\rvert\leq\lvert f(x)\rvert+\lvert f(y)\rvert<\frac{\varepsilon}{4}+\frac{\varepsilon}{4}=\frac{\varepsilon}{2}.$$

Inside a bounded interval, we use continuity instead. Consider the slightly larger interval $[-N-1,N+1]$. Since it is closed and bounded, $f$ is uniformly continuous there. Thus there is a $\rho_0>0$ such that

$$x,y\in[-N-1,N+1],\lvert x-y\rvert<\rho_0\Longrightarrow\lvert f(x)-f(y)\rvert<\frac{\varepsilon}{2}.$$

Choose $\rho>0$ with $\rho\leq1$ and $\rho\leq\rho_0$, and suppose that $\lvert x-y\rvert<\rho$. If both points lie outside $[-N,N]$, the first bound applies. Otherwise, at least one point lies in $[-N,N]$. Suppose it is $x$. Then

$$\lvert y\rvert\leq\lvert x\rvert+\lvert y-x\rvert<N+1,$$

so both points lie in $[-N-1,N+1]$, and the uniform continuity bound applies. The case where $y$ lies in $[-N,N]$ is the same with the roles reversed.

Consequently, every pair with $\lvert x-y\rvert<\rho$ satisfies $\lvert f(x)-f(y)\rvert<\varepsilon/2$. This proves uniform continuity on all of $\mathbb{R}$. The enlarged interval is important: it covers pairs with one point just inside $[-N,N]$ and the other just outside.

Also, $f$ is bounded because it is continuous on bounded closed intervals and tends to zero at infinity. Set $B=\lVert f\rVert_\infty<\infty$.

**Step 2: split the convolution error into nearby and distant contributions.**

The Gaussian kernels are nonnegative and have total integral $1$. Therefore,

$$\begin{aligned}(f*K_\delta)(x)-f(x)&=\int_{\mathbb{R}}K_\delta(t)f(x-t)dt-f(x)\int_{\mathbb{R}}K_\delta(t)dt\\&=\int_{\mathbb{R}}K_\delta(t)\bigl(f(x-t)-f(x)\bigr)dt.\end{aligned}$$

These integrals converge absolutely because $f$ is bounded and $K_\delta$ is integrable.

Fix $\varepsilon>0$. By Step 1, choose $\eta>0$, independent of $x$, such that

$$\lvert t\rvert<\eta\Longrightarrow\lvert f(x-t)-f(x)\rvert<\frac{\varepsilon}{2}\text{ for every }x\in\mathbb{R}.$$

For $\lvert t\rvert<\eta$, the function values are close, so

$$\int_{\lvert t\rvert<\eta}K_\delta(t)\lvert f(x-t)-f(x)\rvert dt\leq\frac{\varepsilon}{2}\int_{\lvert t\rvert<\eta}K_\delta(t)dt\leq\frac{\varepsilon}{2}.$$

For $\lvert t\rvert\geq\eta$, use boundedness:

$$\lvert f(x-t)-f(x)\rvert\leq\lvert f(x-t)\rvert+\lvert f(x)\rvert\leq2B.$$

Combining the two regions gives

$$\begin{aligned}\lvert(f*K_\delta)(x)-f(x)\rvert&\leq\int_{\lvert t\rvert<\eta}K_\delta(t)\lvert f(x-t)-f(x)\rvert dt\\&+\int_{\lvert t\rvert\geq\eta}K_\delta(t)\lvert f(x-t)-f(x)\rvert dt\\&\leq\frac{\varepsilon}{2}+2B\int_{\lvert t\rvert\geq\eta}K_\delta(t)dt.\end{aligned}$$

The remaining integral is the total weight assigned to distant values. To see why it tends to zero, substitute $u=t/\sqrt{\delta}$:

$$\int_{\lvert t\rvert\geq\eta}K_\delta(t)dt=\int_{\lvert u\rvert\geq\eta/\sqrt{\delta}}e^{-\pi u^2}du\longrightarrow0.$$

Here $\eta$ is fixed, so $\eta/\sqrt{\delta}\to\infty$ as $\delta\to0^+$. The integral therefore runs over tails farther and farther from the origin, and those tails have vanishing integrals because the Gaussian is absolutely integrable.

Choose $\delta_0>0$ such that, whenever $0<\delta<\delta_0$,

$$\int_{\lvert t\rvert\geq\eta}K_\delta(t)dt<\frac{\varepsilon}{4(1+B)}.$$

The error bound is independent of $x$. Taking the supremum gives

$$\begin{aligned}\sup_{x\in\mathbb{R}}\lvert(f*K_\delta)(x)-f(x)\rvert&\leq\frac{\varepsilon}{2}+2B\int_{\lvert t\rvert\geq\eta}K_\delta(t)dt\\&\leq\frac{\varepsilon}{2}+\frac{B\varepsilon}{2(1+B)}\\&=\varepsilon-\frac{\varepsilon}{2(1+B)}<\varepsilon.\end{aligned}$$

This proves uniform convergence. The order of the choices is: first choose $\eta$ so that nearby function values are close, then choose $\delta$ so that the kernel assigns little total weight to distant values.

<div style="text-align: right;">\(\square\)</div>

## Remark

**Explicit convergence rate.**

The preceding proof explains convergence using uniform continuity and concentration of the kernel. For a Schwartz function, boundedness of the derivative also gives an explicit estimate for how quickly the error decreases.

Set $L=\lVert f'\rVert_\infty<\infty$. By the fundamental theorem of calculus,

$$f(x-t)-f(x)=-t\int_0^1f'(x-st)ds.$$

Taking absolute values gives

$$\lvert f(x-t)-f(x)\rvert\leq\lvert t\rvert\int_0^1\lvert f'(x-st)\rvert ds\leq L\lvert t\rvert.$$

Thus the change in $f$ is at most its maximum derivative magnitude multiplied by the distance $\lvert t\rvert$. Using the convolution error identity and positivity of $K_\delta$,

$$\begin{aligned}\lvert(f*K_\delta)(x)-f(x)\rvert&\leq\int_{\mathbb{R}}K_\delta(t)\lvert f(x-t)-f(x)\rvert dt\\&\leq L\int_{\mathbb{R}}\lvert t\rvert K_\delta(t)dt.\end{aligned}$$

The remaining integral measures the average distance from zero under the Gaussian weights. Substitute $u=t/\sqrt{\delta}$, so that $t=\sqrt{\delta}u$ and $dt=\sqrt{\delta}du$:

$$\begin{aligned}\int_{\mathbb{R}}\lvert t\rvert K_\delta(t)dt&=\int_{\mathbb{R}}\frac{\lvert t\rvert}{\sqrt{\delta}}e^{-\pi t^2/\delta}dt\\&=\sqrt{\delta}\int_{\mathbb{R}}\lvert u\rvert e^{-\pi u^2}du\\&=2\sqrt{\delta}\int_0^\infty ue^{-\pi u^2}du\\&=\frac{\sqrt{\delta}}{\pi}.\end{aligned}$$

For the last equality, use $v=\pi u^2$, which gives

$$\int_0^\infty ue^{-\pi u^2}du=\frac{1}{2\pi}\int_0^\infty e^{-v}dv=\frac{1}{2\pi}.$$

Since the bound is independent of $x$, we conclude that

$$\sup_{x\in\mathbb{R}}\lvert(f*K_\delta)(x)-f(x)\rvert\leq\frac{\lVert f'\rVert_\infty}{\pi}\sqrt{\delta}.$$

This gives a uniform error bound proportional to $\sqrt{\delta}$. Its two factors have a direct interpretation: $\lVert f'\rVert_\infty$ controls how quickly $f$ can change, and $\sqrt{\delta}/\pi$ is the average distance over which the Gaussian kernel averages its values.

<div style="text-align: right;">\(\square\)</div>

## Reference

- Elias M. Stein and Rami Shakarchi, *Fourier Analysis: An Introduction*.
- [Math 139 Fourier Analysis Notes](https://drive.google.com/file/d/1f1pp1QkF0BqqLELBrKyk69X0ofd3SjdR/view?usp=sharing).
