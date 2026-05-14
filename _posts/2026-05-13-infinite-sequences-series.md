---
title: "Infinite Sequences and Series: From Convergence to Taylor Series"
date: 2026-05-13
author: "Rajib Belbase"
permalink: /posts/2026/05/infinite-sequences-series/
tags:
  - calculus
  - sequences and series
  - calculus II
  - teaching
author_profile: true
header:
  teaser: "/images/taylor_series.png"
---
**By: Rajib Belbase**
> **For students in Calculus II.** This post covers the essential ideas behind infinite sequences and series — what they mean, how to test for convergence, and how to represent functions as power series. All material follows Chapter 11 of *Calculus*, 9th edition, by James Stewart.

---

## 1. Infinite Sequences

An **infinite sequence** is an ordered list of numbers, one for each positive integer:

$$\{a_n\}_{n=1}^{\infty} = \{a_1, a_2, a_3, \ldots\}$$

A sequence can also be viewed as a function whose domain is the positive integers. For example, if $$a_n = \frac{n}{n+1}$$, then $$\{a_n\} = \left\{\frac{1}{2}, \frac{2}{3}, \frac{3}{4}, \frac{4}{5}, \ldots\right\}$$.

### 1.1 Limits of Sequences

We say a sequence **converges** to $$L$$ if:

$$\lim_{n \to \infty} a_n = L$$

meaning the terms get arbitrarily close to $$L$$ as $$n \to \infty$$. If no such $$L$$ exists, the sequence **diverges**. A sequence for which $$\lim_{n \to \infty} a_n = \infty$$ is said to **diverge to infinity** [Stewart §11.1].

The key bridge between sequence limits and function limits:

> **Theorem.** If $$\lim_{x \to \infty} f(x) = L$$ and $$f(n) = a_n$$ for each integer $$n$$, then $$\lim_{n \to \infty} a_n = L$$.

This allows us to use L'Hôpital's Rule on continuous functions and transfer the result to sequences — but you must switch from the integer variable $$n$$ to the real variable $$x$$ before applying any derivative rules.

### 1.2 Bounded Monotonic Sequences

A sequence is **monotone** if it is always increasing or always decreasing. It is **bounded** if all terms lie within some fixed interval.

> **Monotone Convergence Theorem (MCT).** Every sequence that is both monotone and bounded must converge.

The MCT is an existence theorem — it tells you a limit exists without telling you what it is. It is the key tool for proving that certain series and power series converge.

---

## 2. Infinite Series

Now that we understand sequences, we can tackle infinite series. An **infinite series** is a sum of all the terms of a sequence:

$$\sum_{n=1}^{\infty} a_n = a_1 + a_2 + a_3 + \cdots$$

The meaning of this sum requires care. We define the **$$k$$th partial sum**:

$$S_k = \sum_{n=1}^{k} a_n = a_1 + a_2 + \cdots + a_k$$

An infinite series is, fundamentally, a sequence of partial sums $$\{S_k\}_{k=1}^{\infty}$$. We define its sum as:

$$\sum_{n=1}^{\infty} a_n = \lim_{k \to \infty} S_k$$

If this limit is a finite real number, the series **converges**; otherwise it **diverges** [Stewart §11.2]. This is in direct analogy with the improper integral: $$\int_1^{\infty} f(x)\,dx = \lim_{k \to \infty} \int_1^k f(x)\,dx$$.

### 2.1 Geometric Series (Must Memorize)

$$\sum_{n=1}^{\infty} ar^{n-1} = \frac{a}{1-r}, \quad |r| < 1$$

The partial sum formula is $$S_k = \frac{a - ar^k}{1-r}$$, and taking $$k \to \infty$$ gives the result when $$|r| < 1$$. The series diverges for $$|r| \geq 1$$.

### 2.2 Telescoping Series

Some series have partial sums that simplify by cancellation. For example:

$$\sum_{n=1}^{\infty} \left(\frac{1}{2^n} - \frac{1}{2^{n+1}}\right) = \lim_{k\to\infty}\left(\frac{1}{2} - \frac{1}{2^{k+1}}\right) = \frac{1}{2}$$

### 2.3 The Divergence Test

> **Divergence Test.** If $$\lim_{n \to \infty} a_n \neq 0$$, or if the limit does not exist, then $$\sum a_n$$ **diverges**.

