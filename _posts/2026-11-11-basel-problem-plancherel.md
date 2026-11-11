---
title: "Proof of $$\\sum_{n=1}^\\infty n^{-2}=\\pi^2/6$$ via the Plancherel Identity"
date: 2026-11-11
categories:
  - blog
tags:
  - Fourier analysis
  - Plancherel identity
  - Basel problem
  - infinite series
mathjax: true
toc: true
toc_label: "Contents"
toc_sticky: true
excerpt: "A short proof of the Basel problem using Fourier coefficients of the sawtooth function and the Plancherel (Parseval) identity."
---
![A description of the banner image for accessibility](/assets/images/your-banner-image.jpg)
The **Basel problem** asks for the exact value of $$\sum_{n=1}^\infty n^{-2}$$. Euler's answer, $$\pi^2/6$$, has many proofs. One of the cleanest comes from Fourier analysis: compute the Fourier coefficients of a very simple function, then let the Plancherel identity do the rest.

In this post we go through that argument in detail. The idea is to compute the energy of a function in two ways, once in "space" and once in "frequency", and then compare.

## 1. Setting and the Plancherel identity

Let $$L^2(0,1)$$ denote the space of square-integrable functions $$f:[0,1]\to\mathbb{C}$$ with inner product and norm

$$
\langle f,g\rangle=\int_0^1 f(x)\overline{g(x)}\,dx,
\qquad
\|f\|^2=\int_0^1 |f(x)|^2\,dx .
$$

For $$n\in\mathbb{Z}$$ put $$e_n(x)=e^{2\pi i n x}$$. The **$$n$$th Fourier coefficient** of $$f$$ is

$$
\hat f(n)=\langle f,e_n\rangle=\int_0^1 f(x)\,e^{-2\pi i n x}\,dx .
$$

> **Plancherel (Parseval) Identity.** The system $$\{e_n\}_{n\in\mathbb{Z}}$$ is an orthonormal basis of $$L^2(0,1)$$. Consequently, for every $$f\in L^2(0,1)$$,
>
> $$
> \|f\|^2=\int_0^1|f(x)|^2\,dx=\sum_{n=-\infty}^{\infty}|\hat f(n)|^2=\|\hat f\|_{\ell^2}^2 .
> $$

Orthonormality is a direct computation: for $$m\neq n$$,

$$
\langle e_m,e_n\rangle=\int_0^1 e^{2\pi i(m-n)x}\,dx=\left[\frac{e^{2\pi i(m-n)x}}{2\pi i(m-n)}\right]_0^1=0,
$$

and $$\langle e_n,e_n\rangle=1$$. Completeness (the span of the $$e_n$$ is dense) is the deep part of the theorem, and we take it as known.

## 2. The function and its Fourier coefficients

Let $$f(x)=x$$ on $$[0,1)$$, extended $$1$$-periodically (the *sawtooth function*). Then $$f\in L^2(0,1)$$ and

$$
\|f\|^2=\int_0^1 x^2\,dx=\frac13 .
$$

### Case $$n=0$$

$$
\hat f(0)=\int_0^1 x\,dx=\frac12 .
$$

### Case $$n\neq 0$$

Integrate by parts with $$u=x$$ and $$dv=e^{-2\pi i n x}dx$$, so that $$du=dx$$ and $$v=\dfrac{e^{-2\pi i n x}}{-2\pi i n}$$:

$$
\hat f(n)=\int_0^1 x\,e^{-2\pi i n x}\,dx
=\left[\frac{x\,e^{-2\pi i n x}}{-2\pi i n}\right]_0^1
-\int_0^1\frac{e^{-2\pi i n x}}{-2\pi i n}\,dx .
$$

Since $$n\in\mathbb{Z}$$, we have $$e^{-2\pi i n}=1$$, so the boundary term equals $$\dfrac{1}{-2\pi i n}$$. The remaining integral vanishes:

$$
\int_0^1 e^{-2\pi i n x}\,dx=\left[\frac{e^{-2\pi i n x}}{-2\pi i n}\right]_0^1=\frac{1-1}{-2\pi i n}=0 .
$$

Hence

$$
\hat f(n)=-\frac{1}{2\pi i n}=-(2\pi i n)^{-1}\qquad (n\neq0).
$$

### Summary of the coefficients

$$
\int_0^1 x\,e^{-2\pi i n x}\,dx=
\begin{cases}
\dfrac12, & n=0,\\
-(2\pi i n)^{-1}, & n\neq 0.
\end{cases}
$$

## 3. Applying Plancherel

For $$n\neq0$$,

$$
|\hat f(n)|^2=\frac{1}{|2\pi i n|^2}=\frac{1}{4\pi^2 n^2}.
$$

Since $$\lvert\hat f(n)\rvert^2=\lvert\hat f(-n)\rvert^2$$, the terms for $$n$$ and $$-n$$ are equal, so

$$
\sum_{n\in\mathbb{Z}}|\hat f(n)|^2
=\left(\tfrac12\right)^2+\sum_{n\neq0}\frac{1}{4\pi^2n^2}
=\frac14+2\sum_{n=1}^\infty\frac{1}{4\pi^2n^2}
=\frac14+\frac{1}{2\pi^2}\sum_{n=1}^\infty n^{-2}.
$$

(The series converges: it is bounded by $$\|f\|^2<\infty$$ by Plancherel, or simply by comparison with $$\sum n^{-2}$$.)

By the Plancherel identity,

$$
\frac13=\int_0^1x^2\,dx=\|f\|^2=\|\hat f\|^2
=\frac14+(2\pi^2)^{-1}\sum_{n=1}^\infty n^{-2}.
$$

## 4. Solving for the sum

Subtract $$\tfrac14$$ from both sides:

$$
(2\pi^2)^{-1}\sum_{n=1}^\infty n^{-2}=\frac13-\frac14=\frac1{12}.
$$

Multiply by $$2\pi^2$$:

$$
\sum_{n=1}^\infty n^{-2}=\frac{2\pi^2}{12}=\frac{\pi^2}{6}.
\qquad\blacksquare
$$

## Exercise

The same trick works for other even powers. Use the Fourier coefficients of a suitable polynomial (for instance $$x^2$$ on $$[0,1)$$, or an appropriate shift of it) together with Plancherel to check that

$$
\sum_{n=1}^\infty n^{-4}=\frac{\pi^4}{90}.
$$

## Reference

This argument follows Section 1.7 ("Miscellaneous Applications"), part 1, "Evaluation of Sums," on p. 47 of:

H. Dym and H. P. McKean, *Fourier Series and Integrals*, Probability and Mathematical Statistics, Vol. 14, Academic Press, New York–London, 1972.
