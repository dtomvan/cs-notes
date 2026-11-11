---
date: "2026-11-11"
pageDecoration:
  icon: airplay
tags: week
parentCourse: "[[Courses/Year 1/Semester 1b/Discrete Structures]]"
---
# Week 1

## Lecture 1

- Date: 2026-11-11
- Topic: Course Organisation

- We will basically be going over the book start-finish in order...
- Today: Chap 1 of the book, fundamentals

## Sets
- Unordered collection of distinct objects
- Can be defined by predicates
- Empty set: $\forall x (x \notin \emptyset)$
- Subset: $S \subseteq T \iff \forall x (x \in S \rightarrow x \in T)$
- Proper subset: $S \subsetneq T \iff S \subseteq T \land S \neq T$
- Intervals of $\R$:
  - $[a, b] = \{x \in R | A \leq x \leq b\}$
  - $(a, b) = \{x \in R | A \lt x \lt b\}$
  - And so on
- Equality: $A = B \iff \forall x (x \in A \leftrightarrow x \in B)$
- Powerset: $\mathcal{P}(S) = \{T | T \subseteq S\}$
- Cardinality: $|S|$ is the amount of elements
- Universes: like the domain of discourse in logic
- Operations
  - Union: $A \cup B = \{ x | x \in A \lor x \in B\}$
  - Intersection: $A \cap B = \{x | x \in A \land x \in B\}$
  - Difference: $A \setminus B = \{x | x \in A \land x \notin B\}$
  - Complement: $\overline{A} = U \setminus A$
  - Xor/symmetric difference: $A \Delta B = A \oplus B = (A \setminus B) \cup (B \setminus A)$
- Properties of operations:
  - Commutativity: $A \cup B = B \cup A$
  - Associativity: $(A \cup B) \cup C = A \cup (B \cup C)$
  - Distributivity: $A \cup (B \cap C) = (A \cup B) \cap (A \cap C)$
  - Idemptence etc.
  - DeM: $\overline{A \cup B} = \bar A \cap \bar B$

## Sequences
## Integers
## Matrices