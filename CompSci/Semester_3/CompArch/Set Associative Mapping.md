---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 230
---

## Overview

**Set-Associative Mapping** is a compromise between direct mapping and associative mapping. The cache is divided into sets, and each set contains several lines.

## How it Works
- **Sets and Lines**: Memory blocks are first mapped to a set, and within that set, they can be placed in any line.
- **Tag and Set Indexing**: The memory address is divided into three parts: Tag, Set Index, and Block Offset.

## Example
- In a 2-way set-associative cache with 64 sets and a block size of 16 bytes, each set contains 2 lines.
- A memory block is first mapped to one of the 64 sets and then can be placed in either of the 2 lines in that set.

## Pros and Cons
- **Pros**: Balances the simplicity of direct mapping and the flexibility of associative mapping.
- **Cons**: More complex than direct mapping, but less so than associative mapping.

[[Cache Memory]] [[Direct Mapping]] [[Associative Mapping]]

---
#review 