## Overview

The Hamming Code Encoding Algorithm is used to add redundant bits to data bits to create a Hamming code, which can detect and correct single-bit errors. This note explains the encoding process with an example.

## Steps in Encoding

### 1. Determine Redundant Bits

First, calculate the number of redundant bits required. For `n` data bits, the number of redundant bits `r` is the smallest number such that `2^r >= n + r + 1`.

### 2. Position of Redundant Bits

Redundant bits are placed at positions that are powers of 2 (1, 2, 4, 8, ...).

### 3. Calculate Redundant Bits

Each redundant bit covers bits at positions that include its own position in their binary representation. The value of each redundant bit is set to either 0 or 1 to make the total number of 1s in its covered bits even (for even parity).

## Example with 16-Bit Data

Consider a 16-bit data sequence: `1010101010101010`.

### Step-by-Step Encoding

1. Calculate `r`: In this case, `r` is 5, since `2^5 = 32` which is just enough to cover 16 data bits and 5 redundant bits.
2. Insert redundant bits (R) at positions 1, 2, 4, 8, 16: `_R_R_R1010_R10101010`
3. Calculate each redundant bit's value based on the parity of its coverage.

### Final Encoded Sequence

- Show the final encoded sequence with calculated redundant bits.

## Conclusion

This algorithm ensures that the Hamming code can detect and correct single-bit errors in the encoded data.

- See also: [[Hamming Codes]]