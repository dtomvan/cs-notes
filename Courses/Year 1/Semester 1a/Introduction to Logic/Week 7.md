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
- Same quantifier for $\land$:
  - $\forall x P(x) \land \forall x Q(x) \Leftrightarrow \forall x (P(x) \land Q(x))$
  - Note: this does **NOT** go for $\lor$
- 