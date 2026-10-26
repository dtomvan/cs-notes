---
pageDecoration:
  icon: airplay
tags: week
parentCourse: [[Courses/Semester 1a/Introduction to Logic]]
---

## Lecture 6

Slides:
- [[Courses/Semester 1a/Introduction to Logic/L6.pdf]]
- [[Courses/Semester 1a/Introduction to Logic/L7.pdf]]

Date: 2026-10-05

Missed topics:
- First-order models
- Set theory

### Translating and Counting with Quantifiers

- "Everyone who owns a dog, must take good care of it": $\forall x \forall y ((Dog(y) \land Owns(x, y)) \rightarrow GoodCare(x,y))$
- $\exists y \forall x \implies \forall x \exists y$, but not the other way around

### Proof methods and rules

Proof methods are in the slides TBH and on https://u.toostveen.nl/logic-notes.

Example proofs:

```fitch
1 | ∃x ∀y P(x,y)
  |----
2 | | [a]
  | |----
3 | | | [b] ∀y P(b,y)
  | | |----
4 | | | P(b,a)                ∀ Elim: 3
5 | | | ∃x P(x,a)             ∃ Intro: 4
6 | | ∃x P(x,a)               ∃ Elim: 1, 3-5
7 | ∀y ∃x P(x,y)              ∀ Intro: 2-6
```

```fitch
1  | ∀x ∀y (p(x,y)=p(y,x))
2  | ∃z ∀x (p(x,z)=x)
   |----
3  | | [a] ∀x (p(x,a)=x)
   | |----
4  | | | [b]
   | | |----
5  | | | p(b,a)=b                   ∀ Elim: 3
6  | | | ∀y (p(b,y)=p(y,b))         ∀ Elim: 1
7  | | | p(b,a)=p(a,b)              ∀ Elim: 6
8  | | | p(a,b)=b                   = Elim: 5, 7
9  | | ∀x (p(a,x)=x)                ∀ Intro: 4-8
10 | | ∃z ∀x (p(z,x)=x)             ∃ Intro: 9
11 | ∃z ∀x (p(z,x)=x)               ∃ Elim: 2, 3-10
```

```fitch
1 | ∀x (∃y R(x,y) → P(x))
2 | ∀x ∀y ((x=y) → R(x,y))
  |----
3 | ∃y R(a,y) → P(a)               ∀ Elim: 1
4 | ∀y ((a=y) → R(a,y))            ∀ Elim: 2
5 | (a=a) → R(a,a)                 ∀ Elim: 4
6 | a=a                            = Intro
7 | R(a,a)                         → Elim: 5,6
8 | ∃y R(a,y)                      ∃ Intro: 7
9 | P(a)                           → Elim: 3,8
```

```fitch
1  | ∀x (∃y R(x,y) → P(x))
2  | ∃x ∀y ((x=y) → R(x,y))
   |----
3  | | [a] ∀y ((a=y) → R(a,y))
   | |----
4  | | (a=a) → R(a,a)                  ∀ Elim: 3
5  | | a=a                             = Intro
6  | | R(a,a)                          → Elim: 4,5
7  | | ∃y R(a,y) → P(a)                ∀ Elim: 1
8  | | ∃y R(a,y)                       ∃ Intro: 6
9  | | P(a)                            → Elim: 7,8
10 | | ∃x P(x)                         ∃ Intro: 9
11 | ∃x P(x)                           ∃ Elim: 2, 3-10
```

### Conclusion


#cs/logic