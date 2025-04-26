---
layout: default
title: Probability Mass Function
parent: Probability and Statistics
nav_order: 4
---
# Probability Mass Function

Okay, let's explore the Probability Mass Function (PMF). This is a fundamental tool for describing the behavior of a specific type of random variable.

**Prerequisites: Random Variables (The Discrete Kind)**

Before we define the PMF, we must be comfortable with the idea of a **Random Variable (RV)**, specifically a **Discrete Random Variable**.

*   Recall: A Random Variable $X$ is a function $X: \Omega \rightarrow \mathbb{R}$ that assigns a real number to each outcome $\omega$ in the sample space $\Omega$.
*   **Discrete RV:** A random variable $X$ is *discrete* if the set of all possible values it can take is either *finite* (like {0, 1, 2, 3}) or *countably infinite* (like {0, 1, 2, 3, ...}). Think of these values as distinct, separated points on the number line. There are "gaps" between them.
    *   *Examples:*
        *   The number of heads in 5 coin flips (values {0, 1, 2, 3, 4, 5} - finite).
        *   The sum of two dice rolls (values {2, 3, ..., 12} - finite).
        *   The number of coin flips needed until the first Head appears (values {1, 2, 3, ...} - countably infinite).

**The Goal: Describing Probabilities of Discrete RVs**

We have our discrete random variable $X$, which can take on values from a specific set $S_X = \{x_1, x_2, x_3, ...\}$. We know how to calculate $P(X=x)$ for any specific value $x$ by going back to the original sample space Ω: $P(X=x) = P(\{\omega \in \Omega \mid X(\omega) = x\})$.

However, often we want a more direct way to describe the probabilistic behavior of $X$ itself, without explicit reference to Ω every time. We want a function that directly tells us the probability associated with *each possible numerical value* that $X$ can take. This function is the Probability Mass Function (PMF).

**Definition: Probability Mass Function (PMF)**

Let $X$ be a **discrete random variable**. The **Probability Mass Function (PMF)** of $X$, denoted by $p_X(x)$ (or sometimes $f_X(x)$ or simply $P(X=x)$), is a function that gives the probability that the random variable $X$ is exactly equal to some value $x$.

**Mathematical Form:**
The PMF $p_X$ is defined for any real number $x$ as:
$p_X(x) = P(X=x)$

**Key Characteristic:**
Since $X$ is discrete and can only take values from the set $S_X = \{x_1, x_2, x_3, ...\}$ (called the *support* of X), the probability $P(X=x)$ will be zero for any $x$ that is *not* in $S_X$.

So,
*   If $x \in S_X$ (i.e., $x$ is one of the possible values for X), then $p_X(x) > 0$.
*   If $x \notin S_X$ (i.e., $x$ is not a possible value for X), then $p_X(x) = 0$.

**Visual Intuition: Probability as "Mass" on the Number Line**

Think of the total probability (which is 1) as a total amount of "mass" that needs to be distributed.
*   For a **discrete** random variable, this mass is not spread out smoothly. Instead, it is concentrated entirely at the specific, distinct points $\{x_1, x_2, x_3, ...\}$ on the real number line that the random variable can take.
*   The PMF, $p_X(x_i)$, tells you exactly how much probability mass is located *at* the point $x_i$. Everywhere else on the number line, the mass is zero.

Imagine the number line. At each possible value $x_i$ that X can take, draw a vertical line or "spike" whose height is equal to the probability $p_X(x_i) = P(X=x_i)$. The PMF is essentially this collection of spikes.

```
      Probability Mass p_X(x)
          ^
          |          p_X(x₃)
          |            •
          |            |
          | p_X(x₂)    |
          |   •        |
          |   |        |    p_X(x₄)
 p_X(x₁)  |   |        |      •
    •     |   |        |      |
    |     |   |        |      |
----+-----+---+--------+------+------> Real Number Line x
          x₁  x₂       x₃     x₄

 (Mass=p_X(x₁)) (Mass=p_X(x₂)) etc.
 Between these points, the PMF is zero.
```

**Properties of a PMF**

Any function $p_X(x)$ must satisfy two conditions to be a valid PMF, which derive directly from the axioms of probability:

1.  **Non-negativity:** Since $p_X(x)$ represents a probability, it must be non-negative.
    $p_X(x) \ge 0 \quad \text{for all } x \in \mathbb{R}$

2.  **Normalization:** The random variable $X$ *must* take on one of its possible values from the support set $S_X$. The events $\{X=x_i\}$ for $x_i \in S_X$ are mutually exclusive. Therefore, the sum of the probabilities for all possible values must equal 1 (representing the total probability $P(\Omega)=1$).
    $\sum_{x \in S_X} p_X(x) = 1$
    (The sum is taken over all possible values $x$ in the support $S_X$.)

