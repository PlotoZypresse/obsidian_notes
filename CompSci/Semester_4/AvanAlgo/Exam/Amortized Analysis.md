- [ ] Lecture: Stack, Counter, Dynamic Tables. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L06.php)

## Amortized Analysis
Amortized analysis is a technique used to average the time required to perform a sequence of data-structure operations over all the operations performed. This approach helps us ensure that the average performance of each operation is manageable, even if some individual operations may be expensive.

The key idea is that while some operations might have a high cost, most operations will be cheaper. By spreading the cost of the expensive operations over a series of cheaper ones, we can guarantee a small average cost per operation in the worst-case scenario. This way, we can provide more accurate performance guarantees for algorithms and data structures over a long sequence of operations.

### Aggregated Analysis
**Aggregate Analysis Overview:** Aggregate analysis is a method used to determine the average performance of an algorithm over a sequence of operations. Rather than analyzing the worst-case or average-case performance of a single operation, aggregate analysis looks at the total cost of a series of operations to provide a more holistic understanding of the algorithm's efficiency.

**Example Stack Operations**

Fundamental stack operations
- PUSH(S,x) pushes object x onto stack S
- POP(S) pops the top of the stack S and returns the popped object. Calling POP on an empty stack generates an error.
Each of these operations runs in O(1) time. Lets therefor consider the cost of each one to be 1. The total cost of a sequence of POP and PUSH operations is therefor n, therfor the actual running time for n operations is $\Theta(n)$.

We now create a new stack operation MULTIPOP(S,k) which removes the k top objects from the stack S. So if k for example is 5 we remove the 5 top objects from the stack. k has to be positive ofcourse.

**pseudo code MULTIPOP(S,k)**
![[Screenshot 2024-05-30 at 14.52.00.png]]

The running time of the MULTIPOP(S, k) operation, when performed on a stack containing ss objects, depends on the number of POP operations that actually take place. We can evaluate MULTIPOP by considering that each PUSH and POP operation has an abstract cost of 1.

In the context of the MULTIPOP(S, k) operation:
- s represents the number of objects currently in the stack S.
- k represents the number of objects that you want to pop from the stack.

The while loop in MULTIPOP executes a number of times equal to the smaller value between s and k (i.e., $min\{s,k\}$). Each iteration of the loop calls the POP operation once. Therefore, the total cost of the MULTIPOP operation is $min⁡\{s,k\}$, making the actual running time directly proportional to this cost.

If we look at a sequence of PUSH,POP and MULTIPOP operations on an initilly empty stack the worst case cost of MULTIPOP would be O(n) since stack size  is at most n. Thus the worst case time for any stack operation is therefor at most O(n) and hence a sequence of n operations costs $O(n^2)$. This means that if we call MULTIPOP n times we get the cost $n \times O(n) =O(n^2)$. This result is correct but because it came from considering the worst case scenario it is not a tight bound.

Aggregate analysis shows that any sequence of n PUSH, POP and MULTIPOP operations on an initially empty stack has an upper bound on its cost of O(n). This is because an object can not be popped from the stack unless it was first pushed onto it. Therefor the number of times POP can be called on a nonempty stack, including calls within MULTIPOP is at most the number of push operations which is at most n. The total cost of all operations is therfor proportional to the number of elemnts n. 

By avereging the total cost O(n) over n elements we get $O(n)/n=O(1)$. So even tho an operation like MULTIPOP seems expensive if we avereaged out over a large number of operations each operation has an average cost of $O(1)$, thus the amortized cost is $O(1)$.
### The Accounting Method
In the accounting method we assign different costs to different operations. Some operations will cost more or less than they actually cost. The amount an operation is charged is its amortized cost. When an operations amortized cost exceeds its actual cost we assign the difference to specific objects in the data structure as credit. Credit can help pay for later operations whose amortized cost is less  than their actual cost. By this we can look at the amortized cost as being split between  its actual cost and credit that is either deposited or used up. Different operations may have different amortized cost. By this, this methode differs from aggregate analysis, in which all operations have the same amortized cost.

