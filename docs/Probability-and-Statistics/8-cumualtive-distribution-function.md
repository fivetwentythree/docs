---
layout: default
title: Cumulative Distribution Function
parent: Probability and Statistics
nav_order: 4
---
# Cumulative Distribution Function

Okay, let's explore the **Cumulative Distribution Function (CDF)**. This is an incredibly versatile tool in probability because, unlike the Probability Mass Function (PMF) which only works for discrete variables, the CDF works for *all* types of random variables (discrete, continuous, and even mixed types). It provides a standardized way to describe the probability distribution.

**Prerequisites: Setting the Stage**

1.  **Random Variable (RV):** Recall that an RV, $X$, is a function mapping outcomes from a sample space $\Omega$ to real numbers $\mathbb{R}$. $X: \Omega \rightarrow \mathbb{R}$.
2.  **Probability Measure (P):** We have a way to assign probabilities $P(E)$ to events $E \subseteq \Omega$.
3.  **Events involving RVs:** We can talk about events like $\{X \le x\}$, which represents the set of all outcomes $\omega \in \Omega$ such that the random variable's value $X(\omega)$ is less than or equal to some number $x$. That is, $\{\omega \in \Omega \mid X(\omega) \le x\}$.
4.  **PMF (for Discrete RVs):** Recall the PMF $p_X(x) = P(X=x)$ gives the probability that a *discrete* RV $X$ takes on a specific value $x$.

**The "Why": The Need for a Universal Descriptor**

The PMF is great for discrete RVs where probability is concentrated at specific points. But what about *continuous* RVs, like height or temperature, where the variable can take any value within an interval? For a truly continuous RV, the probability of it being *exactly* equal to any single value is zero ($P(X=x) = 0$). A dart hitting *exactly* point 0.5 on the interval [0, 1] has zero probability; there are infinitely many points! So, a PMF isn't very informative for continuous RVs.

We need a function that:
a)  Works for *both* discrete and continuous RVs.
b)  Captures the way probability accumulates across the range of possible values.

This function is the Cumulative Distribution Function (CDF).

**Definition: Cumulative Distribution Function (CDF)**

The **Cumulative Distribution Function (CDF)** of a random variable $X$, denoted by $F_X(x)$ (or often just $F(x)$ if $X$ is understood), is a function that gives the probability that the random variable $X$ takes on a value *less than or equal to* a given real number $x$.

**Mathematical Form:**
For any real number $x$, the CDF is defined as:
$F_X(x) = P(X \le x)$

**Key Points about the Definition:**

*   **Input:** The input $x$ can be *any* real number ($\mathbb{R}$), not just the values the RV can actually take.
*   **Output:** The output $F_X(x)$ is always a probability, so it must be between 0 and 1 (inclusive). $0 \le F_X(x) \le 1$.
*   **Cumulative:** The name emphasizes that it represents the *accumulation* of all probability for values of the RV up to and including $x$.

**Visual Intuition: Accumulating Probability Mass**

Imagine the probability associated with the random variable $X$ as a kind of "mass" distributed along the real number line.
*   For a **discrete** RV, this mass exists only in lumps at specific points $\{x_1, x_2, ...\}$.
*   For a **continuous** RV, this mass is spread out smoothly (or perhaps in chunks) over intervals.

The CDF, $F_X(x)$, measures the **total amount of probability mass accumulated as you sweep from negative infinity ($-\infty$) up to the point $x$**.

```
<-----------------|-------------------> x axis (Real Numbers)
                 x

[xxxxxxxxxxxxxxxxx]
Total accumulated probability mass from -∞ up to and including x = F_X(x)
```

Think of it like sweeping a dustpan along the number line from left to right; $F_X(x)$ is the total amount of "probability dust" in the pan when its right edge is at position $x$.

**Properties of ANY CDF**

Every valid CDF, $F_X(x)$, *must* have the following properties, regardless of whether $X$ is discrete or continuous:

