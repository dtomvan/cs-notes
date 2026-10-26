---
tags: week
parentCourse: "[[Courses/Year 1/Semester 1a/Programming Fundamentals]]"
---

## Lecture 6

Date: Mon 21 Sep 2026 (2026-09-21)

### Functions, I guess

- Beware: in C, everything is passed by value by default, this ain't java
- Has its own scope

### Scope, variables, etc.

These all exist, wow:

- Global variables
- Local variables
- Shadowing

### Arrays

They exist. Wow.

## Lecture 7

Date: Thu 24 Sep 2026 (2026-09-24)

### Pointers

- Pointer is just an integer, except it specifies a location in memory
  (stack/heap), instead of an actual value
- Type is `T*` where T is the type of the value it points to
- Deref:
    - `int *p; printf("%p = %d", p, *p);`
- Ref:
    - `int p; int *addr = &p;`

