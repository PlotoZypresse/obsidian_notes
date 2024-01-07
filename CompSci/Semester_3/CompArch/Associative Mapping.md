---
sr-due: 2024-01-08
sr-interval: 4
sr-ease: 270
---

## Overview

**Associative Mapping** (also known as Fully Associative Mapping) in cache memory allows a block of memory to be stored in any cache line, rather than being restricted to a particular one.

## How it Works

- **Tag Only**: The memory address is divided into only two parts: Tag and Block Offset. The entire cache is searched to find a block.
- **Flexibility**: Any block can go into any line of the cache, as long as there's a free line.

## Example

- Suppose a cache system has 16 lines and a block size of 32 bytes.
- Any block from the main memory can be placed in any of these 16 lines, based solely on tag matching.

## Pros and Cons

- **Pros**: Minimizes conflict misses.
- **Cons**: Requires more complex hardware, can be slower and more expensive.

[[Cache Memory]]

---
#review 