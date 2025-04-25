---
layout: default
title: Combinatorics 
parent: Probability and Statistics
nav_order: 4
---
# Combinatorics or counting techniques


Okay, let's delve into the world of **Combinatorics**, the art of counting. This is incredibly important in probability, especially when dealing with situations where all individual outcomes are equally likely. In such cases, the probability of an event is simply:


$P(\text{Event}) = \frac{\text{Number of outcomes favorable to the Event}}{\text{Total number of possible outcomes in the Sample Space}}$


So, being able to *count* the number of outcomes accurately is fundamental. Combinatorics gives us the tools to do this systematically, especially when the numbers get large.

**Prerequisite 1: The Fundamental Principle of Counting (The Multiplication Principle)**

This is the bedrock upon which most counting techniques are built.

*   **Idea:** If you have a task or process that consists of a sequence of steps, and there are $n_1$ ways to do the first step, $n_2$ ways to do the second step (after the first step is done), $n_3$ ways to do the third step (after the first two are done), ..., and $n_k$ ways to do the $k$-th step (after all preceding steps are done), then the total number of ways to complete the entire task is the product of the number of ways for each step.
*   **Mathematical Form:** Total ways = $n_1 \times n_2 \times n_3 \times \dots \times n_k$
*   **Intuition:** For each choice you make in one step, you have the full range of choices available for the next step (conditioned on the previous choices, but the *number* of choices is what matters here). The possibilities branch out.
*   **Visual (Tree Diagram):** Imagine choosing an outfit from 2 shirts (S1, S2) and 3 pairs of pants (P1, P2, P3).

    
    *   Step 1: Choose a shirt (2 ways).
    *   Step 2: Choose pants (3 ways).
    *   Total outfits = $2 \times 3 = 6$. The tree diagram visually shows all 6 possible paths (outcomes).
*   **Example:** How many different license plates are possible if they consist of 3 letters followed by 3 digits? (Assuming letters and digits can repeat).
    *   Step 1: Choose 1st letter (26 ways).
    *   Step 2: Choose 2nd letter (26 ways).
    *   Step 3: Choose 3rd letter (26 ways).
    *   Step 4: Choose 1st digit (10 ways, 0-9).
    *   Step 5: Choose 2nd digit (10 ways).
    *   Step 6: Choose 3rd digit (10 ways).
    *   Total license plates = $26 \times 26 \times 26 \times 10 \times 10 \times 10 = 26^3 \times 10^3 = 17,576,000$.

**Prerequisite 2: Factorials**

Factorials are a shorthand notation for a common product that appears frequently in counting.

*   **Definition:** For a non-negative integer $n$, the factorial of $n$, denoted by $n!$, is the product of all positive integers less than or equal to $n$.
*   **Mathematical Form:**
    $n! = n \times (n-1) \times (n-2) \times \dots \times 3 \times 2 \times 1$
*   **Examples:**
    *   $5! = 5 \times 4 \times 3 \times 2 \times 1 = 120$
    *   $3! = 3 \times 2 \times 1 = 6$
    *   $1! = 1$
*   **Special Case: Zero Factorial:** By convention (and for mathematical consistency in formulas), we define:
    $0! = 1$
    *   *Why?* One way to think about it is that $n! = n \times (n-1)!$. If this holds for $n=1$, then $1! = 1 \times (1-1)! = 1 \times 0!$. For this to be true ($1 = 1 \times 0!$), $0!$ must be 1. Another reason is that $n!$ often represents the number of ways to arrange $n$ distinct objects. There is exactly *one* way to arrange zero objects (do nothing, arrange the empty set).

Now, let's get to the main techniques:

**1. Permutations: Order Matters!**

A permutation is an **arrangement** of objects in a specific **order**. Think of it as lining things up or assigning specific roles.

*   **Scenario:** You have a set of distinct objects, and you want to know how many different ways you can arrange a subset of them (or all of them).
*   **Key Question:** Does the order in which I select or arrange the objects make a difference? If yes, it's likely a permutation problem.

