---
title: "The Heisenberg Uncertainty Principle for Schwartz Functions"
date: 2026-11-12
layout: single
author_profile: true
read_time: true
toc: true
toc_label: "Contents"
toc_sticky: true
mathjax: true
categories:
  - Fourier Analysis
tags:
  - Fourier transform
  - Heisenberg uncertainty principle
  - Schwartz space
  - Plancherel
excerpt: "A function and its Fourier transform cannot both be sharply concentrated. We prove this precisely, including the equality case."
---

A function and its Fourier transform cannot both be sharply concentrated. This post states and proves the Heisenberg Uncertainty Principle for Schwartz functions on $\mathbb{R}$, together with the equality case. First we list the definitions and facts that the proof needs. The presentation follows Pereyra and Ward [1] and Stein and Shakarchi [2].

## 1. Preliminary definitions and facts

We use the convention

$$
\hat f(\xi)=\int_{\mathbb{R}} f(x)\,e^{-2\pi i x\xi}\,dx ,
$$

as in [2, Chapter 5].

### 1.1 Function spaces

**Definition 1.1 (Schwartz space).** A function $\psi:\mathbb{R}\to\mathbb{C}$ belongs to the Schwartz space $\mathcal{S}(\mathbb{R})$ if $\psi\in C^\infty(\mathbb{R})$ and for all integers $k,\ell\ge 0$,

$$
\sup_{x\in\mathbb{R}}\,|x|^k\,|\psi^{(\ell)}(x)|<\infty .
$$

**Definition 1.2 ($L^2$ norm).** For $\psi\in L^2(\mathbb{R})$ let $\|\psi\|_2=\big(\int_{\mathbb{R}}|\psi(x)|^2\,dx\big)^{1/2}$. We say $\psi$ is *normalized* if $\|\psi\|_2=1$.

**Proposition 1.3 (Inclusion $\mathcal{S}(\mathbb{R})\subset L^2(\mathbb{R})$).**

- (a) $\mathcal{S}(\mathbb{R})\subset L^2(\mathbb{R})$. In fact, if $\psi\in\mathcal{S}(\mathbb{R})$, then $\|\psi\|_2\le\sqrt{\pi/2}\,\sup_{x}(1+x^2)|\psi(x)|$.
- (b) The inclusion is proper.
- (c) $\mathcal{S}(\mathbb{R})$ is dense in $L^2(\mathbb{R})$.

*Proof.* (a) Let $C=\sup_{x}(1+x^2)|\psi(x)|$. This is finite by the definition of $\mathcal{S}(\mathbb{R})$ (take $k\in\{0,2\}$ and $\ell=0$). Then $|\psi(x)|\le C(1+x^2)^{-1}$, so

$$
\|\psi\|_2^2\le C^2\int_{\mathbb{R}}\frac{dx}{(1+x^2)^2}=C^2\,\frac{\pi}{2}<\infty .
$$

(b) The function $\chi_{[-1,1]}$ is in $L^2(\mathbb{R})$ but is not continuous. The function $(1+x^2)^{-1}$ is in $L^2(\mathbb{R})$ and is smooth, but $x^3(1+x^2)^{-1}$ is unbounded, so it is not in $\mathcal{S}(\mathbb{R})$ (take $k=3$, $\ell=0$).

(c) We have $C_c^\infty(\mathbb{R})\subset\mathcal{S}(\mathbb{R})$, and $C_c^\infty(\mathbb{R})$ is dense in $L^2(\mathbb{R})$. $\square$

### 1.2 The Fourier transform

**Definition 1.4 (Fourier transform).** For $f\in L^1(\mathbb{R})$, $\hat f(\xi)=\int_{\mathbb{R}} f(x)\,e^{-2\pi i x\xi}\,dx$.

**Proposition 1.5 (Time-frequency dictionary).** Let $f\in\mathcal{S}(\mathbb{R})$ and $x_0,\xi_0\in\mathbb{R}$. Then

