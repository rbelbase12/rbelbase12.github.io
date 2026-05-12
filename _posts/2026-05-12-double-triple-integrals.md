---
title: "Double and Triple Integrals: Integrating Over Regions in Space"
date: 2026-05-12
author: "Rajib Belbase"
permalink: /posts/2026/05/double-triple-integrals/
tags:
  - calculus
  - multivariable calculus
  - calculus III
  - teaching
author_profile: true
header:
  teaser: "/images/double_integral.png"
---
**By: Rajib Belbase**
> **For students in Calculus III.** This post covers the essential ideas behind double and triple integrals — what they mean geometrically, how to set them up, and how to compute them. All material follows Chapter 15 of *Calculus*, 9th edition, by James Stewart.

---

## 1. From Single to Double Integrals

You already know how to integrate a function of one variable over an interval $$[a, b]$$:

$$\int_a^b f(x)\, dx$$

Geometrically, this computes the **signed area** under the curve $$y = f(x)$$ above the $$x$$-axis.

Now suppose $$f(x, y)$$ is a function of **two variables** defined over a region $$D$$ in the $$xy$$-plane. The **double integral** of $$f$$ over $$D$$ is:

$$\iint_D f(x, y)\, dA$$

Geometrically, when $$f(x, y) \geq 0$$, this gives the **volume** of the solid that lies above $$D$$ and below the surface $$z = f(x, y)$$.

### 1.1 The Big Idea: Slicing and Summing

The double integral is built the same way as the single integral — by dividing, approximating, and taking a limit.

Divide the region $$D$$ into small rectangles of area $$\Delta A = \Delta x \cdot \Delta y$$. Over each small rectangle, approximate the solid by a thin rectangular box of height $$f(x_{ij}^*, y_{ij}^*)$$. The volume of that box is $$f(x_{ij}^*, y_{ij}^*)\,\Delta A$$. Summing over all rectangles and taking the limit as they shrink:

$$\iint_D f(x, y)\, dA = \lim_{m,n \to \infty} \sum_{i=1}^{m}\sum_{j=1}^{n} f(x_{ij}^*, y_{ij}^*)\,\Delta A$$

This is the **Riemann sum definition** of the double integral [Stewart §15.1].

---

## 2. Iterated Integrals and Fubini's Theorem

In practice, we never compute the limit above directly. Instead, we use **Fubini's Theorem**, which converts a double integral into two successive single integrals — called an **iterated integral**.

### 2.1 Fubini's Theorem

**Theorem** (Fubini [Stewart §15.2]). If $$f$$ is continuous on the rectangle $$R = [a,b] \times [c,d]$$, then:

$$\iint_R f(x,y)\, dA = \int_a^b \int_c^d f(x,y)\, dy\, dx = \int_c^d \int_a^b f(x,y)\, dx\, dy$$

Both orders of integration give the same answer. The key idea: **integrate with respect to one variable while treating the other as a constant**, exactly like partial differentiation in reverse.

### 2.2 Example: Double Integral Over a Rectangle

**Compute** $$\displaystyle\iint_R (x + 2y)\, dA$$ where $$R = [0,3] \times [1,2]$$.

$$\int_0^3 \int_1^2 (x + 2y)\, dy\, dx$$

**Inner integral** (fix $$x$$, integrate over $$y$$):

$$\int_1^2 (x + 2y)\, dy = \left[xy + y^2\right]_1^2 = (2x + 4) - (x + 1) = x + 3$$

**Outer integral**:

$$\int_0^3 (x + 3)\, dx = \left[\frac{x^2}{2} + 3x\right]_0^3 = \frac{9}{2} + 9 = \frac{27}{2}$$

---

## 3. Double Integrals Over General Regions

Rectangular regions are easy, but most interesting problems involve non-rectangular domains. Stewart §15.3 classifies these into two types.

### 3.1 Type I Regions

A region $$D$$ is **Type I** if it lies between two functions of $$x$$:

