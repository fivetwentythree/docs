---
layout: default
title: Bayes' Theorem
parent: Probability and Statistics
nav_order: 4
---
# Bayes' Theorem

Okay, let's build upon our understanding of conditional probability to explore two incredibly powerful tools: the Law of Total Probability and Bayes' Theorem. These are fundamental for reasoning under uncertainty and updating our beliefs as new evidence comes in.

**Prerequisites:**

*   We need a solid grasp of **Sample Space (Ω)**, **Events (A, B, E, H...)**, **Probability Axioms**, **Intersection (A ∩ B)**, **Disjoint Events**, **Conditional Probability $P(A \mid B) = P(A \cap B) / P(B)$**, and the **Multiplication Rule $P(A \cap B) = P(A \mid B)P(B)$**.
*   A crucial concept is **Partitioning a Sample Space**.

**Concept: Partitioning the Sample Space**

Imagine the entire set of possibilities, our sample space Ω. A **partition** of Ω is a collection of events, let's call them $H_1, H_2, ..., H_n$, such that:

1.  **They are mutually exclusive (disjoint):** No two events can happen at the same time. Mathematically, $H_i \cap H_j = \emptyset$ for all $i \neq j$.
2.  **They are exhaustive:** Together, they cover all possible outcomes. Mathematically, $H_1 \cup H_2 \cup ... \cup H_n = \Omega$.

*   **Visual Intuition:** Think of the sample space Ω as a rectangular cake. A partition is like cutting the cake into several non-overlapping slices ($H_1, H_2, ...$) that perfectly make up the whole cake. No crumbs left out, no slice overlaps another.

[Imagine a rectangle representing Ω. Draw lines across it to divide it into several vertical strips. Label these strips H1, H2, H3, ... Hn. These strips completely cover the rectangle without overlapping.]

*   **Example:** When rolling a die (Ω = {1, 2, 3, 4, 5, 6}), one possible partition is:
    *   $H_1 = \{1, 2\}$ (Roll is low)
    *   $H_2 = \{3, 4\}$ (Roll is medium)
    *   $H_3 = \{5, 6\}$ (Roll is high)
    These are disjoint ($H_1 \cap H_2 = \emptyset$, etc.) and exhaustive ($H_1 \cup H_2 \cup H_3 = \Omega$).
*   A simpler, very common partition involves just an event $H$ and its complement $H^c$ (everything not in H). $\{H, H^c\}$ always forms a partition.

**1. The Law of Total Probability (LTP)**