#### How the Credit System Works:

- **Excess Amortized Cost**: When an operation's amortized cost is more than its actual cost, the difference is considered credit. This excess cost (credit) is stored and can be used later.
    
	**Example**:
    - If an operation has an actual cost of 2 units but an amortized cost of 5 units, there is an excess of 3 units. These 3 units are stored as credit.
- **Deficient Amortized Cost**: When an operation's amortized cost is less than its actual cost, the system uses previously stored credit to cover the deficit.
    
    **Example**:
    - If an operation has an actual cost of 7 units but an amortized cost of 5 units, there is a deficit of 2 units. This deficit can be covered using the stored credit.

#### Visualization:

- **Operation 1**:
    - Actual Cost = 2 units
    - Amortized Cost = 5 units
    - Credit = 3 units (stored)
- **Operation 2**:
    - Actual Cost = 7 units
    - Amortized Cost = 5 units
    - Credit Used = 2 units (from the previously stored 3 units)

#### Purpose:
The credit system allows for a more balanced and consistent cost distribution over multiple operations. Instead of each operation's cost being highly variable, the credit system smooths out the costs by allowing excess costs to cover future deficits.

The amortized cost of operations has to be choosen carfully. If we want to show that the worst case average cost per operation is small, we must ensure that the total amortized cost of a sequence  of operations provides an upper bound on the total actual cost of the sequence. It doesnt make sense that the total amortized cost is lower than the actual cost in some cases. Lets say that the actual cost for operation i is $c_i$ and the amortized cost of operation i is $\hat{c_i}$. Then we need the total amortized cost for all operations to be bigger and or equal to the actual cost
$$
\sum_{i=1}^n \hat{c_i} \ge \sum_{i=1}^n\ c_i 
$$
THe total credit stored in the datastructure is the difference between the total amortized cost and the total actual cost, or $\sum_{i=1}^n \hat{c_i} - \sum_{i=1}^n c_i$. The total credit of the data structure must be non negative at all times. If the credit becomes negative at some point we violate the formula $$
\sum_{i=1}^n \hat{c_i} \ge \sum_{i=1}^n\ c_i 
$$. In that case the amortized cost for the sequence of operations up until that time would be less theaan the actual cost incurred and the total amortized cost would not be an upper bound.

**Example Stack Operations**
To illustrate the accounting methode we return to the stack example. Recall from the previus part that the actual cost of the operations is 1 for PUSH and POP and $min\ \{s,k\}$ for MULTIPOP. where k is the argument suppliued to MULTIPOP and s the size of the stack when its called. When k(the number of items to  pop) is smaller than the stack size the cost is the number of items to pop. When the number of items to pop is bigger than the stack size we can only pop as many as there are on the stack.

Now for the accounting methode we give the PUSH operation a cost of 2 and POP and MULTIPOP a cost of zero. So when we push an item onto the stack we pay 1 for the push operation but we also already pay the 1 for when the item gets poped by POP or MULTIPOP.

Lets give an example, we have a stack of plates in the cafeteria. The price to put a plate onto the stack is 1$ and to take it of the stack its also 1$. So in the previus example we would place one dollar onto the plate when putting it onto the stack and adding another one when taking it of the stack. In this case we put 2 dollars onto the plate when pushing the plate to the stack. In this case we dont need to pay anything to take the plate of because we payed in advance or the plate has credit.
### The Potential Method
The goal of the potential method is not to represent work as credit like in the accounting method but to represent the prepaid work as potential energy, like in Physics, also just called potential. Also the potential applies to the whole data structure rather than to some operations.

