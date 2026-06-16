---
title: "Challenging Integrals Every Mathematician Should Know"
date: 2026-06-15
permalink: /posts/2026/06/chal_integrals/
tags:
  - mathematics
  - calculus
  - integration
  - analysis
author_profile: true

---
A collection of integrals that are deceptively simple to state yet require ingenuity to solve —
spanning contour integration, special functions, symmetry arguments, and beyond.
Closed forms are given; proofs are left as exercises (or future posts).
---

<!-- MathJax: renders LaTeX in any GitHub Pages theme -->
<script>
MathJax = {
  tex: {
    inlineMath: [['$', '$']],
    displayMath: [['$$', '$$']],
    tags: 'ams'
  }
};
</script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
 
<style>
.integral-block {
  background: #f8f9fa;
  border-left: 4px solid #4a90d9;
  border-radius: 6px;
  padding: 1rem 1.4rem;
  margin: 1.2rem 0;
}
.integral-block p { margin: 0.3rem 0; }
.technique { color: #555; font-style: italic; font-size: 0.95em; }
</style>

---
 
## 1. Classic Improper Integrals
 
<div class="integral-block">
<p><strong>1. Dirichlet Integral</strong></p>
$$\int_0^{\infty} \frac{\sin x}{x} \, dx \;=\; \frac{\pi}{2}$$
 
<p class="technique">Technique: Feynman's trick (differentiation under the integral sign) or contour integration.</p>
</div>
<div class="integral-block">
<p><strong>2. Gaussian Integral</strong></p>
$$\int_{-\infty}^{\infty} e^{-x^2} \, dx \;=\; \sqrt{\pi}$$
 
<p class="technique">Technique: Polar coordinate trick — square the integral and convert to 2D.</p>
</div>
<div class="integral-block">
<p><strong>3. Cauchy Distribution Normalization</strong></p>
$$\int_{-\infty}^{\infty} \frac{1}{1+x^2} \, dx \;=\; \pi$$
 
<p class="technique">Technique: Direct antiderivative via $\arctan$, or the residue theorem.</p>
</div>
<div class="integral-block">
<p><strong>4. Fresnel Integrals</strong></p>
$$\int_0^{\infty} \sin(x^2) \, dx
  \;=\;
  \int_0^{\infty} \cos(x^2) \, dx
  \;=\;
  \frac{1}{2}\sqrt{\frac{\pi}{2}}$$
 
<p class="technique">Technique: Contour integration over a wedge-shaped contour in $\mathbb{C}$.</p>
</div>
---
 
## 2. Logarithmic Integrals
 
<div class="integral-block">
<p><strong>5. Euler's Log-Sine Integral</strong></p>
$$\int_0^{\pi/2} \ln(\sin x) \, dx \;=\; -\frac{\pi}{2} \ln 2$$
 
<p class="technique">Technique: Symmetry and the reflection formula for $\Gamma$.</p>
</div>
<div class="integral-block">
<p><strong>6. Basel-Type Log Integral</strong></p>
$$\int_0^{1} \frac{\ln x}{1-x} \, dx \;=\; -\frac{\pi^2}{6}$$
 
<p class="technique">Technique: Expand $\frac{1}{1-x}$ as a geometric series and integrate term by term.</p>
</div>
<div class="integral-block">
<p><strong>7. Log-Gamma Integral</strong></p>
$$\int_0^{1} \ln \Gamma(x) \, dx \;=\; \frac{1}{2}\ln(2\pi)$$
 
<p class="technique">Technique: Kummer's Fourier series for $\ln\Gamma(x)$.</p>
</div>
<div class="integral-block">
<p><strong>8. Parametric Log Integral</strong></p>
$$\int_0^{1} x^a \ln x \, dx \;=\; -\frac{1}{(a+1)^2}, \qquad a > -1$$
 
<p class="technique">Technique: Differentiate $\int_0^1 x^a \, dx = \frac{1}{a+1}$ with respect to $a$.</p>
</div>
---
 
## 3. Special Function Integrals
 
<div class="integral-block">
<p><strong>9. Beta Function</strong></p>
$$\int_0^{1} x^{\,p-1}(1-x)^{q-1} \, dx \;=\; \frac{\Gamma(p)\,\Gamma(q)}{\Gamma(p+q)}, \qquad p,q > 0$$
 
<p class="technique">Technique: Relate to the Gamma function via substitution and convolution.</p>
</div>
<div class="integral-block">
<p><strong>10. Gamma Function Definition</strong></p>
$$\int_0^{\infty} x^{\,s-1} e^{-x} \, dx \;=\; \Gamma(s), \qquad s > 0$$
 
<p class="technique">Technique: Foundational definition; the functional equation $\Gamma(s+1) = s\,\Gamma(s)$ follows by parts.</p>
</div>
<div class="integral-block">
<p><strong>11. Ramanujan's Master Theorem (special case)</strong></p>
$$\int_0^{\infty} \frac{x^{\,s-1}}{1+x} \, dx \;=\; \frac{\pi}{\sin(\pi s)}, \qquad 0 < s < 1$$
 
<p class="technique">Technique: Residue theorem or the Beta identity $B(s,\,1-s) = \frac{\pi}{\sin(\pi s)}$.</p>
</div>
---
 
## 4. Trigonometric & Oscillatory Integrals
 
<div class="integral-block">
<p><strong>12. Wallis Integral</strong></p>
$$\int_0^{\pi/2} \sin^n x \, dx
  \;=\;
  \frac{\sqrt{\pi}}{2}
  \cdot
  \frac{\,\Gamma\!\left(\dfrac{n+1}{2}\right)}{\Gamma\!\left(\dfrac{n}{2}+1\right)}$$
 
<p class="technique">Technique: Reduction formula or Beta function.</p>
</div>
<div class="integral-block">
<p><strong>13. Frullani's Integral</strong></p>
$$\int_0^{\infty} \frac{f(ax) - f(bx)}{x} \, dx
  \;=\;
  \bigl[f(0) - f(\infty)\bigr]\ln\!\frac{b}{a}$$
 
<p class="technique">Technique: Swap order of integration using $\int_a^b f'(tx)\,dt$.</p>
</div>
<div class="integral-block">
<p><strong>14. Ahmed's Integral</strong></p>
$$\int_0^{1}
  \frac{\arctan\!\left(\sqrt{x^2+2}\right)}{(x^2+1)\sqrt{x^2+2}}
  \, dx
  \;=\;
  \frac{5\pi^2}{96}$$
 
<p class="technique">Technique: Differentiation under the integral sign with a two-parameter family.</p>
</div>
---
 
## 5. Series–Integral Connections
 
<div class="integral-block">
<p><strong>15. Sophomore's Dream</strong></p>
$$\int_0^{1} x^{-x} \, dx \;=\; \sum_{n=1}^{\infty} n^{-n}$$
 
$$\int_0^{1} x^{x} \, dx \;=\; -\!\sum_{n=1}^{\infty} (-n)^{-n}$$
 
<p class="technique">Technique: Expand $x^{-x} = e^{-x\ln x}$ as a power series and integrate term by term.</p>
</div>
<div class="integral-block">
<p><strong>16. Double Integral for $\zeta(2)$</strong></p>
$$\int_0^{1}\!\int_0^{1} \frac{1}{1-xy} \, dx \, dy \;=\; \frac{\pi^2}{6}$$
 
<p class="technique">Technique: Geometric series expansion and Euler's Basel result.</p>
</div>
<div class="integral-block">
<p><strong>17. Parseval–Plancherel Identity (sinc)</strong></p>
$$\int_{-\infty}^{\infty} \left(\frac{\sin x}{x}\right)^{\!2} dx \;=\; \pi$$
 
<p class="technique">Technique: Parseval's theorem applied to the Fourier transform of the sinc function.</p>
</div>
---
 
## 6. Complex & Contour Integration
 
<div class="integral-block">
<p><strong>18. Power-Type Rational Integral</strong></p>
$$\int_0^{\infty} \frac{x^{\,p-1}}{1+x^n} \, dx
  \;=\;
  \frac{\pi}{n\,\sin\!\left(\dfrac{p\pi}{n}\right)},
  \qquad 0 < p < n$$
 
<p class="technique">Technique: Keyhole contour with a branch cut along the positive real axis.</p>
</div>
<div class="integral-block">
<p><strong>19. Rational Function over $\mathbb{R}$</strong></p>
$$\int_{-\infty}^{\infty}
  \frac{x^2}{(x^2+1)(x^2+4)}
  \, dx
  \;=\;
  \frac{\pi}{3}$$
 
<p class="technique">Technique: Partial fractions or upper half-plane residues.</p>
</div>
<div class="integral-block">
<p><strong>20. Poisson Integral</strong></p>
$$\int_0^{2\pi}
  \frac{1 - r^2}{1 - 2r\cos\theta + r^2}
  \, d\theta
  \;=\; 2\pi,
  \qquad |r| < 1$$
 
<p class="technique">Technique: Real part of a geometric series in $re^{i\theta}$.</p>
</div>
---
 
## 7. Exotic & Competition Favorites
 
<div class="integral-block">
<p><strong>21. Gaussian with Cosine Modulation</strong></p>
$$\int_{-\infty}^{\infty} e^{-x^2} \cos(2bx) \, dx \;=\; \sqrt{\pi}\, e^{-b^2}$$
 
<p class="technique">Technique: Complete the square in the exponent; reduces to the Gaussian integral.</p>
</div>
<div class="integral-block">
<p><strong>22. Glasser's Master Theorem</strong></p>
$$\int_{-\infty}^{\infty} f\!\left(x - \frac{1}{x}\right) dx
  \;=\;
  \int_{-\infty}^{\infty} f(x) \, dx$$
 
<p class="technique">Technique: The substitution $x \mapsto x - 1/x$ is measure-preserving on $\mathbb{R}$.</p>
</div>
<div class="integral-block">
<p><strong>23. Laplace Transform of $\sqrt{t}$</strong></p>
$$\int_0^{\infty} \sqrt{t}\; e^{-st} \, dt
  \;=\;
  \frac{\sqrt{\pi}}{2\, s^{3/2}},
  \qquad s > 0$$
 
<p class="technique">Technique: Substitute $u = st$ and recognize $\Gamma\!\left(\tfrac{3}{2}\right) = \tfrac{\sqrt{\pi}}{2}$.</p>
</div>
<div class="integral-block">
<p><strong>24. Dirichlet Kernel Integral</strong></p>
$$\int_0^{\pi}
  \frac{\sin\!\left(\left(n+\tfrac{1}{2}\right)x\right)}{\sin(x/2)}
  \, dx
  \;=\; \pi$$
 
<p class="technique">Technique: Telescoping and orthogonality of trigonometric functions.</p>
</div>
<div class="integral-block">
<p><strong>25. Mellin–Barnes Type</strong></p>
$$\int_0^{\infty}
  \frac{\ln x}{1 + x^2}
  \, dx
  \;=\; 0$$
 
<p class="technique">Technique: Split at $x=1$, substitute $x \mapsto 1/x$ on one piece — the two halves cancel.</p>
</div>
---
 
*This list will grow. Detailed derivations for selected problems are available in individual posts.*