*   **Type 1: Permutations of *n* distinct objects taken *n* at a time (Arranging all objects)**
    *   **Question:** How many ways can you arrange *n* distinct objects?
    *   **Logic (using Multiplication Principle):** You have *n* choices for the first position, then *(n-1)* choices for the second position (since one object is used), *(n-2)* for the third, and so on, until you have only 1 choice for the last position.
    *   **Visual (Slots):** Imagine $n$ slots to fill with $n$ distinct objects.
        ```
        Slot 1   Slot 2   Slot 3   ...  Slot n
        -------  -------  -------  ---  -------
        n choices (n-1)chs (n-2)chs ...  1 choice
        ```
    *   **Formula:** The total number of ways is $n \times (n-1) \times \dots \times 1 = n!$
    *   **Example:** How many ways can you arrange the letters A, B, C?
        *   Objects: {A, B, C}, n=3.
        *   Arrangements: ABC, ACB, BAC, BCA, CAB, CBA.
        *   Formula: $3! = 3 \times 2 \times 1 = 6$. Matches the list.

*   **Type 2: Permutations of *n* distinct objects taken *k* at a time (Arranging a subset)**
    *   **Question:** How many ways can you choose and arrange *k* objects from a set of *n* distinct objects (where $k \le n$)?
    *   **Logic (using Multiplication Principle):** You have *n* choices for the first position, *(n-1)* for the second, ..., down to *(n-k+1)* choices for the *k*-th position.
    *   **Visual (Slots):** Imagine *k* slots to fill from *n* distinct objects.
        ```
        Slot 1   Slot 2   ...  Slot k
        -------  -------  ---  -------
        n choices (n-1)chs ... (n-k+1) choices
        ```
    *   **Formula:** The number of permutations is denoted $P(n, k)$ or ${}_n P_k$.
        $P(n, k) = n \times (n-1) \times \dots \times (n-k+1)$
        This can be written more compactly using factorials:
        $P(n, k) = \frac{n!}{(n-k)!}$
        *   *Derivation:* $n! = [n \times (n-1) \times \dots \times (n-k+1)] \times [(n-k) \times (n-k-1) \times \dots \times 1] = P(n,k) \times (n-k)!$. Divide by $(n-k)!$.
    *   **Example:** A club has 10 members. How many ways can they elect a President, a Vice President, and a Treasurer (assuming no person can hold more than one office)?
        *   Objects: 10 members (n=10).
        *   Positions to fill: President, VP, Treasurer (k=3).
        *   Order matters: (Alice=Pres, Bob=VP, Charlie=Treas) is different from (Bob=Pres, Alice=VP, Charlie=Treas).
        *   Formula: $P(10, 3) = \frac{10!}{(10-3)!} = \frac{10!}{7!} = \frac{10 \times 9 \times 8 \times 7!}{7!} = 10 \times 9 \times 8 = 720$.
        *   Using slots: 10 choices for President, 9 for VP, 8 for Treasurer. $10 \times 9 \times 8 = 720$.

*   **Type 3: Permutations with Repetitions (Arranging objects when some are identical)**
    *   **Question:** How many distinct arrangements are there of *n* objects where there are $n_1$ identical objects of type 1, $n_2$ identical objects of type 2, ..., $n_r$ identical objects of type r, such that $n_1 + n_2 + \dots + n_r = n$?
    *   **Logic:** First, pretend *all* $n$ objects are distinct. The number of arrangements would be $n!$. However, because some objects are identical, we have overcounted. For the $n_1$ identical objects of type 1, any permutation among themselves ($n_1!$ ways) leads to the same overall arrangement. Similarly for type 2 ($n_2!$ ways), and so on. We need to divide the total $n!$ by the number of ways the identical objects can be permuted within their groups.
    *   **Formula:**
        Number of distinct permutations = $\frac{n!}{n_1! n_2! \dots n_r!}$
    *   **Example:** How many distinct ways can you arrange the letters in the word "MISSISSIPPI"?
        *   Total letters: n = 11.
        *   Identical letters: M (1), I (4), S (4), P (2). So $n_1=1, n_2=4, n_3=4, n_4=2$. Check: $1+4+4+2 = 11$.
        *   Formula: $\frac{11!}{1! 4! 4! 2!} = \frac{39,916,800}{(1)(24)(24)(2)} = \frac{39,916,800}{1152} = 34,650$.

**2. Combinations: Order Does NOT Matter!**

A combination is a **selection** of objects where the **order** of selection is **irrelevant**. Think of choosing a group or a subset.

*   **Scenario:** You have a set of distinct objects, and you want to know how many different ways you can select a subset of them, without regard to the order in which you pick them.
*   **Key Question:** Does the order in which I select the objects make a difference? If no, it's likely a combination problem.