⚠️ The converse is **false**: $$\lim a_n = 0$$ does **not** guarantee convergence. The harmonic series $$\sum 1/n$$ is the classic counterexample — its terms go to zero, yet it diverges.

---

## 3. The Integral Test and the $$p$$-Series

### 3.1 The Integral Test

**Setup:** Suppose $$f$$ is continuous, positive, and decreasing on $$[1, \infty)$$, and $$a_k = f(k)$$ for each $$k$$. Then [Stewart §11.3]:

$$\sum_{k=1}^{\infty} a_k \quad \text{and} \quad \int_1^{\infty} f(x)\,dx \quad \text{either both converge or both diverge.}$$

The idea is geometric: the terms of the series correspond to rectangle areas that you can compare to the integral. The Monotone Convergence Theorem is the backbone of the proof.

### 3.2 The $$p$$-Series (Must Memorize)

$$\sum_{n=1}^{\infty} \frac{1}{n^p} \begin{cases} \text{converges} & \text{if } p > 1 \\ \text{diverges} & \text{if } p \leq 1 \end{cases}$$

Note: the sum of a $$p$$-series is only known for even values $$p = 2, 4, 6, \ldots$$ (first discovered by Euler). For example, $$\sum 1/n^2 = \pi^2/6$$. The sum of $$\sum 1/n^3$$ is still unknown.

### 3.3 Remainder Estimate for the Integral Test

If $$\sum a_n$$ converges by the Integral Test and the $$k$$th remainder is $$R_k = a_{k+1} + a_{k+2} + \cdots$$, then:

$$\int_{k+1}^{\infty} f(x)\,dx \leq R_k \leq \int_k^{\infty} f(x)\,dx$$

This also gives an improved estimate for the total sum:

$$S_k + \int_{k+1}^{\infty} f(x)\,dx \leq \sum_{n=1}^{\infty} a_n \leq S_k + \int_k^{\infty} f(x)\,dx$$

---

## 4. Comparison Tests

### 4.1 Direct Comparison Test

Suppose $$0 \leq a_n \leq b_n$$ for all large $$n$$ [Stewart §11.4]:

- If $$\sum b_n$$ converges, then $$\sum a_n$$ converges.
- If $$\sum a_n$$ diverges, then $$\sum b_n$$ diverges.

The intuition comes from the Monotone Convergence Theorem: positive terms give increasing partial sums, and an upper bound keeps them from diverging to $$\infty$$.

### 4.2 Limit Comparison Test

Suppose $$a_n, b_n > 0$$ and:

$$\lim_{n \to \infty} \frac{a_n}{b_n} = c, \quad 0 < c < \infty$$

Then $$\sum a_n$$ and $$\sum b_n$$ either **both converge or both diverge**.

> **Strategy:** Identify the "dominant" terms of $$a_n$$ as $$n \to \infty$$. If $$a_n \sim \frac{1}{n^p}$$ for large $$n$$, use Limit Comparison with the $$p$$-series $$\sum 1/n^p$$.

⚠️ **Important:** If the series behaves like a $$p$$-series, the Ratio Test and Root Test will always be inconclusive (both give $$L = 1$$). Use the Limit Comparison Test instead.

### 4.3 Example: When Direct Comparison Is Awkward

**Determine** whether $$\displaystyle\sum_{n=1}^{\infty} \frac{n+5}{4n^8 - 1}$$ converges or diverges.

Direct Comparison is tricky here because bounding the numerator and denominator separately gives inequalities in the wrong direction. Instead, note that for large $$n$$, $$\frac{n+5}{4n^8-1} \approx \frac{1}{n^7}$$. By the Limit Comparison Test with $$\sum 1/n^7$$ (a $$p$$-series with $$p = 7 > 1$$):

$$\lim_{n \to \infty} \frac{(n+5)/(4n^8-1)}{1/n^7} = \lim_{n \to \infty} \frac{n^8 + 5n^7}{4n^8 - 1} = \frac{1}{4} > 0$$

Since $$\sum 1/n^7$$ converges and the limit is a finite positive number, $$\sum \frac{n+5}{4n^8-1}$$ **converges**.

---

## 5. Alternating Series

### 5.1 Definition and the Alternating Series Test (AST)

A series $$\sum a_n$$ is **alternating** if it can be written as:

$$\sum_{n=1}^{\infty} (-1)^{n-1} b_n = b_1 - b_2 + b_3 - b_4 + \cdots, \quad b_n > 0$$

