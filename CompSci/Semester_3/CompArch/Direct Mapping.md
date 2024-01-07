---
sr-due: 2024-01-05
sr-interval: 1
sr-ease: 230
---

## Overview

**Direct Mapping** is a technique used in cache memory where each block of main memory maps to only one possible cache line. It is the simplest cache mapping technique.

## How it Works

- **Indexing**: The address from main memory is divided into three parts: Tag, Cache Line (Index), and Block Offset.
- **Simple Mapping**: Each memory block maps to exactly one cache line.

## Example

- Consider a cache with 128 lines (7 bits for the cache line number) and a block size of 16 bytes (4 bits for block offset).
- A memory address is divided into a tag, a 7-bit line number, and a 4-bit block offset.
- Memory block 3 will map to cache line 3, block 131 will also map to cache line 3, and so on.

## Pros and Cons

- **Pros**: Simple and fast.
- **Cons**: Can lead to higher miss rates due to conflict misses.

[[Cache Memory]]

--- 
#review 