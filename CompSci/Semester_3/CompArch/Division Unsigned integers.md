---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 234
---

Division can be done just like normal pencil and paper division. 

# Binary Division

## Overview

Binary division is a process of dividing binary numbers (numbers in base 2). It's similar to long division in the decimal system but simpler, as each digit in binary is either 0 or 1.

## Steps of Binary Division

1. **Divide**: Compare the divisor with the first digit of the dividend. If the divisor is larger, extend the selection to the next digit.
2. **Subtract**: If the selected part of the dividend is greater than or equal to the divisor, subtract the divisor from this part.
3. **Write the Result**: Write down the result of the subtraction (either 0 or 1) below the dividend.
4. **Repeat**: Move one digit to the right and repeat the process until you have covered all digits of the dividend.

## Example

- Dividend: 1011 (binary for 11 in decimal)
- Divisor: 11 (binary for 3 in decimal)

### Calculation

1. **1011 ÷ 11**:
    - Compare 1 (dividend) with 11 (divisor). 1 is smaller, so we take the next digit, making it 10.
    - 10 is smaller than 11, so we include the next digit: 101.
    - 101 is smaller than 11, so we write down a 0 and include the next digit: 1011.
    - 1011 is greater than 11, so we perform binary subtraction.
    - The result of the subtraction is 100 (binary for 4 in decimal).
    - The process ends here as there are no more digits left in the dividend.

### Result

- **The quotient is 100 (binary for 4 in decimal), and the remainder is 0.**

## Tips

- Remember that in binary, you can only subtract a number from another if the top number is equal to or larger than the bottom number.
- Binary subtraction is like decimal subtraction, but simpler: 1 - 1 = 0, 1 - 0 = 1, and 0 - 0 = 0.

Sure, let's delve deeper into the example of binary division with the dividend 1011 (which is 11 in decimal) and the divisor 11 (3 in decimal). The process is similar to long division in the decimal system.

### Example: 1011 ÷ 11

#### Step-by-Step Process

1. **Setup**: Write the dividend (1011) under a division bar, and the divisor (11) outside the bar, similar to a long division format.
    
    `11 | 1011`
    
2. **Division Start**: Begin from the left of the dividend.
    
    - Compare the first digit (1) of the dividend with the divisor (11). Since 1 is less than 11, we cannot divide it. So, we take the first two digits (10) of the dividend.
    
    `11 | 1011      10   (First two digits of the dividend)`
    
3. **Extend and Compare**: 10 (which is 2 in decimal) is still less than 11 (3 in decimal). Therefore, we extend one more digit to the right.
    
    `11 | 1011      101  (First three digits of the dividend)`
    
4. **Perform Division**: Now we have 101 (5 in decimal), which is greater than 11 (3 in decimal). In binary division, we simply check if the number formed by the dividend digits is greater than or equal to the divisor. If yes, write 1 in the quotient and perform subtraction; if no, write 0.
    
    `11 | 1011     - 11     -----      101`
    
5. **Subtract**: Subtract 11 from 101. Remember that binary subtraction is performed like decimal subtraction but with binary digits.
    
    `101 -11 ----  10`
    
    The result of 101 - 11 is 10 (2 in decimal).
    
6. **Bring Down Next Digit**: Bring down the next digit of the dividend (the last '1' in 1011). Now our number is 101.
    
    `11 | 1011     - 11     -----       10`
    
7. **Repeat Division Step**: Compare this 101 with 11 again. It is lesser, so we write down a 0 in the quotient.
    
8. **Final Quotient and Remainder**: Since there are no more digits to bring down, the division process is complete. The quotient is the number written at the top, and the remainder is what's left after the final subtraction.
    

#### Final Result

- Quotient: 100 (4 in decimal)
- Remainder: 0

So, 1011 divided by 11 is 100 with a remainder of 0. This is equivalent to saying that 11 divided by 3 is 4 with no remainder in the decimal system.

[[Unsigned Integers]]

---
#review