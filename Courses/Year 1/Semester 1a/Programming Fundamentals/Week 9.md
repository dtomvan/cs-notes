---
date: "2026-11-09"
pageDecoration:
  icon: airplay
tags: week
parentCourse: "[[Courses/Year 1/Semester 1a/Programming Fundamentals]]"
---
# Week 9

## Lecture 10?

- Date: 2026-11-09
- Topic:

## From recurrence to while loop

Usually, when you have some recurrence relation `f(x)`, you can introduce additional local variables, and “accumulate” the computation slowly: (f.i.)

$$
y \leq 0 \implies f(y,z) = z
$$
$$
y > 0 \implies f(y,z) = 10\cdot f(y \textbf{ div } 10, z) + y \textbf{ mod } 10
$$

We will make the invariant:

$$
J : Z = m \cdot f(y,z) + n
$$

The $m$ will accumulate the “multiplication part” of the recurrence relation, and the $n$ will accumulate the “addition part” (though either one might decrease instead in other examples). At the end we can set $z = m \cdot z + n$.

That last step I just mentioned is called _active finalization_, by the way.

Not much to write down here, the lecture is basically practicing proofs...

