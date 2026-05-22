---
title: "The Gaussian Integral"
date: 2026-05-22
permalink: /posts/2026/05/gaussian-integral-polar/
tags:
  - mathematics
  - calculus
  - integration
  - analysis
author_profile: true
---

Because the single-variable function $$e^{-x^2}$$ lacks an elementary antiderivative, evaluating the Gaussian integral over the real line requires a classic mathematical maneuver: changing the dimension to change the perspective. By evaluating its square in a two-dimensional Cartesian system, we can shift our perspective to radial symmetry.

---

<div style="background: #fdfbf7; border-left: 5px solid #b34a1a; padding: 20px; margin: 30px 0; border-radius: 0 8px 8px 0; box-shadow: 0 2px 5px rgba(0,0,0,0.03);">
  <p style="margin: 0; font-weight: 600; color: #1a1209; font-size: 1.1rem;">The Fundamental Objective</p>
  <p style="margin: 5px 0 0 0; color: #4a3f2e;">Let $$I$$ represent the continuous definite integral over the entire domain:</p>
  <div style="margin-top: 15px; font-size: 1.25rem; text-align: center;">
    $$I = \int_{-\infty}^{\infty} e^{-x^2}\,dx$$
  </div>
</div>

By introducing a secondary duplicate integral under an independent dummy variable $$y$, we can structure the squared quantity $$I^2$$ as a bivariate double integral representing the volume beneath an infinite 3D surface:

$$I^2 = \left(\int_{-\infty}^{\infty} e^{-x^2}\,dx\right)\left(\int_{-\infty}^{\infty} e^{-y^2}\,dy\right) = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} e^{-(x^2+y^2)}\,dx\,dy$$

This expression maps a double integral over the entire Cartesian plane $$\mathbb{R}^2$$. 

---

### Shifting to Radial Space

The term $$(x^2 + y^2)$$indicates uniform radial symmetry across the$$xy$$-plane. We transform the system into polar variables $$(r, \theta)$$, scaling the differential area element by the transformation Jacobian ($$dx\,dy = r\,dr\,d\theta$$):

$$x = r\cos\theta, \quad y = r\sin\theta \implies x^2 + y^2 = r^2$$

The infinite planar boundaries map cleanly to the polar space limits $$r \in [0, \infty)$$and$$\theta \in [0, 2\pi)$$:

$$I^2 = \int_{0}^{2\pi} \int_{0}^{\infty} e^{-r^2} \, r\,dr\,d\theta$$

Since the inner integration contains no explicit angular dependence, we can isolate and solve the angular variable completely, yielding a clean multiplier of $$2\pi$$:

$$I^2 = \left(\int_{0}^{2\pi} d\theta\right) \int_{0}^{\infty} r e^{-r^2}\,dr = 2\pi \int_{0}^{\infty} r e^{-r^2}\,dr$$

---

### Evaluation via Substitution

Applying a standard $$u$$-substitution where $$u = r^2$$and$$du = 2r\,dr$$ transforms the calculation into an elementary calculus antiderivative:

$$I^2 = 2\pi \cdot \frac{1}{2} \int_{0}^{\infty} e^{-u}\,du = \pi \Big[ -e^{-u} \Big]_{0}^{\infty}$$

Evaluating the limits reveals the exact volume under the surface:

$$I^2 = \pi (0 - (-1)) = \pi$$

---

<div style="background: #1a1209; color: #fff; padding: 30px; border-radius: 12px; text-align: center; margin: 40px 0; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
  <p style="text-transform: uppercase; letter-spacing: 2px; font-size: 0.85rem; color: #c8a86e; margin: 0 0 10px 0; font-family: monospace;">Analytical Result</p>
  <p style="margin: 0 0 15px 0; color: #dfd5c6; font-size: 1rem;">Because the real-valued function $$e^{-x^2}$$ is strictly positive everywhere, we extract the positive root:</p>
  <div style="font-size: 2rem; color: #f0d090;">
    $$\int_{-\infty}^{\infty} e^{-x^2}\,dx = \sqrt{\pi}$$
  </div>
</div>