> **Alternating Series Test (AST).** Let $$\sum a_n$$ be an alternating series. If $$\{|a_n|\}$$ is decreasing and $$\lim_{n \to \infty} |a_n| = 0$$, then $$\sum a_n$$ converges [Stewart §11.5].

The proof uses the Monotone Convergence Theorem applied separately to the even and odd partial sums; the condition $$\lim |a_n| = 0$$ forces both subsequences to the same limit.

**Classic example:** The alternating harmonic series $$\displaystyle\sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{n} = 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \cdots$$ converges by the AST (and its sum equals $$\ln 2$$).

⚠️ Always check the Divergence Test first. If $$\lim |a_n| \neq 0$$, the series diverges by the Divergence Test — not by the AST.

### 5.2 Alternating Series Estimation Theorem (ASE)

> **ASE Theorem.** If $$\sum a_n$$ converges by the AST and the $$k$$th remainder is $$R_k = S - S_k$$, then:
> $$|R_k| \leq |a_{k+1}|$$
> The error is bounded by the **absolute value of the first omitted term**. Moreover, the true sum $$S$$ always lies between two consecutive partial sums $$S_k$$ and $$S_{k+1}$$.

**Example:** For $$\sum (-1)^{n-1}/n$$, to approximate the sum within $$10^{-4}$$, we need $$1/(n+1) < 10^{-4}$$, which gives $$n > 9999$$. So $$S_{10000}$$ is sufficient.

### 5.3 Absolute and Conditional Convergence

- $$\sum a_n$$ is **absolutely convergent** if $$\sum |a_n|$$ converges.
- $$\sum a_n$$ is **conditionally convergent** if $$\sum a_n$$ converges but $$\sum |a_n|$$ diverges.

**Theorem:** Absolute convergence implies convergence (but not the other way around).

| Series | $$\sum\|a_n\|$$ | Verdict |
|--------|----------------|---------|
| $$\sum \frac{(-1)^{n-1}}{n^2}$$ | Converges ($$p=2$$) | **Absolutely convergent** |
| $$\sum \frac{(-1)^{n-1}}{n}$$ | Diverges (harmonic) | **Conditionally convergent** |

---

## 6. The Ratio Test and Root Test

### 6.1 The Ratio Test

The Ratio Test detects whether a series "behaves like" a geometric series [Stewart §11.6]. Compute:

$$L = \lim_{n \to \infty} \left|\frac{a_{n+1}}{a_n}\right|$$

| $$L$$ | Conclusion |
|--------|-----------|
| $$L < 1$$ | Absolutely convergent |
| $$L > 1$$ or $$L = \infty$$ | Divergent |
| $$L = 1$$ | **Inconclusive** |

> **Best used when:** $$a_n$$ involves **factorials** ($$n!$$) or **exponentials** ($$r^n$$). **Never use** the Ratio Test when $$a_n$$ is a rational or algebraic function of $$n$$ — it will always give $$L = 1$$ (inconclusive).

**Example:** For $$\displaystyle\sum_{n=1}^{\infty} \frac{(-3)^n}{n!}$$, the ratio $$\left|\frac{a_{n+1}}{a_n}\right| = \frac{3}{n+1} \to 0 < 1$$, so the series **converges absolutely**.

### 6.2 The Root Test

$$L = \lim_{n \to \infty} \sqrt[n]{|a_n|}$$

Same conclusion table as the Ratio Test. Best used when $$a_n = (f(n))^n$$.

---

## 7. Strategy for Testing Series

There is no single algorithm, but the following decision process covers most cases:

1. **Divergence Test first.** If $$\lim a_n \neq 0$$, the series diverges. Done.
2. **Recognize special forms.** Geometric? $$p$$-series? Telescoping? Apply the known result directly.
3. **Rational or algebraic terms?** Use Limit Comparison with an appropriate $$p$$-series.
4. **Factorials or exponentials?** Use the Ratio Test.
5. **Terms of the form $$(f(n))^n$$?** Use the Root Test.
6. **Alternating signs?** Try the Alternating Series Test.
7. **Can you bound the terms?** Try Direct Comparison.
8. **Last resort:** Integral Test, if $$a_n = f(n)$$ with $$f$$ decreasing and continuous.

---

## 8. Power Series

### 8.1 Definition