The potential method works as follows. We start with the initial data structure $D_0$, then a sequence of $n$ operations occurs. For each $i=1,2,...,n$ $c_i$ is the actial cost of the i'th operation and $D_i$ is the data structure that results after applying the i'th operation to the data structure $D_{i-1}$. So for example we have an empty stack at $D_0$ and now call the PUSH operation as the first operation. After we pushed something we now have $D_1$. A **potential function $\Phi$** maps each data structure $D_i$ to a real number $\Phi (D_i)$, this is the potential associated with $D_i$. The amortized cost $\hat{c_i}$ of the i'th operation with respect to the potential function $\Phi$ is defined by 
$$
\hat{c_i}=c_i+\Phi(D_i)-\Phi(D_{i-1})
$$
This means that the amortized cost for the i'th operation is equal tothe cost of the i'th operation plus the potential  for $D_i$ minus the potential of $D_{i-1}$ or in other words the amortized cost is equal to the actual cost plus the change in potential from $D_{i-1}$ to $D_i$. From this we can conclude that the total amortized cost  of n operations is 
$$
\begin{split}
\sum_{i=1}^n\hat{c_i}=\sum_{i=1}^n(c_i+ \Phi(D_i)-\Phi(D_{i-1}))\\
=\sum_{i=1}^n c_i+\Phi(D_n)-\Phi(D_0)
\end{split}
$$
The second equation changes because the $\Phi(D_i)$ terms telescope [[Potential function telescope]] 
If we can define a potential function $\Phi$ so that the potential for $D_n$ (cost kinda) is bigger or equal to $\Phi(D_0)$ then the total amortized cost ($\sum_{i=1}^n \hat{c_i}$) gives an upper bound on the total actual cost 
($\sum_{i=1}^n c_i$). In practice we dont always know how many operations might be performed. Because of that if we require that the potential for $D_i$ is bigger or equal to the potential $D_0$ 
($\Phi(D_i) \geq \Phi(D_0)$) for all i, then we guarantee that we have paid in advance. The simplest way is usually to define $\Phi(D_0)$ to be 0 and then show that $D_i$ is bigger than 0 for all i. 

Intuitively if the potential difference $\Phi(D_i)-\Phi(D_{i-1})$ of the i'th operation is positive, then the amortized cost $\hat{c_i}$ represents an overcharge to the i'th operation and the potential of the data structure increases. If the potential difference is negative, then the amortized cost represents an undercharge to the i'th operation and the decrease in the potential pays for the actual cost of the operation.

The amortized cost depends on the choice of the potential function $\Phi$. Different potential functions may yield different amortized costs, yet still be upper bounds on the actual cost. Often there will be trade-offs when choosing a potential function and the best potential function to choose depends on the desired time bounds.

**Example stack operations**
We once again will illustrate this with the example of stack operations(PUSH, POP, MULTIPOP). We define the potential function $\Phi$ on a stack to be the number of objects on the stack. The potential of an empty stack $D_0$ is equal to 0 or $\Phi(D_0)=0$. The stack can not have a negative number of items. Because of that the stack after i iteration, so the stack $D_i$ that results after the i'th iteration has nonnegative potential and thus the potential of $D_i$ will always be bigger or equal to the potentail at $D_0$ or in math words $\Phi(D_i) \geq 0$ or $\Phi(D_i) \geq \Phi(D_0)$. The total amortized cost of n operations with respect to $\Phi$ therefor represents an upper bound on the actual cost.

Lets now compute the Amortized cost of the various stack operations. if the i'th operation on a stack containing s objects is a PUSH operation the the potential difference is 
$$
\begin{split}
\Phi(D_i)-\Phi(D_{i-1}) =(s+1)-s \\
= 1
\end{split}
$$
By equation (16.2) the amortized cost of this PUSH operation is 
$$
\begin{split}
\hat{c_i}=c_i+\Phi(D_i)-\Phi(D_{i-1})\\
= 1+1 \\
=2
\end{split}
$$
Lets now suppose that the i'th operation on the stack of s objects is MULTIPOP(S,k) which causes $k'=min\{s,k\}$ objects to be popped of the stack. The actual cost of the operation is k' and the potential difference is 
$$
\Phi(D_i)-\Phi(D_{i-1})=-k'
$$
This the amortized cost of MULTIPOP is ([[further multipop]])
$$
\begin{split}
\hat{c_i}=c_i+\Phi(D_i)-\Phi(D_{i-1})\\
=k'-k'
=0
\end{split}
$$
Similarly, the amortized cost of an ordinary POP operation is 0. 

