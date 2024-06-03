- [ ] Lecture: Online Algorithms.  [Source](https://imada.sdu.dk/u/kslarsen/dm582/L11.php)
- [ ] Lecture: Meldable Priority Queues. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L12.php | Source)  


## Competitive Analysis

### Machine Scheduleing

### Proof

## Priority Queues

### Leftist Heaps

### Skew Heaps


Sure, here are the detailed notes for your oral presentation, arranged in the correct order, formatted for Obsidian:

# Online Algorithms

## Online Problems and Algorithms
- **Definition**: A problem is online if:
  - We must process a non-empty, finite request sequence.
  - Each request must be processed before receiving the next one.
  - An irrevocable decision must be made for each request.
  - Decisions result in some cost.
- **Examples**: Ski rental, bin packing, machine scheduling.

## Competitive Analysis
- **Purpose**: Measure the quality of an online algorithm in terms of cost efficiency compared to an optimal offline algorithm (Opt).
- **Optimal Offline Algorithm (Opt)**: Has the entire input before computation, knowing the future.
- **Competitive Ratio**: An algorithm $Alg$ is $c$-competitive if there exists a constant $b$ such that $\forall I : Alg(I) \leq c \cdot Opt(I) + b$.
  - The competitive ratio $c$ is the smallest constant for which $Alg$ is $c$-competitive.

## Machine Scheduling
- **Problem**: Assign $n$ jobs of varying sizes to $m$ machines to minimize the makespan (time to finish all jobs).
- **List Scheduling (Ls)**: Place the next job on the least loaded machine.
- **Example**:
  - Jobs: 1, 4, 5, 3, 4, 7
  - Machines: $M_1, M_2, M_3, M_4$
  - Ls assignment: Jobs are assigned to machines based on current load, resulting in different makespans for Ls and Opt.

### Competitive Ratio of List Scheduling
- **Worst-case Example**:
  ```
  Jobs: 1, 1, 1, ..., 1 (m jobs each of size 1)
  Machines: $M_1, M_2, ..., M_m$
  ```
  - Ls makespan: $2m-1$
  - Opt makespan: $m$
  - Competitive ratio: $\frac{2m-1}{m} = 2 - \frac{1}{m}$

### Theorem
- **Result**: The algorithm Ls for minimizing makespan in machine scheduling with $m \geq 1$ machines has a competitive ratio $2 - \frac{1}{m}$.

# The k-Server Problem

## Introduction
- **Problem**: Concerns the cost of moving $k$ servers around in a metric space to serve requests.
- **Metric Space** $(M,d)$:
  - $M$: Set of points.
  - $d: M \times M \rightarrow \mathbb{R}$: Distance function.
  - Properties: $d(x, x) = 0$, $d(x, y) > 0$ for $x \neq y$, $d(x, y) = d(y, x)$, $d(x, z) \leq d(x, y) + d(y, z)$ (triangle inequality).

## Problem Definition
- **Algorithm**: Controls $k$ mobile servers located at points in $M$.
- **Requests**: Sequence $\sigma = r_1, r_2, ..., r_n$ where each $r_i$ is a point in $M$.
- **Objective**: Serve each request sequentially by moving a server to the requested point at minimal cost.
- **Cost**: Moving a server from $r_i$ to $r_j$ incurs a cost $d(r_i, r_j)$.
- **Online Constraint**: Algorithm is not informed of the next request until it has served the current one.

## General Lower Bound
- **Theorem**: Any online algorithm for the k-server problem has a competitive ratio of at least $k$.
- **Proof Outline**:
  - Assume $Alg$ is a lazy online algorithm.
  - Choose $k+1$ points from $M$.
  - Define request sequence such that each request $r_{i+1}$ is at the point not covered by $Alg$ after serving $r_i$.
  - Cost of $Alg$: $\sum_{i=1}^{n-1} d(r_i, r_{i+1})$
  - Total cost of all k different server algorithms: $\sum_{i=2}^{n-1} d(r_{i-1}, r_i)$.
  - One algorithm in $B$ must have a cost at most the average: $\frac{1}{k} \sum_{i=2}^{n-1} d(r_{i-1}, r_i)$.
  - $Alg(\sigma) \geq k \cdot Opt(\sigma)$.

## k-Server Algorithms
- **Conjecture**: For the k-server problem on any metric space, there exists a deterministic online k-competitive algorithm.

