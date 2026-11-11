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
  - Idempotence etc.
  - DeM: $\overline{A \cup B} = \bar A \cap \bar B$
- Proofs (Annotated Linear Proof / ALP / chain-of-equivalences)

## Sequences
- Sequence is a list of objects in definite order
- Characteristic function: $f_A : U \rightarrow \{0,1\}$
  - 1 iff $A \in U$
  - 0 iff $A \notin U$
- Countable set: if all elements of a set can be written as a sequence (enumerated), it’s countable
- String: sequence of symbols in a given alphabet
- Alphabet: non-empty finite set $\Sigma$ of letters
- $\Sigma^{*}$ denotes all possible words/strings under the alphabet
- Language L: $L \subseteq \Sigma^{*}$
- Empty word: $\epsilon$
- concatenation: $w_1 = hello; w_2 = world \implies w_1 \cdot w_2 = helloworld$
- Associative but not commutative
- concatenation of languages: $L \cdot M = LM = \{s \cdot t | s \in L \land t \in M\}$, as in the concatenation of all words in L with all other words in M
- Star of lanhuage: $L^*$ all concatenations with itself (zero or more times)
- Regular expressions: defined recursively in terms of members of the alphabet, and other operations:
  - $\epsilon$ is regexp
  - $\alpha \in \Sigma$ is regexp
  - if $\alpha$ and $\beta$ are regexp, then $(\alpha \cdot \beta)$ and $(\alpha \lor \beta)$ are regexp
  - if $\alpha$ is regexp, then so is $(\alpha)^*$

## Integers

For all $m,n \in \Z$, with $n > 0$, there are unique integers q and r s.t.:

$$
m = q \cdot n + r \land 0 \leq r < n
$$


## Matrices