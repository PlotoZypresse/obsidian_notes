- [ ] Lecture: Network Flows [Source](https://imada.sdu.dk/u/kslarsen/dm582/L01.php)
- [ ] Lecture: Flows: Edmonds-Karp and Examples. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L02.php) 


# Network Flows
A flow network is a directed graph that can be used for material flows for example fluids through pipes or electrical current. Each edge has a capacity that can be interpreted as the maximum flow rate.

A flow network ($G=(V,E)$), where $V$ are the verticies and $E$ are the edges, is a directerd graph where each edge($E$)  $(u,v)\in E$ (read as edge from u to v that is in E) has a capacity that is non negative. $c(u,v)$ (read as capacity of edge from u to v). Also if there is an edge from $(u,v)$ then there is not an edge from $(v,u$). if an edge is not in in E its capacity is 0 ($(u,v) \notin E$ then $c(u,v)=0$). Self loops are forbidden. Each flow network has a source(s) and a sink(t). Which are the "origin" and "finish".

We assume that each vertex($v \in V$) lies on a path from the source to the sink. THis means that for each vertex($v \in V$) the flow network contains a path $s->v->t$. Becauso of that each vertex expect from s has atleast one entering edge giving us $|E| \geq |V|-1$. This means that the number of edges is bigger or equal to the number of verticies minus 1.

A flow in a network is a realvalued function. 

**Capacity constraint:**
The flow from one vertex to another can not be negative and can not exceed the given capacity.
For all $u,v \in V$ we require $0\geq f(u,v) \geq c(u,v)$. f is the flow and c the capacity from u to v 

**Flow conservation:**
For all verticies that are not the source or the sink, the flow into the vertex must be equal to the flow out of the vertex. What goes in goes out
For all u in V excluding the sink and the source $u \in V - {s,t}$ we require:
$$\sum_{\substack{v \in V}} f(v,u) = \sum_{\substack{v \in V}} f(u,v)$$
This means that the sum of flow going into vertex u is equal to the sum of the flow going out.

If an there is no edge from u to v there can be no flow from u to v. 
$$|f|=\sum_{\substack{v \in V}} f(s,v) - \sum_{\substack{v \in V}} f(v,s)$$
This is the flow out of the source minus the flow into the source. Normally there would be no flow into the source. This is important for residiual networks later.

**Anitparellel edges**
If a flow network has antiparallel edges we can circumvent this problem by adding another edges to the flow network(Example)

**Multiple sources and sinks**
If a network has multiple sources and/or sinks we can solve this problem buy adding a super source or sink that has an arbitrary large flow to the other sources or sinks. This results in one sink(implement in example)

**Example of flow network for blackboard**

## Maximum Flow

### Ford-Fulkerson
The Ford-Fulkerson methode is a methode to solve the maximum flow probelm. The methode finds the maxium flow in a flow network. This is done buy giving each edge an initial flow of 0. Then we find an augmenting path in the residual network of the graph. The edges of the augmenting path in the residual network indicate on which edges in the real network get an updated flow value. Each iteration updates the flow. The flow on any particular edge in G may increase or decrease. The methode repeatedly augments the flow until the residual network has has no more augmenting paths
#### Risidual Networks
The residual network Gf of network G with flow f represents how the flow can change. If the edge from u to v has a capacity of 12 and a flow of 7 the edge from u to v in the residual network has a value of 5 as this is the value of the possible flow. In residual networks there are also. Only edges that can admit more flow are part of the residual network Gf. an edges with capacity 5 and flow 5 has maxed out its capcity and is thus not part of the residual network. For the algorithm to work the residual network also has edges that are not in G. Sometimes we need to decrease the flow from one edge to another to increase the overall flow of the network. For this the residual network will have an edge from v to u( opposite direction from u to v). This edge can atmost cancel out the flow from u to c. So in the example earlier the residual capacity of v to u would be 7. These 7 cancel out the 7 flow that are sent from u to v by sending the same flow bakc(fromc v to u)(show with exaple)

