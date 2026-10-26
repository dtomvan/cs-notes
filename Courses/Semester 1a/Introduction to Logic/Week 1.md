---
pageDecoration:
  icon: airplay
tags: week
---

## Lecture 1

Linked slides: [[Courses/Semester 1a/Introduction to Logic/L1.pdf]]

Date: Tue 1 Sep 2026 (2026-09-01)

> Logic is the study of inferences and reasoning -> judging logic to be (in)correct

We will be doing abstract, formal, _symbolic_ reasoning.

### Applications of logic in CS

- Hardware logic
- Formal verification (lean4)
- Theory of computation (computational complexity etc.)
- etc.

> Applied logic is maths, applied maths is physics, applied physics is chemistry, applied chemistry is biology etc.

### Validity of arguments

We don't look at concrete arguments, only the form. For example:

<details>
<summary>Example</summary>

```
All men are mortal.
Socrates is a man.
---
Socrates is mortal
```

Which we would write as:

```
All Ps are Qs.
x is a P.
---
x is a Q.
```

This is perfectly valid.

Another argument:

```
If you are a member, then you get a discount.
You are not a member.
---
You don't get a discount.
```

```
M -> D
\not M
---
\not D
```

This isn't valid though. Because there could be other means to have D.

</details>

- **Valid**: if the conclusion must follow after the premises
- **Sound**: valid + premises are all true

We only focus on validity though.

How do we prove validity?

A proof is a step-by-step demonstration that some conclusion follows from some premises.

### Atomic sentences in FOL

An atomic sentence is a statement that:

- Evals to T or F
- Cannot be broken down into smaller sentences

Built from:

- constants (naming objects)
- functions (mappings from A -> B)
- predicates (functions that map to T or F)
- equalities

#### Constants

- These constants must refer to one thing and one thing only: unambiguous.
- By convention: constants are lowercase.
- Must exist in the current _domain of discourse_.

#### Functions

- Adding functions allows us to build more complex terms compared to just constants
- I.e.: `father(claire)`, `mother(max)`
- Can be nested: `father(mother(max))`
- Have a fixed arity.
- Constants could be seen as functions with arity 0.

<details>
<summary>Example</summary>

```
Let D be the domain of discourse.
father : D -> D
+ : D x D -> D
```

</details>

#### Predicates

- Express properties of objects or relations between objects
- PascalCase
- Also has arity

<details>
<summary>Example</summary>

```
Cube(b): b is a cube
Small(b): b is small
Larger(a,b): a is larger than b
```

etc.

</details>

#### Equalities

- Written as `=`
- Just a special predicate.
- Expresses equality of identity.
- Ex: `father(max) = father(mother(claire))`
- `a = b` might be true; even though you have different constants, they may refer to the same object.
- Beware: is != isa
  - ddlv = Don Diego de la Vega
  - zorro = Zorro
  - `Don diego de la vega is Zorro` -> `ddlv = zorro`
  - `Don diego de la vega is a Nobleman` -> `Nobleman(ddlv)` AND NOT `ddlv = nobleman`
- Beware: predicates aren't symmetrical
  - `Loves(romeo, juliet)`
  - `Loves(juliet, romeo)`
  - These aren't the same, because it doesn't have to be mutual.

#### Examples

- `2 < 5`
- `x < 5`
- `a+t >= min(3 + min(7, b+6), c)`
- `Older(father(max), father(claire))`

Examples of _INVALID_ atomic sentences:

- `father(Knows(claire,max))`: father expects an object, not a bool
- `2 + (3 < 7)`: can't add a bool to a number
- `Cube(Blue(a))`: Cube expects a cube, not a bool

### Formal proofs with atomic sentences

- A deductive system is a collection of inference rules in a formal language (like FOL)
- A proof exists in a certain deductive system

#### `=` Intro

```
1 | x = x       =Intro
```

#### `=` Elim

```
1 | ddlv = zorro
2 | C(ddlv)
  |----
3 | C(zorro)        = Elim: 2, 1
```

### Equality axioms

- Reflexivity: a=a (this is builtin and can be "proven" using `= Intro`)
- Symmetry: a=b -> b=a
- Transitivity: a=b and b=c -> a=c

#### Prove symmetry

```
1 | a=b
  |----
2 | a=a         = Intro
3 | b=a         = Elim: 2, 1
```

#### Prove Transitivity

```
1 | a=b
2 | b=c
  |----
3 | a=c         = Elim: 1,2
```

## Lecture 2

Date: Thu 3 Sep 2026 (2026-09-03)

### Course organization

This is also in the slides.

- 2 homeworks (HW1,HW2)
  - Submit in Brightspace and Themis (PDF in BS, code in Themis)
- Midterm
- Exam (E)
- If your E is higher than HW,M => G = E
- Otherwise weighted average
- You need a 5.0 on E
- You need a 6.0 on G

### Formal Proofs with atomic sentences

- Reit: a _Proof_ is a step-by-step demonstration that some conclusion follows from some premises.
- Reit: Reit :)
- Reit: `= Intro` (identity introduction) and `= Elim` (identity elimination / substitution)
  - Reit: with equality elim, you can replace as many or as little occurrences that you want
- Reit: reflexivity (t=t), symmetry (t=e => e=t), transitivity (s=t and t=e => s=e)

### Boolean connectives and compound sentences

- Atomic sentences: we declare one thing
- Compound sentences: we combine atomic sentences to declare conjunction, disjunction, etc.
- The truth value of a compound sentence is dependent on the truth value of its parts

- Negation: $\neg$ "not" (`!`)
- Conjunction: $\land$ "and" (`&&`)
- Disjunction: $\lor$ "or" (`||`)
- True: $\top$
- False: $\bot$ ($\top = \neg \bot$)
- Formula: atomic sentences + compound sentences

#### How do we translate natural language into logic?

- Provide a translation key.
- Provide the actual translation.

For instance:
_Barbie either stays in Barbieland and does not live an authentic life, or she goes on an adventure and discovers her true self._

Atomic sentences:

- P: Barbie stays in Barbieland
- Q: Barbie lives an authentic life.
- R: Barbie goes on an adventure.
- S: Barbie discovers her true self.

Compound sentence:

$(P \land \neg Q) \lor (R \land S)$

#### NB: ambiguity

- Use parentheses in your homework and exams to prevent ambiguity like in $A \land B \lor C$
- Use: $(A \land B) \lor C$ **or** $A \land (B \lor C)$

### Proof with Boolean connectives

#### Proof of conjunction

- Claim: $P \land Q$
- Proof method: prove both P and Q

Conj. Intro:

```
1 | P
2 | Q
  |----
3 | P ∧ Q  ∧Intro:1,2
```

Conj. Elim:

```
1 | P ∧ Q
  |----
2 | P  ∧Elim: 1
```

<details>
<summary>Example: *rearranging conjunction sentences*</summary>

```
1 | P ∧ (Q ∧ R)
  |----
2 | Q ∧ R               ∧ Elim: 1
3 | Q                   ∧ Elim: 2
4 | R                   ∧ Elim: 2
5 | P                   ∧ Elim: 1
6 | Q ∧ P               ∧ Intro: 3, 5
7 | (Q ∧ P) ∧ R         ∧ Intro: 6, 4
```

</details>

#cs/logic