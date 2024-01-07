---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 229
---
Just like in normal multiplication we have the multiplicand in M and the multiplier in Q. For booths algorithm we also need a 1-bit register $Q_{-1}$ (see pictures) and a shift register $A$. We now add or subtract M from A depending on the Bits in $Q_0$ and in $Q_{-1}$ (see picture) or we just shift. Subtraction is done just like [[Twos Complement Subtraction]]. Because the shift is an arithmetic shift we fill in with the MSB and not just zeros. The number of cycles is defined by the number of bits in the [[Multiplier]]. A is always initialized to 0 at the start.
![[Screenshot 2023-12-23 at 12.27.14.png]]
![[Screenshot 2023-12-23 at 12.25.44.png]]
[[Twos Complement]]

---
#review