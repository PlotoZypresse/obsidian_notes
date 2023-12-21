Addition in twos complement is the same as with unsigned integers. If the two numbers are positive we get a positive number in twos complement form. If they are negative we get a negative number in twos complement form. If there is a carry bit beyond the word it is ignored![[Screenshot 2023-12-20 at 13.04.40.png]]

### Overflow
on addition the result may be larger than what can be stored in a word size. This is called overflow. When overflow occurs the ALU will signal it![[Screenshot 2023-12-20 at 13.00.58.png]] 