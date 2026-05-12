---
title: "A Foundational Review of Functions"
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

> **An Essential Guide to Functions.** This post covers the foundational concepts of functions required for Calculus. We explore how to represent functions, determine domains and ranges, and apply transformations. All material follows Sections 1.1–1.3 of *Calculus*, 9th edition, by James Stewart.

---

## 1. What is a Function?

A **function** $$f$$is a rule that assigns to each element$$x$$in a set$$D$$(the domain) exactly one element, called$$f(x)$$, in a set $$E$$ (the codomain). 



When working with functions algebraically, there are two primary **Domain Restrictions** to keep in mind:

1.  **Rational Functions:** The denominator cannot be zero.
2.  **Radical Functions:** The expression under a square root (or any even root) must be greater than or equal to zero.

### 1.1 The Four Ways to Represent a Function
According to Stewart §1.1, functions can be described in four ways:

1.  **Verbally** (description in words)
2.  **Numerically** (table of values)
3.  **Visually** (graph)
4.  **Algebraically** (explicit formula)

### 1.2 The Vertical Line Test
A curve in the $$xy$$-plane is the graph of a function of $$x$$ if and only if no vertical line intersects the curve more than once. If a vertical line intersects a curve at more than one point, the curve does not represent a function because one input would result in multiple outputs.

---

## 2. New Functions from Old (Transformations)

By applying transformations to a "parent" function (such as $$f(x) = x^2$$or$$f(x) = \sqrt{x}$$), we can model a wide variety of phenomena.

### 2.1 Shifting
* **Vertical Shifts:** $$y = f(x) + c$$moves the graph up$$c$$units;$$y = f(x) - c$$ moves it down.
* **Horizontal Shifts:** $$y = f(x - c)$$moves the graph **right**$$c$$units;$$y = f(x + c)$$ moves it **left**.



### 2.2 Function Composition
The **composite function** $$f \circ g$$ is created by using the output of one function as the input for another:

$$(f \circ g)(x) = f(g(x))$$

**Note on Domain:** The domain of the composition $$f \circ g$$consists of all$$x$$in the domain of$$g$$such that$$g(x)$$is in the domain of$$f$$.

---

## 3. Worked Examples

These examples illustrate the practical application of Stewart's early chapters.

### Example 1: Finding Domain and Range
**Problem:** Find the domain and range of the function $$f(x) = \sqrt{x - 2}$$.

**Solution:**
* **Domain:** We require the radicand to be non-negative to avoid imaginary numbers:
    $$x - 2 \geq 0 \implies x \geq 2$$
    In interval notation, the domain is **$$[2, \infty)$$**.
* **Range:** The output of a square root is always non-negative. Since the minimum value of the radicand is 0, the range is **$$[0, \infty)$$**.

### Example 2: Horizontal and Vertical Shifting
**Problem:** Use the graph of $$g(x) = x^2$$to sketch$$h(x) = (x + 3)^2 - 5$$.

**Solution:**
1.  **Parent Function:** Start with the standard parabola $$y = x^2$$(vertex at$$(0,0)$$).
2.  **Horizontal Shift:** Replace $$x$$with$$(x+3)$$, which shifts the graph 3 units to the **left**.
3.  **Vertical Shift:** Subtract 5 from the result, which shifts the graph 5 units **down**.
4.  **Final Vertex:** The new vertex is located at **$$(-3, -5)$$**.

### Example 3: Composition of Functions
**Problem:** If $$f(x) = x^2$$and$$g(x) = x - 3$$, find the formula for $$(f \circ g)(x)$$.

**Solution:**
$$(f \circ g)(x) = f(g(x))$$

Substitute the expression for $$g(x)$$into the variable in function$$f$$:
$$f(x - 3) = (x - 3)^2$$

Expanded, this result is $$x^2 - 6x + 9$$.

---

## 4. Summary Table

| Concept | Key Definition |
| :--- | :--- |
| **Mathematical Model** | A mathematical description (often a function) of a real-world phenomenon. |
| **Even Function** | $$f(-x) = f(x)$$. The graph is symmetric about the $$y$$-axis. |
| **Odd Function** | $$f(-x) = -f(x)$$. The graph is symmetric about the origin. |
| **Domain Restriction** | Check for zeros in denominators and negatives in even roots. |

---

## References

All section numbers refer to:

Stewart, J. (2021). *Calculus*, 9th edition. Cengage Learning.

- §1.1 — Four Ways to Represent a Function
- §1.2 — Mathematical Models: A Catalog of Essential Functions
- §1.3 — New Functions from Old Functions
