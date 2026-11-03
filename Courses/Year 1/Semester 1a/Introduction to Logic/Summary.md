# Validity of arguments

An argument consists of zero or more premises, and a conclusion. An argument is _valid_ if the conclusion always follows from the premises. (assuming the premises are true)

An argument is *sound* if the premises are also confirmed to be true.

An argument is *valid* if there’s no possible *counterexample* to the argument. A *counterexample* (in)formally describes a situation in which the premises are true, but the conclusion is false. In the midterm, you’ll use an informal counterexample. In the final exam, you’ll be writing a *countermodel*. See the section about [[#Models|models]].

# Fitch proofs

### `= Intro`
```fitch
  | ---
1 | a = a     = Intro
```

### `= Elim`
```fitch
1 | a = b
2 | P(a)
  |---
3 | P(b)     = Elim: 2,1
```

Line numbers: first the formula you’re changing, then the equality you’re using to justify the substitution.

## Boolean connectives

### `∧ Intro`
```fitch
1 | A
2 | B
  |----
3 | A ∧ B         ∧ Intro: 1, 2
```

### `∧ Elim`
```fitch
1 | A ∧ B
  |----
2 | A             ∧ Elim: 1
3 | B             ∧ Elim: 1
```

#### `∨ Intro`
```fitch
1 | A
  |----
2 | A ∨ B         ∨ Intro: 1
```

#### `∨ Elim`
```fitch
1 | A ∨ B
2 | A → C
3 | B → C
  |----
4 | | A
  | |----
5 | | C           → Elim: 2,4
  |
6 | | B
  | |----
7 | | C           → Elim: 3,6
8 | C             ∨ Elim: 1, 4-5, 6-7
```

Line numbers: first the line number with the disjunction, followed by ranges for each of the subproofs that corresponds to each disjunct (in order)

## Negation

### `⊥ Intro`
```fitch
1 | ¬A
2 | A
  |----
3 | ⊥           ⊥ Intro: 2, 1
```

Line numbers: first the positive formula, then the negation of the first line

### `⊥ Elim`
Rule: if you get `⊥`, you may conclude anything you want, because the argument is based on false or contradictory assumptions
```fitch
1 | ⊥
  |----
2 | p=np         ⊥ Elim: 1
```

### `

## (bi-)implication

## Quantifiers

# Logical Equivalences and laws

# Normal forms

In general: use the above laws to achieve the normal forms below. Some tips:
- NNF: usually `(DeM,NN)` is enough
- CNF/DNF: usually you can eliminate a connective that shouldn’t be at that “level” with a distributivity law

## Negation normal form (NNF)
## Conjunction normal form (CNF)
## Disjunction normal form (DNF)

## Quantifier normal forms

### Prenex normal form

*Def.* a wff is in Prenex normal form if it is in NNF, and no quantifiers under boolean connectives, i.e. all quantifiers “at the top”

Logical laws:
- Renaming: $\forall x P(x) \Leftrightarrow \forall y P(y)$
- DeMorgan:
  - $\neg\forall x P(x) \Leftrightarrow \exists x \neg P(x)$
  - $\neg\exists x P(x) \Leftrightarrow \forall x \neg P(x)$
  - etc.
- Same quantifier:
  - $\forall x P(x) \land \forall x Q(x) \Leftrightarrow \forall x (P(x) \land Q(x))$
  - $\forall x P(x) \lor \forall x Q(x) \Leftrightarrow \forall x (P(x) \lor Q(x))$
- Implications:
  - These next two assume no free $x$ in $P$.
  - $P \rightarrow \forall x Q(x) \Leftrightarrow \forall x (P \rightarrow Q(x))$
  - $\forall x Q(x) \rightarrow P \Leftrightarrow \exists x (Q(x) \rightarrow P)$

### Skolem normal form

*Def.* a wff is in Skolem normal form if it is in Prenex normal form, without $\exists$ in the formula

Steps:
- Make it Prenex first
- For each $\exists$:
  - $\exists$ in front: make a constant
  - $\exists$ after a $\forall$: make a function that depends on all previous $\forall$‘s

For instance:

$$
\exists x \forall y \forall z \exists w \forall e \exists g P(x,y,z,w,e,g)
$$
becomes

$$
\forall y \forall z \forall e P(c, y, z, f_1(y, z), e, f_2(y,z,e))
$$

_Note:_ I’ve used $f_1$ and $f_2$ here because I’ve ran out of letters. Use different letters for the functions preferably.

# Models