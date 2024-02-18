## Augmenting Paths

Given a flow network $G = (V, E)$ and a flow $f$, an **augmenting path** is a simple path from the source $s$ to the sink $t$ in the [[Residual networks|residual network]] $G_f$. The residual network represents how the flow can be adjusted on the edges of $G$ without violating capacity constraints. Each edge in an augmenting path can potentially carry more flow up to its residual capacity, $c_f(u, v)$, which is the capacity of edge $(u, v)$ minus the flow $f(u, v)$ that edge is already carrying.

### Definition

An augmenting path allows for the increase of the overall flow from $s$ to $t$ by adjusting the flows along the paths of the residual network. The path must satisfy the capacity constraint for every edge it traverses, meaning the flow increase must not exceed the edge's residual capacity.

### Residual Capacity of an Augmenting Path

The **residual capacity** of an augmenting path $p$, denoted as $c_f(p)$, is the minimum residual capacity of all edges in $p$:

$$c_f(p) = \min\{c_f(u, v) : (u, v) \text{ is in } p\}$$

This value determines how much additional flow can be pushed through the augmenting path without exceeding any edge's capacity.

### Role in Flow Augmentation

When an augmenting path is identified, the flow along this path can be increased by up to $c_f(p)$. This process adjusts the original flow $f$ to a new flow $f'$ where:

- For each edge $(u, v)$ in the path, the flow $f(u, v)$ is increased.
- If the path utilizes a reverse edge $(v, u)$ in the residual network, it signifies reducing the flow previously sent from $u$ to $v$.

### Importance

Augmenting paths are central to algorithms for finding maximum flows in networks, such as the Ford-Fulkerson method. These paths iteratively increase the flow until no more augmenting paths can be found in the residual network, at which point the flow is maximized.

Identifying and augmenting flow along these paths directly impacts the efficiency and outcome of maximum flow algorithms, highlighting their significance in solving network flow problems.