*   **Purpose:** The LTP provides a way to calculate the total probability of an event (let's call it E) by considering how likely it is under different scenarios or conditions (given by a partition of the sample space).
*   **Scenario:** Suppose we want to find the overall probability of event E, but it's easier to think about the probability of E happening under each of the conditions $H_1, H_2, ..., H_n$ which form a partition of Ω.
*   **Derivation:**
    1.  Consider the event E. Since the partition $H_1, ..., H_n$ covers the entire sample space, any outcome in E must also be in exactly one of the $H_i$.
    2.  Therefore, we can break down event E into disjoint pieces based on which $H_i$ it intersects with:
        $E = (E \cap H_1) \cup (E \cap H_2) \cup ... \cup (E \cap H_n)$
        (Think of E as a shape drawn over the sliced cake. The total area of E is the sum of the areas of its parts within each slice $H_i$).
    3.  Since the $H_i$ are disjoint, the events $(E \cap H_i)$ are also disjoint.
    4.  Using the additivity axiom of probability (Axiom 3) for disjoint events:
        $P(E) = P(E \cap H_1) + P(E \cap H_2) + ... + P(E \cap H_n)$
        $P(E) = \sum_{i=1}^{n} P(E \cap H_i)$
    5.  Now, apply the Multiplication Rule ($P(A \cap B) = P(A \mid B)P(B)$) to each term $P(E \cap H_i)$:
        $P(E \cap H_i) = P(E|H_i) P(H_i)$
    6.  Substitute this back into the sum:

*   **The Law of Total Probability Formula:**
    $P(E) = \sum_{i=1}^{n} P(E \mid H_i) P(H_i)$
    $P(E) = P(E \mid H_1)P(H_1) + P(E \mid H_2)P(H_2) + ... + P(E \mid H_n)P(H_n)$

*   **Intuition:** The total probability of event E is a *weighted average* of its conditional probabilities given each scenario ($P(E \mid H_i)$), where the weights are the probabilities of those scenarios themselves ($P(H_i)$).

*   **Visual Intuition:**
    [Refer back to the partitioned rectangle Ω with strips H1, H2, ... and the overlaid shape E.]
    The total area of E ($P(E)$) is the sum of the areas of the parts of E within each strip ($P(E \cap H_i)$). The area of the part within strip $H_i$ is $P(E \cap H_i)$. We can also think of this area as the *proportion* of strip $H_i$ that is covered by E 
    ($P(E \mid H_i)$) multiplied by the total area of strip $H_i$ ($P(H_i)$). So, $P(E \cap H_i) = P(E \mid H_i)P(H_i)$. Summing these gives the total area P(E).

*   **Example:** Imagine two factories, F1 and F2, produce all the widgets in a town.
    *   Factory F1 produces 60% of the widgets ($P(F1) = 0.6$).
    *   Factory F2 produces 40% of the widgets ($P(F2) = 0.4$).
    Notice {F1, F2} forms a partition of the sample space of widgets.
    *   Suppose 2% of widgets from F1 are defective ($P(D \mid F1) = 0.02$).
    *   Suppose 5% of widgets from F2 are defective ($P(D \mid F2) = 0.05$).
    What is the overall probability that a randomly selected widget is defective ($P(D)$)?
    Using LTP:
    $P(D) = P(D \mid F1)P(F1) + P(D \mid F2)P(F2)$
    $P(D) = (0.02)(0.6) + (0.05)(0.4)$
    $P(D) = 0.012 + 0.020$
    $P(D) = 0.032$
    So, 3.2% of all widgets produced in the town are defective.

**2. Bayes' Theorem**

*   **Purpose:** Bayes' Theorem is arguably one of the most important results in probability theory. It tells us how to formally **update our beliefs (probabilities) about a hypothesis in light of new evidence**. It allows us to "invert" conditional probabilities. Often we know $P(\text{Evidence} \mid \text{Hypothesis})$, but we want to find $P(\text{Hypothesis} \mid \text{Evidence})$.
*   **Scenario:** You have an initial belief about a hypothesis H, represented by its **prior probability** $P(H)$. Then, you observe some new evidence E. You want to calculate the **posterior probability** of the hypothesis, $P(H \mid E)$, which is the updated probability of H *after* considering the evidence E.
*   **Derivation:**
    1.  Start with the definition of conditional probability for $P(H \mid E)$:
        $P(H \mid E) = \frac{P(H \cap E)}{P(E)}$ (Requires $P(E) > 0$)
    2.  Also, consider the definition for $P(E|H)$:
        $P(E \mid H) = \frac{P(E \cap H)}{P(H)}$ (Requires $P(H) > 0$)
    3.  Rearrange the second definition using the multiplication rule (and noting $H \cap E = E \cap H$):
        $P(H \cap E) = P(E \mid H)P(H)$
    4.  Substitute this expression for $P(H \cap E)$ into the numerator of the first equation:
        $P(H \mid E) = \frac{P(E|H)P(H)}{P(E)}$
        This is a common form of Bayes' Theorem.
    5.  Now, often we don't know $P(E)$ directly. We can calculate it using the Law of Total Probability! The simplest and most common partition to use here is $\{H, H^c\}$ (Hypothesis H is true, or Hypothesis H is false). Using LTP with this partition:
        $P(E) = P(E \mid H)P(H) + P(E \mid H^c)P(H^c)$
    6.  Substitute this expansion for $P(E)$ into the denominator of step 4:

*   **Bayes' Theorem Formula (Common Form for Hypothesis H vs H<sup>c</sup>):**
    $P(H \mid E) = \frac{P(E \mid H)P(H)}{P(E \mid H)P(H) + P(E \mid H^c)P(H^c)}$

*   **General Form (using any partition $H_1, ..., H_n$):**
    If we want to find the posterior probability of a specific hypothesis $H_i$ from the partition, given evidence E:
    $P(H_i \mid E) = \frac{P(E\mid H_i)P(H_i)}{P(E)}$
    And expanding $P(E)$ using LTP over the partition $H_1, ..., H_n$:
    $P(H_i \mid E) = \frac{P(E \mid H_i)P(H_i)}{\sum_{j=1}^{n} P(E|H_j) P(H_j)}$

*   **The Components of Bayes' Theorem:**
    *   $P(H \mid E)$: **Posterior Probability:** The probability of hypothesis H *after* observing evidence E. This is what we usually want to compute.
    *   $P(H)$: **Prior Probability:** The initial probability of hypothesis H *before* observing evidence E. Represents our prior belief.
    *   $P(E \mid H)$: **Likelihood:** The probability of observing evidence E *if* hypothesis H were true. This quantifies how well the hypothesis explains the evidence.
    *   $P(E)$: **Probability of the Evidence (Marginal Likelihood):** The overall probability of observing the evidence E, averaged over all possible hypotheses (calculated using LTP). It acts as a normalizing constant, ensuring the posterior probabilities sum to 1 across all hypotheses.
    *   $P(E \mid H^c)$: Likelihood of the evidence under the alternative hypothesis.

*   **Intuition:** Bayes' theorem mathematically combines our prior beliefs with how well our hypothesis explains the new data, relative to how well alternative hypotheses explain the data, to arrive at an updated belief.
    *   Posterior probability is high if:
        *   The prior belief $P(H)$ was already high.
        *   The evidence E is highly likely under hypothesis H ($P(E \mid H)$ is high).
        *   The evidence E is unlikely under alternative hypotheses (making $P(E)$ relatively small, or specifically $P(E \mid H^c)$ small).

*   **Visual Intuition (Relating to LTP visual):**
    [Again, picture the rectangle Ω partitioned into H and H<sup>c</sup>, with the shape E overlaid.]
    Bayes' Theorem $P(H\mid E) = P(H \cap E) / P(E)$ asks: "Given that we landed inside the shape E, what's the probability we also landed in the region H?" This is the ratio of the area of the overlap ($P(H \cap E)$) to the total area of E ($P(E)$).
    *   The numerator $P(E\mid H)P(H)$ *is* the area of the overlap $P(H \cap E)$. It's the part of H that overlaps with E.
    *   The denominator $P(E)$ is the *total* area of E, calculated using LTP by summing the area of E within H ($P(E\mid H)P(H)$) and the area of E within H<sup>c</sup> 
    ($P(E\mid H^c)P(H^c)$).
    So Bayes' Theorem is calculating $\frac{\text{Area of E inside H}}{\text{Total Area of E}}$.


*   **Example: Medical Diagnosis** (Classic Bayes' example)
    Suppose there's a disease (D) that 1% of the population has.
    *   Prior Probability: $P(D) = 0.01$. This implies $P(D^c) = 1 - P(D) = 0.99$.
    There's a test (T) for this disease.
    *   If a person has the disease, the test correctly comes back positive (+) 95% of the time (Sensitivity). Likelihood: $P(+\mid D) = 0.95$.
    *   If a person does *not* have the disease, the test incorrectly comes back positive (false positive) 2% of the time. Likelihood under alternative: $P(+\mid D^c) = 0.02$.
    A person takes the test and it comes back positive. What is the probability they actually have the disease? We want to find $P(D\mid +)$.
    Using Bayes' Theorem:
    $P(D\mid+) = \frac{P(+\mid D)P(D)}{P(+\mid D)P(D) + P(+\mid D^c)P(D^c)}$
    Plug in the values:
    $P(D\mid +) = \frac{(0.95)(0.01)}{(0.95)(0.01) + (0.02)(0.99)}$
    $P(D\mid +) = \frac{0.0095}{0.0095 + 0.0198}$
    $P(D\mid+) = \frac{0.0095}{0.0293} \approx 0.324$

    *   **Interpretation:** Even though the test seems quite accurate (95% sensitivity, only 2% false positive rate), if someone tests positive, the probability they actually have the disease is only about 32.4%! This counter-intuitive result happens because the disease is rare (low prior probability $P(D)$). Most positive tests actually come from the large pool of healthy people getting a false positive ($P(+\mid D^c)P(D^c)$ term dominates the denominator). Bayes' theorem correctly balances the test accuracy with the underlying prevalence of the disease.

**Summary**

*   **Law of Total Probability:** Calculates the overall probability of an event by summing its probabilities across different conditional scenarios (a partition), weighted by the probabilities of those scenarios. Formula: $P(E) = \sum P(E\mid H_i)P(H_i)$.
*   **Bayes' Theorem:** Updates the probability of a hypothesis based on new evidence by relating the desired posterior $P(H\mid E)$ to the prior $P(H)$ and the likelihood $P(E\mid H)$. Formula: $P(H\mid E) = \frac{P(E\mid H)P(H)}{P(E)}$. It provides the mathematically sound way to learn from data.

These two concepts are deeply connected and form the basis for much of statistical inference, machine learning, and scientific reasoning where we need to quantify and update our understanding in the face of new observations.