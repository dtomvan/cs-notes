---
tags: week
parentCourse: "[[Courses/Year 1/Semester 1a/Introduction to Logic]]"
---

Slides: [[Courses/Year 1/Semester 1a/Introduction to Logic/L7.pdf]]

Haven’t actually written any notes for this one. Set theory I already know and models are just plain practice mostly. Also nigh impossible to note down with mathjax.

# Prenex Normal Form

Logical laws:
- Renaming: $\forall x P(x) \Leftrightarrow \forall y P(y)$
- DeMorgan:
  - $\neg\forall x P(x) \Leftrightarrow \exists x \neg P(x)$
  - $\neg\exists x P(x) \Leftrightarrow \forall x \neg P(x)$
- Same quantifier:
  - $\forall x P(x) \land \forall x Q(x) \Leftrightarrow \forall x (P(x) \land Q(x))$
  - $\forall x P(x) \lor \forall x Q(x) \Leftrightarrow \forall x (P(x) \land Q(x))$
- Implications:
  - These next two assume no free $x$ in $P$.
  - $P \rightarrow \forall x Q(x) \Leftrightarrow \forall x (P \rightarrow Q(x))$
  - $\forall x Q(x) \rightarrow P \Leftrightarrow \exists x (Q(x) \rightarrow P)$

# Skolem normal form

- Make it Prenex first
-  $\exists$ in front: make a constant
- $\exists$ after a $\forall$: make a function that depends on all previous $\forall$‘s

For instance:

$\exists x \forall y \forall z \exists w