- (a) $\widehat{f'}(\xi)=2\pi i\,\xi\,\hat f(\xi)$.
- (b) If $g(x)=f(x+x_0)$, then $\hat g(\xi)=e^{2\pi i x_0\xi}\hat f(\xi)$.
- (c) If $g(x)=e^{-2\pi i x\xi_0}f(x)$, then $\hat g(\xi)=\hat f(\xi+\xi_0)$.

Moreover, the Fourier transform maps $\mathcal{S}(\mathbb{R})$ into itself.

**Theorem 1.6 (Plancherel's identity).** If $f\in\mathcal{S}(\mathbb{R})$ (more generally $f\in L^2(\mathbb{R})$), then

$$
\int_{\mathbb{R}}|f(x)|^2\,dx=\int_{\mathbb{R}}|\hat f(\xi)|^2\,d\xi .
$$

**Corollary 1.7.** If $\psi\in\mathcal{S}(\mathbb{R})$, then

$$
\int_{\mathbb{R}}|\psi'(x)|^2\,dx=4\pi^2\int_{\mathbb{R}}\xi^2\,|\hat\psi(\xi)|^2\,d\xi .
$$

*Proof.* Apply Plancherel to $\psi'$ and use Proposition 1.5(a): $|\widehat{\psi'}(\xi)|^2=4\pi^2\xi^2|\hat\psi(\xi)|^2$. $\square$

### 1.3 Analytic tools

**Lemma 1.8 (Cauchy-Schwarz).** For $f,g\in L^2(\mathbb{R})$,

$$
\int_{\mathbb{R}}|f||g|\,dx\le
\Big(\int_{\mathbb{R}}|f|^2\,dx\Big)^{1/2}\Big(\int_{\mathbb{R}}|g|^2\,dx\Big)^{1/2}.
$$

Equality holds if and only if one of $f,g$ is a scalar multiple of the other.

Since $\mathcal{S}(\mathbb{R})\subset L^2(\mathbb{R})$ and $\mathcal{S}(\mathbb{R})$ is closed under multiplication by polynomials and under differentiation, the inequality applies to the pair $x\psi$ and $\psi'$ whenever $\psi\in\mathcal{S}(\mathbb{R})$.

**Lemma 1.9 (Elementary facts).**

- (a) For $z\in\mathbb{C}$, $\mathrm{Re}\,z\le |z|$.
- (b) For integrable $f$, $\big|\int f\big|\le\int|f|$.
- (c) $\dfrac{d}{dx}|\psi|^2=\bar\psi\psi'+\psi\bar\psi'=2\mathrm{Re}(\bar\psi\psi')$.

**Lemma 1.10 (Gaussian integrals).** For every $a>0$,

$$
\int_{\mathbb{R}}e^{-ax^2}\,dx=\sqrt{\frac{\pi}{a}},\qquad
\int_{\mathbb{R}}x^2e^{-ax^2}\,dx=\frac{\sqrt{\pi}}{2a^{3/2}} .
$$

*Proof.* Let $I=\int_{\mathbb{R}}e^{-ax^2}dx$. In polar coordinates,

$$
I^2=\iint_{\mathbb{R}^2}e^{-a(x^2+y^2)}\,dx\,dy
=\int_0^{2\pi}\!\!\int_0^{\infty}e^{-ar^2}\,r\,dr\,d\theta
=2\pi\cdot\frac{1}{2a}=\frac{\pi}{a},
$$

so $I=\sqrt{\pi/a}$. For the second formula, integrate by parts with $u=x$ and $dv=xe^{-ax^2}dx$, so $v=-\frac{1}{2a}e^{-ax^2}$. The boundary term vanishes, and

$$
\int_{\mathbb{R}}x^2e^{-ax^2}\,dx=\frac{1}{2a}\int_{\mathbb{R}}e^{-ax^2}\,dx=\frac{\sqrt\pi}{2a^{3/2}} .\qquad\square
$$

### 1.4 Mean and variance

**Definition 1.11.** Let $\psi\in\mathcal{S}(\mathbb{R})$ with $\|\psi\|_2=1$. By Plancherel, $|\psi(x)|^2dx$ and $|\hat\psi(\xi)|^2d\xi$ are probability densities. Their means are

$$
\bar x=\int_{\mathbb{R}}x\,|\psi(x)|^2\,dx,\qquad
\bar\xi=\int_{\mathbb{R}}\xi\,|\hat\psi(\xi)|^2\,d\xi ,
$$

and their variances (the uncertainties) are

$$
\Delta_x^2=\int_{\mathbb{R}}(x-\bar x)^2|\psi(x)|^2\,dx,\qquad
\Delta_\xi^2=\int_{\mathbb{R}}(\xi-\bar\xi)^2|\hat\psi(\xi)|^2\,d\xi .
$$

The mean $\bar x$ is the value of $x_0$ that minimizes $\int(x-x_0)^2|\psi(x)|^2dx$; see [2, Section 5.4].

## 2. The Heisenberg Uncertainty Principle

**Theorem 2.1 (Heisenberg Uncertainty Principle).** Let $\psi\in\mathcal{S}(\mathbb{R})$ with $\|\psi\|_2=1$. Then

$$
\left(\int_{\mathbb{R}}x^2|\psi(x)|^2\,dx\right)
\left(\int_{\mathbb{R}}\xi^2|\hat\psi(\xi)|^2\,d\xi\right)\ge\frac{1}{16\pi^2}.
\tag{1}
$$

Equality holds if and only if $\psi(x)=Ae^{-Bx^2}$ with $B>0$ and $|A|^2=\sqrt{2B/\pi}$. More generally, for all $x_0,\xi_0\in\mathbb{R}$,

$$
\left(\int_{\mathbb{R}}(x-x_0)^2|\psi(x)|^2\,dx\right)
\left(\int_{\mathbb{R}}(\xi-\xi_0)^2|\hat\psi(\xi)|^2\,d\xi\right)\ge\frac{1}{16\pi^2}.
\tag{2}
$$

This is Theorem 8.44 in [1] and Theorem 4.1 of Chapter 5 in [2].

### 2.1 Proof of inequality (1)

Write

$$
X=\int_{\mathbb{R}}x^2|\psi(x)|^2\,dx,\qquad
\Xi=\int_{\mathbb{R}}\xi^2|\hat\psi(\xi)|^2\,d\xi .
$$

Both are finite, because $x\psi$ and $\xi\hat\psi$ are Schwartz functions.

**Step 1: Integration by parts.** Take $u=|\psi(x)|^2$ and $dv=dx$. The boundary term $x|\psi(x)|^2$ vanishes at $\pm\infty$ because $\psi\in\mathcal{S}(\mathbb{R})$. By Lemma 1.9(c),

$$
1=\int_{\mathbb{R}}|\psi|^2\,dx=-\int_{\mathbb{R}}x\,\frac{d}{dx}|\psi|^2\,dx
=-2\int_{\mathbb{R}}x\,\mathrm{Re}\big(\bar\psi\psi'\big)\,dx .
$$

**Step 2: Absolute values.** Since $\mathrm{Re}\,z\le|z|$ and $|\int f|\le\int|f|$,

$$
1\le 2\int_{\mathbb{R}}|x|\,|\psi(x)|\,|\psi'(x)|\,dx .
$$

**Step 3: Cauchy-Schwarz.** Apply Lemma 1.8 to $x\psi$ and $\psi'$:

$$
1\le 2\Big(\int_{\mathbb{R}}x^2|\psi|^2\,dx\Big)^{1/2}
\Big(\int_{\mathbb{R}}|\psi'|^2\,dx\Big)^{1/2}.
$$

**Step 4: Plancherel.** By Corollary 1.7,

$$
1\le 4\pi\,X^{1/2}\,\Xi^{1/2}.
$$

**Step 5: Square.** Both sides are nonnegative, so squaring gives $1\le 16\pi^2X\,\Xi$, which is (1). $\square$

### 2.2 The equality case

**Proposition 2.2.** Let $\psi\in\mathcal{S}(\mathbb{R})$ with $\|\psi\|_2=1$. Equality holds in (1) if and only if $\psi(x)=Ae^{-Bx^2}$ with $B>0$ and $|A|^2=\sqrt{2B/\pi}$.

*Proof.* ($\Rightarrow$) If equality holds in (1), then every inequality in the chain

$$
1=-2\int_{\mathbb{R}}x\,\mathrm{Re}(\bar\psi\psi')\,dx\le 2\int_{\mathbb{R}}|x||\psi||\psi'|\,dx
\le 2X^{1/2}\Big(\int_{\mathbb{R}}|\psi'|^2\,dx\Big)^{1/2}
$$

is an equality.

- *Phase condition.* Equality in the first step means that $|x||\psi||\psi'|+x\mathrm{Re}(\bar\psi\psi')$ has integral zero. This function is continuous and nonnegative, so it vanishes identically. Put $z=x\,\bar\psi\psi'$. Then $\mathrm{Re}\,z=-|z|$, which forces $z=-|z|\le 0$.
- *Modulus condition.* Equality in Cauchy-Schwarz gives a constant $\lambda\ge0$ with $|\psi'|=\lambda|x||\psi|$.

Together, $x\,\bar\psi\,\psi'=-\lambda x^2|\psi|^2$. This gives

$$
\psi'(x)=-\lambda\,x\,\psi(x)\qquad\text{for all }x\in\mathbb{R}.
$$

(At points with $x\ne0$ and $\psi(x)\ne0$, divide by $x\bar\psi$. If $\psi(x)=0$, the modulus condition gives $\psi'(x)=0$. At $x=0$, use continuity.)

If $\lambda=0$, then $\psi$ is constant, which contradicts $\|\psi\|_2=1$. So $\lambda=2B$ with $B>0$. Since

$$
\frac{d}{dx}\big(e^{Bx^2}\psi(x)\big)=e^{Bx^2}\big(\psi'+2Bx\psi\big)=0,
$$

we get $\psi(x)=Ae^{-Bx^2}$. By Lemma 1.10 with $a=2B$,

$$
1=|A|^2\int_{\mathbb{R}}e^{-2Bx^2}\,dx=|A|^2\sqrt{\frac{\pi}{2B}},
\qquad\text{so}\qquad |A|^2=\sqrt{\frac{2B}{\pi}} .
$$

($\Leftarrow$) Let $\psi(x)=Ae^{-Bx^2}$ with $|A|^2=\sqrt{2B/\pi}$. By Lemma 1.10,

$$
X=\sqrt{\frac{2B}{\pi}}\cdot\frac{\sqrt\pi}{2(2B)^{3/2}}=\frac{1}{4B}.
$$

Since $\psi'=-2Bx\psi$, we have $\int|\psi'|^2dx=4B^2X=B$. By Corollary 1.7, $\Xi=B/(4\pi^2)$. Therefore

$$
X\,\Xi=\frac{1}{4B}\cdot\frac{B}{4\pi^2}=\frac{1}{16\pi^2}. \qquad\square
$$

A remark on the constant. Equality in Cauchy-Schwarz alone only gives $|\psi'|=\lambda|x||\psi|$. It is the phase condition, from equality in $\mathrm{Re}\,z\le|z|$, that makes the constant in $\psi'=\beta x\psi$ real and negative.

### 2.3 Proof of inequality (2): translation and modulation

Let $\varphi(x)=e^{-2\pi i x\xi_0}\psi(x+x_0)$. Then $\|\varphi\|_2=1$ and, by Proposition 1.5, $|\hat\varphi(\xi)|=|\hat\psi(\xi+\xi_0)|$. Changing variables,

$$
\int_{\mathbb{R}}x^2|\varphi|^2\,dx=\int_{\mathbb{R}}(x-x_0)^2|\psi|^2\,dx,\qquad
\int_{\mathbb{R}}\xi^2|\hat\varphi|^2\,d\xi=\int_{\mathbb{R}}(\xi-\xi_0)^2|\hat\psi|^2\,d\xi .
$$

Applying (1) to $\varphi$ gives (2). $\square$

## 3. A support version

**Corollary 3.1.** Let $f\in\mathcal{S}(\mathbb{R})$ with $\|f\|_2=1$, $\mathrm{supp}(f)\subset[-a,a]$ and $\mathrm{supp}(\hat f)\subset[-b,b]$, where $a,b>0$. Then

$$
ab\ge\frac{1}{4\pi}.
$$

*Proof.* By Plancherel, $\|\hat f\|_2=\|f\|_2=1$.

Since $f(x)=0$ for $|x|>a$ and $x^2\le a^2$ for $|x|\le a$,

$$
\int_{\mathbb{R}}x^2|f|^2\,dx=\int_{-a}^{a}x^2|f|^2\,dx\le a^2\int_{\mathbb{R}}|f|^2\,dx=a^2 .
$$

In the same way, $\int_{\mathbb{R}}\xi^2|\hat f|^2\,d\xi\le b^2$. All quantities are nonnegative, so the bounds can be multiplied. With (1),

$$
\frac{1}{16\pi^2}\le\left(\int_{\mathbb{R}}x^2|f|^2\,dx\right)\left(\int_{\mathbb{R}}\xi^2|\hat f|^2\,d\xi\right)\le a^2b^2 .
$$

Taking square roots gives $ab\ge 1/(4\pi)$. $\square$

The hypotheses cannot actually be met by a nonzero function. No nonzero function is compactly supported both in time and in frequency [1, Exercise 8.47]. The corollary still says that if $f$ is concentrated on $[-a,a]$ and $\hat f$ on $[-b,b]$, then $ab$ cannot be small.

## References

1. M. C. Pereyra and L. A. Ward, *Harmonic Analysis: From Fourier to Wavelets*, Student Mathematical Library, vol. 63, American Mathematical Society, Providence, RI, 2012.
​2. E. M. Stein and R. Shakarchi, *Fourier Analysis: An Introduction*, Princeton Lectures in Analysis, vol. 1, Princeton University Press, Princeton, NJ, 2003.
