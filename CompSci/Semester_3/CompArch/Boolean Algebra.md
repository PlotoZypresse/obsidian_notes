---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 228
---

## Introduction to Boolean Algebra

- **Definition**: Boolean Algebra is a branch of algebra that deals with variables that have two distinct values: true (1) and false (0).
- **Applications**: Widely used in digital electronics, computer science, and mathematical logic.

## Basic Concepts

### Variables

- **Boolean Variables**: Represented by symbols (e.g., A, B, C) and can take the values 0 (false) or 1 (true).

### Operators

- **AND** (Conjunction): Denoted as A⋅B or simply AB. Output is true if both inputs are true.
- **OR** (Disjunction): Denoted as A+B. Output is true if at least one input is true.
- **NOT** (Negation): Denoted as Aˉˉ or NOT  A. Inverts the input value.

## Fundamental Laws of Boolean Algebra

1. **Identity Law**:
    - $A+0=A$
    - $A⋅1=A$
2. **Null Law**:
    - $A+1=1$
    - $A⋅0=0$
3. **Idempotent Law**:
    - $A+A=A$
    - $A⋅A=A$
4. **Complement Law**:
    - $A+Aˉ=1$
    - $A⋅Aˉ=0$
5. **Commutative Law**:
    - $A+B=B+A$
    - $AB=BA$
6. **Associative Law**:
    - $(A+B)+C=A+(B+C)$
    - $(AB)C=A(BC)$
7. **Distributive Law**:
    - $A(B+C)=AB+AC$
    - $A+(BC)=(A+B)(A+C)$
8. **Absorption Law**:
    - $A+AB=A$
    - $A(A+B)=A$
9. **De Morgan’s Theorems**:
    - $not(A+B)=not(A)⋅not(B)$ 
    - $AB‾=Aˉ+Bˉ$

## Boolean Functions and Expressions

- **Boolean Function**: Represents a combination of Boolean variables and operators.
- Can be simplified using the laws of Boolean algebra.
- Useful in designing and optimizing digital circuits.

[[Karnaugh Maps (K-maps)]] [[Gates]] [[Sum of Products(SOP)]] [[Product of sum(POS)]]

--- 
#review 