A **power series centered at $$a$$** is an infinite series of the form [Stewart §11.8]:

$$\sum_{n=0}^{\infty} c_n(x-a)^n = c_0 + c_1(x-a) + c_2(x-a)^2 + c_3(x-a)^3 + \cdots$$

For each fixed $$x$$, this is an ordinary infinite series that may converge or diverge. The domain of the resulting function is the set of all $$x$$ for which the series converges. Note: by convention, $$x^0 = 1$$ for all $$x$$, including $$x = 0$$.

### 8.2 Radius and Interval of Convergence

For any power series, exactly one of three things is true:

1. The series converges **only** at $$x = a$$ (radius $$R = 0$$).
2. The series converges for **all** $$x$$ (radius $$R = \infty$$).
3. There is a number $$R > 0$$ such that the series converges for $$|x - a| < R$$ and diverges for $$|x - a| > R$$.

$$R$$ is the **radius of convergence**. The **interval of convergence** is centered at $$a$$ with half-width $$R$$. There are six possibilities for its exact form:

$$\{a\}, \quad (-R+a,\, R+a), \quad [-R+a,\, R+a), \quad (-R+a,\, R+a], \quad [-R+a,\, R+a], \quad (-\infty, \infty)$$

Always check the **endpoints** separately after finding $$R$$, since the series may converge or diverge there.

> **To find $$R$$:** Apply the Ratio Test (or Root Test) to the power series, treating $$x$$ as a fixed but unspecified constant. Solve $$L < 1$$ for $$x$$.

### 8.3 Differentiation and Integration of Power Series

If $$f(x) = \sum_{n=0}^{\infty} c_n(x-a)^n$$ has radius of convergence $$R > 0$$, then $$f$$ is differentiable and integrable on $$(a-R,\, a+R)$$:

$$f'(x) = \sum_{n=1}^{\infty} n\, c_n(x-a)^{n-1}, \qquad \int f(x)\,dx = C + \sum_{n=0}^{\infty} \frac{c_n}{n+1}(x-a)^{n+1}$$

Both the derivative and antiderivative have the **same radius of convergence** $$R$$ (though the endpoints may change).

---

## 9. Representations of Functions as Power Series

### 9.1 Starting From the Geometric Series

The most basic power series is [Stewart §11.9]:

$$\frac{1}{1-x} = \sum_{n=0}^{\infty} x^n = 1 + x + x^2 + x^3 + \cdots, \quad R = 1$$

By **substitution**, **differentiation**, and **integration**, we can derive power series for many other functions from this single starting point.

### 9.2 Deriving $$\ln(1+x)$$

Since $$\frac{d}{dx}\ln(1+x) = \frac{1}{1+x} = \sum_{n=0}^{\infty}(-1)^n x^n$$ for $$|x|<1$$, integrating term-by-term:

$$\ln(1+x) = C + \sum_{n=1}^{\infty} \frac{(-1)^{n-1}}{n} x^n$$

Setting $$x = 0$$ gives $$C = \ln(1) = 0$$, so:

$$\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots, \quad R = 1$$

### 9.3 Deriving $$\arctan x$$

Since $$\frac{1}{1+x^2} = \sum_{n=0}^{\infty}(-1)^n x^{2n}$$ for $$|x|<1$$, integrating:

$$\arctan x = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots = \sum_{n=0}^{\infty} \frac{(-1)^n}{2n+1} x^{2n+1}, \quad R = 1$$

Power series are integrable term-by-term and **keep their radius of convergence** — this is what makes it possible to evaluate integrals like $$\int \frac{\ln(1+x)}{x}\,dx$$ as power series.

---

## 10. Taylor and Maclaurin Series

### 10.1 Meaning of the Coefficients

Suppose a function $$f$$ is represented by a power series centered at $$a$$ with radius $$R > 0$$:

$$f(x) = c_0 + c_1(x-a) + c_2(x-a)^2 + c_3(x-a)^3 + \cdots$$

Plugging in $$x = a$$: $$f(a) = c_0$$. Differentiating and plugging in $$x = a$$: $$f'(a) = c_1$$. Differentiating twice: $$f''(a) = 2c_2$$, so $$c_2 = f''(a)/2$$. In general:

$$c_n = \frac{f^{(n)}(a)}{n!}$$

### 10.2 The Taylor Series

