- CLRS Exercises 24.1-3, 24.1-4, 24.1-6, 24.1-7, 24.2-2, 24.2-4, 24.2-5.
- CLRS Problem 24.4.

![[Screenshot 2024-02-09 at 15.17.24.png]]
- Since there is no path to u there is nothing going into u. If no flow can enter u no flow can leave u so $f(v,u)=0$ and $f(u,v)=0$. if there would be an edge from u to t for example we would have a max flow of 0

![[Screenshot 2024-02-09 at 15.18.00.png]]
- 

![[Screenshot 2024-02-09 at 15.18.20.png]]
- the house is the source(s) and the school is the sink(t). Every edge cpacity is one as only one child can use one edge. If there is a max flow it has to be 2 or more

![[Screenshot 2024-02-09 at 15.18.42.png]]
- vertex capacity is the same as the amount of flow that goes into a vertex and thus also goes out of it. so using that we can transform the graph

![[Screenshot 2024-02-09 at 15.19.12.png]]
![[Screenshot 2024-02-09 at 15.46.17.png]]
- ![[IMG_74EB5AE0252E-1.jpeg]]
- $capacity=16+4+7+4=31$ capacity er hvad der teoretisk set kan sendes fra s til t så man medbergner ikke de flows der går fra t til s

![[Screenshot 2024-02-09 at 15.19.36.png]]
![[Screenshot 2024-02-09 at 15.47.14.png]]
- e is the max flow
- max cut is v3 and t in t
- in c we cancel flow in v1 to v2 and v2 to v3

![[Screenshot 2024-02-09 at 15.19.56.png]]
- if they have infinite capacity they still can only provide the flow that the edges provide after the added sink

![[Screenshot 2024-02-09 at 15.20.43.png]]
- breath first search until finding the place where we can add 1 and then go to t. one iteration of FF
- 