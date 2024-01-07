## Overview

This note outlines the procedure for detecting and correcting errors in data encoded with Hamming Code.

## Error Detection and Correction Steps

### 1. Calculate Parity Bits

On receiving a Hamming code, re-calculate the parity for each redundant bit position using the same method as in the encoding process.

### 2. Compare Parity Bits

Compare the calculated parity bits with the received ones. If they all match, the data is assumed to be error-free.

### 3. Locate and Correct the Error

If there is a mismatch, the position of the error is given by the binary sum of the positions of the incorrect parity bits. Flip the bit at this position to correct the error.

## Example

### Given Encoded Data

Assume you receive a 21-bit Hamming code (16 data bits + 5 redundant bits).

### Error Detection

- Calculate parity bits.
- Identify mismatched parity bits.

### Error Correction

- Determine the position of the erroneous bit.
- Correct the error by flipping the bit at that position.

### Corrected Data

- Show the corrected data sequence.

## Conclusion

The Hamming Code Error Correction Procedure is crucial for maintaining data integrity in noisy communication channels or unreliable storage media.

- See also: [[Hamming Code Encoding Algorithm]], [[Hamming Codes]] 