## Simplest Nontrivial Problem
- **Example**: Line with three points $a, b, c$ and $k=2$ servers initially on $a$ and $c$.
- **Algorithm Greedy**: Moves the server that can serve the request at the lowest cost.
- **Performance**: Analyze how Greedy and Opt perform on sequence $\sigma = b, a, b, a, ...$.

## Double-Coverage Algorithm (DC)
- **Definition**: 
  - If the request is on the same side of all servers, move the nearest server to the request.
  - If the request is between two adjacent servers, move both towards the request at equal speeds until one reaches the request.
- **Example**: Three points $a, b, c$ with servers on $a$ and $c$. Requests: $b, a, b, ...$.

## DC's Competitive Ratio
- **Theorem**: DC is k-competitive.
- **Proof**:
  - Define potential function $k \cdot M_{\text{min}} + \sum \text{DC}$.
  - Analyze potential changes when Opt and DC move.
  - When Opt moves distance $d$, potential increases by at most $kd$.
  - When DC moves distance $d$, potential decreases by at least $d$.

# The Treasure Hunt Problem

## Problem Definition
- **Scenario**: Either box $A$ or $B$ contains an object we need to find. Costs of opening $A$ and $B$ are $a$ and $b$ respectively.
- **Objective**: Find a good competitive algorithm.
- **Deterministic Strategy**: Adversary hides object to maximize cost. Competitive ratio: $\frac{a+b}{\max(a,b)}$.

## Randomized Algorithm
- **Assumption**: Adversary knows our algorithm but not our coin flip.
- **Strategy**: Open $A$ with probability $p$, $B$ with probability $1-p$.
- **Expected Competitive Ratio**:
  - Adversary hides in $A$: $\frac{pa + (1-p)(a+b)}{a}$
  - Adversary hides in $B$: $\frac{p(a+b) + (1-p)b}{b}$
- **Optimal Probability**: Set equal expected ratios:
  $$
  p = \frac{b^2}{a^2 + b^2}
  $$
- **Expected Competitive Ratio**:
  $$
  \frac{a^2 + b^2 + ab}{a^2 + b^2}
  $$
  - Note: This is $\frac{3}{2}$ when $a = b$. All other situations are better, and the ratio approaches 1 as $b \to 0$ or $b \to \infty$.

## Conclusion
- Theoretical insights into online algorithms provide efficient solutions for dynamic and real-time problems.
- The k-server problem and randomized strategies like in the treasure hunt problem illustrate the practical applications and complexities of designing competitive online algorithms.

# Meldable Priority Queues

## Priority Queues
- **Definition**: A priority queue is a data type for a collection of elements, each with an associated priority.
- **Basic Operations**:
  - `q = PriorityQueue()`: Initializes an empty priority queue.
  - `q.insert(e, p)`: Inserts the element $e$ with priority $p$ into $q$.
  - `q.findMin()`: Returns the element of highest priority (traditionally the smallest value) in $q$.
  - `q.deleteMin()`: Deletes and returns the element of highest priority from $q$.
- **Additional Operations**: Priority queues may also support operations like `decreaseKey`, `meld`, etc.

## Binary Heaps
- **Most well-known implementation** of priority queues.
- **Operations**:
  - `findMin()`: $O(1)$ time.
  - `insert(e, p)`: $O(\log n)$ time.
  - `deleteMin()`: $O(\log n)$ time.
- **Meld Operation**:
  - `meld(q, p)`: Returns a new priority queue containing all elements from $q$ and $p$ (destructive).
  - **Challenge**: Standard binary heaps cannot provide an efficient meld operation.

## Leftist Heaps
- **Definition**: A leftist heap is implemented as an annotated binary tree.
  - **Node Structure**: Each node contains an element with a priority and a rank.
  - **Heap-Ordered**: The priority of a node is at most the priority of its children.
  - **Rank**: Defined as the distance to nil (a special node with rank zero). For other nodes, rank is one plus the minimum of the ranks of its children.
  - **Leftist Property**: For any node $u$, $u.\text{left().rank()} \geq u.\text{right().rank()}$.

## Example Leftist Heap
```
    16 1
   /    \
  14 1  12 1
 /     /   \
4 2  11 1  20 1
     /    /      \
   10 2  6 1     3 2
```

