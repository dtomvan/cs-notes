# Validity of arguments

An argument consists of zero or more premises, and a conclusion. An argument is _valid_ if the conclusion always follows from the premises. (assuming the premises are true)

An argument is *sound* if the premises are also confirmed to be true.

An argument is *valid* if there’s no possible *counterexample* to the argument. A *counterexample* (in)formally describes a situation in which the premises are true, but the conclusion is false. In the midterm, you’ll use an informal counterexample. In the final exam, you’ll be writing a *countermodel*. See the section about [[#Models|models]].

# Fitch proofs

I have a big ass repo of example fitch proofs, you can use it either as an LPL answer key or as a way to learn how to go about certain proofs: https://github.com/dtomvan/fitch-proofs

### `= Intro`
```fitch
  |---
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

### `¬ Intro`
```fitch
1 | A
  |----
2 | | ¬A
  | |----
3 | | ⊥           ⊥ Intro: 1, 2
4 | ¬¬A           ¬ Intro: 2-3
```

Line numbers: just the subproof range which starts with `P` and ends with `⊥`, then conclude `¬P`

### `¬ Elim`
```fitch
1 | ¬¬A
  |----
2 | A           ¬ Elim: 1
```

## (bi-)implication
### `→ Intro`
```fitch
1 | a=b
  |----
2 | | P(a)
  | |----
3 | | P(b)              = Elim: 2, 1
4 | P(a) → P(b)         → Intro: 2-3
```

### `→ Elim`
```fitch
1 | P
2 | P → Q
  |----
3 | Q             → Elim: 2,1
```

**NB:** these line numbers are the other way around when compared to `= Elim`; implication first, then the formula on the left-hand side of the implication

### `↔ Intro`

Both `↔` rules are just the same as implications, but both ways
```fitch
1 | a=b
  |----
2 | | P(a)
  | |----
3 | | P(b)              = Elim: 2, 1
  |
4 | | P(b)
  | |----
5 | | a=a               = Intro
6 | | b=a               = Elim: 5, 1
7 | | P(a)              = Elim: 4, 6
8 | P(a) ↔ P(b)         ↔ Intro: 2-3, 4-7
```

### `↔ Elim`
Look mom, it goes left as well! It’s almost like the arrow is pointing both ways.
```fitch
1 | P ↔ Q
2 | Q
  |----
3 | P             ↔ Elim: 1, 2
```

## Quantifiers

### `∀ Intro`
```fitch
  |----
1 | | [a]
  | |----
2 | | a=a            = Intro
3 | ∀x (x=x)         ∀ Intro: 1-2
```

### `∀ Elim`
```fitch
1 | ∀x (P(x) → Q(x))
2 | P(a)
  |----
3 | P(a) → Q(a)              ∀ Elim: 1
4 | Q(a)                     → Elim: 3,2
```

### `∃ Intro`
```fitch
1 | P(a)
  |----
2 | ∃x P(x)         ∃ Intro: 1
```

### `∃ Elim`
```fitch
1 | ∃x P(x)
  |----
2 | | [a] P(a)
  | |----
3 | | P(a) ∨ Q(a)              ∨ Intro: 2
4 | | ∃x (P(x) ∨ Q(x))         ∃ Intro: 3
5 | ∃x (P(x) ∨ Q(x))           ∃ Elim: 1, 2-4
```

# Logical Equivalences and laws
These laws are used for NNF, CNF, and DNF. For Prenex, see [[#Prenex normal form|the section about Prenex]].
- Double negation elimination (`NN`): $\neg\neg P \iff P$
- Associativity:
  - $P \land (Q \land R) \iff (P \land Q) \land R$
  - $P \lor (Q \lor R) \iff (P \lor Q) \lor R$
- Commutativity:
  - $P \land Q \iff Q \land P$
  - $P \lor Q \iff Q \lor P$
- Idempotency:
  - $P \land P \iff P$
  - $P \lor P \iff P$
- DeMorgan’s laws (`DeM`):
  - $\neg(P \lor Q) \iff \neg P \land \neg Q$
  - $\neg(P \land Q) \iff \neg P \lor \neg Q$
- Definition of $\rightarrow$ (`Def. ->`): $P \rightarrow Q \iff \neg P \lor Q$
- Definition of $\leftrightarrow$ (`Def. <->`):
  - $P \leftrightarrow Q \iff (P \rightarrow Q) \land (Q \rightarrow P)$
  - Alternatively, use `Def. ->` immediately. This is allowed on the test, but the above line is more intuitive.
  - $P \leftrightarrow Q \iff (\neg P \lor Q) \land (\neg Q \lor P)$

# Normal forms

In general: use the above laws to achieve the normal forms below. Some tips:
- NNF: usually `(DeM,NN)` is enough
- CNF/DNF: usually you can eliminate a connective that shouldn’t be at that “level” with a distributivity law

## Negation normal form (NNF)

*Def.* a sentence is in NNF if all negations are over atomic sentences, and not compound sentences. Also no $\rightarrow$ or $\leftrightarrow$.

This is fine:
$P \land (\neg Q \lor R)$
This is not:
$P \land \neg(Q \lor R)$

## Conjunction normal form (CNF)

*Def.* a sentence is in CNF if it’s NNF, and all conjunctions are above disjunctions.

This is fine:
$P \land (Q \lor R)$
This is not:
$P \lor (Q \land R)$

## Disjunction normal form (DNF)

*Def.* a sentence is in DNF if it’s NNF, and all disjunctions are above conjunctions.

This is fine:
$P \lor (Q \land R)$
This is not:
$P \land (Q \lor R)$


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

## Horn form
*Def.* a wff is in Horn form if it is in Prenex form, and the quantifier-free part is in CNF, where each conjunct has at most 1 positive literal.

Usually written as a conjunction of implications, in either of these forms:
- $\top \rightarrow P$
- $P \rightarrow \bot$
- $P \rightarrow Q$
Notice how using `Def ->` on the above forms results in either zero or one positive literals.

#### Horn’s algorithm
Suppose you have the following sentence:
$(\top \rightarrow A) \land (A \rightarrow D) \land (C \rightarrow \bot) \land ((D \land A) \rightarrow B) \land ((B \land D) \rightarrow E)$

Apply the following steps:
1. Make a table (example below), for each of the atomic sentences, and $\bot$.
2. 

# Models

## Interpretations

Models are used to interpret a FO-language, and describe a situation in that language. We will define a FO-language $\mathcal{L}$ in this section, to show how each of the elements can be represented in a model.

Let $\mathcal{L}$ be a first-order language with the following elements:
- constant $ah$: Albert Heijn
- constant $plus$: Plus supermarket
- unary function $ceo(x)$: the CEO of $x$
- unary predicate $Best(x)$: $x$ is the best
- binary predicate $Better(x, y)$: $x$ is better than $y$

Now let’s describe the following situation:
- The CEO of Albert Heijn is Margaret
- The CEO of Plus is Aart
- Albert Heijn is better than Plus
- Aart is the best CEO ever

So, let’s now define a first-order model $\mathfrak{M}$:

- $\mathfrak{M}(\forall) = \{\text{Albert Heijn}, \text{Plus}, \text{Aart}, \text{Margaret}\}$ (this is our domain of discourse)
- $\mathfrak{M}(ah) = \text{Albert Heijn}$ (interpretation of a constant)
- $\mathfrak{M}(plus) = \text{Plus}$
- $\mathfrak{M}(ceo)(\text{Albert Heijn}) = \text{Margaret}$ (interpretation of a function)
- $\mathfrak{M}(ceo)(\text{Plus}) = \text{Aart}$
- $\mathfrak{M}(Best) = \{ \text{Aart} \}$ (interpretation of a unary predicate is a set)
- $\mathfrak{M}(Better) = \{ \langle \text{Albert Heijn},\text{Plus} \rangle \}$ (interpretation of a binary predicate is a relation)

## Variable assignments
Special notation in the segment below, used to specify what the values of variables are (x,y,z, etc.)

The test will define variable assignments as such: let $h$ be a variable assignment such that $h(x) = 69$ and $h(y) = 420$.

Notations:
- $h(x)$: the value of $x$ in the variable assignment $h$
- $h[x/d]$: a copy of $h$, where the variable $x$ is overwritten with value $d$
- $h_\varnothing$: empty variable assignment
- $\mathfrak{M} \models P[h]$: the model satisfies $P$ under variable assignment $h$

## Proving satisfiability in a model
For this summary, I will write down the equivalences you’ll need to memorize. Practice applying them with the various model exercises that are available.

### Atomics
- Unary predicates:
  - $\mathfrak{M} \models P(x)[h] \text{ iff } \llbracket x \rrbracket ^{\mathfrak{M}}_h \in \mathfrak{M}(P)$
  - $\mathfrak{M} \not\models P(x)[h] \text{ iff } \llbracket x \rrbracket ^{\mathfrak{M}}_h \notin \mathfrak{M}(P)$
- Binary predicates:
  - $\mathfrak{M} \models Q(x,y)[h] \text{ iff } \langle \llbracket x \rrbracket ^{\mathfrak{M}}_h,\llbracket y \rrbracket ^{\mathfrak{M}}_h \rangle \in \mathfrak{M}(Q)$
  - $\mathfrak{M} \not\models Q(x,y)[h] \text{ iff } \langle \llbracket x \rrbracket ^{\mathfrak{M}}_h,\llbracket y \rrbracket ^{\mathfrak{M}}_h \rangle \notin \mathfrak{M}(Q)$

### Boolean connectives
- $\mathfrak{M} \models (P \land Q)[h] \text{ iff } \mathfrak{M} \models P[h] \text { and } \mathfrak{M} \models Q[h]$
- $\mathfrak{M} \models (P \lor Q)[h] \text{ iff } \mathfrak{M} \models P[h] \text { or } \mathfrak{M} \models Q[h]$
- $\mathfrak{M} \models \neg P[h] \text{ iff } \mathfrak{M} \not\models P[h]$
- $\mathfrak{M} \models (P \rightarrow Q)[h] \text{ iff } \mathfrak{M} \not\models P[h] \text { or } \mathfrak{M} \models Q[h]$
- $\mathfrak{M} \models (P \leftrightarrow Q)[h] \text{ iff } (\mathfrak{M} \models P[h] \text { and } \mathfrak{M} \models Q[h]) \text{ or } (\mathfrak{M} \not\models P[h] \text { and } \mathfrak{M} \not\models Q[h])$

### Quantifiers
- $\mathfrak{M} \models \forall x P(x)[h] \text{ iff for all } d \in \mathfrak{M}(\forall): \mathfrak{M} \models P(x)[h[x/d]]$
- $\mathfrak{M} \models \exists x P(x)[h] \text{ iff for some } d \in \mathfrak{M}(\forall): \mathfrak{M} \models P(x)[h[x/d]]$