> **Theorem** [Stewart §11.10]. IF $$f$$ has a power series representation at $$a$$ with radius $$R > 0$$, THEN it must be:
>
> $$\boxed{f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x-a)^n = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \frac{f'''(a)}{3!}(x-a)^3 + \cdots}$$

This is the **Taylor series** of $$f$$ centered at $$a$$. When $$a = 0$$, it is called the **Maclaurin series**:

$$f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!} x^n = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f'''(0)}{3!}x^3 + \cdots$$

> **Uniqueness.** Since the representation is unique, every center $$a$$ gives at most one power series for $$f$$. There are no other power series representations to find.

**Two important warnings:**

- **Warning 1:** For some functions, the Taylor series may have radius of convergence zero.
- **Warning 2:** Even if the radius of convergence is nonzero, the Taylor series may not equal $$f$$ everywhere in the interval.

### 10.3 The Essential Maclaurin Series (Memorize These)

| Function | Maclaurin Series | Radius |
|----------|-----------------|--------|
| $$e^x$$ | $$\displaystyle 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots = \sum_{n=0}^{\infty}\frac{x^n}{n!}$$ | $$R = \infty$$ |
| $$\sin x$$ | $$\displaystyle x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots = \sum_{n=0}^{\infty}\frac{(-1)^n x^{2n+1}}{(2n+1)!}$$ | $$R = \infty$$ |
| $$\cos x$$ | $$\displaystyle 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots = \sum_{n=0}^{\infty}\frac{(-1)^n x^{2n}}{(2n)!}$$ | $$R = \infty$$ |
| $$\dfrac{1}{1-x}$$ | $$\displaystyle 1 + x + x^2 + x^3 + \cdots = \sum_{n=0}^{\infty} x^n$$ | $$R = 1$$ |
| $$\ln(1+x)$$ | $$\displaystyle x - \frac{x^2}{2} + \frac{x^3}{3} - \cdots = \sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n}x^n$$ | $$R = 1$$ |
| $$\arctan x$$ | $$\displaystyle x - \frac{x^3}{3} + \frac{x^5}{5} - \cdots = \sum_{n=0}^{\infty}\frac{(-1)^n x^{2n+1}}{2n+1}$$ | $$R = 1$$ |
| $$(1+x)^k$$ | $$\displaystyle 1 + kx + \frac{k(k-1)}{2!}x^2 + \cdots = \sum_{n=0}^{\infty}\binom{k}{n}x^n$$ | $$R = 1$$ |

### 10.4 Taylor Polynomials

Each partial sum of the Taylor series is a polynomial. The **$$k$$th degree Taylor polynomial of $$f$$ centered at $$a$$** is:

$$T_k(x) = \sum_{n=0}^{k} \frac{f^{(n)}(a)}{n!}(x-a)^n = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \cdots + \frac{f^{(k)}(a)}{k!}(x-a)^k$$

$$T_k$$ is the best degree-$$k$$ polynomial approximation to $$f$$ near $$x = a$$. As $$k$$ increases, $$T_k$$ hugs the curve more closely over a wider interval.

### 10.5 Taylor's Remainder Formula (Taylor's Inequality)

The error in using $$T_k(x_0)$$ to approximate $$f(x_0)$$ is $$R_k(x_0) = f(x_0) - T_k(x_0)$$. If $$|f^{(k+1)}(z)| \leq M$$ for all $$z$$ between $$x_0$$ and $$a$$, then:

$$|R_k(x_0)| \leq \frac{M}{(k+1)!}|x_0 - a|^{k+1}$$

A useful fact: for $$f(x) = \sin x$$ or $$\cos x$$, all derivatives satisfy $$|f^{(k+1)}(z)| \leq 1$$, so $$M = 1$$ always works.

> If $$|R_k(x_0)| \to 0$$ as $$k \to \infty$$, then $$T(x_0) = f(x_0)$$ — the Taylor series truly equals the function at that point.

Using Taylor's Inequality, one can prove that $$e^x$$, $$\sin x$$, and $$\cos x$$ are each represented by their Maclaurin series everywhere ($$R = \infty$$).

---

## 11. Applications of Taylor Series

With the Maclaurin series table in hand, Taylor series become a Swiss army knife for problems that ordinary calculus cannot handle directly [Stewart §11.11].

### 11.1 Evaluating Integrals Without Closed Forms

Some integrands have no elementary antiderivative. Substitute a known Maclaurin series and integrate term-by-term:

$$\int e^{-x^2}\,dx = \int \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n}}{n!}\,dx = C + \sum_{n=0}^{\infty} \frac{(-1)^n x^{2n+1}}{n!(2n+1)}$$

For a definite integral like $$\int_0^{0.5} e^{-x^2}\,dx$$, we substitute the upper limit and use the ASE Theorem to bound the error. The resulting alternating series lets us compute the answer to any desired precision.

### 11.2 Identifying the Sum of a Series

To find the sum of a series like $$\displaystyle\frac{\pi}{3} - \frac{\pi^3}{3!\cdot 3^3} + \frac{\pi^5}{5!\cdot 3^5} - \cdots$$, factor out $$\pi/3$$ and recognize $$\sin(\pi/3) = \sqrt{3}/2$$.

**Example:**

$$7 - \frac{7}{2!} + \frac{7}{3!} - \frac{7}{4!} + \cdots = 7\sum_{n=0}^{\infty}\frac{(-1)^n}{n!} = 7e^{-1} = \frac{7}{e}$$

### 11.3 Evaluating Limits Using Taylor Series

For indeterminate forms, substituting Taylor series is often far easier than repeated L'Hôpital's Rule:

$$\lim_{x \to 0} \frac{\sin x - x}{x^3} = \lim_{x \to 0} \frac{\left(x - \frac{x^3}{6} + \cdots\right) - x}{x^3} = \lim_{x \to 0} \frac{-\frac{x^3}{6} + \cdots}{x^3} = -\frac{1}{6}$$

### 11.4 Approximating Functions and Bounding Errors

A Taylor polynomial of degree 2 centered at $$a = 8$$ for $$f(x) = x^{2/3}$$ gives:

$$T_2(x) = 4 + \frac{1}{3}(x-8) - \frac{1}{72}(x-8)^2$$

Use it to estimate $$f(8.1) \approx T_2(8.1)$$, then apply Taylor's Inequality to bound how far off that estimate could be.

---

## 12. Summary

| Concept | Key Formula or Fact |
|---------|-------------------|
| Sequence limit | $$\lim_{n\to\infty} a_n = L$$; use $$f(x)$$ and L'Hôpital if needed |
| Monotone Convergence Thm | Bounded + monotone $$\Rightarrow$$ convergent |
| Geometric series | $$\sum ar^{n-1} = \frac{a}{1-r}$$ for $$\|r\| < 1$$ |
| Divergence Test | $$\lim a_n \neq 0 \Rightarrow$$ diverges |
| $$p$$-series | Converges iff $$p > 1$$ |
| Integral Test | $$\sum a_n$$ and $$\int f\,dx$$ share convergence/divergence |
| Limit Comparison Test | $$\lim a_n/b_n = c \in (0,\infty) \Rightarrow$$ same behavior |
| AST | Alternating, $$|a_n|$$ decreasing, $$|a_n|\to 0 \Rightarrow$$ converges |
| ASE Theorem | $$\|R_k\| \leq \|a_{k+1}\|$$ |
| Ratio Test | $$L = \lim \|a_{n+1}/a_n\|$$; converges abs. if $$L < 1$$ |
| Power series | Radius of convergence via Ratio/Root Test |
| Taylor series | $$\sum f^{(n)}(a)(x-a)^n/n!$$; unique if it exists |
| Taylor's Inequality | $$\|R_k(x_0)\| \leq \frac{M}{(k+1)!}\|x_0-a\|^{k+1}$$ |

The deepest payoff of Chapter 11 is the realization that familiar functions like $$e^x$$, $$\sin x$$, and $$\cos x$$ are nothing more than infinite polynomials — and that fact alone lets us integrate them over any interval, approximate them to any precision, and compute their values from scratch using only addition and multiplication.

---

## References

All section numbers refer to:

Stewart, J. (2021). *Calculus*, 9th edition. Cengage Learning.

- §11.1 — Sequences
- §11.2 — Series
- §11.3 — The Integral Test and Estimates of Sums
- §11.4 — The Comparison Tests
- §11.5 — Alternating Series and Absolute Convergence
- §11.6 — The Ratio and Root Tests
- §11.7 — Strategy for Testing Series
- §11.8 — Power Series
- §11.9 — Representations of Functions as Power Series
- §11.10 — Taylor and Maclaurin Series
- §11.11 — Applications of Taylor Polynomials
