---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 229
---

[[Booths Algorithm]]
## Overview

Two's complement is a binary representation of integers, allowing for both positive and negative numbers. It's widely used in computer systems. Multiplication in two's complement is similar to regular binary multiplication, with additional steps to handle the sign bits.

## Sign Representation

- Positive numbers are represented normally in binary.
- Negative numbers are represented by inverting all bits of the absolute value and then adding 1.

## Steps for Multiplication

When multiplying two's complement numbers, the sign and magnitude of the operands must be considered.

1. **Determine the Sign of the Result**:
    
    - The result is negative if the signs of the operands are different, and positive if they are the same.
2. **Convert to Absolute Values**:
    
    - If necessary, convert the operands to their absolute values using two's complement.
3. **Perform Binary Multiplication**:
    
    - Multiply the absolute values using standard binary multiplication.
4. **Adjust for Negative Result**:
    
    - If the result should be negative, convert it into two's complement.

## Example

- Multiplicand: -4 (1100 in two's complement)
- Multiplier: 3 (0011 in binary)

### Calculation

1. **Sign of Result**: Negative (since the multiplicand is negative and the multiplier is positive).
2. **Convert to Absolute Values**:
    - Convert -4 to its absolute value: 0100.
3. **Binary Multiplication**:
    - Perform multiplication with 0100 (4) × 0011 (3).
    - The product is 1100 (12 in binary).
4. **Adjust for Negative Result**:
    - Since the result should be negative, convert 12 into two's complement: 11110100 (-12 in two's complement).

### Result

- The product is 11110100, representing -12 in two's complement.

## Tips

- Carefully determine the sign of the result before starting the multiplication.
- Remember to convert negative operands to their absolute values before multiplying.
[[Twos Complement]]

---
#review