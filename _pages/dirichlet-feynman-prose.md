---
layout: page
title: "Dirichlet Integral via Feynman's Trick"
mathjax: true
---

# Dirichlet Integral via Feynman's Trick

We want the value of $\int_0^\infty \frac{\sin x}{x}\,dx$. The trick — due to Feynman, though the underlying idea goes back to Leibniz — is to embed this integral inside a more flexible family, where an extra parameter gives us room to maneuver. Define

$$
I(t) = \int_0^\infty \frac{\sin x}{x}\,e^{-tx}\,dx, \qquad t \ge 0,
$$

so that the integral we actually want is $I(0)$. The factor $e^{-tx}$ is there purely as scaffolding: for $t>0$ it makes the integral converge absolutely and well-behaved, and as $t\to\infty$ it crushes the integrand to zero everywhere, so $I(t) \to 0$. That limiting fact will be essential later.

Rather than attacking $I(t)$ directly, differentiate it with respect to $t$. Since the integrand is smooth in $t$ and decays nicely, we're allowed to push the derivative inside the integral sign:

$$
I'(t) = \int_0^\infty \frac{\partial}{\partial t}\left(\frac{\sin x}{x}e^{-tx}\right)dx = -\int_0^\infty \sin x\, e^{-tx}\,dx.
$$

The awkward $1/x$ has vanished — differentiating against $t$ pulled down a factor of $-x$ that exactly cancels it. What's left is a textbook Laplace transform, the kind that comes from integrating $e^{-tx}\sin x$ by parts twice and solving for the integral algebraically:

$$
\int_0^\infty \sin x\, e^{-tx}\,dx = \frac{1}{1+t^2}.
$$

So we've reduced the problem to a much friendlier differential statement:

$$
I'(t) = -\frac{1}{1+t^2}.
$$

This integrates immediately, since $-1/(1+t^2)$ is the derivative of $-\arctan(t)$:

$$
I(t) = -\arctan(t) + C
$$

for some constant $C$ that the differentiation step lost. To recover it, use the boundary behavior we set up earlier: as $t \to \infty$, $I(t) \to 0$, while $\arctan(t) \to \pi/2$. Plugging into the formula,

$$
0 = -\frac{\pi}{2} + C \implies C = \frac{\pi}{2}.
$$

So the whole family is now pinned down explicitly:

$$
I(t) = \frac{\pi}{2} - \arctan(t).
$$

This curve starts at $\pi/2$ when $t=0$ and decays toward $0$ as $t$ grows, exactly mirroring how the damping factor $e^{-tx}$ increasingly suppresses the integral. Setting $t=0$ recovers the answer we were after from the start:

$$
I(0) = \frac{\pi}{2} - \arctan(0) = \frac{\pi}{2}.
$$

So

$$
\boxed{\int_0^\infty \frac{\sin x}{x}\,dx = \frac{\pi}{2}}
$$

The elegance of the method is that it never directly confronts the hard integral — it builds a one-parameter family around it, finds a differential equation that family obeys, and lets the easy endpoint ($t\to\infty$) fix the constant needed to read off the hard endpoint ($t=0$).