The amortized cost of each of the  operations is O(1) and thus the total amortized cost of a sequence of n operations is O(n). Since $\Phi(D_i) \geq \Phi(D_0)$ the total amortized cost of n operations is an upper bound on the total cost. The worst case cost of n operations is therefor O(n)
### Dynamic Tables
When designing applications that use tables it is not always known in advance how many items the table will hold. We might allocate space for a table and later find out that the allocated space was not enough. The program must then reallocate the table with a larger size and copy the items from the old table to the new table. On the other hand the opposite can also become a problem. If we start with a big table and after some time only a few items are left we are using way more space than we actually need. 

We will see that the amortized cost of inserting or deleting is only O(1), even thoug the actual cost of an operation is much larger than that if an expansion or contraction is trigged. Also we will se how we can guarantee that the unused space in a dynamic table never exceeds a constant fraction of the total space.

Lets start by assuming that a dynamic table supports the operation TABLE-INSERT, TABLE-DELET. As the name suggests table insert inserts an item into the table taht then occupies a single slot. Dlete removes an item from the table and there by freeing a slot. A table also has a load factor 
$$
\alpha(T)
$$
The load factor of a nonempty table $T$ is defined as the number of items stored in the table divided by the size(number of slots) of the table. This means that an empty table has a size of 0 and a load factor of 1. If the load factor of a table is bounded below by a constant, the unused space in the table is never more than a constant fraction of the total amount of space. Here is and example
#### Explanation with an Example:
- **Suppose** the constant lower bound on the load factor is $c=0.5$.
- **If** the dynamic table has a capacity for 100 elements, then the number of elements in the table must be at least $0.5×100=50$ 
- **This implies** that the unused space can be at most 50 elements (100 total capacity - 50 elements in use).

#### Table expansion

If we insert an item into a full table the table will be expanded. This happens by allocating a new table with more slots, moving the data into the new table. A common heuristic is that the table size doubles everytime the table expands.

Below is the pseudo code for TABLE insert. The attribute $T.table$ conatins a pointer to the block of storage representing the table. $T.num$ contains the number of items in the table and $T.size$ gives the total number of slots in the table. Initially the table is empty: $T.num=T.size=0$. There are two types of insertion. One is the normal insert of one item into the table. The other is inserting all items from the old table into the new. Each insertion has a cost of one for each item that is inserted. The overhead for allocating an initial table like in line 2 is constant and the cost of freeing storage like in line 7 and 5 is dominated by the cost of transfering items in line 6. Thus the actual running time of TABLE-INSERT is linear in the number of elementary insertions. Expansion occures when lines 5-9 execute.
![[Screenshot 2024-05-31 at 19.24.24.png]]

Now we can use amortized analysis. First we need to determine the actual cost $c_i$ of the i'th operation. If the table has room its a simple insert so the cost is one. If the table is full an expansion occures then $c_i$ cost is equal to i. This is true because we need to pay one for the insertion and $i-1$ to move all the previous data into the new table. So for $n$ operations the worst case cost of an operation is O(n), which leads to an upper bound of $O(n^2)$ on the total running time for n operations. This Bound is not tight, because the table rarely expands in the course of n TABLE-INSERT operations. Specifically the i'th operation cases an expansion only when $i-1$ is an exact power of 2. The amortized cost of an operation is in fact O(1) as an aggregate analysis shows. The cost of the i'th operation is
$$
c_i =
  \begin{cases}
    i       & \quad \text{if } i-1 \text{ is an exact power of 2}\\
    1  & \quad \text{otherwise} 
  \end{cases}
$$

