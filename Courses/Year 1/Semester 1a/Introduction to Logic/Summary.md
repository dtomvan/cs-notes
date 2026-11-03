# Validity of arguments

# Fitch proofs

## Boolean connectives
## Negation
## (bi-)implication
## Quantifiers

# Logical Equivalences and laws

# Normal forms

## Quantifier normal forms

### Prenex normal form

*Def.* a wff is in Prenex normal form if it is in NNF, and no quantifiers under boolean connectives, i.e. all quantifiers “at the top”

Logical laws:
- Renaming: $\forall x P(x) \Leftrightarrow \forall y P(y)$
- DeMorgan:
  - $\neg\forall x P(x) \Leftrightarrow \exists x \neg P(x)$
  - $\neg\exists x P(x) \Leftrightarrow \forall x \neg P(x)$
- Same quantifier:
  - $\forall x P(x) \land \forall x Q(x) \Leftrightarrow \forall x (P(x) \land Q(x))$
  - $\forall x P(x) \lor \forall x Q(x) \Leftrightarrow \forall x (P(x) \lor Q(x))$
- Implications:
  - These next two assume no free $x$ in $P$.
  - $P \rightarrow \forall x Q(x) \Leftrightarrow \forall x (P \rightarrow Q(x))$
  - $\forall x Q(x) \rightarrow P \Leftrightarrow \exists x (Q(x) \rightarrow P)$

### Skolem normal form

*Def.* a wff is in Skolem normal form if it is in Prenex normal form, without $\exists$ in the formula

Steps:
- Make it Prenex first
- For each $\exists$:
  - $\exists$ in front: make a constant
  - $\exists$ after a $\forall$: make a function that depends on all previous $\forall$‘s

For instance:

$$
\exists x \forall y \forall z \exists w \forall e \exists g P(x,y,z,w,e,g)
$$
becomes

$$
\forall y \forall z \forall e P(c, y, z, f_1(y, z), e, f_2(y,z,e))
$$

_Note:_ I’ve used $f_1$ and $f_2$ here because I’ve ran out of letters. Use different letters for the functions preferably.