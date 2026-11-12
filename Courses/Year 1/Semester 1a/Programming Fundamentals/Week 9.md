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
- Topic: Dafny

## Recall: proof rules for while loops
1. Invariant: $J \land \neg B \rightarrow Q$
2. Initialization: $\{P\} S; \{J\}$
3. variant function: $J \land B \rightarrow vf \ge 0$
4. Body:
   1. $\{J \land B \land vf = V\}$
   2. $S$
   3. $\{J \land vf < V\}$
5. RIID (Rewrite It In Dafny)

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

## Lemma’s 
In dafny, we can “program” a proof (example from the slides):

```dafny
lemma {:induction false} Increasing (x: int)
ensures x < More(x)
{
  if x > 0 {
    var y := x - 2;
    Increasing(y);
  }
}
```

## Calc

Dafny can verify that your calculus is correct.

```
assert 5 * (x+3) == 5*x + 15 by
calc {
  5 * (x+3);
  ==
  5 * x + 5 * 3;
  ==
  5*x + 15;
}
```

## Sets
- Split rule: $\#V = \#(V \cap W) + \#(V \setminus W)$
- $\#V = \#(V \setminus \{a\}) + ord(a \in V)$
- Intervals:
  - Closed: $[m..n] = \{k | m \leq k \leq n\}$
  - Open: $(m..n) = \{k | m \lt k \lt n\}$
  - Half-open: $[m..n) = \{k | m \leq k \lt n\}$
  - Half open is very useful: $\#[m..n) = |m-n|$
- Min and Max:
  - They have definitions, but I don’t bother here sorry
  - Max $\emptyset = -\infty$
  - Min $\emptyset = \infty$
  - $Max V = Max (V \cap W) \textbf{ max } Max (V \setminus W)$
  - $Min V = Min (V \cap W) \textbf{ min } Min (V \setminus W)$
- Families: sets but with parens
- Product operator: $\Pi(\emptyset) = 1$