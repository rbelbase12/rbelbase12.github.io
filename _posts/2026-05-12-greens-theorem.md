---
title: "Green's Theorem: Connecting Line Integrals and Double Integrals"
date: 2026-05-12
author: "Rajib Belbase"
permalink: /posts/2026/05/greens-theorem/
tags:
  - calculus
  - multivariable calculus
  - calculus III
  - vector calculus
author_profile: true
header:
  teaser: "/images/greens_theorem.png"
---

> **For students in Calculus III.** This post explores Green's Theorem, one of the cornerstones of vector calculus. It establishes a profound link between a line integral around a closed curve and a double integral over the region it encloses. All material follows Chapter 16 of *Calculus*, 9th edition, by James Stewart.

---

## 1. The Core Concept

Green's Theorem provides a way to evaluate the line integral of a vector field over a simple closed curve $$C$$ by instead calculating a double integral over the plane region $$D$$ bounded by $$C$$.

It is essentially the two-dimensional version of the **Fundamental Theorem of Calculus**. Just as the FTC relates the integral of a derivative on an interval $$[a, b]$$ to the values of the function at the boundaries, Green's Theorem relates the double integral of a "derivative" (the curl) over a region to the values of the field on its boundary.

---

## 2. Statement of Green's Theorem

**Theorem** (Green's Theorem [Stewart §16.4]). Let $$C$$ be a positively oriented, piecewise-smooth, simple closed curve in the plane and let $$D$$ be the region bounded by $$C$$. If $$P$$ and $$Q$$ have continuous partial derivatives on an open region that contains $$D$$, then:

$$\oint_C P\, dx + Q\, dy = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dA$$

### 2.1 Understanding "Positive Orientation"
A curve $$C$$ is **positively oriented** if it is traversed in a counterclockwise direction. A helpful rule of thumb: if you were walking along $$C$$ in the positive direction, the region $$D$$ would always be on your **left**.

---

## 3. Example: Evaluating a Line Integral

**Compute** $$\displaystyle\oint_C (y + e^{\sqrt{x}})\, dx + (2x + \cos y^2)\, dy$$, where $$C$$ is the boundary of the region enclosed by the parabolas $$y = x^2$$ and $$x = y^2$$.

Direct evaluation would be difficult due to the $$e^{\sqrt{x}}$$ term. Green's Theorem simplifies this significantly.

**Identify P and Q:**
*   $$P(x, y) = y + e^{\sqrt{x}} \implies \frac{\partial P}{\partial y} = 1$$
*   $$Q(x, y) = 2x + \cos y^2 \implies \frac{\partial Q}{\partial x} = 2$$

**Apply the Theorem:**
$$\iint_D (2 - 1)\, dA = \iint_D 1\, dA$$

This is the area of the region between the two curves:
$$\int_0^1 \int_{x^2}^{\sqrt{x}} 1\, dy\, dx = \int_0^1 (\sqrt{x} - x^2)\, dx = \left[ \frac{2}{3}x^{3/2} - \frac{1}{3}x^3 \right]_0^1 = \frac{1}{3}$$

---

## 4. Using Green's Theorem to Find Area

Since $$\text{Area}(D) = \iint_D 1\, dA$$, we can use Green's Theorem in reverse to find area using a line integral. Common formulas include:

$$A = \oint_C x\, dy \quad \text{or} \quad A = -\oint_C y\, dx \quad \text{or} \quad A = \frac{1}{2} \oint_C x\, dy - y\, dx$$

**Example: Area of an Ellipse**
For the ellipse $$x = a\cos t, y = b\sin t$$:
$$A = \frac{1}{2} \int_0^{2\pi} (a\cos t)(b\cos t) - (b\sin t)(-a\sin t)\, dt = \pi ab$$

---

## 5. Summary Table

| Feature | Requirement |
|---|---|
| **Curve Type** | Simple and Closed |
| **Orientation** | Positive (Counterclockwise) |
| **Integrand** | $$Q_x - P_y$$ |

---

## References

Stewart, J. (2021). *Calculus*, 9th edition. Cengage Learning.
- §16.4 — Green’s Theorem
