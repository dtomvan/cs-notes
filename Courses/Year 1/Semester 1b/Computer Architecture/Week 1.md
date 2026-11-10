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
  - p is used to **p**ull the voltage u**p**
  - n is used to take the voltage dow**n**
  - 