---
pageDecoration:
  icon: airplay
tags: week
---

## Lecture 5

Slides: [[Courses/Semester 1a/Introduction to Logic/L5.pdf]]

### Quantifiers

- Construct sentences with quantifiers
- Translate quantified sentences from English to FOL

Quantifiers are words like: some, many, all

- Universal quantifier: "for all"/fa/$\forall$
  - Example: $\forall x \text{ } (Happy(x) \land Satisfied(x))$
  - Depends on the DoD
- Existential quantifier: "there exists"/ex/$\exists$
- Combined: $\forall x \exists y Loves(x, y)$ "anybody can find love"
- Categorical propositions:
  - universal affirmative: Every S is a P: $\forall x (S(x) \rightarrow P(x))$
    - It is NOT $\forall x (S(x) \land P(x))$
    - Why: because then you're saying every x is _BOTH_ S and P
  - particular affirmative: Some S is a P: $\exists x (S(x) \land P(s))$
  - universal negative: No S is a P: $\forall x (S(x) \rightarrow \neg P(x))$
  - particular negative: Some S is not a: $\exists x (S(x) \land \neg P(x))$

_Obsersation:_ we can write previous arguments into FOL now (translation key omitted for brevity):

```fitch
1 | ∃x (Politician(x) ∧ Dishonest(x))
2 | Politician(algore)
  |---
3 | | Dishonest(algore)
  | |---
4 | | ⊥
```

### Other new stuff

- variables
- well-formed-formulas
  - atomic sentences are wff
  - you can conjunct, disjunct, neg, bic, impl wff's
  - you can fa,ex wff's
  - nothing else is a wff
- well-formed sentences: wff but all variables have to be bound

### Counting with fa,ex

- Exactly one: $\exists x \forall y (P(y) \leftrightarrow x = y)$
- At least one: $\exists x P(x)$
- At most one: either a conjunction of the first two, or: $\forall x \forall y ((P(x) \land P(y)) \rightarrow x = y)$
- Exactly two: $\exists x \exists y (x = y \land \forall z (A(z) \leftrightarrow (x = z \lor y = z)))$
- At least two: $\exists x \exists y (\neg (x = y) \land P(x) \land P(y))$
- At most two: $\forall x \forall y \forall z ((P(x) \land P(y) \land P(z)) \rightarrow (x = y \lor x = z \lor y = z)$

#cs/logic