## Ford-Fulkerson Method

The Ford-Fulkerson method is a greedy approach used to compute the maximum flow in a flow network. It iteratively searches for augmenting paths in the residual network and increases the flow until no more augmenting paths can be found.

### Key Concepts

- **Flow network**: A directed graph $G = (V, E)$ with a source $s$, a sink $t$, and a capacity $c(u, v)$ for every edge $(u, v) \in E$.
- **[[Residual networks]]** $G_f$: For each edge, it includes a residual capacity, which is the original capacity minus the current flow. It also includes reverse edges to allow flow to be decreased along a path.
- **[[Augmenting path]]**: A path from $s$ to $t$ in the residual network $G_f$ where each edge has a positive residual capacity. Finding an augmenting path implies that the current flow is not maximum.

### Algorithm Steps

1. **Initialization**: Start with $f(u, v) = 0$ for all edges $(u, v) \in E$.
2. **Search for augmenting path**: Find a path $p$ from $s$ to $t$ in the residual network $G_f$ where each edge has a positive residual capacity.
3. **Augment flow**: Increase the flow along the augmenting path $p$ by the minimum residual capacity of the edges on $p$.
4. **Update residual network**: For each edge $(u, v)$ on the path $p$, decrease the residual capacity by the amount added to the flow and increase the residual capacity of the reverse edge $(v, u)$.
5. **Repeat**: Continue the process until no augmenting paths can be found in the residual network.

### Termination and Optimality

The Ford-Fulkerson method terminates when no augmenting paths are left in the residual network. At this point, the flow is maximized, and the value of the flow $|f|$ from $s$ to $t$ is the maximum flow through the network.

### Complexity

The time complexity of the Ford-Fulkerson method depends on how the augmenting paths are found and the magnitudes of the capacities. In the worst case, the algorithm's running time can be polynomial in $|V|$ and exponential in $|E|$, particularly if capacities are integers and the path selection is made optimally.

### Practical Considerations

- The efficiency of the Ford-Fulkerson method significantly depends on the method used to find augmenting paths. The Edmonds-Karp algorithm, an implementation of the Ford-Fulkerson method, uses BFS to find the shortest augmenting path, ensuring polynomial time complexity.
- The Ford-Fulkerson method assumes that all capacities are integers. If capacities are real numbers, the algorithm might not terminate or might not produce the correct maximum flow.

The Ford-Fulkerson method is foundational in the study of network flow problems, providing a straightforward approach to solving the maximum flow problem with the key concept of augmenting paths and residual networks.
