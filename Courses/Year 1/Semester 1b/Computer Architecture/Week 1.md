---
date: "2026-11-09"
pageDecoration:
  icon: airplay
tags: week
parentCourse: "[[Courses/Year 1/Semester 1b/Computer Architecture]]"
---
# Week 1

## Lecture 1

- Date: 2026-11-09
- Topic: Course introduction, combinational logic and circuits

Reading assignments for this week:
- P&P: Chap. 1-3
- H&H: Chap. 1-2

## Course organisation
- Covering Chap. 1-8 in H&H
- Some additional lecture material tho
- 7 tutorials
- 7 labs
- 3 bonus assignments

## The Transformation Hierarchy
- Electrons
- Devices
- Logic
- Micro-architecture
- ISA
- Other stuff that’s not really related to CA

## What we will cover
- Combinatorial logic design
- Hardware description languages
- Sequential logic design
- Timing and verification
- ISA (MIPS)
- Assembly programming
- Micro-architecture fundamentals
- Pipelining
- Branch Prediction
- Out-of-order execution
- Microcontrollers
- Memory Hierarchy
- Caches
- Prefetching
- Virtual memory
- etc.

## Combinational logic circuits
Multiple types of design philisophies, from general-purpose to special-purpose:
- CPU (easy to program, slow)
- GPU (harder to program, efficient for big-parallel or vector operations)
- FPGA (programmable board)
- ASIC (App-Specific Integrated Circuit, not really programmable), for instance TPU

We will learn how CPUs work by programming FPGA’s with Verilog.

## Transistors
Wanna fuck around w this shit? https://nandgame.com

- MOS Transistor (Metal, Oxide, Semiconductors)
- Consists of source+gate+drain
- n-type: drain at the top, source at the bottom
  - Closed at 3v at the gate
- p-type: bubble, source at the top, drain at the bottom
  - Closed at 0v at the gate
- work like wall switches
- CMOS = Complementary MOS, it’s nMOS + pMOS
  - p is used to **p**ull the voltage u**p** (carry 1’s)
  - n is used to take the voltage dow**n** (carry 0’s)
  - these are combined because p’s are bad at carrying zeroes, and vice versa, for electron reasons :D

## Circuits
- Chaining transistors in different ways create logic gates
- Chaining logic gates can create other logic gates:
  - f.i. NAND+NOT=AND
- What you get is a *logic circuit*
- Composed of:
  - Functional spec
    - It’s literally writing the relationship between the inputs and the outputs as a *function*
    - f.i.: given three inputs $A$, $B$, and $C$, we can have outputs $E$ and $G$:
      - $E = F(A, B, C)$
      - $G = F(C,B,A)$
      - where $F(X,Y,Z) = (X \oplus Y) \oplus Z$
  - Timing spec (delay between inputs changing and outputs updating)
- Two types:
  - Combinational logic
  - Sequential logic

## Boolean algebra
- The functional spec for logic circuits relies on boolean algebra, which in turn rely on certain axioms (skip this shit if you took logic tbh):
  - Def. B: $B = \{0,1\} \text{ where } 0\not=1$
  - Closure: $a,b \in B \implies (a + b \in B) \land (a \cdot b \in B)$
  - Associativity: $a,b,c \in B \implies a + (b + c) = (a + b) + c$
  - Commutativity: $a,b \in B \implies (a + b = b + a) \land (a \cdot b = b \cdot a)$
  - Identity: $0,1 \in B \implies (a + 0 = a) \land (a \cdot 1 = a)$
  - Distributive laws:
    - $a,b,c \in B \implies a + (b \cdot c) = (a + b) \cdot (a + c)$
    - $a,b,c \in B \implies a \cdot (b + c) = (a \cdot b) + (a \cdot c)$
  - Complement:
    - $a + \bar a = 1$
    - $a \cdot \bar a = 0$
  - Operations with 0 and 1:
    - $a + 0 = a$
    - $a + 1 = 1$
    - $a \cdot 0 = 0$
    - $a \cdot 1 = a$
  - Idempotency:
    - $a + a = a$
    - $a \cdot a = a$
  - Involution: $\overline{(\bar a)} = a$
  - Laws of complementarity:
    - $a + \bar a = 1$
    - $a \cdot \bar a = 0$
  - Simplification theorems:
    - $a \cdot b + a \cdot \bar b = a$
    - $a + a \cdot b = a$
    - DeM: $\overline{a_1+a_2+\dotso+a_n} = \overline{a_1} \cdot \overline{a_2} \cdot \dotso \cdot \overline{a_n}$
- Standardized function representations:
  - SOP (sum-of-product) = DNF
  - POS (product-of-sum) = CNF
- Some definitions:
  - Complement: negation
  - Literal: literal
  - Implicant: conjunction of literals
  - Minterm: implicant with all input variables
  - Maxterm: disjunction with all input variables as literals

## Combinational components
### Decoder
- $n$ inputs -> $2^n$ outputs
- “detects” which bit pattern is passed in
- f.i.:
  - 00 -> 0001
  - 01 -> 0010
  - 10 -> 0100
  - 11 -> 1000

## Multiplexer
- “Selector”
- Given a selector S ($log_2 n$ bits) and n inputs, “select” one of 