---
title: "Calculus I: A Foundational Review of Functions"
date: 2026-05-12
author: "Rajib Belbase"
permalink: /posts/2026/05/calculus-i-review-functions/
tags:
  - calculus
  - differential calculus
  - calculus I
  - teaching
author_profile: true
header:
  teaser: "/images/calculus_1_review.png"
---

> **For students in Calculus I.** This post covers the essential review of functions based on our class materials. We will look at how to represent functions, find their domains and ranges, and apply common transformations. All material follows Sections 1.1–1.3 of *Calculus*, 9th edition, by James Stewart.

---

## 1. What is a Function?

A **function** $$f$$is a rule that assigns to each element$$x$$in a set$$D$$(the domain) exactly one element, called$$f(x)$$, in a set $$E$$ (the codomain). 



As noted in our class review, we must be particularly careful with **Domain Restrictions**:
1.  **Division by zero:** The denominator cannot be zero.
2.  **Even roots:** The expression under a square root (or any even root) must be greater than or equal to zero.

### 1.1 The Four Ways to Represent a Function
According to Stewart §1.1, we can describe functions in four ways:
1. **Verbally** (by a description in words)
2. **Numerically** (by a table of values)
3. **Visually** (by a graph)
4. **Algebraically** (by an explicit formula)

### 1.2 The Vertical Line Test
A curve in the $$xy$$-plane is the graph of a function of $$x$$ if and only if no vertical line intersects the curve more than once. If a vertical line hits the graph twice, it means one input has two outputs, which violates the definition of a function.

---

## 2. New Functions from Old (Transformations)

We can transform a basic function (like $$f(x) = x^2$$or$$f(x) = \sqrt{x}$$) to create more complex graphs.

### 2.1 Shifting
* **Vertical Shifts:** $$y = f(x) + c$$moves the graph up$$c$$units;$$y = f(x) - c$$ moves it down.
* **Horizontal Shifts:** $$y = f(x - c)$$moves the graph **right**$$c$$units;$$y = f(x + c)$$ moves it **left**.



### 2.2 Function Composition
The **composite function** $$f \circ g$$ is defined by plugging the "inner" function into the "outer" function:
$$(f \circ g)(x) = f(g(x))$$

**Crucial Note on Domain:** The domain of $$f \circ g$$is the set of all$$x$$in the domain of$$g$$such that$$g(x)$$is in the domain of$$f$$.

---

## 3. Worked Examples (From Annotated Notes)

These examples follow the logic used in our Section 1.1–1.3 review.

### Example 1: Finding Domain and Range
**Problem:** Find the domain and range of the function $$f(x) = \sqrt{x - 2}$$.

**Solution:**
* **Domain:** We require the radicand to be non-negative:
    $$x - 2 \geq 0 \implies x \geq 2$$
    In interval notation, the domain is **$$[2, \infty)$$**.
* **Range:** The smallest value occurs at $$x = 2$$, where $$f(2) = \sqrt{0} = 0$$. As $$x$$increases,$$f(x)$$ increases indefinitely. 
    The range is **$$[0, \infty)$$**.

### Example 2: Horizontal and Vertical Shifting
**Problem:** Use the graph of $$g(x) = x^2$$to sketch$$h(x) = (x + 3)^2 - 5$$.

**Solution:**
1.  Start with the parent function $$y = x^2$$(vertex at$$(0,0)$$).
2.  **Shift Left:** Replace $$x$$with$$(x+3)$$ to move the graph 3 units to the left.
3.  **Shift Down:** Subtract 5 to move the graph 5 units down.
4.  **Final Vertex:** The new vertex is located at **$$(-3, -5)$$**.

### Example 3: Composition of Functions
**Problem:** If $$f(x) = x^2$$and$$g(x) = x - 3$$, find the formula for $$(f \circ g)(x)$$.

**Solution:**
$$(f \circ g)(x) = f(g(x))$$
Substitute $$g(x) = x - 3$$into the function$$f$$:
$$f(x - 3) = (x - 3)^2$$
Expanding this gives $$x^2 - 6x + 9$$.

---

## 4. Summary Table

| Concept | Key Definition |
|---|---|
| **Mathematical Model** | An idealization of real-world phenomena. |
| **Even Function** | $$f(-x) = f(x)$$. Symmetric about the $$y$$-axis. |
| **Odd Function** | $$f(-x) = -f(x)$$. Symmetric about the origin. |
| **Domain Requirement** | No division by zero, no negatives under even roots. |

---

## References

All section numbers and materials refer to:

Stewart, J. (2021). *Calculus*, 9th edition. Cengage Learning.

- §1.1 — Four Ways to Represent a Function
- §1.2 — Mathematical Models: A Catalog of Essential Functions
- §1.3 — New Functions from Old Functions
