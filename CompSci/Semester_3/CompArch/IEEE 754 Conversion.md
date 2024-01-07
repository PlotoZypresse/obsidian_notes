## Decimal to [[IEEE 754 Standard|IEEE 754]]

### Steps

1. **Determine Sign Bit**:
    - 0 for positive, 1 for negative.
2. **Convert to Binary**:
    - Convert the absolute value of the decimal number to binary.
3. **Normalize the Number**:
    - Adjust the binary number so it’s in the form 1.xxxx.
4. **Find the Exponent**:
    - Calculate the exponent needed to scale the normalized number back to its original value.
    - Use bias (127 for single precision, 1023 for double precision).
5. **Encode Exponent and Mantissa**:
    - Write the biased exponent in binary.
    - Write the mantissa (normalized number without the leading 1).

\pagebreak
### Example: Convert Decimal 10 to IEEE 754 Single Precision

1. **Sign**: 10 is positive, so sign bit = 0.
2. **Binary Conversion**: 10 in binary is 1010.
3. **Normalization**: 1.010 × 2³.
4. **Exponent**: 3 + 127 (bias) = 130, which is 10000010 in binary.
5. **Result**: 0 10000010 01000000000000000000000.

## IEEE 754 to Decimal

### Steps

1. **Determine Sign**:
    - Based on the sign bit.
2. **Decode Exponent**:
    - Convert exponent to decimal and subtract the bias.
3. **Decode Mantissa**:
    - Interpret mantissa as a fraction.
4. **Denormalize**:
    - Apply the exponent to scale the mantissa back.

### Example: Convert IEEE 754 Single Precision 0 10000010 01000000000000000000000 to Decimal

1. **Sign**: 0, so the number is positive.
2. **Exponent**: 10000010 is 130 in decimal. 130 - 127 (bias) = 3.
3. **Mantissa**: 1.01000000000000000000000 (implicit leading 1).
4. **Result**: 1.01 in binary is 1.25 in decimal, so 1.25 × 2³ = 10.



---
#review 