$$D = \{(x, y) \mid a \leq x \leq b,\; g_1(x) \leq y \leq g_2(x)\}$$

The double integral becomes:

$$\iint_D f(x,y)\, dA = \int_a^b \int_{g_1(x)}^{g_2(x)} f(x,y)\, dy\, dx$$

**The limits on the inner integral depend on $$x$$** — this is what makes it different from the rectangular case.

### 3.2 Type II Regions

A region $$D$$ is **Type II** if it lies between two functions of $$y$$:

$$D = \{(x, y) \mid c \leq y \leq d,\; h_1(y) \leq x \leq h_2(y)\}$$

$$\iint_D f(x,y)\, dA = \int_c^d \int_{h_1(y)}^{h_2(y)} f(x,y)\, dx\, dy$$

### 3.3 Example: Integral Over a Triangular Region

**Compute** $$\displaystyle\iint_D xy\, dA$$ where $$D$$ is the triangle with vertices $$(0,0)$$, $$(1,0)$$, $$(1,1)$$.

The region is bounded by $$x = 1$$ on the right, $$y = 0$$ below, and $$y = x$$ above — a Type I region with $$0 \leq x \leq 1$$ and $$0 \leq y \leq x$$.

$$\int_0^1 \int_0^x xy\, dy\, dx$$

**Inner integral**:

$$\int_0^x xy\, dy = x \cdot \left[\frac{y^2}{2}\right]_0^x = \frac{x^3}{2}$$

**Outer integral**:

$$\int_0^1 \frac{x^3}{2}\, dx = \frac{1}{2} \cdot \frac{x^4}{4}\Bigg|_0^1 = \frac{1}{8}$$

### 3.4 Choosing the Right Order

Sometimes one order of integration leads to an integral that is impossible (or very hard) to evaluate in closed form, while the other is straightforward. A classic example is:

$$\int_0^1 \int_x^1 \sin(y^2)\, dy\, dx$$

Integrating $$\sin(y^2)$$ with respect to $$y$$ first has no elementary antiderivative. But switching to Type II (integrating $$x$$ first, with $$0 \leq x \leq y$$):

$$\int_0^1 \int_0^y \sin(y^2)\, dx\, dy = \int_0^1 y\sin(y^2)\, dy = \left[-\frac{\cos(y^2)}{2}\right]_0^1 = \frac{1 - \cos 1}{2}$$

**Moral**: always sketch the region and consider both orders before committing.

---

## 4. Double Integrals in Polar Coordinates

When the region $$D$$ is a disk, ring, or sector, **polar coordinates** $$x = r\cos\theta$$, $$y = r\sin\theta$$ often simplify the computation dramatically [Stewart §15.4].

The key substitution for the area element is:

$$dA = r\, dr\, d\theta$$

The extra factor of $$r$$ — the **Jacobian** — is essential and must not be omitted.

$$\iint_D f(x,y)\, dA = \int_\alpha^\beta \int_{r_1(\theta)}^{r_2(\theta)} f(r\cos\theta, r\sin\theta)\cdot r\, dr\, d\theta$$

### 4.1 Example: Area of a Disk

**Compute** $$\displaystyle\iint_D 1\, dA$$ where $$D$$ is the disk $$x^2 + y^2 \leq a^2$$.

In polar: $$0 \leq r \leq a$$, $$0 \leq \theta \leq 2\pi$$.

$$\int_0^{2\pi}\int_0^a r\, dr\, d\theta = \int_0^{2\pi} \frac{a^2}{2}\, d\theta = \pi a^2$$

Reassuringly, the double integral recovers the familiar formula for the area of a circle.

### 4.2 Example: Gaussian Integral

The famous integral $$\int_{-\infty}^\infty e^{-x^2}\, dx = \sqrt{\pi}$$ is proved using polar coordinates. Let $$I = \int_{-\infty}^\infty e^{-x^2}\, dx$$. Then:

$$I^2 = \int_{-\infty}^\infty\int_{-\infty}^\infty e^{-(x^2+y^2)}\, dx\, dy = \int_0^{2\pi}\int_0^\infty e^{-r^2} r\, dr\, d\theta = 2\pi \cdot \frac{1}{2} = \pi$$

So $$I = \sqrt{\pi}$$ — a result that single-variable calculus alone cannot prove.

---

## 5. Applications of Double Integrals

Double integrals compute more than volumes [Stewart §15.5].

| Quantity | Formula |
|----------|---------|
| **Area** of $$D$$ | $$A(D) = \iint_D 1\, dA$$ |
| **Volume** below $$z = f(x,y)$$ | $$V = \iint_D f(x,y)\, dA$$ |
| **Mass** of a lamina with density $$\rho(x,y)$$ | $$m = \iint_D \rho(x,y)\, dA$$ |
| **Center of mass** | $$\bar{x} = \frac{1}{m}\iint_D x\,\rho\, dA,\quad \bar{y} = \frac{1}{m}\iint_D y\,\rho\, dA$$ |
| **Moment of inertia** about $$x$$-axis | $$I_x = \iint_D y^2\,\rho(x,y)\, dA$$ |
| **Average value** of $$f$$ over $$D$$ | $$f_{\text{avg}} = \dfrac{1}{A(D)}\iint_D f(x,y)\, dA$$ |

---

## 6. Triple Integrals

The step from double to triple integrals is conceptually identical — we integrate over a **3D solid region** $$E$$ instead of a 2D region.

$$\iiint_E f(x, y, z)\, dV$$

When $$f(x,y,z) = 1$$, the triple integral gives the **volume** of $$E$$. More generally it computes mass, charge, or any quantity distributed throughout a solid [Stewart §15.7].

### 6.1 Fubini's Theorem for Triple Integrals

If $$f$$ is continuous on the box $$B = [a,b]\times[c,d]\times[r,s]$$:

$$\iiint_B f(x,y,z)\, dV = \int_r^s\int_c^d\int_a^b f(x,y,z)\, dx\, dy\, dz$$

There are $$3! = 6$$ possible orders of integration, and any valid order gives the same result.

### 6.2 General Solid Regions

For a **Type 1** solid (the most common setup), $$E$$ lies between two surfaces above a 2D region $$D$$:

$$E = \{(x,y,z) \mid (x,y) \in D,\; u_1(x,y) \leq z \leq u_2(x,y)\}$$

$$\iiint_E f\, dV = \iint_D \left[\int_{u_1(x,y)}^{u_2(x,y)} f(x,y,z)\, dz\right] dA$$

The strategy: **integrate in $$z$$ first** (between the two bounding surfaces), then handle the resulting double integral over $$D$$ by Type I or Type II methods.

### 6.3 Example: Volume of a Tetrahedron

**Find the volume** of the tetrahedron bounded by the planes $$x = 0$$, $$y = 0$$, $$z = 0$$, and $$x + y + z = 1$$.

The solid: $$0 \leq x \leq 1$$, $$0 \leq y \leq 1-x$$, $$0 \leq z \leq 1-x-y$$.

$$V = \int_0^1\int_0^{1-x}\int_0^{1-x-y} dz\, dy\, dx$$

**Innermost integral**:

$$\int_0^{1-x-y} dz = 1 - x - y$$

**Middle integral**:

$$\int_0^{1-x}(1-x-y)\, dy = \left[(1-x)y - \frac{y^2}{2}\right]_0^{1-x} = \frac{(1-x)^2}{2}$$

**Outer integral**:

$$\int_0^1 \frac{(1-x)^2}{2}\, dx = \frac{1}{2}\cdot\frac{(1-x)^3}{-3}\Bigg|_0^1 \cdot(-1)= \frac{1}{6}$$

The volume of a tetrahedron with unit side is $$\boxed{\dfrac{1}{6}}$$.

