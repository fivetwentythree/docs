---
layout: default
title: Sample spaces and events
parent: Probability and Statistics
nav_order: 4
---
# Sample spaces and events

**Prerequisite: The Idea of a Set**

Before we talk about probability, we need to understand what a **set** is. It's one of the most fundamental ideas in mathematics.

*   **Definition:** A **set** is simply a collection of distinct objects. These objects are called the **elements** or **members** of the set.
*   **Key Points:**
    *   The objects in a set must be distinct (no repeats matter). {1, 2, 2} is the same set as {1, 2}.
    *   The order of elements in a set doesn't matter. {1, 2, 3} is the same set as {3, 1, 2}.
    *   We usually write sets using curly braces `{}`.
*   **Notation:**
    *   If an object `x` is an element of a set `A`, we write $x \in A$. (Read as "x is in A" or "x is an element of A").
    *   If an object `y` is *not* an element of a set `A`, we write $y \notin A$. (Read as "y is not in A").
*   **Examples:**
    *   The set of primary colors: $C = \{\text{red, yellow, blue}\}$
    *   The set of the first five positive whole numbers: $N = \{1, 2, 3, 4, 5\}$
    *   The set of possible outcomes when flipping a coin: $F = \{\text{Heads, Tails}\}$

Now that we have the idea of a set, we can move into the world of probability.

**1. Experiments and Outcomes**

*   **Experiment:** In probability, an **experiment** is any process or action whose result is uncertain. It's something we can repeat, and although we know what *could* happen, we don't know for sure *what will* happen each time.
    *   *Examples:* Flipping a coin, rolling a standard six-sided die, drawing a card from a deck, measuring the height of a randomly chosen student.

*   **Outcome:** An **outcome** is a single possible result of an experiment. It's the most basic possible result that cannot be broken down further in the context of the experiment.
    *   *Examples:*
        *   Experiment: Flipping a coin. Possible Outcomes: Heads, Tails.
        *   Experiment: Rolling a six-sided die. Possible Outcomes: 1, 2, 3, 4, 5, 6.
        *   Experiment: Drawing a card from a standard 52-card deck. Possible Outcomes: Ace of Spades, 2 of Spades, ..., King of Clubs, King of Diamonds (52 distinct outcomes).

**2. The Sample Space (S)**