*   **Combinations of *n* distinct objects taken *k* at a time**
    *   **Question:** How many ways can you choose a subset of *k* objects from a set of *n* distinct objects (where $k \le n$)?
    *   **Logic:** Let's start with the number of *ordered* arrangements of *k* items from *n*, which is $P(n, k)$. Now, consider any specific group of *k* items chosen. How many ways can these *k* items be arranged among themselves? That's $k!$. Since order *doesn't* matter for combinations, all $k!$ permutations of a chosen set correspond to just *one* combination. Therefore, the number of combinations is the number of permutations divided by the number of ways to order the chosen items.
    *   **Formula:** The number of combinations is denoted $C(n, k)$, $\binom{n}{k}$, or ${}_n C_k$. It's often read as "n choose k".
        $C(n, k) = \binom{n}{k} = \frac{P(n, k)}{k!} = \frac{n!}{k!(n-k)!}$
    *   **Visual Comparison (Choosing 2 from {A, B, C})**: n=3, k=2
        *   *Permutations* $P(3, 2) = \frac{3!}{1!} = 6$: (AB), (BA), (AC), (CA), (BC), (CB) - Order matters.
        *   *Combinations* $C(3, 2) = \frac{3!}{2!1!} = 3$: {A, B}, {A, C}, {B, C} - Order doesn't matter; (AB) and (BA) are the same *set*. Notice $6 / 2! = 6 / 2 = 3$.
            
    *   **Example:** A committee of 3 people is to be formed from a group of 10 members. How many different committees are possible?
        *   Objects: 10 members (n=10).
        *   Subset size: 3 people (k=3).
        *   Order doesn't matter: A committee of {Alice, Bob, Charlie} is the same as {Charlie, Alice, Bob}.
        *   Formula: $C(10, 3) = \binom{10}{3} = \frac{10!}{3!(10-3)!} = \frac{10!}{3!7!} = \frac{10 \times 9 \times 8 \times 7!}{ (3 \times 2 \times 1) \times 7!} = \frac{10 \times 9 \times 8}{3 \times 2 \times 1} = \frac{720}{6} = 120$.
    *   **Useful Property:** $\binom{n}{k} = \binom{n}{n-k}$.
        *   *Intuition:* Choosing $k$ items to be on the committee is equivalent to choosing $n-k$ items to *not* be on the committee. The number of ways to do either must be the same.
        *   *Proof:* $\binom{n}{n-k} = \frac{n!}{(n-k)!(n-(n-k))!} = \frac{n!}{(n-k)!k!}$, which is the same as $\binom{n}{k}$.

**3. Partitions: Dividing into Groups**

Partitioning involves dividing a set of objects into several disjoint subsets (groups or cells).

*   **Scenario:** You have *n* objects and want to divide them into distinct groups.

*   **Type 1: Ordered Partitions (Multinomial Coefficients)**
    *   **Question:** How many ways can you divide *n* distinct objects into *r* distinct groups (or boxes), where the first group must have exactly $n_1$ objects, the second exactly $n_2$ objects, ..., and the *r*-th exactly $n_r$ objects, such that $n_1 + n_2 + \dots + n_r = n$?
    *   **Logic:** This can be thought of as a sequence of combinations.
        1.  Choose $n_1$ objects for the first group from the $n$ available: $\binom{n}{n_1}$ ways.
        2.  Choose $n_2$ objects for the second group from the remaining $n-n_1$ objects: $\binom{n-n_1}{n_2}$ ways.
        3.  Choose $n_3$ objects for the third group from the remaining $n-n_1-n_2$ objects: $\binom{n-n_1-n_2}{n_3}$ ways.
        4.  ... Continue until the last group. Choose $n_r$ objects for the $r$-th group from the remaining $n-n_1-\dots-n_{r-1} = n_r$ objects: $\binom{n_r}{n_r} = 1$ way.
        Using the Multiplication Principle, multiply the number of ways for each step.
    *   **Formula:** The number of ways is given by the multinomial coefficient:
        $\binom{n}{n_1, n_2, \dots, n_r} = \binom{n}{n_1} \binom{n-n_1}{n_2} \dots \binom{n_r}{n_r}$
        Expanding this out and simplifying leads to:
        $\binom{n}{n_1, n_2, \dots, n_r} = \frac{n!}{n_1! n_2! \dots n_r!}$
    *   **Connection:** Notice this is the *exact same formula* as permutations with repetitions! How can that be?
        *   *Permutations with Repetitions:* We were arranging $n$ items where some were identical. Think of it as assigning each of the $n$ *positions* in the arrangement to one of the $r$ types of letters. Position 1 gets type S, Position 2 gets type I, etc.
        *   *Ordered Partitions:* We are assigning each of the $n$ distinct *objects* to one of the $r$ distinct groups. Object 1 goes to group 2, Object 2 goes to group 1, etc.
        Mathematically, assigning positions to letter types is equivalent to assigning objects to groups, hence the same formula.
    *   **Example:** In a class of 12 students, how many ways can the teacher divide them into three discussion groups: Group A (4 students), Group B (5 students), and Group C (3 students)?
        *   Objects: 12 distinct students (n=12).
        *   Groups: Group A, Group B, Group C (r=3, distinct groups).
        *   Group sizes: $n_1=4, n_2=5, n_3=3$. Check: $4+5+3 = 12$.
        *   Formula: $\binom{12}{4, 5, 3} = \frac{12!}{4! 5! 3!} = \frac{479,001,600}{(24)(120)(6)} = \frac{479,001,600}{17,280} = 27,720$.
    *   **Relationship to Binomial Coefficient:** A combination $\binom{n}{k}$ is just a partition into two groups: the $k$ items chosen, and the $n-k$ items not chosen. $\binom{n}{k} = \binom{n}{k, n-k} = \frac{n!}{k!(n-k)!}$.

