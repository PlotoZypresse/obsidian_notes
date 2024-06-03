### Lemma 24.7
**Statement**: If the Edmonds-Karp algorithm is run on a flow network $G = (V, E)$ with source $s$ and sink $t$, then for all vertices $v \in V - \{s, t\}$, the shortest-path distance $\delta_f (s, v)$ in the residual network $G_f$ increases monotonically with each flow augmentation.

**Proof**: The proof is by contradiction.

1. **Assumption**: Suppose there exists a flow augmentation that causes the shortest-path distance from $s$ to some vertex $v \in V - \{s, t\}$ to decrease.

2. Let $f$ be the flow just before the augmentation and $f'$ be the flow just after the augmentation. Let $v$ be the vertex with the minimum $\delta_{f'} (s, v)$ whose distance was decreased by the augmentation, so that $\delta_{f'} (s, v) < \delta_f (s, v)$.

3. Let $p = s \rightsquigarrow u \rightarrow v$ be a shortest path from $s$ to $v$ in $G_{f'}$, so that $(u, v) \in E_{f'}$ and $\delta_{f'} (s, u) = \delta_{f'} (s, v) - 1$.

4. Because $v$ was chosen with the minimum decreased distance, $\delta_{f'} (s, u) \geq \delta_f (s, u)$.

5. The proof shows that $(u, v) \notin E_f$:
   - If $(u, v) \in E_f$, then by using the properties of shortest paths and the triangle inequality, we derive that:
     $$
     \delta_f (s, v) \leq \delta_f (s, u) + 1 \leq \delta_f (s, v)
     $$
	This contradicts the assumption $\delta_{f'} (s, v) < \delta_f (s, v)$.

6. Since $(u, v) \notin E_f$ but $(u, v) \in E_{f'}$, the augmentation must have increased the flow from $v$ to $u$, making $(v, u)$ part of the augmenting path.

7. This augmenting path includes a shortest path from $s$ to $u$ in $G_{f'}$, and since any subpath of a shortest path is itself a shortest path, we get:
   $$
   \delta_f (s, v) = \delta_f (s, u) - 1 \leq \delta_f (s, u) - 2
   $$
   So that:
   $$
   \delta_f (s, v) > \delta_f (s, v)
   $$
   This is a contradiction.

Thus, the assumption that there exists a vertex $v$ whose shortest-path distance decreases is incorrect. Therefore, the shortest-path distance $\delta_f (s, v)$ increases monotonically with each flow augmentation.

The proof hinges on the contradiction derived from the properties of the shortest path and the triangle inequality, demonstrating that the distance in the residual network cannot decrease during the execution of the Edmonds-Karp algorithm.