The total cost of n Table insert operations is bounded by 3n, the amortized cost of a single operations is at most 3

The acounting methode gives great intuiton for this. If we add an item to the table we pay 1 dollar to insert it, we pay one to move it in the future and we pay one to move one of the items already in the table. Because 
![[Screenshot 2024-05-31 at 19.47.33.png]]

Now lets look at the potential function. Just like before, just after expansion the table has no stored credit or in math word when the the number of items in the table is equal to the size of the table divided by 2 ($T.num=T.size/2$). As before when elements get inserted the potential needs to increas enough to pay for all the reinsertions that will happen when the table expands. In otehr words the potential must increase from 0 to the table size $T.size$ but this needs to happen over the course of $T.size/2$ TABLE-INSERT operations. To achive this the potential needs to increase by 
$$
\frac{T.size}{T.size/2}=2
$$
T.size will always be equal to $T.size/2*2$. When looking at the potential function below we can see that it will equal 0 immediatly after the table expands(when $T.num=T.size/2$) and it increases by 2 upon each insertion until the table fills that is when $T.num = T.size$. Then the potential function $\Phi(T)$ equals $T.size$ 
$$
\Phi(T)=2(T.num - T.size/2)
$$
To analyze the amortized cost of table operations, it is convenient to think in terms of the change in potential due to each operation. $\Phi_i$ denotes the potential after the i'th operation. We can rewrite the equation 16.2 as 
$$
\begin{split}
\hat{c_i}=c_i+\Phi_i-\Phi_{i-1}\\
=c_i+\Delta\Phi_i
\end{split}
$$
where Delta Phi is the change in potential due to the ith operation. Lets first consider the case where the i'th insertion does not cause the table to expand. In this case $\Delta\Phi_i$ is 2 and the actual cost $c_i$ is 1 the amortized cost is 3
![[Screenshot 2024-05-31 at 20.04.31.png]]
Lets now consider the change in potential when the table does expand during the ith insertion. 

1. **Definitions**:
   - $\text{num}_i$: Number of items stored in the table after the $ i $th operation.
   - $\text{size}_i$: Total size of the table after the $ i $th operation.
   - $\Phi_i$: Potential function representing the extra cost associated with the state of the table.

2. **State Before $i$th Insertion**:
   - Just before the $i$th insertion, the table is full. This means $\text{size}_{i-1} = \text{num}_{i-1} = i - 1$.
   - The potential function just before the expansion is given by:
 $$
     \Phi_{i-1} = 2(\text{size}_{i-1} - \text{size}_{i-1}/2) = 2((i - 1) - (i - 1)/2) = 2(i - 1)/2 = i - 1.
     $$

3. **State After Expansion**:
   - After the expansion, the table's size doubles, and the potential function drops to 0 because the table is now half-empty.
   - After inserting the new item, the potential increases to:
     $$
     \Phi_i = 2 \text{ (since only one slot is filled out of the expanded table)}
     $$

4. **Change in Potential**:
   - The change in potential when the $i$th insertion causes an expansion is:
     $$
     \Delta \Phi_i = \Phi_i - \Phi_{i-1} = 2 - (i - 1) = 3 - i.
     $$

5. **Cost of $i$th Insertion with Expansion**:
   - The actual cost $c_i$ of the $i$th insertion that triggers an expansion includes re-inserting $i - 1$ items plus inserting the new item, so $c_i = i$.

6. **Amortized Cost Calculation**:
   - The amortized cost $\hat{c}_i$ is the actual cost plus the change in potential:
     $$
     \hat{c}_i = c_i + \Delta \Phi_i = i + (3 - i) = 3.
     $$

**Conclusion**: The amortized cost of an insertion operation, even when it triggers an expansion, is constant and equal to 3. This analysis shows that while individual operations may have varying actual costs, the amortized cost remains consistent, providing a clear measure of performance over a sequence of operations.

