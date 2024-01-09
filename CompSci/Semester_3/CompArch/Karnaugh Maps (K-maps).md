---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 230
---

## What is a Karnaugh Map?

- A **Karnaugh Map** is a visual tool for simplifying Boolean algebra expressions in digital circuit design.
- It helps in reducing the complexity of logic functions.

## Layout of a 4-Variable Karnaugh Map

- The map is a 4x4 grid for handling 4 variables.
- **Rows**: Labeled with combinations of A and B (in Gray Code).
- **Columns**: Labeled with combinations of C and D (in Gray Code).

## Filling the Map

- Each cell represents the output (0 or 1) for each combination of the variables.

## Grouping for Simplification

- Cells with the same value (1s) are grouped to simplify the expression.
- The aim is to form the largest possible groups.

## Example: Simplifying Function F(A, B, C, D)

### Truth Table for Function F

|A|B|C|D|F|
|---|---|---|---|---|
|0|0|0|0|0|
|0|0|0|1|1|
|0|0|1|0|0|
|0|0|1|1|1|
|0|1|0|0|1|
|0|1|0|1|0|
|0|1|1|0|0|
|0|1|1|1|1|
|1|0|0|0|0|
|1|0|0|1|0|
|1|0|1|0|1|
|1|0|1|1|1|
|1|1|0|0|1|
|1|1|0|1|1|
|1|1|1|0|1|
|1|1|1|1|1|

### Karnaugh Map Representation

|AB \ CD|00|01|11|10|
|---|---|---|---|---|
|00|0|1|1|0|
|01|1|0|1|0|
|11|1|1|1|1|
|10|0|0|1|1|

### Simplification Process

- Group 1: All four '1's in the row $AB=11$.
- Group 2: The two '1's in column $CD=11$ for rows $AB=00$ and $AB=01$.
- Group 3: The two '1's in column $CD=01$ for rows $AB=01$ and $AB=11$.

### Simplified Expression

- Group 1 (AB=11): Represents $AB$.
- Group 2 (CD=11): Represents $AˉBˉD$.
- Group 3 (CD=01): Represents $BC$.
- Final Expression: $F=AB+AˉBˉD+BC$.
![[Screenshot 2024-01-08 at 17.45.59.png]]
[[Gates]]

--- 
#review 