---
pageDecoration:
  icon: airplay
tags: week cs/prog-fund
---

# Week 2

## Lecture 1

Date: Mon 7 Sep 2026 (2026-09-07)

- We will be programming in C and Dafnik
- C: Linux and GCC
- Our compilation command: `gcc -std=c99 -Wall -O2 progr.c`

### Hoare Triples
- Of the form `{ P } S { Q }`
- `P` is the precondition
- `Q` is the postcondition
- `S` is the code that turns `P` into `Q`
- Ex: `{x != 0} y = x*x; {y > 0}` is valid

## Lecture 2

Date: Thu 10 Sep 2026 (2026-09-10)

- `printf`, `scanf`
