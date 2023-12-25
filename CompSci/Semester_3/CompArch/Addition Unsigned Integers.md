---
sr-due: 2023-12-26
sr-interval: 1
sr-ease: 230
---

The addition of unsigned integers involves summing two numbers without considering any sign (positive or negative). In computing, unsigned integers are often used when only non-negative values are required. Here's how the process typically works:

1. **Binary Representation**: Computers operate using binary (base-2) numbers. So, the first step is to represent the integers in binary form. For example, in an 8-bit system, the number 5 is represented as `00000101`.

2. **Bitwise Addition**: Each bit from the two numbers is added starting from the least significant bit (the rightmost bit) to the most significant bit (the leftmost bit).

3. **Carry**: If adding two bits results in a sum of 2 (`10` in binary), a carry is generated. This carry is added to the sum of the next higher order bit.

4. **Handling [[Overflow]]**: In the context of a fixed-size data type, if a carry is generated out of the most significant bit, it results in an overflow. In unsigned integer arithmetic, this overflow is typically ignored, effectively wrapping around the maximum value that can be stored in the given number of bits.

For example, let's add two 8-bit unsigned integers, `5` (which is `00000101` in binary) and `3` (which is `00000011` in binary):

1. Start from the rightmost bit: `1 + 1 = 10` (2 in decimal), so write down `0` and carry `1`.
2. Move to the next bit: `0 + 1 + 1 (carry) = 10`, so write down `0` and carry `1`.
3. Continue this process for all bits.
4. If there's a carry from the most significant bit, it's discarded in unsigned arithmetic.

The result of this addition will be the binary sum of the two numbers, respecting the bit-size of the integers. For instance, in our example of adding 5 and 3, the binary result would be `00001000`, which is `8` in decimal.![[Screenshot 2023-12-23 at 11.16.19.png]]

[[Unsigned Integers]]

---
#review