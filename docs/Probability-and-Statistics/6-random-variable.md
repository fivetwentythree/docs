---
layout: default
title: Random Variable
parent: Probability and Statistics
nav_order: 4
---
# Random Variable

**Prerequisites: Setting the Scene**

1.  **Random Experiment:** An action or process with an uncertain outcome (e.g., flipping a coin, rolling dice, measuring someone's height).
2.  **Sample Space (Ω):** The set of *all possible* distinct outcomes of the experiment. Outcomes don't have to be numbers.
    *   Coin Flip: Ω = {Heads, Tails}
    *   Roll two Dice: Ω = {(1,1), (1,2), ..., (1,6), (2,1), ..., (6,6)} (36 outcomes)
    *   Choose a student from class: Ω = {Alice, Bob, Charlie, ...}
3.  **Events:** Subsets of Ω (e.g., getting 'Heads', rolling a sum of 7, choosing a female student).
4.  **Probability Measure (P):** A function assigning a probability $P(E)$ to each event $E \subseteq \Omega$, satisfying the axioms of probability.
5.  **Functions (Basic Idea):** A rule that assigns exactly one output element to each input element. You have a set of inputs (the domain) and a set of possible outputs (the codomain). Example: $f(x) = x^2$ takes a number $x$ (input) and assigns its square $x^2$ (output).

**The "Why": Why Do We Need Random Variables?**

Often, the raw outcomes in our sample space Ω aren't numbers themselves (like "Heads" or "Tails", or a specific person "Alice"). However, we are frequently interested in some *numerical characteristic* associated with the outcome.

*   For a coin flip, we might care *how many* heads we got (0 or 1).
*   For rolling two dice, we might care about the *sum* of the numbers shown.
*   For choosing a student, we might care about their *height* or their *test score*.

We need a formal way to link the actual outcomes (elements $\omega$ in Ω) to these numerical values of interest. This bridge is the **Random Variable**.

**Definition: Random Variable**

A **Random Variable** (often abbreviated RV) is formally a **function** that maps each outcome in the sample space (Ω) to a real number ($\mathbb{R}$).

*   **Notation:** We usually denote random variables with capital letters, like X, Y, or Z.
*   **Mapping:** If $\omega$ represents a specific outcome in the sample space Ω, then $X(\omega)$ is the real number assigned to that outcome by the random variable X.

**Mathematical Form:**
A random variable X is a function:
$X: \Omega \rightarrow \mathbb{R}$

This means:
*   The **domain** of the function X is the sample space Ω.
*   The **codomain** of the function X is the set of all real numbers $\mathbb{R}$.
*   For every possible outcome $\omega \in \Omega$, the function X assigns a single real number $X(\omega)$.

**Visual Intuition: The Mapping**

Imagine the sample space Ω as a cloud containing all possible outcomes. Imagine the real number line $\mathbb{R}$ stretched out separately. A random variable X is a set of arrows, one starting from *each* outcome $\omega$ in the cloud Ω and pointing to *exactly one* specific point $X(\omega)$ on the real number line.

```
      Sample Space (Ω)                  Real Number Line (ℝ)
  +-----------------------+             <---------------------->
  |                       |                |    |    |    |    |
  |    ω₁ • --------------+--------------->• x₁ |    |    |    |
  |         \             |                |    |    |    |    |
  |          \            |                |    |    |    |    |
  |    ω₂ • ---+----------+--------------->• x₂ |    |    |    |
  |            |          |                |    |    |    |    |
  |    ω₃ • ---+----------+--------------->• x₂ |    |    |    |  <- Note: Different outcomes
  |            |          |                |    |    |    |       can map to the same number.
  |    ω₄ • --------------+--------------->• x₃ |    |    |    |
  |                       |                |    |    |    |    |
  +-----------------------+             ... -2  -1   0    1    2 ...

     (Outcomes like           (Numerical values assigned by X)
      'Heads', '(1,4)',
      'Alice', etc.)
```

**Crucial Distinction: The Random Variable vs. Its Values**

*   The **Random Variable (e.g., X)** is the *function itself* – the rule, the mapping, the entire set of arrows in the visual. Before the experiment happens, X represents an uncertain numerical quantity whose value depends on the outcome.
*   The **value (or realization) of the random variable (e.g., $x = X(\omega)$)** is the specific number that the function assigns *after* a particular outcome $\omega$ has occurred.

Think of $X$ as the question "What will the sum of the dice be?" and $x=7$ as a possible answer after you've rolled the dice and the outcome was, say, $\omega = (3, 4)$.

**Examples**

1.  **Single Coin Flip:**
    *   Ω = {Heads, Tails}
    *   Define RV X = "Number of Heads".
    *   Mapping:
        *   $X(\text{Heads}) = 1$
        *   $X(\text{Tails}) = 0$
    *   The possible values for X are {0, 1}.

2.  **Roll Two Fair Dice:**
    *   Ω = {(1,1), (1,2), ..., (6,6)} (36 outcomes)
    *   Define RV S = "Sum of the numbers on the two dice".
    *   Mapping (examples):
        *   $S((1,1)) = 1+1 = 2$
        *   $S((1,2)) = 1+2 = 3$
        *   $S((2,1)) = 2+1 = 3$
        *   $S((4,6)) = 4+6 = 10$
        *   $S((6,6)) = 6+6 = 12$
    *   The possible values for S are {2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12}. Notice multiple outcomes in Ω map to the same value of S (e.g., (1,2) and (2,1) both map to S=3).

3.  **Roll Two Fair Dice (Different RV):**
    *   Ω = {(1,1), (1,2), ..., (6,6)} (Same sample space)
    *   Define RV M = "Maximum of the numbers on the two dice".
    *   Mapping (examples):
        *   $M((1,1)) = \max(1,1) = 1$
        *   $M((1,5)) = \max(1,5) = 5$
        *   $M((5,1)) = \max(5,1) = 5$
        *   $M((3,4)) = \max(3,4) = 4$
    *   The possible values for M are {1, 2, 3, 4, 5, 6}. This is a *different* function (different RV) defined on the *same* sample space as S.

4.  **Height Measurement:**
    *   Experiment: Select a random student from a university.
    *   Ω = {Student 1, Student 2, ..., Student N}
    *   Define RV H = "Height of the selected student in centimeters".
    *   Mapping:
        *   $H(\text{Student 1}) = 172.5$
        *   $H(\text{Student 2}) = 165.1$
        *   ...
    *   The possible values for H could theoretically be any positive real number within a certain range (e.g., [140 cm, 220 cm]).

**Connecting Random Variables to Probability**

The power of RVs comes when we combine them with the probability measure P defined on the original sample space Ω. Since an RV links outcomes to numbers, we can now ask about the probability of the RV taking on certain numerical values or ranges of values.

*   **Notation:** We write $P(X=x)$ to mean "the probability that the random variable X takes on the value $x$".
*   **Meaning:** This is shorthand for the probability of the *set of all outcomes in Ω that get mapped to the value x by X*.
    $P(X=x) \equiv P(\{\omega \in \Omega \mid X(\omega) = x\})$

*   **Notation:** We write $P(X \le x)$ to mean "the probability that the random variable X takes on a value less than or equal to $x$".
*   **Meaning:** This is shorthand for the probability of the *set of all outcomes in Ω that get mapped to any value less than or equal to x by X*.
    $P(X \le x) \equiv P(\{\omega \in \Omega \mid X(\omega) \le x\})$

**Example: Probability for the Sum of Two Dice (RV S)**

Let's find $P(S=3)$.
1.  Identify the outcomes $\omega$ in Ω for which $S(\omega)=3$: These are (1,2) and (2,1).
2.  Find the probability of this set of outcomes in the original sample space:
    $\{\omega \in \Omega \mid S(\omega)=3\} = \{(1,2), (2,1)\}$
    Assuming fair dice, each outcome $(i,j)$ has probability 1/36.
    $P(S=3) = P(\{(1,2), (2,1)\}) = P(\{(1,2)\}) + P(\{(2,1)\}) = \frac{1}{36} + \frac{1}{36} = \frac{2}{36} = \frac{1}{18}$.

Let's find $P(S \le 3)$.
1.  Identify outcomes $\omega$ where $S(\omega) \le 3$: These are outcomes where the sum is 2 or 3.
    *   $S=2$: (1,1)
    *   $S=3$: (1,2), (2,1)
2.  Find the probability of this set of outcomes:
    $\{\omega \in \Omega \mid S(\omega) \le 3\} = \{(1,1), (1,2), (2,1)\}$
    $P(S \le 3) = P(\{(1,1), (1,2), (2,1)\}) = P(\{(1,1)\}) + P(\{(1,2)\}) + P(\{(2,1)\}) = \frac{1}{36} + \frac{1}{36} + \frac{1}{36} = \frac{3}{36} = \frac{1}{12}$.

**Types of Random Variables (A Preview)**

Based on the set of possible values the RV can take, we categorize them:

1.  **Discrete Random Variable:** Can only take on a finite number of values or a countably infinite sequence of values (like 0, 1, 2, 3,...). There are "gaps" between the possible values.
    *   Examples: Number of heads (X), Sum of dice (S), Maximum of dice (M).
2.  **Continuous Random Variable:** Can take on *any* value within a given interval or collection of intervals on the real number line. There are no gaps between possible values within the range.
    *   Examples: Height of a student (H), Temperature tomorrow, Time until a device fails.

This distinction is important because the way we describe their probabilities (using Probability Mass Functions for discrete RVs vs. Probability Density Functions for continuous RVs) is different.

**Summary**

*   A random variable is a **function** $X: \Omega \rightarrow \mathbb{R}$.
*   It assigns a **real number** $X(\omega)$ to each **outcome** $\omega$ in the sample space.
*   It allows us to translate (potentially non-numeric) outcomes into numbers we can analyze.
*   We can calculate probabilities like $P(X=x)$ or $P(X \le x)$ by looking at the probability of the corresponding set of original outcomes in Ω.
*   Random variables provide the essential link between the abstract world of sample spaces and the quantitative analysis of random phenomena. They are the central objects of study in probability theory and statistics.

**(Technical Note for the Thurston-minded):** For the probabilities like $P(X \le x)$ to be well-defined for *any* real number x, the function X must be "measurable". This means that the set $\{\omega \in \Omega \mid X(\omega) \le x\}$ must be a valid event in the original sample space (i.e., it must belong to the sigma-algebra associated with Ω). In practice, nearly all natural functions we define from sample spaces to real numbers satisfy this condition.