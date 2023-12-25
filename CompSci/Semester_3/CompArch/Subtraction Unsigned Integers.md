Subtraction of unsigned integers in binary, much like addition, follows a specific process. However, because you're dealing with unsigned integers, there are some extra considerations regarding underflow (when the result is supposed to be negative, which isn't representable in unsigned integers). Here's how you can perform subtraction:

1. **Binary Representation**: First, represent both numbers in binary. For instance, in an 8-bit system, the number 5 is `00000101`.
    
2. **[[Twos Complement]]**: Instead of directly subtracting, you use the two's complement method. To subtract `B` from `A` (`A - B`), you find the two's complement of `B` and then add it to `A`. The two's complement of a number is obtained by inverting all the bits (turning 0s to 1s and 1s to 0s) and then adding 1 to the result.
    
3. **[[Addition Unsigned Integers|Bitwise Addition]]**: Add `A` and the two's complement of `B`. Handle carries as you would in addition. If there's a carry out of the most significant bit, simply ignore it (it's discarded).
    
4. **Underflow**: If `A` is smaller than `B`, the result will be the two's complement of the actual difference. This result is typically interpreted as a very large number in unsigned arithmetic, representing underflow.

For example, let's subtract 3 (`00000011` in binary) from 5 (`00000101` in binary) in an 8-bit system:

1. Find the two's complement of 3: Invert the bits (`11111100`) and add 1 (`11111101`).
2. Add this result to 5 (`00000101` + `11111101`).
3. Perform binary addition: `00000101` + `11111101` = `00000010`.
4. The result is `00000010`, which is 2 in decimal, the correct result of 5 - 3.

In cases where `A` is less than `B`, the result is interpreted as a large number due to underflow. For instance, subtracting 5 from 3 in an 8-bit system would yield `11111110` in binary, which is 254 in decimal, a representation of underflow in unsigned arithmetic.
[[Unsigned Integers]]

---
#review