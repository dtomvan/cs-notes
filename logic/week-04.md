## Lecture 7 & 8

Date: 2026-09-21 & 2026-09-22

### Logical laws

- Def ->: $(P \rightarrow Q) \Leftrightarrow (\neg P \lor Q)$
- Def <->: $(P \leftrightarrow Q) \Leftrightarrow ((P \rightarrow Q) \land (Q \rightarrow P))$
- De Morgan laws
    - $\neg(P \lor Q) \Leftrightarrow \neg P \land \neg Q$
    - $\neg(P \land Q) \Leftrightarrow \neg P \lor \neg Q$
- ACI laws
    - Associativity: $(P \land Q) \land R \Leftrightarrow P \land (Q \land R)$
    - Commutativity: $P \land R \Leftrightarrow R \land P$
    - Idempotence: $(P \land P) \Leftrightarrow P$
- Distributivity laws
    - i.e.: $P \lor (Q \land R) \Leftrightarrow (P \lor Q) \land (P \lor R)$
    - Beware: there's left and right-distrib. If you have right-distrib, write the correct order!

<details>

<summary>Fitch proof for left-distributivity of ∨!</summary>

```fitch
   |----
1  | | P ∨ (Q ∧ R)
   | |----
2  | | | P
   | | |----
3  | | | P ∨ Q                                   ∨ Intro: 2
4  | | | P ∨ R                                   ∨ Intro: 2
5  | | | (P ∨ Q) ∧ (P ∨ R)                       ∧ Intro: 3, 4
   | |
6  | | | Q ∧ R
   | | |----
7  | | | Q                                       ∧ Elim: 6
8  | | | R                                       ∧ Elim: 6
9  | | | P ∨ Q                                   ∨ Intro: 7
10 | | | P ∨ R                                   ∨ Intro: 8
11 | | | (P ∨ Q) ∧ (P ∨ R)                       ∧ Intro: 9, 10
12 | | (P ∨ Q) ∧ (P ∨ R)                         ∨ Elim: 1, 2-5, 6-11
   |
13 | | (P ∨ Q) ∧ (P ∨ R)
   | |----
14 | | P ∨ Q                                     ∧ Elim: 13
15 | | P ∨ R                                     ∧ Elim: 13
16 | | | P
   | | |----
17 | | | P ∨ (Q ∧ R)                             ∨ Intro: 16
   | |
18 | | | Q
   | | |----
19 | | | | R
   | | | |----
20 | | | | Q ∧ R                                 ∧ Intro: 18, 19
21 | | | | P ∨ (Q ∧ R)                           ∨ Intro: 20
   | | |
22 | | | | P
   | | | |----
23 | | | | P ∨ (Q ∧ R)                           ∨ Intro: 22
24 | | | P ∨ (Q ∧ R)                             ∨ Elim: 15, 22-23, 19-21
25 | | P ∨ (Q ∧ R)                               ∨ Elim: 14, 16-17, 18-24
26 | (P ∨ (Q ∧ R)) ↔ ((P ∨ Q) ∧ (P ∨ R))         ↔ Intro: 1-12, 13-25
```

</details>

### Normal forms

- Negation normal form (NNF):
    - just and,or,neg
    - only atomic negations: not(P and Q) is invalid
    - you can apparently rewrite any sentence which has just and,or,neg into NNF
- Disjunctive normal form (DNF)
    - It's basically NNF, but no disjunctions below conjunctions
    - A sentence S is DNF if it is a disjunction of one or more conjunctions of literals
- Conjunctive normal form:
    - NNF, no conjunctions below disjunctions

### TT-completeness

- For n-ary boolean connectives, you have 2^2^n possible different ones
- In binary connectives, i.e.: xor, nand, nor
- **Claim:** for n-ary connectives defined by a truth table can be also defined by a sentence with only and,or,neg
    - The fun part: you'll get a DNF formula, which means you can indeed write any formula as DNF, because you can write *any truth table* as DNF!!
- TT-completeness: and,or,neg is a complete set of connectives, that is, you can do anything
- You can even do it with 2: $P \lor Q \rightarrow \neg\neg(P \lor Q) \rightarrow \neg(\neg P \land \neg Q)$
    - Also, the other way around!
    - It's just De Morgan!
- Just nor or nand is actually truth-functionally complete! Because for example you can do negation with `!(P && P) == !P`

## Tutorial

### Counterexamples

Please be **THIS FUCKING EXPLICIT**:

1. Find the premises and the conclusion
2. Introduce a domain of discourse
3. Explain how the premises are true
4. Explain how the conclusion is false

```
| The majority of politicians are dishonest.
| Al gore is a politician.
---
| Al gore is dishonest.
```

Imagine a world where there are *3 politicians*; namely Al Gore, who is honest,
politicians B and C, who are dishonest. The 1st premise is true, because 2/3 of
the politicians (B and C) are dishonest, meaning the majority is dishonest. The
2nd premise is also true, because Al gore is a politician. But Al gore is
honest, so the conclusion doesn't follow.