If a function $p(x)$ satisfies these two properties over a discrete set $S_X$, then it is a valid PMF for some discrete random variable.

**Examples**

1.  **Fair Coin Flip:**
    *   Experiment: Flip a fair coin. Ω = {H, T}.
    *   RV: $X = 1$ if Heads, $X=0$ if Tails.
    *   Support: $S_X = \{0, 1\}$.
    *   PMF:
        *   $p_X(0) = P(X=0) = P(\{\text{Tails}\}) = 1/2$
        *   $p_X(1) = P(X=1) = P(\{\text{Heads}\}) = 1/2$
        *   $p_X(x) = 0$ for all $x \neq 0, 1$.
    *   Check Properties: $p_X(0) \ge 0$, $p_X(1) \ge 0$. Sum: $p_X(0) + p_X(1) = 1/2 + 1/2 = 1$.
    *   Visual: Two spikes of height 1/2 at x=0 and x=1.

2.  **Fair Die Roll:**
    *   Experiment: Roll a fair six-sided die. Ω = {1, 2, 3, 4, 5, 6}.
    *   RV: $Y = $ the number shown.
    *   Support: $S_Y = \{1, 2, 3, 4, 5, 6\}$.
    *   PMF: Since each outcome has probability 1/6:
        *   $p_Y(k) = P(Y=k) = P(\{k\}) = 1/6$ for $k \in \{1, 2, 3, 4, 5, 6\}$.
        *   $p_Y(y) = 0$ for all other $y$.
    *   Check Properties: $1/6 \ge 0$. Sum: $\sum_{k=1}^{6} p_Y(k) = 6 \times (1/6) = 1$.
    *   Visual: Six equal spikes of height 1/6 at x=1, 2, 3, 4, 5, 6.

3.  **Number of Heads in Two Fair Coin Flips:**
    *   Experiment: Flip a fair coin twice. Ω = {HH, HT, TH, TT}.
    *   RV: $Z = $ number of Heads.
    *   Support: $S_Z = \{0, 1, 2\}$.
    *   PMF Calculation:
        *   $Z=0$: Outcome {TT}. $p_Z(0) = P(Z=0) = P(\{TT\}) = 1/4$.
        *   $Z=1$: Outcomes {HT, TH}. $p_Z(1) = P(Z=1) = P(\{HT, TH\}) = P(\{HT\}) + P(\{TH\}) = 1/4 + 1/4 = 2/4 = 1/2$.
        *   $Z=2$: Outcome {HH}. $p_Z(2) = P(Z=2) = P(\{HH\}) = 1/4$.
        *   $p_Z(z) = 0$ otherwise.
    *   PMF can be summarized as:
        $p_Z(z) = \begin{cases} 1/4 & \text{if } z=0 \\ 1/2 & \text{if } z=1 \\ 1/4 & \text{if } z=2 \\ 0 & \text{otherwise} \end{cases}$
    *   Check Properties: All values $\ge 0$. Sum: $1/4 + 1/2 + 1/4 = 1$.
    *   Visual: Spikes at x=0 (height 1/4), x=1 (height 1/2), x=2 (height 1/4).

**Using the PMF**

Once you have the PMF for a discrete random variable $X$, you can easily calculate the probability that $X$ falls into any set $A$ of real numbers: you just sum the PMF values for all possible outcomes $x_i$ that are in the set $A$.

$P(X \in A) = \sum_{x_i \in A \cap S_X} p_X(x_i)$

*   Example (Two coin flips, $Z$): What is the probability of getting at least one head? This is $P(Z \ge 1)$. The values in the support $S_Z=\{0, 1, 2\}$ that satisfy $z \ge 1$ are {1, 2}.
    $P(Z \ge 1) = P(Z=1) + P(Z=2) = p_Z(1) + p_Z(2) = 1/2 + 1/4 = 3/4$.
    Alternatively, $P(Z \ge 1) = 1 - P(Z < 1) = 1 - P(Z=0) = 1 - p_Z(0) = 1 - 1/4 = 3/4$.

**Summary**

*   The Probability Mass Function (PMF), $p_X(x)$, describes the probability distribution of a **discrete** random variable $X$.
*   It gives the probability that $X$ is exactly equal to a specific value $x$: $p_X(x) = P(X=x)$.
*   The probability "mass" is concentrated only at the discrete points $x_i$ that $X$ can take; $p_X(x)=0$ elsewhere.
*   A valid PMF must be non-negative ($p_X(x) \ge 0$) and sum to 1 over all possible values ($\sum p_X(x_i) = 1$).
*   It provides a complete and direct description of the random variable's probabilistic behavior, moving the focus from the original sample space Ω to the numerical values of X itself.