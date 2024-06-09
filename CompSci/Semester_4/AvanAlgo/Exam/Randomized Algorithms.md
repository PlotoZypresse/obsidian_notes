- [ ] Lecture: Contention Resolution, Global Minimum Cut.  [Source](https://imada.sdu.dk/u/kslarsen/dm582/L03.php)
- [ ] Lecture: Waiting Times, MAX 3-SAT Approximation. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L04.php)
- [ ] Lecture: Quicksort and Selection. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L05.php)

## Contention Resolution

### The problem

### The algorithm

### Algorithm Analysis


## Global Minimum Cut

### The problem

### The Algorithm

### Algorithm Analysis


## Random Variables and their Expectation

### Example Waiting for first success

### Linearity of  Expectation

### Example Guessing Cards

### Example Collecting Coupons

### Conditional Expectation


## MAX 3-SAT Approximation

### The Problem

### The algorithm

### Algorithm analysis


## Randomized Quicksort and Selection
Randomized algortihms are as the name implies algorithms that utilize randomnes.
There are subcategories for these algorithms. We have
- Las Vegas algorithms: These algorithms always give the right result or give an error. But run in expected time.
- Monte Carlo algorithms: These algorithms run have controllable run time, but the drawback is that the result only has a certain probability to be correct.
there are also some other "sub categories" like atlantic city

### The Algorithm
#### Quicksort 
Randomized quicksort is a Las Vegas algorithm as the the result always is correct. A not correct result in a sorting algorithm might not be a good idea. The random version of quicksort is not that much different than the normal version of the algorithm. In a simple version of quick sort one would choose the pivot element as the last element in the array. In the random version we choose a random element as the pivot element. So every element in the array has the same probability to be choosen as the pivot element. After one element is choosen its swapped with the last element in the array and we run the normal quick sort algorithm.
#### Selection in expected linear time


### Analysis
#### Quicksort
The worst case running time for the non random quicksort is $O(n)$. THe expected running time for randomized quicksort is $O(n lg n)$. This is because if in every level of the recursion the split induced by randomized-partition puts any constant fraction of the elements on one side of the partition then the recursion tree has depth $\Theta(lg n)$ and O(n) work is performed at each level

The differnce between randomized and normal quick sort is only the randomized partition. We can therefor analyze it by considering the quicksort and partition procedures, But ofcourse with the assumption that the pivot elements are selceted randomly from the array.

Lets start with Lemma 7.1
The running time of Quicksort on an n-element array is O(n+X), where X  is the number of element comparisons performed.

Lemma 7.2
During RQS on an array of n distinct elements $z_1<z_2<....<z_n$ an element $z_i$ is compared with an element $z_j$ where i is smaller than j. if and only if one of them is chosen as a pivot before any otehr element in the set $Z_{ji}$ and no two elements are compared twice

Lemma 7.3
consider an execution of RQS on an array of n distinct elements $z_1<z_2<....<z_n$. GIven two arbitray elements $z_i$ and $z_j$ where $i<j$ the probability that they are compared is $2/(j-i+1)$.


**Proof** 
Lets proof that the expected running time of RQS is O(n log n)
We let n distinct elements be $z_1<z_2<....<z_n$ and for $1 \leq i <j \leq n$, We define the indicator random variable $X_{ij}=I \{z_i\ is\ compared\ with\ z_j\}$ from lemma 7.2 we know each pair is compared at most once so we can express X as follows:
$$
X = \sum_{i=1}^{n-1}\sum_{j=i+1}^{n}=X_{ij}
$$
By taking expectations of both sides and using linearity of expectation we obtain
$$
\begin{split}
E[X]=E[\sum_{i=1}^{n-1}\sum_{j=i+1}^nX_{ij}]\\
= \sum_{i=1}^{n-1}\sum_{j=i+1}^nE[X_{ij}]
\end{split}
$$
Instead of the expectation we can now insert the probability that two items get compared from lemma 7.3
$$
\sum_{i=1}^{n-1}\sum_{j=i+1}^n\frac{2}{j-i+1}
$$
We can change $j-i$ to $k$
$$
\sum_{i=1}^{n-1}\sum_{j=i+1}^n\frac{2}{k+1}
$$
We can now see that the innersum is related to a harmonic series. Using the properties of a harmonic series we can bound the expectation $E[X]$ by 
$$
< \sum_{i=1}^{n-1}\sum_{j=i+1}^n\frac{2}{k}
$$
As the inner sum is a harmonic series which can be approximated by $O(lg\ n)$ we get the outer sum and $O(lg\ n)$
$$
=\sum_{i=1}^{n-1}O(lg\ n)
$$
$$
=O(n\ lg\ n) 
$$
#### Selection



## Notes
![[AvanAlgoLecture5.pdf]]
![[AvanAlgoLecture3-4.pdf]]
