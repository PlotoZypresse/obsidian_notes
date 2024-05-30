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


### Bipartheit Matching

## Notes
![[AvanAlgoLecture1-2.pdf]]
