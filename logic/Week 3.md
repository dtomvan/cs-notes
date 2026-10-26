## Lecture 5

Date: Monday 14 september 2026 (2026-09-14)

### Practice proofs

```fitch
1 | ¬P ∧ ¬Q
  |----
2 | ¬P               ∧ Elim: 1
3 | ¬Q               ∧ Elim: 1
4 | | P ∧ Q
  | |----
5 | | P              ∧ Elim: 4
6 | | ⊥              ⊥ Intro: 5, 2
7 | ¬(P ∧ Q)         ¬ Intro: 4-6
```

```fitch
1  | ¬(P ∨ Q)
   |----
2  | | P
   | |----
3  | | P ∨ Q          ∨ Intro: 2
4  | | ⊥              ⊥ Intro: 3, 1
   |
5  | | Q
   | |----
6  | | P ∨ Q          ∨ Intro: 5
7  | | ⊥              ⊥ Intro: 6, 1
8  | ¬P               ¬ Intro: 2-4
9  | ¬Q               ¬ Intro: 5-7
10 | ¬P ∧ ¬Q          ∧ Intro: 8, 9
```

```fitch
1  | ¬P ∧ ¬Q
   |----
2  | ¬P               ∧ Elim: 1
3  | ¬Q               ∧ Elim: 1
4  | | P ∨ Q
   | |----
5  | | | P
   | | |----
6  | | | ⊥            ⊥ Intro: 5, 2
   | |
7  | | | Q
   | | |----
8  | | | ⊥            ⊥ Intro: 7, 3
9  | | ⊥              ∨ Elim: 4, 5-6, 7-8
10 | ¬(P ∨ Q)         ¬ Intro: 4-9
```

```fitch
1  | P ∨ Q
   |----
2  | | ¬P ∧ ¬Q
   | |----
3  | | ¬P               ∧ Elim: 2
4  | | ¬Q               ∧ Elim: 2
5  | | | P
   | | |----
6  | | | ⊥              ⊥ Intro: 5, 3
   | |
7  | | | Q
   | | |----
8  | | | ⊥              ⊥ Intro: 7, 4
9  | | ⊥                ∨ Elim: 1, 5-6, 7-8
10 | ¬(¬P ∧ ¬Q)         ¬ Intro: 2-9
```

(difficult 1:)

```fitch
1  | ¬(¬P ∧ ¬Q)
   |----
2  | | ¬(P ∨ Q)
   | |----
3  | | | P
   | | |----
4  | | | P ∨ Q          ∨ Intro: 3
5  | | | ⊥              ⊥ Intro: 4, 2
   | |
6  | | | Q
   | | |----
7  | | | P ∨ Q          ∨ Intro: 6
8  | | | ⊥              ⊥ Intro: 7, 2
9  | | ¬P               ¬ Intro: 3-5
10 | | ¬Q               ¬ Intro: 6-8
11 | | ¬P ∧ ¬Q          ∧ Intro: 9, 10
12 | | ⊥                ⊥ Intro: 11, 1
13 | ¬¬(P ∨ Q)          ¬ Intro: 2-12
14 | P ∨ Q              ¬ Elim: 13
```

(difficult 2:)

```fitch
1  | ¬(P ∧ Q)
   |----
2  | | ¬(¬P ∨ ¬Q)
   | |----
3  | | | ¬P
   | | |----
4  | | | ¬P ∨ ¬Q          ∨ Intro: 3
5  | | | ⊥                ⊥ Intro: 4, 2
   | |
6  | | | ¬Q
   | | |----
7  | | | ¬P ∨ ¬Q          ∨ Intro: 6
8  | | | ⊥                ⊥ Intro: 7, 2
9  | | ¬¬P                ¬ Intro: 3-5
10 | | ¬¬Q                ¬ Intro: 6-8
11 | | P                  ¬ Elim: 9
12 | | Q                  ¬ Elim: 10
13 | | P ∧ Q              ∧ Intro: 11, 12
14 | | ⊥                  ⊥ Intro: 13, 1
15 | ¬¬(¬P ∨ ¬Q)          ¬ Intro: 2-14
16 | ¬P ∨ ¬Q              ¬ Elim: 15
```

### Conversational implicature

Imma be honest I didn't take any notes during this. I just had an energy burst above for writing these fitch proofs...

## Lecture 6

Date: Wednesday 16 september 2026 (2026-09-16)

I was sick that day... no notes.

### Proofs with conditionals

### Proofs with biconditionals

#cs/logic