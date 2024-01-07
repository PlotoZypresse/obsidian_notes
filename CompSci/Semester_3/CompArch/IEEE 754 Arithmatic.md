## Overview

Arithmetic in the [[IEEE 754 Standard]] floating-point format involves several key steps and considerations, distinct from regular integer arithmetic, due to the unique representation of floating-point numbers.

## Key Operations

The IEEE 754 standard defines rules for basic arithmetic operations: addition, subtraction, multiplication, division, and square root.

### 1. Addition/Subtraction
- get both on the form of $mantissa*2^{exponent-127}$ 
- **Align Exponents**: Adjust the exponent of the smaller number to match the larger one.
- **Add/Subtract Mantissas**: Perform the addition or subtraction on the aligned mantissas.
- **Normalize the Result**: Adjust the result to fit the standard format (e.g., ensure there's only one non-zero digit before the decimal point in the mantissa).
- **Round**: Apply the appropriate rounding rule if necessary.
85+(-63.5)=21.5
### 2. Multiplication

- **Multiply Mantissas**: Multiply the mantissas of the two numbers.
- **Add Exponents**: Add the exponents of the two numbers and subtract the bias.
- **Normalize and Round**: Normalize the result and apply rounding.

### 3. Division

- **Divide Mantissas**: Divide the mantissa of the dividend by the divisor's mantissa.
- **Subtract Exponents**: Subtract the exponent of the divisor from that of the dividend and add the bias.
- **Normalize and Round**: Adjust the result to the standard format and round as needed.

### 4. Square Root

- **Calculate Square Root**: Compute the square root of the mantissa.
- **Adjust Exponent**: Divide the exponent by two, considering the bias.

## Special Cases

- **Zero**: Operations involving zero are defined, e.g., anything minus zero is itself.
- **Infinity**: Operations involving infinity follow specific rules, e.g., anything times infinity is infinity.
- **NaN (Not a Number)**: Indicates an undefined or unrepresentable result (like 0/0).

## Rounding Modes

IEEE 754 specifies several rounding modes, like round-to-nearest, round-up, round-down, and round-toward-zero.

## Handling Exceptions

The standard defines how to handle exceptional scenarios like overflow (result too large), underflow (result too small), and invalid operations.

## Importance in Computing

- **Consistency**: Ensures uniform behavior of floating-point calculations across different hardware and software platforms.
- **Accuracy**: Balances the need for precision with the limitations of a finite representation.

## Conclusion

Understanding and correctly implementing floating-point arithmetic according to the IEEE 754 standard is crucial for the accuracy and reliability of numerical computations in various fields of computing.