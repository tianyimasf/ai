---
layout: post
title: "Mathematical Statistics Cheatsheet: Chapter 2"
categories: [Mathematics, Statistics, Lecture Notes]
excerpt: "Basic Concepts of Probability: definition, sample space, axioms, mutual exclusivity, independence, calculating unions and intersections, Baye's Law"
---

Note: (*) means that bullet point is not mentioned in class but in handout.

- If there are N equally likely possibilities, of which one must occur and n are regarded as favorable, or as a “success”, then the probability of a “success” is given by the ratio $ \frac{n}{N} $.

- **Experiment**: Any process of observation or measurement.

- **Outcomes**: The results one obtains from an experiment. (Ex. sensor readings, value counts, “yes”, or “no” answers)

- **Sample space**: The set of all possible outcomes of an experiment, denoted by $S$.

- **Element/Sample Point**: Each outcome in a sample space.

- **Discrete sample space**: A sample space that contains either a finite or a countable number of distinct sample points.

- **Event**: A subset of a sample space.

- **Union $A \cup B$**: the subset of S that contains all the elements that are either in A or in B, or in both.

- **Intersection $A \cap B$**: the subset of S that contains all the elements that are both in A and B.

- **Complement $A'$ of $A$**: the subset of S that contains all the elements of S that are not in A.

- Events A and B are **mutually exclusive** if $A \cap B = \emptyset$ (A and B doesn't occur at the same time).

- A is **contained** in B is written as $A \subset B$.

- Basic operation properties:
    - **Commutative**
        - $A \cup B = B \cup A$
        - $A \cap B = B \cap A$
    - **Associative**
        - $(A \cup B) \cup C = A \cup (B \cup C)$
        - $(A \cap B) \cap C = A \cap (B \cap C)$
    - **De Morgan's Law**:
        - $(A \cup B)' = A' \cap B'$
        - $(A \cap B)' = A' \cup B'$
        - $(A \cup B \cup C)' = A' \cup B' \cup C'$
        - $(A \cap B \cap C)' = A' \cap B' \cap C'$

- **Probability Axioms**: given $P(A)$ the probability of event A,
    1. $P(A)$ is a **nonnegative real number**; that is, $P(A) \geq 0 \text{ for any } A \subseteq S$.
    2. $P(S) = 1$
    3. If $A_1$, $A_2$, ..., is a finite or infinite sequence of **mutulally exclusive** events of S, then $P(A_1 \cup A_2 \cup A_3 \cup ...) = P(A_1) + P(A_2) + P(A_3) + ...$

- **Theorem 2.1**: If: 

<p style="text-align: center;">A is an event in S, and</p>

<p style="text-align: center;">S is a discrete sample space, then</p>   

P(A) is the sum of the probabilities of the inidividual outcomes in A.

- **Rules of Probability**:
    1. If A and A' are complementary events in a sample space S, then $P(A') = 1 - P(A)$.
    2. $P(\emptyset) = 0$ for any sample space S.
    3. If A and B are events in a sample space S and $A \subset B$, then $P(A) \leq P(B)$.
    4. $0 \leq P(A) \leq 1$ for any event A.
    5. If A and B are any events in a sample space S, then $$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

- If **A, B and C** are events in a sample space S,then $$P(A \cup B \cup C) = P(A) + P(B) + P(C) - P(A \cap B) - P(A \cap C) - P(B \cap C) + P(A \cap B \cap C)$$

- **Odds** of an event A: P(A) to P(A'), provided neither probability is zero.
    - Odds are usually written in terms of positive integers having no common factor.
    - If the odds are a to b that an event A will occur, then $P(A) = \frac{a}{a + b}$.

- **Conditional Probability**:
    - If A and B are any 2 events in a sample space S and P(A) $\neq$ 0, the conditional probability of B given A is $P(B \mid A) = \frac{P(A \cap B)}{P(A)}$.

- If A and B are events in a sample space S and P(A) $\neq$ 0, then $P(A \cap B) = P(B) \times P(A \mid B) = P(A) \times P(B \mid A)$.

- Events A and B are independent if and only if $P(A \cap B) = P(A)P(B) \Leftrightarrow P(A \mid B) = P(A) \Leftrightarrow P(B \mid A) = P(B)$.

- **The rule of total probability**: If the events $B_1$, $B_2$, ..., and $B_k$ constitute a partition of the sample space S and $P(B_i) \neq 0$, for i = 1, 2, ..., k, then for any event A in S: $P(A) = \sum_{i=1}^{k}P(B_i)P(A \mid B_i)$.

- **Bayes' Theorem**: If $B_1$, $B_2$, ..., and $B_k$ constitute apartition of the sample space S and $P(B_i) \neq 0$ for i=1,2, ..., k then for any event A such that P(A) $\neq$ 0, $$P(B_r \mid A) = \frac{P(B_r)P(A \mid B_r)}{\sum_{i=1}^{k}P(B_i)P(A \mid B_i)}$$
    - When $S = B \cup B'$, $P(B \mid A) = \frac{P(B)P(A \mid B)}{P(B)P(A \mid B) + P(B')P(A \mid B')}$

- (*)If A, B, and C are events in a sample space S and $P(A \cap B) \neq 0$, then $P(A \cap B \cap C) = P(B) \times P(A \mid B) \times P(C \mid A \cap B)$.

- (*)If A and B are independent, then A and B' are also independent: $P(A \cap B') = P(A) \times P(B')$.

- (*)Events $A_1$, $A_2$, ..., and $A_k$ are **independent** if and only if the probability of the intersection of any 2, 3, ..., k of these events equals the product of their respective probabilities. 

- (*)Note that 3 or more events can be **pairwise independent** without being independent. 

---

## Questions

1. What is the definition of a continuous sample space, according to the handhout?

