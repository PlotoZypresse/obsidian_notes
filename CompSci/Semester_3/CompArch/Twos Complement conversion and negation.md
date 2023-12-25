
![Image.png](Image.png)
### From Unsigned to Twos Complement
To convert an unsigned integer to its two's complement representation, you can follow these steps:

1. **Binary Representation**: First, express the unsigned integer in binary. Make sure it fits within the bit size you're working with. For example, in an 8-bit system, the number 5 is represented as `00000101`.
    
2. **Invert the Bits**: Flip each bit of the number. This means turning all 0s into 1s and all 1s into 0s. For the number 5 (`00000101`), this would result in `11111010`.
    
3. **Add One**: Finally, add 1 to the inverted number. Continuing with the example, adding 1 to `11111010` results in `11111011`.
    
This final result is the two's complement representation of the original unsigned integer. In this example, `11111011` is the two's complement of 5 in an 8-bit system.

It's important to note that the two's complement system is a method for representing positive and negative integers. The process of taking the two's complement of an unsigned integer essentially gives you the binary representation of the negative of that number in two's complement form. For instance, in the example given, `11111011` represents -5 in an 8-bit two's complement system.![[Screenshot 2023-12-23 at 11.26.33.png]]
### Negation
![[Screenshot 2023-12-18 at 17.09.03.png]]

---
#review