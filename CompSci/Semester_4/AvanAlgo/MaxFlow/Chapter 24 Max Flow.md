## Chapter 24: Maximum Flow

### 24.1 Flow Networks and Flows

A **flow network** is a directed graph $G = (V, E)$ where each edge $(u, v) \in E$ has a nonnegative capacity $c(u, v) \geq 0$. The network includes a source node $s$ and a sink node $t$, with the requirement that every other node has a path from $s$ to $t$.

Key concepts:

- **Capacity constraint**: The flow $f(u, v)$ on an edge $(u, v)$ must satisfy $0 \leq f(u, v) \leq c(u, v)$.
- **Flow conservation**: For all nodes $u$ except $s$ and $t$, the total incoming flow equals the total outgoing flow.

The **value of a flow** $|f|$ is defined as the total flow out of the source minus the flow into the source. The maximum flow problem seeks to maximize $|f|$.

### 24.2 The Ford-Fulkerson Method

The Ford-Fulkerson method iteratively increases the flow in the network by finding **augmenting paths** in a **residual network** $G_f$, which is derived from the original network by considering the residual capacities of edges.

Key elements:

- **[[Residual networks]]** reflect the remaining capacity for flow along edges, including the possibility of "undoing" flow along a path by considering reverse edges.
- **[[Augmenting path]]**: A path from $s$ to $t$ in $G_f$ along which additional flow can be sent.
- **Cuts**: A cut $(S, T)$ partitions the nodes into two disjoint sets with $s \in S$ and $t \in T$, which helps in understanding the maximum flow through the network.

The method stops when no augmenting path can be found in the residual network, ensuring that the flow is maximized.

**Proofs and Theoretical Insights**:

- **Augmenting paths** effectively increase the flow until reaching the maximum flow possible under the given constraints.
- **[[Max-flow min-cut theorem]]**: The maximum amount of flow from $s$ to $t$ equals the minimum capacity of a cut separating $s$ and $t$.

### Implementation and Running Time

- The [[Ford-Fulkerson method]] can vary in efficiency based on how the augmenting paths are chosen.
- The running time depends critically on the method used to find augmenting paths and the capacities of the edges.

This summary outlines the foundational concepts of flow networks, the Ford-Fulkerson method for solving the maximum flow problem, and touches on the underlying theoretical principles without going into the detailed proofs. For a deeper understanding, reviewing the specific lemmas, corollaries, and theorems presented in the textbook would be beneficial.
