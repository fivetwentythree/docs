---
layout: default
title: Conditional Probability 
parent: Probability and Statistics 
nav_order: 4
---
# Conditional Probability

Okay, let's explore the fascinating idea of conditional probability. It's all about how our knowledge or assumptions about one event change our assessment of the likelihood of another event.

**Prerequisites: The Foundation**

Before we dive in, let's quickly recall what we need:

1.  **Sample Space (Ω):** The set of all possible outcomes of an experiment. (Think of it as the "universe" of possibilities).
2.  **Event (A, B, ...):** A subset of the sample space; a collection of outcomes we're interested in.
3.  **Probability Measure (P):** A function assigning a number P(A) between 0 and 1 to each event A, representing its likelihood. We assume P satisfies the Axioms of Probability (non-negativity, normalization P(Ω)=1, additivity).
4.  **Intersection (A ∩ B):** The event that *both* A *and* B occur. These are the outcomes common to both sets A and B.

**The Core Idea: Updating Probabilities with Information**

Imagine you're rolling a standard six-sided die. The sample space is Ω = {1, 2, 3, 4, 5, 6}. Let event A be "rolling a number greater than 3", so A = {4, 5, 6}. Assuming a fair die, $P(A) = 3/6 = 1/2$.

Now, suppose someone performs the roll, hides the result, but tells you, "By the way, the number rolled was *even*." Let event B be "rolling an even number", so B = {2, 4, 6}.

Does this new information (knowing B occurred) change the probability of A (rolling > 3)? Yes, it should! We started with {1, 2, 3, 4, 5, 6}, but now we *know* the outcome must be in {2, 4, 6}. Our world of possibilities has shrunk. Within this new, smaller world, which outcomes also satisfy A (> 3)? Only {4, 6}.

Intuitively, within the reduced set of possibilities {2, 4, 6}, two out of the three outcomes ({4, 6}) satisfy event A. So, the *updated* probability of A, given the information B, seems to be 2/3.

This updated probability is what we call **conditional probability**.

**Definition: Conditional Probability**

The conditional probability of event A occurring *given that* event B has already occurred is denoted by $P(A \mid B)$. It is defined as:

$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$

provided that $P(B) > 0$. (We cannot condition on an event that has zero probability of happening).

*   **$P(A \mid B)$:** Read as "the probability of A given B".
*   **$P(A \cap B)$:** The probability that *both* A and B occur. This represents the outcomes that satisfy the event we care about (A) *within* the context of the information we received (B).
*   **$P(B)$:** The probability of the event B that we know (or assume) has occurred.

**Visual Intuition: The Reduced Sample Space**

Think of the sample space Ω as a square with area 1 (since $P(\Omega)=1$). Events A and B are regions within this square, and their areas correspond to their probabilities, P(A) and P(B). The overlapping area is $A \cap B$, with area $P(A \cap B)$.

[Imagine a square representing Ω. Inside, draw two overlapping shapes, one for A and one for B. The area where they overlap is A ∩ B.]

Now, when we are *given* that event B has occurred, we are effectively throwing away all the outcomes outside of B. Our entire universe of possibilities shrinks down to just the region B.

[Imagine erasing everything outside the shape B. The remaining shape B is our new, effective sample space.]

Within this new sample space (the region B), we want to know the probability of A happening. The outcomes that correspond to A happening *within this new space* are precisely the outcomes in the intersection $A \cap B$.

Probability is a relative measure. The conditional probability $P(A \mid B)$ is the *proportion* of the new sample space (B) that is occupied by the event of interest (A, restricted to B). It's the ratio of the "favorable" area within the new space to the total area of the new space.

$P(A \mid B) = \frac{\text{Area}(A \cap B)}{\text{Area}(B)} = \frac{P(A \cap B)}{P(B)}$

**Example 1: Rolling a Die (Revisited)**

*   Ω = {1, 2, 3, 4, 5, 6}
*   A = {4, 5, 6} (Roll > 3)
*   B = {2, 4, 6} (Roll is even)
*   $A \cap B = \{4, 6\}$ (Roll is even AND > 3)
*   Assuming a fair die: $P(A) = 3/6$, $P(B) = 3/6$, $P(A \cap B) = 2/6$.