**Table delete**
To implement table delete it is simple as simple as to remove a specific item from the table. But now we have a new problem. When removing items from the table we get a lot of unused space. This leads to the desire to shrink the table when the load factor becomes to samll. So we do the opposite of a table expansion and move the items of the larger table to a bigger one.

In order to not waste space and yet keep amortized cost low the insertion and deletion procedures should preserve two properties.
- the load factor of the dynamic table is bounded below by a positive constant aswell as above by 1
- the amortized cost of a table operation is bounded above by a constant
The actual cost of each operation equals the number of elementary insertions or deletions.

When thinking about table shrinkage the first method that probably comes to mind is. Doing the opposite to when we expand the table and shrink it by halving its size when the table is less than halft full. This would guarantee that the load factor never drops below 1/2, but it alsow causes the amortized cost to become quite large. Think about the case where we meet the threshold and expand the table. But then we delete 2 items again and the table shrinks. then we add two items again and the table expands again. The problem with this is that after the table expands not enough deletions occur to pay for a contraction. Also not enough insertions have taken place to pay for an expansion.

So how do we fix this problem? To fix it we need to let the load factor of the table to drop below 1/2. More specific we continue to double the table size upon inserting an item into a full Table but we only halve the table size when deleting an item causes the table to become less than 1/4 full, rather than 1/2 full as before. The load factor of the table is thus bounded below by the constant 1/4 and the load factor is imediatly 1/2 after contraction.

An expansion and contraction should exhaust the table potential so that the potential is 0 after expansion or contraction when the load factor is 1/2
![[Screenshot 2024-06-01 at 16.42.29.png]]

When the load factor of the table is atleast 1/2 we use the potential function from before, that we used for insertion. So when the table if at least half full each insertion increases teh potential by 2 if the table does not expand and each deletion reduces the potential by 2 if it does not cause the load factor to drop below 1/2
$$
\Phi(T)=2(T.num - T.size/2)
$$
But what about when the loadfactor is under 12, that is when $1/4 \leq \alpha(T) < 1/2$? as before when $\alpha(T)=1/2$ so that the table is half full $T.num=T.size/2$ the potential should be 0
Certainly, here’s the formatted explanation:

#### Explanation of the Potential Function for Insertions and Deletions When ($\alpha(T) < 1/2$a)

When the load factor \($\alpha(T) < 1/2$), the behavior of the potential function and its adjustments for insertions and deletions need to be defined in a way that ensures constant amortized time.

#### Potential Function for Load Factor Between 1/4 and 1/2:

For \( $\frac{1}{4} \leq \alpha(T) < \frac{1}{2}$ \), the potential function is defined as:
$$
\Phi(T) = \frac{T.\text{size}}{2} - T.\text{num}
$$

This potential function reflects the difference between half the table size and the number of elements.

#### Effect of TABLE-INSERT When \($\alpha(T) < 1/2$\):

When \($\alpha(T) < 1/2$\), each call of TABLE-INSERT should decrease the potential by 1. This means that every insertion operation reduces the potential function value by 1.

#### Effect of TABLE-DELETE When \($\alpha(T) < 1/2$\):

Similarly, each call of TABLE-DELETE should increase the potential by 1 until the table contracts. This ensures that the potential accumulates enough to cover the cost of resizing operations when the load factor decreases sufficiently to trigger a contraction.

#### Why These Adjustments Work:

**Insertions Decrease Potential:**

When the load factor is less than 1/2, the table is less than half full, and the cost of insertion is relatively low because there is ample space. By decreasing the potential by 1 for each insertion, we ensure that the amortized cost remains constant because we are essentially borrowing against the future cost of maintaining or expanding the table.

**Deletions Increase Potential:**

Conversely, deletions in a table that is less than half full potentially bring us closer to the point where the table needs to contract. By increasing the potential by 1 for each deletion, we are accumulating a buffer (or credit) that will be used to pay for the cost of resizing when the table eventually needs to contract. This mechanism ensures that the cost of the resizing operation is distributed over many deletion operations, keeping the amortized cost constant.

