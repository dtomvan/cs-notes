# Week 2

## Lecture 3 and 4

Date: Mon 7 Sep 2026 (2026-09-06) AND Tue 8 Sep 2026 (2026-09-06)

Topic: Boolean connectives and Formal Proofs

### Formal Proofs for Conjunction and Disjunction

- We know how to prove `P` from \\(P \land Q\\) (`and elim`)
- Now for \\(\lor\\)
- **Intro:** In order to prove \\(P \lor Q\\) we have to either prove `P` or `Q` and the condition is satisfied
- **Elim:** If we have already established \\(P \lor Q\\) we cannot really conclude anything about `P` and `Q` seperately, but maybe some `R`
    - We don't know if `P` or `Q` holds, but we can prove that given `P` we can derive `R` or given `Q` we can derive `R`

Example of both (commutativity of disjunction):

```
1 | P ∨ Q
  |----
2 | | P
  | |----
3 | | Q ∨ P         ∨ Intro: 2
  |
4 | | Q
  | |----
5 | | Q ∨ P         ∨ Intro: 4
6 | Q ∨ P           ∨ Elim: 1, 2-3, 4-5
```

or even (assiociativity or disjunction):

```
1  | P ∨ (Q ∨ R)
   |----
2  | | P
   | |----
3  | | P ∨ Q                 ∨ Intro: 2
4  | | (P ∨ Q) ∨ R           ∨ Intro: 3
   |
5  | | Q ∨ R
   | |----
6  | | | Q
   | | |----
7  | | | P ∨ Q               ∨ Intro: 6
8  | | | (P ∨ Q) ∨ R         ∨ Intro: 7
   | |
9  | | | R
   | | |----
10 | | | (P ∨ Q) ∨ R         ∨ Intro: 9
11 | | (P ∨ Q) ∨ R           ∨ Elim: 5, 6-8, 9-10
12 | (P ∨ Q) ∨ R             ∨ Elim: 1, 2-4, 5-11
```

### Formal Proofs for Negation and Falsity

- **Claim**: \\(\neg P\\)
- **Proof method**: Suppose that `P` holds, and arrive at a contradiction (achieve both `P` and `!P`).

Examples:

```
  |----
1 | | ⊥
  | |----
2 | | ⊥           Reit: 1
3 | ¬⊥            ¬ Intro: 1-2
```

```
1 | P
  |----
2 | | ¬P
  | |----
3 | | ⊥           ⊥ Intro: 1, 2
4 | ¬¬P           ¬ Intro: 2-3
```
i
### General Proof construction

- *Pro tip*: first, try to understand the proof intuitively, only then write it out in Fitch

### Conditionals

- implication
    - \\(P \rightarrow Q\\)
    - says that:
        - P is a *sufficient* condition for Q (that is, if P then Q, but there may be other ways to achieve Q)
        - Q is a *nessecary* condition for P
    - If P is false, then `P -> Q` is always true.
    - The arrow doesn't imply causality though.
- *if-then-else*: "If P then Q else R" translates to \\((P \rightarrow Q) \land (\neg P \rightarrow R)\\)
- **if and only if**: "iff" translates to \\(\leftrightarrow\\) (or \\((P \rightarrow Q) \land (Q \rightarrow P)\\))
    - Sort-of equality check: the bic evals to T if both `P` and `Q` have the same truth value

## Lecture 5

Date: 

### Proofs with conditionals

### Proofs with biconditionals