*   **Type 2: Unordered Partitions (More Advanced)**
    *   **Question:** How many ways can you divide *n* distinct objects into *k* non-empty, *indistinguishable* groups? (The group sizes are not fixed beforehand, only the number of groups).
    *   **Example:** How many ways to put 4 distinct balls {A,B,C,D} into 2 identical bags (neither bag can be empty)?
        *   Possible groupings (ignoring bag identity): {A},{B,C,D}; {B},{A,C,D}; {C},{A,B,D}; {D},{A,B,C}; {A,B},{C,D}; {A,C},{B,D}; {A,D},{B,C}.
        *   There are 7 ways.
    *   **Formula:** This involves Stirling Numbers of the Second Kind, denoted $S(n, k)$.
 Calculating these is more complex and often involves recurrence relations. $S(4, 2) = 7$ in the example above. The total number of ways to partition a set of $n$ elements into *any* number of non-empty indistinguishable subsets is given by the Bell numbers.
    *   **Note:** This type is less commonly needed for introductory probability than ordered partitions but is important in deeper combinatorics.

**Connecting Back to Probability**

These techniques are essential for calculating probabilities in discrete sample spaces where outcomes are equally likely (like rolling fair dice, drawing cards from a well-shuffled deck, etc.).

*   **Example:** You draw 5 cards from a standard 52-card deck. What is the probability of getting exactly 3 Hearts?
    1.  **Calculate the size of the sample space |Ω|:** The total number of ways to choose 5 cards from 52, where order doesn't matter.
        $\Omega = \binom{52}{5} = \frac{52!}{5!47!} = 2,598,960$.
    2.  **Calculate the number of outcomes in the event E:** We need exactly 3 Hearts and (therefore) 2 non-Hearts.
        *   Step 1: Choose 3 Hearts from the 13 available Hearts. Order doesn't matter: $\binom{13}{3}$ ways.
        *   Step 2: Choose 2 non-Hearts from the 39 available non-Hearts. Order doesn't matter: $\binom{39}{2}$ ways.
        *   Using the Multiplication Principle, the total number of ways to get exactly 3 Hearts and 2 non-Hearts is:
            $E = \binom{13}{3} \times \binom{39}{2} = \left(\frac{13!}{3!10!}\right) \times \left(\frac{39!}{2!37!}\right) = 286 \times 741 = 211,946$.
    3.  **Calculate the probability:**
        $P(E) = \frac{E}{\Omega} = \frac{211,946}{2,598,960} \approx 0.08155$ or about 8.16%.

**Summary: Key Differences**

*   **Permutation:** Order matters. Arrangement. Think: race results, elected offices (Pres/VP), arranging letters. Formulas: $n!$, $P(n,k)$, $\frac{n!}{n_1!\dots n_r!}$.
*   **Combination:** Order does *not* matter. Selection. Think: committee members, choosing cards for a hand, picking lottery numbers. Formula: $\binom{n}{k}$.
*   **Partition (Ordered):** Dividing into distinct groups of fixed sizes. Think: assigning items to labeled boxes, dealing cards to specific players. Formula: $\binom{n}{n_1, \dots, n_r} = \frac{n!}{n_1!\dots n_r!}$.

Mastering these techniques requires practice and carefully analyzing whether the order of selection/arrangement is important for the specific problem you are trying to solve. They provide the quantitative backbone for exploring discrete probability.