#### Summary:
The potential function and its adjustments for insertions and deletions are designed to ensure that the amortized cost of these operations remains constant, regardless of the actual load factor of the table. By carefully managing the potential function, we can balance the costs of table expansions and contractions over a series of operations, providing efficient performance for dynamic resizing scenarios in hash tables.

Putting all this together we get this
$$
f(n) =
  \begin{cases}
    2(T.num-T.size/2)       & \quad \text{if } \alpha(T) \geq 1/2\\
	T.size/2-T.num & \quad \text{if } \alpha(T)<1/2
  \end{cases}
$$
The potential of an empty table is 0 and the potential is never negative. Thus the total amortized cost of a sequence of operations with respect to $\Phi$ provides an upper bound on the actual cost of the sequence of insertions and deletions.

Lets now determine the amortized cost of each operation. As before $num_i$ denotes the number of items in the table after i iterations, $size_i$ denotes the total size of the table after the i'th operation, $\alpha_i=num_i/size_i$ denotes the load factor after the ith operation. $\Phi_i$ denotes the potential after the ith operation, and $\Delta\Phi_i$ denotes the change in potential due to the ith operation. Initially, $num_0=0$, $size_0=0$, and $\Phi_0=0$. 

The cases where the table does not contract or expand and the load factor does not cross $\alpha=1/2$ are straightforward. So if $\alpha_{i-1} \geq 1/2$ and the ith operation is an insertion that does not cause the table to expand, then $\Delta\Phi_i=2$. Likwise if the ith operation is a deletion and $\alpha_i \geq 1/2$ then $\Delta\Phi_i=-2$. Furthermore if $\alpha_{i-1}<1/2$ and the ith operation is a deletion that does not trigger a contraction then $\Delta\Phi_i=1$, and if the ith operation is an insertion an $\alpha_i<1/2$, then $\Delta\Phi=-1$. In other words if no expansion or contraction occurs and the load factor does not cross $\alpha=1/2$, then
- if the load factor stays at or above 1/2, then the potential increases by 2 for an insertion and decreases by 2 for a deletion
- if the load factor stays below 1/2, then the potential increases by 1 for a deletion and decreases by 1 for an insertion.
In each of these cases the actial cost $c_i$ of the i'th operation is just 1 and so
- if the i'th operation is an insertion its amortized cost $\hat{c_i}$ is $c_i+\Delta\Phi_i$ which is $1+2=3$ if the load factor stays at or above 1/2 and $1+(-1)=0$ if the laod factor stays below 1/2
- if the i'th operation is a deletion, its amortized cost $\hat{c_i}$ is $c_i=\Delta\Phi_i$, which is $1+(-2)=-1$ if the load factor stays at or above 1/2 and $1+1=2 of the load factor stays below 1/2

But we are still missing four cases:
- an insertion that takes the load factor from below 1/2 to 1/2
- a deletion that takes the load factor from 1/2 to below 1/2
- a deletion that causes the table to contract
- an insertion that causes the table to expand
	- This was analysed before to have amortized cost of 3

When the ith operation is a delition that causes the table to contract we have $num_{i-1}=size_{i-1}/4$ before the contraction, then the item is deleted, and finally $num_i=size_i/2-1$ after the contraction. Thus by equation 16.5 we have
![[Screenshot 2024-06-01 at 21.16.23.png]]
which also equals the actual cost $c_i$ of deleting one item and copying $size_{i-1}/4-1$ items into the new samller table. Since $num_i=size_i/2-1$ after the operation has completed, $\alpha<1/2$ and so
![[Screenshot 2024-06-01 at 21.18.55.png]]
giving $\Delta\Phi_i=1-size_i-1/4$. Therefor, when the ith operation is a deletion that triggers a contraction, its amortized cost is
![[Screenshot 2024-06-01 at 21.21.07.png]]