*   **Definition:** The **sample space**, usually denoted by the capital letter $S$ (or sometimes the Greek letter Omega, $\Omega$), is the **set** of *all possible distinct outcomes* of an experiment.
*   **Key Idea:** The sample space lists *everything* that could possibly happen as a result of the experiment. It must be complete (no possible outcome is left out) and the outcomes within it must be distinct (mutually exclusive - only one can happen per trial).
*   **Examples:**
    *   Experiment: Flipping a coin once.
        Sample Space: $S = \{\text{Heads, Tails}\}$
    *   Experiment: Rolling a standard six-sided die once.
        Sample Space: $S = \{1, 2, 3, 4, 5, 6\}$
    *   Experiment: Flipping a coin twice. (Let H=Heads, T=Tails)
        Sample Space: $S = \{\text{HH, HT, TH, TT}\}$ (Note: HT means Heads on the first flip, Tails on the second. It's different from TH).
    *   Experiment: Drawing a card from a standard deck.
        Sample Space: $S = \{\text{Ace of Spades, 2 of Spades, ..., King of Diamonds}\}$ (This set has 52 elements).

**3. Events (E)**

*   **Definition:** An **event**, usually denoted by a capital letter (like $E$, $A$, $B$, etc.), is any **subset** of the sample space $S$. In simpler terms, an event is a specific collection of one or more possible outcomes that we might be interested in.
*   **Key Idea:** An event represents a particular result or group of results from the experiment. An event "occurs" if the actual outcome of the experiment is one of the elements in that event set.
*   **Types of Events:**
    *   **Simple Event:** An event consisting of exactly one outcome. Example: Getting a 3 when rolling a die. $E = \{3\}$.
    *   **Compound Event:** An event consisting of more than one outcome. Example: Getting an even number when rolling a die. $E = \{2, 4, 6\}$.
    *   **Certain Event:** The entire sample space $S$ itself is an event. It represents the event that *some* possible outcome occurs (which is certain to happen). $E = S$.
    *   **Impossible Event (Empty Set):** The empty set, denoted by $\emptyset$ or `{}`, is also an event. It represents an event with no outcomes. This event can never occur. Example: Rolling a 7 on a standard six-sided die. $E = \emptyset$.

*   **Examples:**
    *   Experiment: Rolling a six-sided die. $S = \{1, 2, 3, 4, 5, 6\}$.
        *   Event A: Rolling an even number. $A = \{2, 4, 6\}$. (This is a subset of S).
        *   Event B: Rolling a number greater than 4. $B = \{5, 6\}$. (This is a subset of S).
        *   Event C: Rolling a 1. $C = \{1\}$. (This is a simple event and a subset of S).
        *   Event D: Rolling a number less than 7. $D = \{1, 2, 3, 4, 5, 6\} = S$. (This is the certain event).
        *   Event F: Rolling a 0. $F = \{\} = \emptyset$. (This is the impossible event).

**Relationship:** Experiment -> Defines Possible Outcomes -> Collection of all Outcomes = Sample Space (S) -> A specific subset of Outcomes = Event (E). Crucially, an event *is* a set.

**4. Set Theory Operations on Events**

Since events are sets (subsets of the sample space $S$), we can use the standard operations from set theory to combine or modify events. These operations have specific meanings in terms of the occurrence of events. Let $A$ and $B$ be two events associated with a sample space $S$.

*   **Union (A ∪ B): "A or B (or both)"**
    *   **Set Definition:** The union of A and B, written $A \cup B$, is the set containing all outcomes that are in $A$, or in $B$, or in both.
    *   **Probability Meaning:** The event $A \cup B$ occurs if event $A$ occurs, or event $B$ occurs, or both occur.
    *   **Mathematical Notation:**
        $A \cup B = \{x \in S \mid x \in A \text{ or } x \in B\}$
        (Read as: "The set of all outcomes x in S such that x is in A or x is in B")
    *   **Example:** Rolling a die, $S = \{1, 2, 3, 4, 5, 6\}$.
        Let $A = \text{Rolling an even number} = \{2, 4, 6\}$.
        Let $B = \text{Rolling a number greater than 4} = \{5, 6\}$.
        Then $A \cup B = \text{Rolling an even number OR a number greater than 4} = \{2, 4, 5, 6\}$.
        If you roll a 2, 4, 5, or 6, the event $A \cup B$ has occurred.

*   **Intersection (A ∩ B): "A and B"**
    *   **Set Definition:** The intersection of A and B, written $A \cap B$, is the set containing all outcomes that are in *both* $A$ and $B$ simultaneously.
    *   **Probability Meaning:** The event $A \cap B$ occurs only if *both* event $A$ and event $B$ occur during a single trial of the experiment.
    *   **Mathematical Notation:**
        $A \cap B = \{x \in S \mid x \in A \text{ and } x \in B\}$
        (Read as: "The set of all outcomes x in S such that x is in A and x is in B")
    *   **Example:** Rolling a die, $S = \{1, 2, 3, 4, 5, 6\}$.
        Let $A = \text{Rolling an even number} = \{2, 4, 6\}$.
        Let $B = \text{Rolling a number greater than 4} = \{5, 6\}$.
        Then $A \cap B = \text{Rolling an even number AND a number greater than 4} = \{6\}$.
        The event $A \cap B$ only occurs if you roll a 6.

*   **Complement (Aᶜ or A'): "Not A"**
    *   **Set Definition:** The complement of A, written $A^c$ (or sometimes $A'$ or $\bar{A}$), is the set containing all outcomes in the sample space $S$ that are *not* in $A$.
    *   **Probability Meaning:** The event $A^c$ occurs if and only if event $A$ does *not* occur.
    *   **Mathematical Notation:**
        $A^c = \{x \in S \mid x \notin A\}$
        (Read as: "The set of all outcomes x in S such that x is not in A")
    *   **Example:** Rolling a die, $S = \{1, 2, 3, 4, 5, 6\}$.
        Let $A = \text{Rolling an even number} = \{2, 4, 6\}$.
        Then $A^c = \text{NOT rolling an even number} = \{1, 3, 5\}$. (This is the set of odd numbers).
        If you roll a 1, 3, or 5, the event $A^c$ has occurred.

**Important Concept: Mutually Exclusive (Disjoint) Events**

*   **Definition:** Two events $A$ and $B$ are called **mutually exclusive** (or **disjoint**) if they have no outcomes in common. In set terms, their intersection is the empty set.
*   **Meaning:** If events A and B are mutually exclusive, they cannot both happen at the same time in a single trial of the experiment. If one occurs, the other cannot.
*   **Mathematical Notation:** $A \cap B = \emptyset$
*   **Example:** Rolling a die, $S = \{1, 2, 3, 4, 5, 6\}$.
    Let $A = \text{Rolling an even number} = \{2, 4, 6\}$.
    Let $C = \text{Rolling a 1} = \{1\}$.
    Events $A$ and $C$ are mutually exclusive because $A \cap C = \emptyset$. You cannot roll an even number and a 1 on the same single roll.
    However, $A$ and $B$ (Rolling > 4, $B=\{5, 6\}$) are *not* mutually exclusive because $A \cap B = \{6\} \neq \emptyset$. You can roll a 6, which is both even and greater than 4.

**Summary and Why This Matters**

1.  An **Experiment** is an uncertain process.
2.  An **Outcome** is a single basic result of the experiment.
3.  The **Sample Space (S)** is the *set* of all possible outcomes.
4.  An **Event (E)** is a *subset* of the sample space (a collection of outcomes we care about).
5.  Because events are sets, we can use **Set Operations** to combine them:
    *   **Union (∪):** Means "OR" (at least one event occurs).
    *   **Intersection (∩):** Means "AND" (both events occur).
    *   **Complement (ᶜ):** Means "NOT" (the event does not occur).

Understanding these concepts is absolutely essential because **probability itself is defined as a measure assigned to events**. When we ask "What is the probability of rolling an even number?", we are asking for a value associated with the *event* $E = \{2, 4, 6\}$. The rules of probability (which you'll learn next) are built directly upon these definitions and set operations. For example, the probability of $A \cup B$ occurring is related to the probabilities of $A$, $B$, and $A \cap B$.

By defining experiments, outcomes, sample spaces, and events using the precise language of sets, we create a solid, logical framework for analyzing chance and making predictions. You now have the fundamental vocabulary and structure needed to explore probability calculations.