### Melding Two Leftist Heaps
1. **Merge the right-most paths** of the two argument heaps according to priorities via their right child references.
2. **Adjust the ranks** bottom-up on the right-most path in the result.
3. **Switch the children** of nodes on the right-most path if the leftist property is violated.
4. **Result**: A new leftist heap.
5. **Complexity**: Time proportional to the sum of the lengths of the right-most paths of the arguments.

## Leftist Heap Complexity
- **Lemma**: In a leftist tree, the subtree of a node with rank $r$ contains at least $2^r - 1$ nodes.
  - **Proof**: By structural induction.
    - **Base Case**: A node with no children has rank 1 and its subtree contains $2^1 - 1 = 1$ nodes.
    - **Induction Step**: A node with rank $r$ has children with rank at least $r-1$. Hence, its subtree has at least $2(2^{r-1} - 1) + 1 = 2^r - 1$ nodes.
- **Corollary**: The maximal rank of the root of a leftist heap with $n$ elements is $\log(n + 1)$.
  - **Proof**: If $r$ is the rank of the root, $n \geq 2^r - 1$, so $r \leq \log(n + 1)$.

## Meld Complexity
- **Theorem**: A meld of two leftist heaps with $n_1$ and $n_2$ elements takes time $O(\log n)$, where $n = n_1 + n_2$.
  - **Proof**:
    - For any node of rank $r$ with left and right children ranks of $r_l$ and $r_r$, since $r_l \geq r_r$ (the leftist property), $r = $r_r + 1$.
    - The time to meld the two heaps is proportional to the sum of the lengths of the two right-most paths: $\log(n_1 + 1) + \log(n_2 + 1) \leq 2 \log(\max\{n_1, n_2\} + 1) \leq 2 \log n$.

## Operations of Leftist Heaps
- **Initialization**: $q = PriorityQueue()$: $O(1)$.
- **Insertion**: $q.insert(e, p)$: Create a singleton heap and meld with $q$ in $O(\log n)$.
- **Finding Minimum**: $q.findMin()$: $O(1)$.
- **Deletion**: $q.deleteMin()$: Remove the root, meld its two children in $O(\log n)$.
- **Building Heap**: $q = buildHeap(elements)$: Annotate a classic heap with ranks in linear time, $O(n)$.

## Skew Heaps
- **Definition**: A variant of leftist heaps without rank information.
  - **Operation**: After merging right-most paths by priority, switch subtrees of every node on that path.
- **Example**:
  ```
  Before:
       8 1
      /   \
     30 1  15 1
    /    /    \
   5 2  16 1  14 1

  After:
       16 1
      /    \
     14 1  12 1
    /    /    \
   4 2  11 1  20 1
  ```

## Skew Heap Analysis
- **Definitions**:
  - **Heavy Node**: A node is heavy if its right subtree contains more nodes than its left subtree.
  - **Light Node**: Otherwise, it is light.
- **Properties**:
  - During merge, heavy nodes become light.
  - We do not know if a light node changes status.

### Complexity
- **Lemma**: At most $\log n$ light nodes on the right-most path of a skew heap.
  - **Proof**: A heavy node has $|B| > |A|$, but is light, so $|B| \leq |A|$. Traversing the right-most path, we always move towards the subtree with at most half of the nodes, occurring $\log n$ times.

- **Theorem**: Meld operation for skew heaps is amortized $O(\log n)$.
  - **Proof**: Using potential function $\Phi(T)$ as the number of heavy nodes:
    - **Cost of meld**: $(l_1 + h_1) + (l_2 + h_2)$
    - **Potential change**: $\Delta\Phi = -h_1 - h_2 + l_1 + l_2$
    - **Amortized cost**: $2(l_1 + l_2)$

### Skew Heap Operations
- **Initialization**: $q = PriorityQueue()$: $O(1)$.
- **Insertion**: $q.insert(e, p)$: Create a singleton heap and meld with $q$ in amortized $O(\log n)$.
- **Finding Minimum**: $q.findMin()$: $O(1)$.
- **Deletion**: $q.deleteMin()$: Remove the root, meld its two children in amortized $O(\log n)$.
- **Building Heap**: $q = buildHeap(elements)$: Shape of a classic heap makes all nodes light. This operation can be performed in $O(n)$ and the potential is zero, maintaining the amortized results.

## Conclusion
- Theoretical insights into meldable priority queues provide efficient solutions for dynamic and real-time problems.
- Leftist heaps and skew heaps offer efficient melding operations, making them suitable for applications where priority queue merging is frequent.

Feel free to ask for any additional details or clarifications you may need!