Finally we handle the cases where the load factor fits one case of equation 16.5 before the operation and the other case afterwards.  Lets start with deletion, we hace $num_{i-1}=size_{i-1}/2$ so that $\alpha_{i-1}=1/2$ beforehand and $num_{i}=size_{i}/2-1$ so that  $\alpha_{i}<1/2$. Because  $\alpha_{i-1}=1/2$ we have $\Phi_{i-1}=0$ and because $\alpha_i<1/2$, we have $\Phi_i=size_i/2-num_i=1$. Thus we get that $\Delta\Phi_i=1/0=1$/ SInce the ith operation is a deletion that does not cause a contraction the actual cost $c_i$ equals 1, and the amortized cost $\hat{c_i}$ is $c_i+\Delta\Phi=1+1=2$. 

Conversley, if the i'th operation is an insertion that takes the load factor from below 1/2 to equalling 1/2 the change in potential $\Delta\Phi_i$ equals -1. Again the actual cost $c_i$ is 1, and now the amortized cost $\hat{c_i}$ is $c_i+\Delta\Phi_i=1+(-1)=0$.

In summary since the amortized cost of each operation is bounded above by a constant the actual time for any sequence of n operations on a dynammic table is O(n).
### Notes

Notes
![[AvanAlgoLecture6.pdf]]

### Plan
Understood. Here’s a revised plan that includes a brief overview of the accounting method and aggregate analysis, focusing mainly on dynamic tables and the potential method.

### Slide 1: Introduction (1 minute)
- **Title Slide**: "Amortized Analysis: Dynamic Tables and the Potential Method"
- **Objective**: Briefly introduce the topic and mention the main points: definition, overview of methods, and focus on dynamic tables and the potential method.

### Slide 2: What is Amortized Analysis? (1 minute)
- **Definition**: 
  - Explain that amortized analysis averages the time required for a sequence of operations to provide more accurate performance guarantees.

### Slide 3: Key Idea (1 minute)
- **Concept**: 
  - Explain that expensive operations are spread over many cheap ones to achieve a small average cost per operation.

### Slide 4: Overview of Methods (1 minute)
- **Aggregate Analysis**: 
  - Explain briefly that it looks at the total cost of a series of operations to provide an average cost.
- **Accounting Method**: 
  - Introduce the concept of assigning different costs to different operations and using credits to balance the cost.

### Slide 5: The Potential Method (1.5 minutes)
- **Overview**:
  - Introduce the potential method and how it represents prepaid work as potential energy.
  - Explain that potential applies to the whole data structure.

### Slide 6: Potential Method Calculation (2 minutes)
- **Calculation**:
  - Define the potential function for operations.
  - Explain how the amortized cost is calculated using the potential method.

### Slide 7: Dynamic Tables (1.5 minutes)
- **Introduction**:
  - Explain the problem of unknown table sizes in advance and the need for resizing.
  - Mention that the amortized cost of operations in dynamic tables is O(1).

### Slide 8: Table Expansion (2 minutes)
- **Explanation**:
  - Describe the TABLE-INSERT operation and the cost associated with expanding the table.
  - Use pseudo code to illustrate the process.
  - Explain how the potential method ensures an amortized cost of O(1).

### Slide 9: Table Contraction Strategy (2 minutes)
- **Load Factor**:
  - Explain the strategy to manage space and cost by allowing the load factor to drop below 1/2.
  - Describe how to manage the load factor to ensure efficient performance using the potential method.

### Slide 10: Summary (1 minute)
- **Recap**:
  - Summarize the key points: what amortized analysis is, brief overview of methods (aggregate, accounting), and focus on the potential method and its application to dynamic tables.
  - Emphasize the importance of amortized analysis in providing performance guarantees for data structures and algorithms.

### Slide 11: Q&A (1 minute)
- **Questions**:
  - Invite questions from the audience to clarify any doubts or provide further explanations.

This plan provides a concise yet comprehensive presentation within the 10-12 minute timeframe, with a focus on dynamic tables and the potential method, while briefly covering other methods.