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

![[AvanAlgoLecture7.pdf]]

Fordrag plan
- hvad er en universel hashfunction
- hvad er perfect hashing
- hvordan bruger man en universel hashfunction i perfect hashing
- 