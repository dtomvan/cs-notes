---
tags: week
parentCourse: "[[Courses/Semester 1a/Programming Fundamentals]]"
---

## Lecture 3

Date: Mon 14 Sep 2026 (2026-09-14)

Quick `printf` formatter reference:

- `%d`: decimal
- `%ld`: long decimal
- `%u`: unsigned decimal
- `%c`: character
- `%s`: string ending in `\0`
- `%f`: float (11 positions)
- `%X.Yf`: use at least `X` positions, of which `Y` after decimal dot
- `%e`: float as scientific notation
- `%E`: idem except capital E in the exponent

## Lecture 4

Date: Thu 17 Sep 2026 (2026-09-17)

### Exponentiation

- Accomplish: $c = a^b$
- Assume: no overflow

```c
/* compute a^b, call this M */

/* a^b == M */

int c = 1;

/* c*a^b == M */ // now multiply by a, b times
while (b > 0) {
    c *= a;
    b--;
    /* c*a^b == M */ // this STILL holds!
}

/* b == 0, c == M */
```

now, faster! (binary exponentiation)

```c
// O(log2 b)
int c = 1;
while (b > 0) {
    if (b%2==0) { // even b means we can extract a square :) a^2^(b/2) == a^b
        a *= a;
        b /= 2;
    } else {
        c *= a;
        b--;
    }
}
```

### Modular arithmetic

For integers `n` and `d > n` we have:
$n = (n / d) * d + r$ and $0 \le r \lt d$
where `r = n mod d`. (remainder division)

- **Lemma 1:** for modular _addition_ we have `(a + b) % d == ((a % d) + (b % d)) % d`. The rhs is _much_ faster to compute for large values of `a` and `b` (and smaller values of `d`
  - Proof is in the slides, but you don't need to make them yourselves anyways
- **Lemma 2:** modular _multiplication_: `(a * b) % d == ((a % d) * (b % d)) % d`
- **Lemma 3:** modular _exponentiation_: `(a ^ n) % d == ((a % d)^n) % d`

### Modular exponentiation

- If we want to compute the last 2 digits of some huge exponentiation, we can
  use lemma 3 to do that without overflowing!
- Used in encryption
- For instance: `(2^100) % 100`
- Don't compute `2^100` first! `2^100 == 4^50 == 16^25`
- All of the following is `mod 100`:
  - `16^25 == (16 * (16^24))`
  - `(16 * (16^24)) == (16 * (256^12))`
  - = `(16 * (56^12))`
  - = `(16 * (3136^6))`
  - = `(16 * (36^6))`
  - = `(16 * (1296^3))`
  - = `(16 * (96^3))`
  - = `(16 * 16 * (96^2))`
  - = `(16 * 96 * 96^2)`
  - = `(1536 * 96^2)`
  - = `(36 * 9216)`
  - = `(36 * 16)`
  - = `576`
  - = `76`

The program then becomes:

```c
// NOT A LAB
/* file : fastexp.c */
/* author : Tom Oostveen (t.oostveen@student.rug.nl) */
/* date : 2026-09-17 */
/* version: 1.0 */

/* Description:
 * Calculate a^b % d
 */

#include <stdio.h>

int main(int argc, char **argv) {
  unsigned long a, b, d;
  scanf("%ld%ld%ld", &a, &b, &d);
  unsigned long c = 1;
  while (b > 0) {
    if (b % 2 == 0) {
      a *= a;
      b /= 2;
    } else {
      c *= a;
      b--;
    }
    // we can mod anything, always :)
    a %= d;
    b %= d;
    c %= d;
  }
  printf("%ld", c);
  return 0;
}
```

### Perfect numbers

Got distracted writing the above program, missed it :)

- Number that's equal to the sum of its own divisors: `6 == 1*2*3 == 1+2+3`
- Algo goes here :p

### GCD

- For non-negative integers `a` and `b`,
- The `gcd(a, b)` is the largest common factor of `a` and `b`, without a remainder
- `gcd(a, 0) == gcd(0, a) == a`
- If `a>b` then: `gcd(a,b) == gcd(a-b,b)`
- Loop time!
- `gcd(26, 8) == gcd(18, 8) == gcd(10, 8) == gcd(2, 8) == gcd(8, 2) == gcd(0, 2) == 2`
  - Ergo: either swap or subtract, until one of them becomes zero! Then the other value is the gcd.

```c
/* a==A, b==B */
while (b!=0) {
    int r = a % b; // this is the subtract part
    // we can always swap! because we know that r < b
    a = b;
    /* r < a */
    b = r;
    /* b < a */
    // now b might be zero, and we'd be done! then a must contain the gcd
}
/* a==gcd(A, B) */
```

- Used for simplifying fractions: for a fraction `a/b`, the simplified fraction becomes `(a/gcd(a,b))/(b/gcd(a,b))`

### Nested loops

- They exist.

### Functions

- They exist. Go read the syntax spec or something.
