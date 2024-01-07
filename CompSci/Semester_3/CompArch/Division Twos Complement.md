---
sr-due: 2024-01-06
sr-interval: 2
sr-ease: 249
---

# Two's Complement Division

## Overview

Two's complement is a method used in computing to represent positive and negative integers in binary form. The most significant bit (MSB) indicates the sign (0 for positive, 1 for negative), and the value is represented in a way that makes addition and subtraction more straightforward.

## Sign Representation

- Positive numbers are represented as usual in binary.
- Negative numbers are represented by inverting all the bits of the absolute value and then adding 1 to the result.

## Steps for Division

Division of two's complement numbers involves a few additional steps to handle the signs of the operands.

1. **Determine the Sign of the Result**:
    
    - The result is negative if the signs of the operands are different, and positive if they are the same.
2. **Convert to Absolute Values**:
    
    - If necessary, convert the operands to their absolute values using two's complement.
3. **Perform Binary Division**:
    
    - Divide the numbers as in normal binary division.
4. **Convert Back if Negative**:
    
    - If the result should be negative, convert it back to two's complement.

## Example

- Dividend: -6 (1110 in two's complement)
- Divisor: 3 (0011 in binary)

### Calculation

1. **Sign of Result**: Negative (since the dividend is negative and the divisor is positive).
2. **Convert to Absolute Values**:
    - Convert -6 to its absolute value: 0110.
3. **Binary Division**:
    - Perform division with 0110 (6) ÷ 0011 (3).
    - The quotient is 0010 (2 in binary).
4. **Convert Back**:
    - Since the result should be negative, convert 2 into two's complement: 1110 (-2 in two's complement).

### Result

- The quotient is 1110 (-2 in two's complement), indicating -2.

## Tips

- Always check the sign of the operands before beginning the division.
- Remember to convert back to two's complement if the result is negative.

[[Division Unsigned integers]]
[[Twos Complement]]

---
#review