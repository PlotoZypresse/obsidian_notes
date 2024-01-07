1. **Immediate Addressing**
    
    - Format: `instruction $value, %dest`
    - Description: The operand is a constant value (immediate). For example, `movq $10, %rax` moves the constant value 10 into the `%rax` register.
2. **Register Addressing**
    
    - Format: `instruction %source, %dest`
    - Description: The operand is a register. For example, `movq %rax, %rbx` moves the value from `%rax` to `%rbx`.
3. **Direct (or Absolute) Addressing**
    
    - Format: `instruction address, %dest`
    - Description: The operand is a direct memory address. For example, `movq 0x404000, %rax` moves the content at memory address `0x404000` into `%rax`.
4. **Register Indirect Addressing**
    
    - Format: `instruction (%reg), %dest`
    - Description: The operand's address is in a register. For example, `movq (%rbx), %rax` moves data from the memory location pointed to by `%rbx` into `%rax`.
5. **Base-Plus-Index Addressing**
    
    - Format: `instruction (%base, %index), %dest`
    - Description: Adds base register and index register to get the address. For example, `movq (%rbx, %rcx), %rax` moves data from the address computed by adding `%rbx` and `%rcx` into `%rax`.
6. **Scaled Index Addressing**
    
    - Format: `instruction (%base, %index, scale), %dest`
    - Description: Similar to base-plus-index, but the index is multiplied by a scale factor (1, 2, 4, or 8). For example, `movq (%rbx, %rcx, 4), %rax` moves data from the address `%rbx + (%rcx * 4)` into `%rax`.
7. **Base-Plus-Index-Displacement Addressing**
    
    - Format: `instruction displacement(%base, %index, scale), %dest`
    - Description: A combination of base register, index register, scale factor, and a displacement. For example, `movq 8(%rbx, %rcx, 4), %rax` moves data from the address `%rbx + (%rcx * 4) + 8` into `%rax`.
8. **Register Indirect with Displacement Addressing**
    
    - Format: `instruction displacement(%reg), %dest`
    - Description: The operand's address is in a register plus a displacement. For example, `movq 4(%rbx), %rax` moves data from the address `4 + contents of %rbx` into `%rax`.
9. **RIP (Instruction Pointer) Relative Addressing**
    
    - Format: `instruction displacement(%rip), %dest`
    - Description: Used for position-independent code, where the address is relative to the instruction pointer `%rip`. For example, `movq label(%rip), %rax` accesses the address of `label` relative to the current instruction.