1.  **Non-decreasing:** As you sweep from left to right (increasing $x$), you can only accumulate more probability mass or keep the accumulated amount the same. You never lose mass.
    *   If $x_1 < x_2$, then $F_X(x_1) \le F_X(x_2)$.
    *   *Visual:* The graph of $F_X(x)$ versus $x$ can only go up or stay level; it never goes down.

2.  **Limit to the Left is 0:** As you go very far to the left on the number line ($x \to -\infty$), you haven't accumulated any probability mass yet.
    *   $\lim_{x \to -\infty} F_X(x) = 0$
    *   *Visual:* The graph of the CDF starts at height 0 on the far left.

3.  **Limit to the Right is 1:** As you go very far to the right ($x \to +\infty$), you must eventually accumulate *all* the probability mass (total probability is 1).
    *   $\lim_{x \to +\infty} F_X(x) = 1$
    *   *Visual:* The graph of the CDF approaches height 1 on the far right.

4.  **Right-Continuous:** The function is continuous from the right. This means that as you approach a point $x$ from values slightly larger than $x$, the value of the CDF approaches $F_X(x)$.
    *   $\lim_{y \to x^+} F_X(y) = F_X(x)$ for all $x \in \mathbb{R}$.
    *   *Intuition:* This property is related to the use of "$\le$" in the definition $P(X \le x)$. If there's a jump (a point mass) exactly *at* $x$, that mass is included in $F_X(x)$. The value of the CDF *at* a jump point is the value at the *top* of the jump.

**Examples**

1.  **Discrete RV: Fair Die Roll**
    *   RV: $Y = $ number shown. Support $S_Y = \{1, 2, 3, 4, 5, 6\}$. PMF: $p_Y(k) = 1/6$ for $k \in S_Y$.
    *   Let's find the CDF, $F_Y(y) = P(Y \le y)$.
        *   If $y < 1$: No possible outcome is $\le y$. $F_Y(y) = 0$.
        *   If $1 \le y < 2$: Only outcome $Y=1$ satisfies $Y \le y$. $F_Y(y) = P(Y=1) = 1/6$.
        *   If $2 \le y < 3$: Outcomes $Y=1, Y=2$ satisfy $Y \le y$. $F_Y(y) = P(Y=1) + P(Y=2) = 1/6 + 1/6 = 2/6$.
        *   If $3 \le y < 4$: Outcomes $Y=1, 2, 3$. $F_Y(y) = 3/6$.
        *   If $4 \le y < 5$: Outcomes $Y=1, 2, 3, 4$. $F_Y(y) = 4/6$.
        *   If $5 \le y < 6$: Outcomes $Y=1, 2, 3, 4, 5$. $F_Y(y) = 5/6$.
        *   If $y \ge 6$: All outcomes $Y=1, ..., 6$ satisfy $Y \le y$. $F_Y(y) = 6/6 = 1$.
    *   **CDF Function:**
        $F_Y(y) = \begin{cases} 0 & \text{if } y < 1 \\ 1/6 & \text{if } 1 \le y < 2 \\ 2/6 & \text{if } 2 \le y < 3 \\ 3/6 & \text{if } 3 \le y < 4 \\ 4/6 & \text{if } 4 \le y < 5 \\ 5/6 & \text{if } 5 \le y < 6 \\ 1 & \text{if } y \ge 6 \end{cases}$
    *   **Visual:** A **step function**. It starts at 0, jumps up by 1/6 at $y=1$, stays flat, jumps by 1/6 at $y=2$, stays flat, etc., until it reaches 1 at $y=6$ and stays flat thereafter. The jumps occur exactly at the values in the support, and the size of the jump at $k$ is $p_Y(k)$. Notice it's right-continuous (the value at 2 is 2/6, not 1/6).

    ```
      F_Y(y) ^
           1 +-------
             |
           5/6 o-------
             | |
           4/6 o-------
             | |
           3/6 o-------
             | |
           2/6 o-------
             | |
           1/6 o-------
             | |
           0 +-------o
             +---+---+---+---+---+---+---> y
                 1   2   3   4   5   6
       (o represents endpoint included in interval)
    ```