Residual Capacity is defeined by 
$$ 
c_f(u,v) =
\begin{cases}
	c(u,v)-f(u,v)       & \quad \text{if } (u,v) \in E,\\
	f(v,u)              & \quad \text{if } (v,u) \in E,\\
	0                   & \text{otherwise}
\end{cases}
  $$
This means for example that the residual capcity($c_f$), if $c(u,v)=16$ (the capacity from u to v is 16) and the flow is $f(u,v)=11$, is equal to 5(using line one). 

The residual network is technicaly not a flow network but because the only difference are the anitparallel edges we can use the residual network to "map" the flow onto the original network. So if f is a flow in the "original network" G and f' is a flow in the corresponding residual network Gf. The augmentation(addition or increased) of the flow f by f' is ($f\uparrow f'$)
$$
f\uparrow f'(u,v) =
\begin{cases}
	f(u,v)+f'(u,v)-f'(v,u)       & \quad \text{if } (u,v) \in E,\\
	0                   & \text{otherwise}
\end{cases}
$$
This makes intuitive sense if we add f'(u,v) to f(u,v) the flow increases by f'(u,v) but because we have the back edge the flow also decreses by f'(v,u).

**Capcity constraint**
Flow augmentation obeys the capacity constraint. We do not add any flow that is not already in the flow network. When augmenting a path we either send everything from u to v and thereby keeping the capacity constraint or we "split it" by sending something from u to v and something from v to u.

**Flow conservation**
The sum of all flow augmentations going into v and out of v gives us the total flow of that augmentation.
$$
\begin{equation*}
\begin{split}
\sum_{\substack{v \in V}}(f \uparrow f')(u,v)-\sum_{\substack{v \in V}}(f \uparrow f')(v,u)\\
= \sum_{\substack{v \in V}}f(u,v)-\sum_{\substack{v \in V}}f(v,u) + \sum_{\substack{v \in V}}f'(u,v)-\sum_{\substack{v \in V}}f'(v,u)\\
\end{split}
\end{equation*}
$$
So the sum of all flow augmentations into v minus all the flow augmentations out from v is equal to the the value of the flow f plus the value of the flow f'. To show that the value of the flow augemntation is equal to the value of the flow f plus the value of the flow f' and thus showing that the flow conservation holds(below u=s)


$$
\begin{equation*}
\begin{split}
|f \uparrow f'| = \sum_{\substack{v \in V}}(f \uparrow f')(s,v)-\sum_{\substack{v \in V}}(f \uparrow f')(v,s)\\
= \sum_{\substack{v \in V}}f(s,v)-\sum_{\substack{v \in V}}f(v,s) + \sum_{\substack{v \in V}}f'(s,v)-\sum_{\substack{v \in V}}f'(v,s)\\
= |f|+|f'|
\end{split}
\end{equation*}
$$
As we can see $|f\uparrow f'|$ is equal to $|f|+|f'|$ . Writing out the equation to calculate the value of the flow augmentation we can see that $|f\uparrow f'|$ is equal to $|f|+|f'|$ 
#### Augmenting Paths
In a flow network $G=(V,E)$ and a flow f an augmenting path is  path from s to t in the residual newtork $G_f$ . The flow on and edge (u,v) of an augmenting path may increase by up to $c_f(u,v)$ without violating the capacity conatraint. 
#### Cuts of flow Networks
The Ford-Fulkersen methode repeatedly augments  the flow along augmenting paths. The Max-Flow Min-Cut theorem Tells us that a flow is maximum if and  only if its residual network contains no augmenting path. Lets start with some basic definitions before proving the Max Flow min cut theorem.

A $cut(S,T)$ of a flow network $G=(V,E)$ is a partition of V into S and $T=V-S$ such that $s \in S$ and $t \in T$. If f is a flow then the $net\ flow\ f(S,T)$ across the cut (S,T) is defined as 
$$
f(S,T) = \sum_{\substack{u\in S}}\sum_{\substack{v\in T}}f(u,v)- \sum_{\substack{u\in S}}\sum_{\substack{v\in T}}f(v,u)
$$
So the net flow of the cut is the flow from the s side to the t side minus the flow from the t side to the s side.

The capacity of the cut is only counting the edges that go from the source side to the sink side of the cut
$$
c(S,T)=\sum_{\substack{u\in S}}\sum_{\substack{v\in T}}c(u,v)
$$
A minimum cut is, as the name implies the cut whose capacity is the minimum over all cuts of the the network

For a given flow f, the net flow across a cut is equal to the value of the flow $|f|$

The value of any flow f in a flow network G is bounded from above by the capacity of any cut of G
### Max Flow min cut Theorem
If f is a flow iln a dlow network $G=(V,E)$ with source s and sink t, then the following conditions are equivalent:

1. f is a maximum flow in G
2. The residual network for Gf contains no augmenting paths.
3. $|f|=c(S,T)$ for some cut (S,T) of G

Lets suppose for the sake of contradiction that f is a maximum flow in G but that Gf has an augmenting path p. This would mean that the maximum flow found in G is not a maximum flow as we can augment the flow f.
Lets now suppose that  Gf has no augmenting path meaning there is no path from s to t. S is the set of verticies reacheable from s in Gf and $T=V-S$(T are all the verticies V that are not in S). This means that T contains all the verticies that are not reachable from s and S contains all the verticies reachable from s. The partion (S,T) forms a cut and  $s \in S$ and $t \notin S$. 

A pair of verticies $u \in S$ and $v \in T$. If $(u,v) \in E$ we must have $f(u,v) = c(u,v)$, meaning that for the edge not to be in Gf the flow across the adge must be equal to its capacity as only then it is not respected in Gf. 

if $(v,u)∈E$, then $f(v,u)=0$ because if there were positive flow $f(v,u)$, the residual capacity $cf(u,v)$ would be positive and $(u,v)$ would exist in Gf. This would make v reachable from s, contradicting $v∈T$. This means that if the reverse from (u,v), so (v,u) is in the set of edges E then the flow from (v,u) has to be 0. Because if there was positive flow the residual capacity would be positive and thus (v,u) would exist in Gf. THis in turn would make is so that v is reachable from s contradicting our hypothisis that this is not possible

So for our asumption to hold true (u,v) is either fully saturated or the flow over the edge is 0
This concludes that the flow across the cut is equal to the capacity of the cut

If we now assume that the flow value $|f|$ is equal to the capacity of the cut (S,T) $c_f=(S,T)$
By collary 24.5 $|f| \leq c(S,T)$ for all cuts (S,T)
![[Screenshot 2024-05-28 at 17.20.55.png]]
and because We know from the previus step that the flow across the cut is equal to the capacity of the cut the flow must be a max flow because it is bounded by the capacity of the cut.

### Basic Ford-Fulkerson Algorithm
The flow is initialized to zero. While there exists and  augmenting path p we augment the flow in the residual graph and we update the real Graph. If there are no more augmenting paths we have found the maximum flow

By using deapth first search the algorithm will run in polynomial time. 
For a worst case approach we can look at the maximum flow(f*) of the flow network. To update the flow we execute the while loop atlest $|f*|$ times since the flow will increase with at least one each iteration

A good implementation, with a good datastructure, would have a running time of $O(E*|f*|)$ .
This is the case if the graph is representet with a datastructure that makes it possible to find a path in the resdiual network in linear time $O(V+E') = E$.

![[Screenshot 2024-05-28 at 20.47.24.png]]
### Edmonds-Karp
By using Breadht first search to find an augemnting path in the residual network the algorithm runs in polynomial time and is independent of the maximum flow value. The running time is thus $O(VE^2)$ 
To prove this the analysis relies on the distances to verticies in the residual networ $G_f$.
$\delta_f(u,v)$ denotes the shortest path from u to v in $G_f$ and each edge has unit distance.

#### Analysis
Sure, let's combine the intuitive explanation with the mathematical notation.

#### Lemma 24.7
**Statement**: If the Edmonds-Karp algorithm is run on a flow network $G = (V, E)$ with source $s$ and sink $t$, then for all vertices $v \in V - \{s, t\}$, the shortest-path distance $\delta_f (s, v)$ in the residual network $G_f$ increases monotonically with each flow augmentation.

#### Proof
The proof uses a "proof by contradiction" approach.

1. **Assumption**: Suppose there exists a flow augmentation that causes the shortest-path distance from $s$ to some vertex $v \in V - \{s, t\}$ to decrease. 

2. Let $f$ be the flow just before this augmentation and $f'$ be the flow just afterward. Let $v$ be the vertex with the minimum $\delta_{f'}(s, v)$ whose distance was decreased by the augmentation, so that $\delta_{f'} (s, v) < \delta_f (s, v)$.

3. Let $p = s \rightsquigarrow u \rightarrow v$ be a shortest path from $s$ to $v$ in $G_{f'}$, so that $(u, v) \in E_{f'}$ and
   $$
   \delta_{f'} (s, u) = \delta_{f'} (s, v) - 1.
   $$

4. Because $v$ was chosen with the minimum decreased distance, we know that the distance of vertex $u$ from the source $s$ did not decrease, that is,
   $$
   \delta_{f'} (s, u) \geq \delta_f (s, u).
   $$

5. We claim that $(u, v) \notin E_f$. Why? If we have $(u, v) \in E_f$, then we also have
   $$
   \begin{split}
   \delta_f (s, v) \leq \delta_f (s, u) + 1 \quad \text{(by Lemma 22.10, the triangle inequality)} \\
   \leq \delta_f (s, u) + 1 \quad \text{(by inequality (24.12))} \\
   = \delta_f (s, v) \quad \text{(by equation (24.11))},
   \end{split}
   $$
   which contradicts our assumption that $\delta_{f'} (s, v) < \delta_f (s, v)$.

6. **Flow Augmentation Effects**: How can we have $(u, v) \notin E_f$ and $(u, v) \in E_{f'}$? The augmentation must have increased the flow from $v$ to $u$, so that edge $(v, u)$ was in the augmenting path. The augmenting path was a shortest path from $s$ to $t$ in $G_f$, and since any subpath of a shortest path is itself a shortest path, this augmenting path includes a shortest path from $s$ to $u$ in $G_f$ that has $(v, u)$ as its last edge. Therefore,
   $$
   \begin{split}
   \delta_f (s, v) = \delta_f (s, u) - 1 \\
   \leq \delta_f (s, u) - 1 \quad \text{(by inequality (24.12))} \\
   = \delta_f (s, v) - 2 \quad \text{(by equation (24.11))},
   \end{split}
   $$
   
   so that $\delta_f (s, v) > \delta_f (s, v)$, contradicting our assumption that $\delta_{f'} (s, v) < \delta_f (s, v)$.

7. **Conclusion**: We conclude that our assumption that such a vertex $v$ exists is incorrect.

Thus, the shortest-path distance $\delta_f (s, v)$ in the residual network $G_f$ increases monotonically with each flow augmentation.

### Bipartite Matching

**Definition:**
Bipartite matching is a problem where we aim to find the maximum matching in a bipartite graph. A bipartite graph is a graph whose vertices can be divided into two disjoint sets $U$ and $V$ such that every edge connects a vertex in $U$ to a vertex in $V$. There are no edges between vertices within the same set.

**Application:**
Bipartite matching has applications in various fields, such as job assignments (matching applicants to jobs), network switching, and pairing problems in markets or networks.

**Maximum Bipartite Matching:**
The goal is to find the largest possible set of edges such that no two edges share a vertex. This set is called a maximum matching.

**Reduction to Flow Network:**
Bipartite matching can be solved using network flow algorithms by transforming the bipartite graph into a flow network:
1. **Construct the Flow Network:**
   - Add a source vertex $s$.
   - Add a sink vertex $t$.
   - Connect the source $s$ to each vertex in set $U$ with an edge of capacity 1.
   - Connect each vertex in set $V$ to the sink $t$ with an edge of capacity 1.
   - For each edge $(u, v)$ in the bipartite graph (where $u \in U$ and $v \in V$), add an edge with capacity 1.

2. **Apply Maximum Flow Algorithm:**
   - Use the Ford-Fulkerson or Edmonds-Karp algorithm to find the maximum flow from $s$ to $t$ in the constructed flow network.

3. **Interpret the Flow:**
   - The maximum flow value will correspond to the size of the maximum matching in the bipartite graph.
   - The edges that carry flow in the resulting flow network correspond to the matched pairs in the bipartite graph.

**Example:**
Consider a bipartite graph with sets $U = \{A, B, C\}$ and $V = \{1, 2, 3\}$ and edges $\{(A,1), (A,2), (B,2), (C,2), (C,3)\}$.
1. **Construct the Flow Network:**
   - Add edges from $s$ to $A$, $B$, and $C$ with capacity 1.
   - Add edges from $1$, $2$, and $3$ to $t$ with capacity 1.
   - Add edges $(A,1)$, $(A,2)$, $(B,2)$, $(C,2)$, and $(C,3)$ with capacity 1.

2. **Apply Maximum Flow Algorithm:**
   - Find the maximum flow from $s$ to $t$.

3. **Interpret the Flow:**
   - The maximum flow value (e.g., 3) indicates the maximum number of matches.
   - The edges carrying flow from $U$ to $V$ (e.g., $(A,1)$, $(B,2)$, $(C,3)$) represent the matched pairs.

By transforming the bipartite matching problem into a maximum flow problem, we can leverage efficient flow algorithms to solve it. This approach ensures that we find the maximum number of matches in the bipartite graph.
## Notes
![[AvanAlgoLecture1-2.pdf]]


## Plan

Here's the outline formatted with inline and block math for easy copying into Obsidian:

### Introduction (1 minute)
1. **Definition of Flow Networks**
   - Directed graph for material flows (e.g., fluids, electrical current)
   - Source ($s$) and sink ($t$)

### Flow Network Fundamentals (2 minutes)
2. **Basic Components**
   - Vertices ($V$) and Edges ($E$)
   - Capacities $c(u,v)$

3. **Properties**
   - Flow conservation: $\sum_{v \in V} f(v,u) = \sum_{v \in V} f(u,v)$ for $u \neq s,t$
   - Capacity constraint: $0 \leq f(u,v) \leq c(u,v)$

### Maximum Flow Problem (1 minute)
4. **Objective**
   - Maximizing flow from source to sink

### Ford-Fulkerson Method (3 minutes)
5. **Overview**
   - Initial flow set to zero
   - Finding augmenting paths in the residual network
   - Updating flow values iteratively

6. **Residual Networks**
   - Definition and significance
   - Residual capacity $c_f(u,v)$

### Key Concepts (2 minutes)
7. **Flow Augmentation**
   - Updating flow with augmenting paths
   - Ensuring capacity constraints and flow conservation

8. **Cuts in Flow Networks**
   - Definition of a cut ($S, T$)
   - Max-Flow Min-Cut Theorem: A flow is maximum if and only if no augmenting paths exist in the residual network

### Algorithms (2 minutes)
9. **Edmonds-Karp Algorithm**
   - Uses breadth-first search for finding augmenting paths
   - Runtime: $O(VE^2)$

### Applications (1 minute)
10. **Bipartite Matching**
    - Example of practical use of flow networks

### Conclusion (1 minute)
11. **Summary**
    - Key points: flow networks, Ford-Fulkerson method, residual networks, and Max-Flow Min-Cut Theorem
    - Importance in various fields

### Additional Tips:
- Use one or two diagrams to illustrate key concepts like flow networks and residual networks.
- Practice to ensure you can cover each section within the allocated time.
- Be prepared to elaborate on any section if asked for more detail.