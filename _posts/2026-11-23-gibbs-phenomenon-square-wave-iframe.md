---
layout: single
title: "The Gibbs Phenomenon of the Square Wave"
date: 2026-11-23
excerpt: "Why adding more sine waves never removes the overshoot at a jump, and exactly how big it is."
categories:
  - Fourier Analysis
tags:
  - Fourier series
  - Gibbs phenomenon
  - square wave
author_profile: true
read_time: true
toc: true
toc_label: "Contents"
toc_sticky: true
---

<script>
window.MathJax = {
  tex: { inlineMath: [['\\(', '\\)']], displayMath: [['\\[', '\\]']] },
  startup: {
    ready: function () {
      // Kramdown turns $$...$$ into <script type="math/tex">; convert to delimiters MathJax 3 reads.
      document.querySelectorAll('script[type^="math/tex"]').forEach(function (s) {
        var display = s.type.indexOf('mode=display') !== -1;
        var span = document.createElement(display ? 'div' : 'span');
        span.textContent = display ? '\\[' + s.text + '\\]' : '\\(' + s.text + '\\)';
        s.parentNode.replaceChild(span, s);
      });
      MathJax.startup.defaultReady();
    }
  }
};
</script>
<script async src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-chtml.js"></script>

Take a function with a jump in it, write it as a sum of sines and cosines, and keep adding terms. Away from the jump the sums settle down nicely. At the jump they do something surprising: they overshoot, and the overshoot does not go away. This post builds the idea from the beginning, using the simplest example, the square wave, and ends with an exact computation of the overshoot.

## 1. Periodic functions

A function $$f$$ is **periodic with period $$2\pi$$** if $$f(x+2\pi)=f(x)$$ for every $$x$$. The basic examples are $$\sin(kx)$$ and $$\cos(kx)$$ for integers $$k\ge 1$$. Because of periodicity, it is enough to describe $$f$$ on one interval such as $$(-\pi,\pi)$$.

## 2. The square wave

Our test function is

$$
f(x)=\begin{cases}-1, & -\pi<x<0,\\ \;\;\,1, & 0<x<\pi,\end{cases}
\qquad f(x+2\pi)=f(x).
$$

It is smooth except at multiples of $$\pi$$, where it **jumps** by $$2$$. The value at the jump itself does not matter for what follows. Everything interesting happens near $$x=0$$.

## 3. Fourier series

The idea of Fourier analysis is to write a periodic function as a sum of sines and cosines:

$$
f(x)\sim \frac{a_0}{2}+\sum_{k=1}^{\infty}\bigl(a_k\cos kx+b_k\sin kx\bigr),
$$

where the **Fourier coefficients** are

$$
a_k=\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\cos kx\,dx,\qquad
b_k=\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\sin kx\,dx .
$$

These formulas come from the orthogonality of the trigonometric functions on $$[-\pi,\pi]$$. For example, $$\int_{-\pi}^{\pi}\sin jx\,\sin kx\,dx=0$$ for $$j\neq k$$ and equals $$\pi$$ when $$j=k\ge 1$$. Multiplying the series by $$\sin kx$$ and integrating isolates $$b_k$$.

### Coefficients of the square wave

The square wave is an odd function, so $$f(x)\cos kx$$ is odd and every $$a_k=0$$. For the sine coefficients, since $$f(x)\sin kx$$ is even,

$$
b_k=\frac{2}{\pi}\int_0^{\pi}\sin kx\,dx=\frac{2}{\pi}\cdot\frac{1-\cos k\pi}{k}.
$$

Since $$\cos k\pi=(-1)^k$$, we get $$b_k=\dfrac{4}{\pi k}$$ when $$k$$ is odd and $$b_k=0$$ when $$k$$ is even. Therefore

$$
f(x)\sim\frac{4}{\pi}\left(\sin x+\frac{\sin 3x}{3}+\frac{\sin 5x}{5}+\cdots\right)
=\frac{4}{\pi}\sum_{j=1}^{\infty}\frac{\sin\bigl((2j-1)x\bigr)}{2j-1}.
$$

## 4. Partial sums

Let $$S_m$$ be the partial sum with the first $$m$$ nonzero terms:

$$
S_m(x)=\frac{4}{\pi}\sum_{j=1}^{m}\frac{\sin\bigl((2j-1)x\bigr)}{2j-1}.
$$

At every point where $$f$$ is continuous, $$S_m(x)\to f(x)$$ as $$m\to\infty$$. The question is what $$S_m$$ looks like near the jump. Try it yourself in the interactive figure below. Drag the slider, turn on "show first harmonics", and then compare the zoomed plot near $$x=0$$.