### 6.4 Example: Triple Integral of a Function

**Compute** $$\displaystyle\iiint_E z\, dV$$ where $$E = \{(x,y,z) \mid 0 \leq x \leq 1,\; 0 \leq y \leq x,\; 0 \leq z \leq x+y\}$$.

**Inner** (over $$z$$):

$$\int_0^{x+y} z\, dz = \frac{(x+y)^2}{2}$$

**Middle** (over $$y$$, $$0 \leq y \leq x$$):

$$\int_0^x \frac{(x+y)^2}{2}\, dy = \frac{1}{2}\cdot\frac{(x+y)^3}{3}\Bigg|_0^x = \frac{(2x)^3 - x^3}{6} = \frac{7x^3}{6}$$

**Outer** (over $$x$$):

$$\int_0^1 \frac{7x^3}{6}\, dx = \frac{7}{6}\cdot\frac{1}{4} = \frac{7}{24}$$

---

## 7. Triple Integrals in Cylindrical Coordinates

When the solid $$E$$ has **circular symmetry about the $$z$$-axis**, cylindrical coordinates are the natural choice [Stewart §15.8]:

$$x = r\cos\theta, \quad y = r\sin\theta, \quad z = z$$

The volume element becomes:

$$dV = r\, dr\, d\theta\, dz$$

Again, the Jacobian factor $$r$$ is mandatory.

### 7.1 Example: Volume Inside a Cylinder Below a Paraboloid

**Find** the volume of the solid bounded above by $$z = 9 - r^2$$ and below by $$z = 0$$, inside the cylinder $$r = 2$$.

$$V = \int_0^{2\pi}\int_0^2\int_0^{9-r^2} r\, dz\, dr\, d\theta$$

**Inner**:

$$\int_0^{9-r^2} dz = 9 - r^2$$

**Middle**:

$$\int_0^2 r(9-r^2)\, dr = \int_0^2 (9r - r^3)\, dr = \left[\frac{9r^2}{2} - \frac{r^4}{4}\right]_0^2 = 18 - 4 = 14$$

**Outer**:

$$\int_0^{2\pi} 14\, d\theta = 28\pi$$

---

## 8. Triple Integrals in Spherical Coordinates

When the solid is a **sphere, cone, or spherical shell**, spherical coordinates are ideal [Stewart §15.9]:

$$x = \rho\sin\phi\cos\theta, \quad y = \rho\sin\phi\sin\theta, \quad z = \rho\cos\phi$$

where $$\rho \geq 0$$ is the distance from the origin, $$0 \leq \phi \leq \pi$$ is the polar angle from the $$z$$-axis, and $$0 \leq \theta \leq 2\pi$$ is the azimuthal angle. Note that $$\rho^2 = x^2 + y^2 + z^2$$.

The volume element is:

$$dV = \rho^2 \sin\phi\, d\rho\, d\phi\, d\theta$$

### 8.1 Example: Volume of a Sphere

**Find** the volume of the ball $$\rho \leq a$$.

$$V = \int_0^{2\pi}\int_0^{\pi}\int_0^a \rho^2\sin\phi\, d\rho\, d\phi\, d\theta$$

$$= \int_0^{2\pi}d\theta \cdot \int_0^{\pi}\sin\phi\, d\phi \cdot \int_0^a \rho^2\, d\rho = 2\pi \cdot 2 \cdot \frac{a^3}{3} = \frac{4}{3}\pi a^3$$

### 8.2 Example: Integral Over a Ball

**Compute** $$\displaystyle\iiint_B e^{(x^2+y^2+z^2)^{3/2}}\, dV$$ where $$B$$ is the unit ball $$x^2+y^2+z^2 \leq 1$$.

In spherical coordinates, $$x^2+y^2+z^2 = \rho^2$$, so $$(x^2+y^2+z^2)^{3/2} = \rho^3$$.