2.  **Continuous RV: Uniform Distribution on [0, 1]**
    *   RV: $U =$ a number chosen uniformly from [0, 1].
    *   Let's find the CDF, $F_U(u) = P(U \le u)$.
        *   If $u < 0$: No outcome in [0, 1] is $\le u$. $F_U(u) = 0$.
        *   If $0 \le u \le 1$: The probability is the length of the interval $[0, u]$ relative to the total length of the interval [0, 1]. $F_U(u) = \frac{\text{length}([0, u])}{\text{length}([0, 1])} = \frac{u - 0}{1 - 0} = u$.
        *   If $u > 1$: Any outcome in [0, 1] is definitely $\le u$. $F_U(u) = 1$.
    *   **CDF Function:**
        $F_U(u) = \begin{cases} 0 & \text{if } u < 0 \\ u & \text{if } 0 \le u \le 1 \\ 1 & \text{if } u > 1 \end{cases}$
    *   **Visual:** A **continuous ramp function**. Starts at 0, increases linearly from (0,0) to (1,1), and then stays flat at 1 for $u > 1$. There are no jumps. This reflects the continuous nature of the RV.

    ```
      F_U(u) ^
           1 +---------
             |       /
             |     /
             |   /
             | /
           0 +---------+---> u
                     1
    ```

**How is the CDF Useful?**

1.  **Unified Description:** It describes *any* random variable's probability distribution.
2.  **Calculating Interval Probabilities:** This is a key use! For any $a < b$:
    $P(a < X \le b) = P(X \le b) - P(X \le a) = F_X(b) - F_X(a)$
    *   *Derivation:* The event $\{X \le b\}$ can be split into two disjoint events: $\{X \le a\}$ and $\{a < X \le b\}$. By probability additivity, $P(X \le b) = P(X \le a) + P(a < X \le b)$. Rearrange this.
    *   *Visual:* The probability mass strictly between $a$ and up to $b$ is the total mass up to $b$ minus the total mass up to $a$.
    *   *Example (Die Roll):* $P(2 < Y \le 4) = F_Y(4) - F_Y(2) = 4/6 - 2/6 = 2/6$. (This corresponds to $Y=3$ or $Y=4$).
    *   *Example (Uniform):* $P(0.2 < U \le 0.7) = F_U(0.7) - F_U(0.2) = 0.7 - 0.2 = 0.5$.

3.  **Calculating Other Probabilities:**
    *   $P(X > x) = 1 - P(X \le x) = 1 - F_X(x)$
    *   $P(X < x) = \lim_{y \to x^-} F_X(y)$ (limit from the left; excludes point mass at $x$ if any)
    *   $P(X \ge x) = 1 - P(X < x) = 1 - \lim_{y \to x^-} F_X(y)$
    *   $P(X = x) = F_X(x) - \lim_{y \to x^-} F_X(y)$. This is the *size of the jump* in the CDF at point $x$.
        *   For a continuous RV, the CDF is continuous everywhere, so the limit from the left equals the function value, the jump size is 0, and $P(X=x) = 0$.
        *   For a discrete RV, this formula recovers the PMF: $P(X=x_i) = p_X(x_i) = F_X(x_i) - F_X(x_i^-)$.

**Summary**

*   The Cumulative Distribution Function (CDF), $F_X(x) = P(X \le x)$, gives the accumulated probability up to a value $x$.
*   It's defined for *all* random variables (discrete, continuous, mixed).
*   It's always non-decreasing, goes from 0 to 1, and is right-continuous.
*   Its graph is a step function for discrete RVs and typically smooth (or piecewise smooth) for continuous RVs.
*   It's fundamental for calculating probabilities of intervals: $P(a < X \le b) = F_X(b) - F_X(a)$.
*   It fully characterizes the probability distribution of a random variable.