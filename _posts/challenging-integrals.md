---
layout: post
title: "Challenging Integrals Every Mathematician Should Know"
date: 2026-06-15
categories: [mathematics, calculus]
tags: [integrals, analysis, techniques]
math: true
---

Some integrals resist elementary methods yet yield beautiful closed forms through clever techniques — contour integration, differentiation under the integral sign, symmetry arguments, and more. This post collects a few of my favorites, with full derivations.

---

## 1. The Dirichlet Integral

$$\int_0^{\infty} \frac{\sin x}{x}\, dx = \frac{\pi}{2}$$

This is perhaps the most famous improper integral in analysis. The integrand is continuous everywhere (with a removable singularity at $x = 0$), yet the integral cannot be computed by finding an antiderivative in closed form.

### Method: Differentiation Under the Integral Sign (Feynman's Trick)

Introduce a parameter $s \geq 0$ by considering the family of integrals:

$$I(s) = \int_0^{\infty} \frac{\sin x}{x} e^{-sx}\, dx$$

Notice that $I(0) = \int_0^{\infty} \frac{\sin x}{x}\, dx$, which is exactly what we want, and $I(s) \to 0$ as $s \to \infty$.

**Step 1: Differentiate with respect to $s$.**

$$I'(s) = \frac{d}{ds} \int_0^{\infty} \frac{\sin x}{x} e^{-sx}\, dx = -\int_0^{\infty} \sin x\, e^{-sx}\, dx$$

The $x$ in the denominator cancels with the $x$ brought down by differentiating $e^{-sx}$.

**Step 2: Evaluate $I'(s)$ using integration by parts (twice).**

$$\int_0^{\infty} e^{-sx} \sin x\, dx$$

Let $u = \sin x$, $dv = e^{-sx}dx$. Then $du = \cos x\, dx$, $v = -\frac{1}{s}e^{-sx}$:

$$= \left[-\frac{e^{-sx}\sin x}{s}\right]_0^{\infty} + \frac{1}{s}\int_0^{\infty} e^{-sx}\cos x\, dx = \frac{1}{s}\int_0^{\infty} e^{-sx}\cos x\, dx$$

Integrate by parts again: let $u = \cos x$, $dv = e^{-sx}dx$:

$$\frac{1}{s}\left(\left[-\frac{e^{-sx}\cos x}{s}\right]_0^{\infty} - \frac{1}{s}\int_0^{\infty} e^{-sx}\sin x\, dx\right) = \frac{1}{s}\left(\frac{1}{s} - \frac{1}{s}\int_0^{\infty} e^{-sx}\sin x\, dx\right)$$

Calling the original integral $J$:

$$J = \frac{1}{s^2} - \frac{J}{s^2} \implies J\!\left(1 + \frac{1}{s^2}\right) = \frac{1}{s^2} \implies J = \frac{1}{1 + s^2}$$

Therefore:

$$I'(s) = -\frac{1}{1+s^2}$$

**Step 3: Integrate back.**

$$I(s) = -\arctan(s) + C$$

Using the boundary condition $I(s) \to 0$ as $s \to \infty$:

$$0 = -\frac{\pi}{2} + C \implies C = \frac{\pi}{2}$$

So $I(s) = \frac{\pi}{2} - \arctan(s)$, and finally:

$$\boxed{\int_0^{\infty} \frac{\sin x}{x}\, dx = I(0) = \frac{\pi}{2}}$$

### Why Is This Tricky?

- The integral is **conditionally convergent** but not absolutely convergent — $\int_0^\infty \frac{|\sin x|}{x}\, dx$ diverges.
- Naively swapping differentiation and integration requires justification (dominated convergence or uniform convergence arguments for $s > 0$).
- There is no elementary antiderivative of $\frac{\sin x}{x}$; the antiderivative is the special function $\operatorname{Si}(x)$.

### Alternative: Contour Integration

One may also obtain this result via residues by integrating $\frac{e^{iz}}{z}$ around an indented semicircular contour in the upper half-plane, which yields the same answer through a slicker but less elementary argument.

---

*More challenging integrals coming soon — the Gaussian integral $\int_{-\infty}^{\infty} e^{-x^2}dx$, the Beta function connection, and integrals involving $\log\sin$.*
