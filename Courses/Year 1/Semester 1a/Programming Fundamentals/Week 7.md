---
date: "2026-10-26"
pageDecoration:
  icon: airplay
tags: week
parentCourse: "[[Courses/Year 1/Semester 1a/Programming Fundamentals]]"
---
# Week 7

## Lecture IDK anymore

- Date: 2026-10-19
- Topic: Dafny :D

### Proving a `while` loop
We choose 4 propositions:
- Guard $B$: `while B`
- Invariant $J$
- Precondition $P$
- Postcondition $Q$

We now want $\{ P \} S_i \{ J \land B \}$ for initialization.
We want $J$ to be true before, after and during each iteration of the loop.
After execution we want to make sure that $J \land \neg B \implies Q$

To prove that it terminates, we use a variant-function `vf`, which needs to start as a non-negative integer, and should be bounded below zero after the loop. Also each iteration we need to prove that the `vf` decreases.