Using the formula:
$P(A \mid B) = \frac{P(A \cap B)}{P(B)} = \frac{2/6}{3/6} = \frac{2}{3}$
This matches our earlier intuition. Knowing the roll was even increased the probability of it being greater than 3 (from 1/2 to 2/3).

**Example 2: Drawing Cards**

Draw one card from a standard 52-card deck.
*   Ω = {52 cards}
*   A = {Card is a King} (4 outcomes) => $P(A) = 4/52 = 1/13$
*   B = {Card is a Face Card} (K, Q, J of each suit: 12 outcomes) => $P(B) = 12/52 = 3/13$
*   $A \cap B$: {Card is a King AND a Face Card}. Since all Kings are Face Cards, $A \cap B = A$. => $P(A \cap B) = P(A) = 4/52$.

What is the probability the card is a King, *given* that it is a Face Card? $P(A \mid B)$?

$P(A \mid B) = \frac{P(A \cap B)}{P(B)} = \frac{4/52}{12/52} = \frac{4}{12} = \frac{1}{3}$

*   *Intuition Check:* If we know we have a Face Card, our sample space shrinks to just those 12 cards {J♠, Q♠, K♠, ..., K♣}. Within these 12 cards, 4 are Kings. So the probability is 4/12 = 1/3. It works!

**The Multiplication Rule**

The definition of conditional probability can be rearranged to give us a way to calculate the probability of the intersection of two events. This is called the Multiplication Rule.

Starting from $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$, multiply both sides by $P(B)$:

$P(A \cap B) = P(A \mid B) P(B)$

Similarly, starting from $P(B \mid A) = \frac{P(B \cap A)}{P(A)}$ and knowing $A \cap B = B \cap A$:

$P(A \cap B) = P(B \mid A) P(A)$

*   **Intuition:** The probability that *both* A and B occur is the probability that B occurs ($P(B)$) times the probability that A occurs *given that B occurred* ($P(A \mid B)$). Symmetrically, it's the probability A occurs ($P(A)$) times the probability B occurs *given A occurred* ($P(B \mid A)$). This is very useful when dealing with sequential events.

**Example 3: Drawing Cards Without Replacement**

Draw two cards from a standard 52-card deck *without* replacing the first card. What is the probability that both cards are Hearts?
*   Let A = {1st card is a Heart}.
*   Let B = {2nd card is a Heart}.
*   We want to find $P(A \cap B)$.

Using the Multiplication Rule: $P(A \cap B) = P(B \mid A) P(A)$

1.  Calculate $P(A)$: There are 13 Hearts in 52 cards. $P(A) = 13/52 = 1/4$.
2.  Calculate $P(B \mid A)$: This is the probability the second card is a Heart *given* the first was a Heart. If the first was a Heart, there are now 51 cards left, and 12 of them are Hearts. So, $P(B \mid A) = 12/51$.
3.  Apply the rule:
    $P(A \cap B) = P(B \mid A) P(A) = \frac{12}{51} \times \frac{13}{52} = \frac{12}{51} \times \frac{1}{4} = \frac{3}{51} = \frac{1}{17}$

So, the probability of drawing two Hearts in a row is 1/17.

**Independence of Events**

Now, we come to a crucial special case. What if knowing that B occurred gives us *absolutely no information* about the likelihood of A? In this case, the conditional probability 
$P(A \mid B)$ would be exactly the same as the original probability $P(A)$. This situation is called **independence**.

**Definition 1 (via Conditional Probability):**
Two events A and B are **independent** if:
$P(A \mid B) = P(A)$ (assuming $P(B) > 0$)
Equivalently, if $P(A) > 0$, independence also means:
$P(B \mid A) = P(B)$

**Definition 2 (via Multiplication Rule - often more practical):**
Substitute $P(A \mid B) = P(A)$ into the Multiplication Rule $P(A \cap B) = P(A \mid B)P(B)$. This gives us the most common definition of independence:
Two events A and B are **independent** if and only if:

$P(A \cap B) = P(A) P(B)$

*   **Intuition:** For independent events, the probability of both happening together is simply the product of their individual probabilities. This feels right for things that don't influence each other, like separate coin flips or dice rolls.

**Example 4: Fair Coin Flips**

Flip a fair coin twice.
*   Ω = {HH, HT, TH, TT}
*   A = {1st flip is Heads} = {HH, HT}. $P(A) = 2/4 = 1/2$.
*   B = {2nd flip is Heads} = {HH, TH}. $P(B) = 2/4 = 1/2$.
*   $A \cap B$ = {Both flips are Heads} = {HH}. $P(A \cap B) = 1/4$.

Are A and B independent? Let's check using the multiplication rule definition:
Is $P(A \cap B) = P(A) P(B)$?
Is $1/4 = (1/2) \times (1/2)$?
Yes, $1/4 = 1/4$. Therefore, the events are independent. Knowing the result of the first flip doesn't change the probability of getting Heads on the second flip.

**Example 5: Rolling a Die Once**

*   Ω = {1, 2, 3, 4, 5, 6}
*   A = {Roll is even} = {2, 4, 6}. $P(A) = 3/6 = 1/2$.
*   B = {Roll is > 4} = {5, 6}. $P(B) = 2/6 = 1/3$.
*   $A \cap B$ = {Roll is even AND > 4} = {6}. $P(A \cap B) = 1/6$.

Are A and B independent?
Is $P(A \cap B) = P(A) P(B)$?
Is $1/6 = (1/2) \times (1/3)$?
Yes, $1/6 = 1/6$. So, in a single roll of a fair die, the event "getting an even number" and the event "getting a number greater than 4" are independent.

**Example 6: Are disjoint events independent? (Important Distinction!)**

Let's roll a die again.
*   A = {Roll is a 1} = {1}. $P(A) = 1/6$.
*   B = {Roll is a 6} = {6}. $P(B) = 1/6$.
These events are **disjoint** (mutually exclusive) because they cannot happen at the same time. $A \cap B = \emptyset$.
Therefore, $P(A \cap B) = P(\emptyset) = 0$.

Are they independent? Let's check the rule:
Is $P(A \cap B) = P(A) P(B)$?
Is $0 = (1/6) \times (1/6)$?
Is $0 = 1/36$? No!

**Disjoint events (with non-zero probabilities) are NOT independent.** In fact, they are highly *dependent*. If you know A occurred (the roll was 1), you know for certain that B (the roll is 6) *did not* occur. $P(B \mid A) = 0$, which is not equal to $P(B) = 1/6$. Don't confuse disjointness (cannot happen together) with independence (occurrence of one doesn't affect the probability of the other).

**Visual Intuition for Independence:**

If A and B are independent, the proportion of region B that is also covered by A is the same as the proportion of the entire space Ω that is covered by A. A takes up the same relative "slice" of B as it does of the whole space.

[Imagine the square Ω again with regions A and B. If P(A)=1/4 and P(B)=1/3, and they are independent, the overlap area P(A ∩ B) must be exactly (1/4) * (1/3) = 1/12. The region A occupies exactly 1/4 of the area within B, just like it occupies 1/4 of the area within Ω.]

**Summary**

*   **Conditional Probability $P(A \mid B)$:** The updated probability of A, given that B has occurred. It's calculated as $P(A \cap B) / P(B)$, representing the proportion of the reduced sample space (B) that satisfies A.
*   **Multiplication Rule $P(A \cap B) = P(A \mid B)P(B) = P(B \mid A)P(A)$:** A way to find the probability of both events happening, especially useful for sequential processes.
*   **Independence:** The special case where knowing B doesn't change the probability of A ($P(A \mid B) = P(A)$). This is equivalent to the condition $P(A \cap B) = P(A)P(B)$. Independent events are fundamentally different from disjoint events.

Understanding conditional probability and independence is crucial for reasoning about uncertainty, making predictions based on partial information, and building more complex probabilistic models. It's a cornerstone of probability theory and its applications.