<iframe src="{{ '/assets/gibbs-demo.html' | relative_url }}"
        title="Interactive Gibbs phenomenon demo"
        style="width:100%;height:1450px;border:0;"
        loading="lazy"></iframe>

## 5. Where the overshoot comes from

To find the height of the bump, locate the maximum of $$S_m$$ near $$0$$. Differentiating and using the identity $$\sum_{j=1}^{m}\cos\bigl((2j-1)x\bigr)=\dfrac{\sin 2mx}{2\sin x}$$ gives

$$
S_m'(x)=\frac{4}{\pi}\sum_{j=1}^{m}\cos\bigl((2j-1)x\bigr)=\frac{2}{\pi}\,\frac{\sin 2mx}{\sin x}.
$$

The first positive zero is at $$x_m=\dfrac{\pi}{2m}$$, and $$S_m$$ increases on $$(0,x_m)$$, so this is the first peak. Its height is

$$
S_m(x_m)=\frac{2}{\pi}\int_0^{\pi/2m}\frac{\sin 2mt}{\sin t}\,dt .
$$

Substitute $$u=2mt$$. For large $$m$$ the variable $$t=u/2m$$ is small, so $$\sin t\approx t$$ and the integral becomes

$$
S_m(x_m)\;\longrightarrow\;\frac{2}{\pi}\int_0^{\pi}\frac{\sin u}{u}\,du=\frac{2}{\pi}\,\mathrm{Si}(\pi)\approx 1.17898 .
$$

The true value just to the right of the jump is $$1$$, so the partial sums overshoot by about $$0.17898$$. The jump has size $$2$$, so the overshoot is

$$
\frac{\tfrac{2}{\pi}\mathrm{Si}(\pi)-1}{2}\approx 0.0895,
$$

about **9% of the jump**, no matter how many terms we take. This is the **Gibbs phenomenon**. The sums converge to $$f$$ at each fixed point away from the jump, but the convergence is not uniform near the jump.

A quick numerical check, which you can run yourself:

```python
import numpy as np

def S(x, m):
    k = 2 * np.arange(1, m + 1) - 1
    return 4 / np.pi * np.sum(np.sin(np.outer(x, k)) / k, axis=1)

x = np.linspace(1e-6, np.pi / 2, 200_000)
for m in [1, 5, 25, 100, 500]:
    peak = S(x, m).max()
    print(m, round(peak, 4), round((peak - 1) / 2, 4))
```

The peak climbs toward $$1.1790$$ and the overshoot relative to the jump toward $$0.0895$$.

## 6. Can the overshoot be removed?

Yes, by changing how we add up the terms. Both of the following multiply the $$k$$-th term by a damping factor $$\sigma_k$$, where $$M=2m-1$$ is the highest harmonic used:

$$
\text{Lanczos: }\ \sigma_k=\frac{\sin\bigl(\pi k/(M+1)\bigr)}{\pi k/(M+1)},
\qquad
\text{Fejér: }\ \sigma_k=1-\frac{k}{M+1}.
$$

Use the "Method" menu in the demo above to compare them with the plain partial sum. The Fejér means are averages of partial sums and have no overshoot at all, because the Fejér kernel is positive.

## Exercises

1. Compute the Fourier series of the sawtooth $$g(x)=x$$ on $$(-\pi,\pi)$$. Does the Gibbs phenomenon occur at $$x=\pm\pi$$? How large is the overshoot relative to the jump?
2. Plug $$x=\pi/2$$ into the Fourier series of the square wave and derive the Leibniz formula $$1-\tfrac13+\tfrac15-\cdots=\tfrac{\pi}{4}$$.
3. Show that $$\dfrac{2}{\pi}\mathrm{Si}(\pi)=\dfrac{2}{\pi}\displaystyle\int_0^{\pi}\dfrac{\sin u}{u}\,du$$ can be computed from the Taylor series of $$\sin u/u$$, and use it to confirm $$1.17898$$.

## References

- H. S. Carslaw, *Introduction to the Theory of Fourier's Series and Integrals*, 1921.
- E. M. Stein and R. Shakarchi, *Fourier Analysis: An Introduction*, Princeton University Press, 2003.
- G. B. Folland, *Fourier Analysis and Its Applications*, AMS, 2009.
- A. Zygmund, *Trigonometric Series*, Cambridge University Press, 2015.
- E. Hewitt and R. E. Hewitt, "The Gibbs–Wilbraham phenomenon: an episode in Fourier analysis," *Archive for History of Exact Sciences* 21 (1979), 129–160.
