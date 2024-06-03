- [ ] Lecture: Universal and Perfect [Source](https://imada.sdu.dk/u/kslarsen/dm582/L07.php)


## Universal Hashing
If we suppose that a malicious adversary chooses the keys to be hashed by a fixed hash function, the adversary can choose keys that all hash to the same slot which gives us an average retrieval time of $\Theta(n)$. The only effective way to mitigate this problem is to randomly choose the hash function in a way that is independent of the keys. This is called random hashing. A special case of this approach is called universal hashing.

To use random hashing instead of having one defined hash function we pick one hash function at random from a suitable family of functions. Because of this random selection the algorithm can behave differently on each execution. This prevents that one single input always evokes the worst case behavior of the hash function. Thus guaranteeing good average case performance.

$H$ is a finite family of hash functions that map a given universe $U$ of keys into the range $\{0,1,....,m-1\}$. For the family to be universal if for each pair of distinct keys $k_1,k_2 \in U$ the number of hash function in the family ($h \in H$) for which $h(k_1)=h(k_2)$ is at most $|H|/m$. This means that when choosing a random hash function from $H$ the probability that it will hash two different keys to the same value is $1/m$(one because we choose one hash function).  

Let $H$ be a family of hash functions each with domain U and range $\{0,1,...,m-1\}$. h is any hash function that is picked at uniformly at random from $H$ 

- The family $H$ is **uniform** if for any key $k$ in $U$ and any slot $q$ in the range $\{0,1,...,m-1\}$ the probability that $h(k) = q$ is $1/m$. This means that the probability of picking any slot with any hash function $h$ is equal to 1 divided by the number of slots $m$.
- The family $H$ is **universal** if for any distinct keys $k_1$ and $k_2$ in the universe $U$, the probability that one hash function hashes both keys to the same value(slot) is at **most** $1/m$ $$h(k_1)=h(k_2)$$
- The family $H$ of hash function is $\epsilon-universal$(epsilon universal) if for any distinct keys $k_1$ and $k_2$ in $U$, the probability that $h(k_1)=h(k_2)$ is at most **$\epsilon$**. So a universal family of hash functions would for example be $1/m$-universal. 
- The family $H$ is **d-independent** for any distinct keys $k_1,k_2,....,k_d$ in $U$ and any slots $q_1,q_2,.....,q_d$ (not necessarily distinct) in  $\{0,1,...,m-1\}$ if the probability that $H(k_i)=q_i$ for $i=1,2,...,d$ is $1/m^d$ 

Universal hash function families are of paricular interest because they are the simplest type of provably efficient hash table operations for any inpyt data set.

**Designing a universal family of hash functions**
We can begin designing a universal family of hash functions by starting with choosing a prime number $p$ that is large enough so that every possible key is smaller that $p$ (key $k$ lies in the range 0 to $p-1$). We let $\mathbb{Z}_p$ denote the set $\{0,1,...,p-1\}$, and we let $\mathbb{Z}_{p}^*$ denote the set $\{1,2,...,p-1\}$. Because the size of the universe of keys is greater than the number of slots in the hash table we have $p>m$ 

Given that any a in $\mathbb{Z}_{p}^*$ ($a \in \mathbb{Z}_{p}^*$) and any b in $\mathbb{Z}_{p}$ ($b \in \mathbb{Z}_{p}^*$) (this also means that a and b are integers smaller than the choosen prime $p$), define a hash function $h_{ab}$ as a linear transormation followed by reductions modulo $p$ and then modulo $m$ 
$$h_{ab}(k)=((ak+b)mod\ p)mod \ m$$
An example:
We have $p=17$ and $m=6$, here $p$ is the choosen prime and $m$ is the number of slots in the hash table.
$$
\begin{split}
h_{3,4}(8)=((3*8+4)mod\ 17) mod\ 6\\
= (28\ mod\ 17)mod\ 6 \\
= 11\ mod\ 6 \\
=5
\end{split}
$$
Now we have to proof that this family of hash functions($H_{pm}$) is universal.
To do that consider to distinct keys $k_1$ and $k_2$ from $\mathbb{Z}_p$ so that $k_1 \neq k_2$. For a given hash ffunction $h_{ab}$ let 
$$
\begin{split}
r_1=(ak_1 +b)mod\ p\\
r_2=(ak_2+b)mod\ p
\end{split}
$$
Since $r_1-r_2=a(k_1-k_2)(mod\ p)$ this is true $r_1 \neq r_2$, because p is prime and both a nad $(k_1-k_2)$ are nonzero modulo p. So their product must also be nonzero modulo p. Because of that when we computing any hash function in $H$ ($h_{ab}\in H_{pm}$) distinct inputs k1 and k2 map to distinct values r1 and r2 modulo p. When choosing numbers for the values of a and b and $a \neq 0$ there are $p(p-1)$ choices for a and b. This yields a different resulting pair $(r_1,r_2)$ with r1 not being equal to r2. We can solve for a and b using r1 and r2
$$
\begin{split}

a=((r_1-r_2)((k_1-k_2)^{-1}\ mod\ p))mod\ p,\\
b=(r_1-ak_1)mod\ p
\end{split}
$$
$((k_1-k_2)^{-1}\ mod\ p)$ denotes the unique multiplicative inverse, modulo p, of $k_1-k_2$. For each of  the possible p values of $r_1$ there are only $p-1$ possible values for $r_2$ that do not equal $r_1$. This gives us $p(p-1)$ possible pairs for ($r_1,r_2$) with r1 not being equal to r2. So there is a one-to-one correspondence between pairs (a,b) where a is not equal to 0 and pairs (r1,r2) with r1 not being equal to r2. Thus for any given pair of distinct inputs k1 and k2 if we pick a and b uniformly at random from $\mathbb{Z}_{p}^* \times \mathbb{Z}_{p}$ the resulting pair (r1,r2) is equally likely to be any pair of distinct values modulo p. Therefor the probability that distinct keys k1 and k2 collide is equal to the probability that r1 is equal to r2 modulus m, when r1 and r2 are randomly chosen as distinct values modulo p. For a given value of r1, of the p-1 possible remaining values for r2, the number of values such that r2 is not equal to r1 and r2=r1 mod(m) is at most
![[Screenshot 2024-05-29 at 16.51.29.png]]
the probability that r2 collides with r1 when reduced modulo m is at most $((p-1)/m)/(p-1)=1/m$, since r2 is equally likely to be any of the p-1 values in $\mathbb{Z}_p$ that are different from r1, but at most $(p-1)/m$ of theose values are equivalent to r1 modulo m
THere for any distinct values $k_1,k_2 \in \mathbb{Z}_p$, $Pr{h_{ab}(k1)=h_{ab}(k2)} \leq 1/m$ so $H_{pm}$ is indeed universal
## Perfect Hashing 
Hashing is excelent for tus average case performance, but hashing can also provide excellent worst-case perfromance when the set of keys is static: THis means that when the keys are stored in the table the set of keys never changes. Some applications naturally have static sets of keys: for example words in a  programming language or the set of file names on a CD.

Hashing is called perfect hashing if O(1) memory accces is required to perform a search in the worst case.

To create perfect hashing we use two levels of hashing, where both levels use universal hashing. The first level is like normal hashing. We hash the keys n into the slots m using the hash function h which is a universal hash function. Instead of using a linked list to store all the keys that hashed to the same slot we use a secondary hashtable $S_j$ with a hash function $h_j$. By choosing the right hash function for $h_j$ we can guarantee that there are no collisons at the secondary level. For that to be the case tho the size of $m_j$ the hash table $S_j$ has to be the squared number of $n_j$, so the number of keys hashing into the slot j. On the first glance this looks like storage would be a problem. But by choosing the right hash function for the first level we can limit the expected amount of space used to O(n)

To show that the secondary hash tables have no collisions and to show that the overall memory use for the primary and the secondary hash tables is O(n), we will use the universal hash function of the class $H_{pm}$ for the first hash table and $H_{pm_j}$ for the secondary hash tables.


---
### Theorem 11.9

**Statement:**

If we store $n$ keys in a hash table of size $m = n^2$ using a hash function $h$ randomly chosen from a universal class of hash functions, then the probability is less than $1/2$ that there are any collisions.

**Proof:**

1. **Number of Key Pairs:**

   When we have $n$ keys, the number of distinct pairs of keys that might collide is given by the combination formula $\binom{n}{2}$. This represents choosing 2 keys out of $n$ without regard to order:
$$
   \binom{n}{2} = \frac{n(n-1)}{2}
   $$

2. **Probability of Collision for a Pair:**
   Since the hash function $h$ is chosen from a universal class of hash functions, the probability that any particular pair of keys collides (i.e., they hash to the same slot) is $\frac{1}{m}$.

3. **Expected Number of Collisions:**
   Let $X$ be the random variable representing the total number of collisions. The expected value of $X$, denoted $\mathbb{E}[X]$, is calculated by summing the probabilities of all possible collisions:
$$
   \mathbb{E}[X] = \binom{n}{2} \cdot \frac{1}{m}
   $$
   Substituting $m = n^2$ and the value of $\binom{n}{2}$:
$$
   \mathbb{E}[X] = \frac{n(n-1)}{2} \cdot \frac{1}{n^2}
   $$
   Simplifying this expression:
$$
   \mathbb{E}[X] = \frac{n^2 - n}{2} \cdot \frac{1}{n^2} = \frac{n^2 - n}{2n^2} = \frac{n - 1}{2n}
   $$
   Since $\frac{n - 1}{2n}$ is always less than $\frac{1}{2}$ for any $n \geq 1$, we have:
   $$
   \mathbb{E}[X] < \frac{1}{2}
   $$

4. **Probability of Having Any Collisions:**
   The expectation $\mathbb{E}[X]$ gives the average number of collisions. To bound the probability that there is at least one collision, we can use Markov's inequality. Markov's inequality states that for any non-negative random variable $X$ and any $t > 0$:

   $$
   \Pr(X \geq t) \leq \frac{\mathbb{E}[X]}{t}
   $$
   By setting $t = 1$, we get:
$$
   \Pr(X \geq 1) \leq \mathbb{E}[X]
   $$

   Since we have shown that $\mathbb{E}[X] < \frac{1}{2}$, we get:
   $$
   \Pr(X \geq 1) \leq \frac{1}{2}
   $$
   This means the probability of having at least one collision is less than $\frac{1}{2}$.

### Theorem 11.10

**Statement:**
Suppose that we store $n$ keys in a hash table of size $m = n$ using a hash function $h$ randomly chosen from a universal class of hash functions. Then, we have:
$$
\mathbb{E} \left[ \sum_{j=0}^{m-1} n_j^2 \right] < 2n
$$

where $n_j$ is the number of keys hashing to slot $j$.

**Proof:**
We start with the following identity, which holds for any nonnegative integer $a$:

$$
a^2 = a + 2 \binom{a}{2} \quad (11.6)
$$
Using this identity, we have:
$$
\mathbb{E} \left[ \sum_{j=0}^{m-1} n_j^2 \right]
$$
Applying equation (11.6):
$$
= \mathbb{E} \left[ \sum_{j=0}^{m-1} \left( n_j + 2 \binom{n_j}{2} \right) \right]
$$
By the linearity of expectation:
$$
= \mathbb{E} \left[ \sum_{j=0}^{m-1} n_j \right] + 2 \mathbb{E} \left[ \sum_{j=0}^{m-1} \binom{n_j}{2} \right]
$$
By equation (11.1):
$$
= \mathbb{E}[n] + 2 \mathbb{E} \left[ \sum_{j=0}^{m-1} \binom{n_j}{2} \right]
$$
Since $n$ is not a random variable:
$$
= n + 2 \mathbb{E} \left[ \sum_{j=0}^{m-1} \binom{n_j}{2} \right]
$$
To evaluate the summation $\sum_{j=0}^{m-1} \binom{n_j}{2}$, we observe that it is just the total number of pairs of keys in the hash table that collide. By the properties of universal hashing, the expected value of this summation is at most:
$$
\binom{n}{2} \cdot \frac{1}{m} = \frac{n(n-1)}{2m}
$$
Since $m = n$:
$$
= \frac{n(n-1)}{2n} = \frac{n-1}{2}
$$

Thus:
$$
\mathbb{E} \left[ \sum_{j=0}^{m-1} n_j^2 \right] \leq n + 2 \cdot \frac{n-1}{2} = n + (n-1) = 2n - 1 < 2n
$$

### Why Collisions are Bad

1. **Performance Degradation**:
    
    - **Average Case**: Hashing typically offers average-case O(1) lookup time. However, if many keys collide, the time complexity can degrade to O(n) in the worst case.
    - **Worst Case**: If an adversary knows the hash function and can force collisions, they can degrade the performance of hash table operations, causing severe inefficiencies.
2. **Increased Load Factor**:
    
    - **Load Factor**: High collision rates increase the load factor (number of elements divided by the number of slots), leading to more collisions and longer chains or more probing steps, further degrading performance.
3. **Resource Utilization**:
    
    - **Space Efficiency**: Collisions may require additional data structures like linked lists or secondary hash tables, increasing memory usage and potentially leading to inefficient use of space.
    - **Time Efficiency**: Resolving collisions through methods like chaining or open addressing requires additional operations, which increase the time complexity for insertions, deletions, and lookups.
4. **Security Risks**:
    
    - **Denial of Service (DoS)**: In security-sensitive applications, collisions can be exploited for DoS attacks, where an adversary forces many keys to hash to the same slot, causing the system to spend excessive time handling these collisions.
5. **Predictability and Consistency**:
    
    - **Inconsistent Performance**: High collision rates can lead to unpredictable performance, which is undesirable in real-time systems where consistent response times are critical.

By minimizing collisions, universal hashing helps ensure that the hash table performs efficiently and predictably, maintaining O(1) average-case lookup times and reducing the risk of performance degradation and security vulnerabilities.

## Notes
![[AvanAlgoLecture7.pdf]]

## Plan
Fordrag plan
- hvad er en universel hashfunction
- hvad er perfect hashing
- tegn eksempel![[Screenshot 2024-05-30 at 13.06.47.png]]
- hvordan bruger man en universel hashfunction i perfect hashing
- theorem 11.9 

### Refined Presentation Plan (10-12 minutes)

1. **Introduction to Hashing (1-2 minutes)**
    
    - Briefly define hashing and its common applications, such as quick data retrieval in hash tables.
    - Explain the problem of collisions in hash tables, where multiple keys hash to the same slot, leading to inefficiencies.
2. **Universal Hashing (4-5 minutes)**
    
    - **Definition and Importance**: Explain that universal hashing is a technique where we randomly choose a hash function from a family of hash functions to minimize the chance of collisions, even if an adversary is selecting the keys.
    - **Mathematical Definitions**:
        - A family H of hash functions is **universal** if for any two distinct keys k1​ and k2k, the probability that they hash to the same slot is at most 1/m.
        - A family H is **uniform** if for any key k and any slot q, the probability that h(k)= is 1/m.
    - **Designing a Universal Family**:
        - Example: Use a prime number pp and design the hash function hab(k)=((ak+b)mod  p)mod  mhab​(k)=((ak+b)modp)modm.
        - Explain with a simple example: p=17p=17, m=6m=6, h3,4(8)=((3⋅8+4)mod  17)mod  6=5h3,4​(8)=((3⋅8+4)mod17)mod6=5.
    - **Proof of Universality**:
        - Outline the proof briefly: For two distinct keys k1k1​ and k2k2​, show that Pr(hab(k1)=hab(k2))≤1/mPr(hab​(k1​)=hab​(k2​))≤1/m by considering the number of possible hash functions and the distribution of r1r1​ and r2r2​.
3. **Perfect Hashing (4-5 minutes)**
    
    - **Definition and Use Case**: Define perfect hashing as a method to ensure O(1) lookup time in the worst case for static sets of keys, such as keywords in a programming language or file names on a CD.
    - **Two-Level Hashing Scheme**:
        - **Primary Hashing**: Hash keys into a primary table using a universal hash function.
        - **Secondary Hashing**: Use secondary hash tables for each slot in the primary table to handle collisions. The size of each secondary table is the square of the number of keys hashing into that slot.
        - Example: Illustrate with a diagram showing how keys are first hashed into the primary table and then into secondary tables.
    - **Space Efficiency**: Explain that by choosing the right hash functions, the total space used by the primary and secondary tables can be kept to O(n).
4. **Conclusion (1 minute)**
    
    - **Summary**: Recap the benefits of universal and perfect hashing: Universal hashing provides good average-case performance, while perfect hashing ensures excellent worst-case performance for static sets.
    - **Implications**: Highlight practical applications and the importance of these techniques in computer science and data structures.