$$\int_0^{2\pi}\int_0^{\pi}\int_0^1 e^{\rho^3}\rho^2\sin\phi\, d\rho\, d\phi\, d\theta = 2\pi \cdot 2 \cdot \int_0^1 \rho^2 e^{\rho^3}\, d\rho$$

Let $$u = \rho^3$$, $$du = 3\rho^2\, d\rho$$:

$$4\pi \cdot \frac{1}{3}\int_0^1 e^u\, du = \frac{4\pi}{3}(e - 1)$$

---

## 9. A Quick Guide: Which Coordinates to Use

| Region shape | Best coordinates |
|---|---|
| Rectangle or general polygon | Cartesian $$(x, y)$$ or $$(x, y, z)$$ |
| Disk, ring, sector | Polar $$(r, \theta)$$ |
| Cylinder, cone, solid with circular cross-sections | Cylindrical $$(r, \theta, z)$$ |
| Sphere, spherical shell, cone from origin | Spherical $$(\rho, \phi, \theta)$$ |

**The rule of thumb**: match the coordinate system to the symmetry of the region. A sphere described in Cartesian coordinates requires painful algebra; in spherical coordinates it is two lines.

---

## 10. Common Mistakes to Avoid

**1. Forgetting the Jacobian.** The area element in polar is $$r\, dr\, d\theta$$, not $$dr\, d\theta$$. The volume element in cylindrical is $$r\, dr\, d\theta\, dz$$, and in spherical it is $$\rho^2\sin\phi\, d\rho\, d\phi\, d\theta$$. Omitting these factors is the single most common error in this chapter.

**2. Wrong limits on the inner integral.** The inner limits generally depend on the outer variables. For a Type I region, the $$y$$-limits are functions of $$x$$. Always draw and label the region before writing the integral.

**3. Integrating in an impossible order.** If the inner integral has no closed form, try switching the order. Always check whether the integrand suggests a preferred order.

**4. Confusing $$\phi$$ and $$\theta$$ in spherical.** Stewart uses $$\phi$$ for the polar angle (from the $$z$$-axis) and $$\theta$$ for the azimuthal angle. Some textbooks reverse this convention. Be consistent.

**5. Setting up limits for the wrong region.** Sketch the region in 3D (or at least its projection onto the $$xy$$-plane). A solid bounded *above* by a paraboloid and *below* by a plane requires $$z$$ to run from the plane up to the paraboloid — not the other way around.

---

## 11. Summary

| Concept | Key Formula |
|---|---|
| Double integral (rectangle) | $$\iint_R f\, dA = \int_a^b\int_c^d f\, dy\, dx$$ |
| Double integral (Type I) | $$\int_a^b\int_{g_1(x)}^{g_2(x)} f\, dy\, dx$$ |
| Polar area element | $$dA = r\, dr\, d\theta$$ |
| Triple integral (general solid) | $$\iint_D\int_{u_1}^{u_2} f\, dz\, dA$$ |
| Cylindrical volume element | $$dV = r\, dr\, d\theta\, dz$$ |
| Spherical volume element | $$dV = \rho^2\sin\phi\, d\rho\, d\phi\, d\theta$$ |

The single most important skill in this chapter is **setting up the limits correctly**. The integration itself is usually routine single-variable calculus — it is the geometry of the region that requires care. Draw every region. Label every boundary. Then write the integral.

Good luck — and remember that every triple integral in spherical coordinates is just three single integrals waiting to be separated.

---

## References

All section numbers refer to:

Stewart, J. (2021). *Calculus*, 9th edition. Cengage Learning.

- §15.1 — Double Integrals over Rectangles
- §15.2 — Double Integrals over General Regions
- §15.3 — Double Integrals in Polar Coordinates
- §15.4 — Applications of Double Integrals
- §15.7 — Triple Integrals
- §15.8 — Triple Integrals in Cylindrical Coordinates
- §15.9 — Triple Integrals in Spherical Coordinates
