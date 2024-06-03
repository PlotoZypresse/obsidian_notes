- [ ] Lecture: Naive, Rabin-Karp, Finite Automata. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L08.php)
- [ ] Lecture: Finite Automata, Knuth-Morris-Pratt. [Source](https://imada.sdu.dk/u/kslarsen/dm582/L08.php)


String matching is used to find the occurences of a pattern in a text. It is for example used in text editors or to find particular petterns in DNA sequences.

It can be stated formally as follows
- The text is given as an array $T[1:n]$ of length n
- The pattern is an array $P[1:m]$ that is not longer than T so $m \leq n$ 
- The elements of P and T are characters drawn from the alphabet $\Sigma$ which is a finite character set. Example $\Sigma$ could be the set {0,1} or it could just be the noraml english alphabet {a, b, c, ...., z}.

In the figure below we can see that the pattern P occurs with shift s in the text T(The pattern begins at s+1). Also the pattern shift s must at the start of the string T and the maximum s is n-m. 

If the pattern P occurs in the string T with shift s then s is a valid shift, otherwise s is an invalid shift. Mathematically it looks like this:
- For $P$ to occur with shift $s$ in $T$, the substring of T from position s to $s+m−1$ must be exactly equal to the pattern P.
- Mathematically, this is expressed as $T[s+1:s+m]=P[1:m]$. This means that for each position $j(where\ 1≤j≤m)$, $T[s+j]$ must equal $P[j]$.

Every method except the naive/brute force method preprocess the string before they start the matching phase. So the total running time is obviously the preprocessing time plus the matching time.

## Notation end terminology
$\Sigma^*$ (read sigma-star) denotes all finite length strings formed using characters from the alphabet $\Sigma$. The 0 length or empty strng denoted as **$\epsilon$** also belongs to $\Sigma^*$. The length of the string x is denoted $|x|$. The concatenation of two strings x and y denoted xy has length $|x|+|y|$ and consists of the characters from x followed by the characters of y.

A string w is a prefix of string x if $x=wy$. This is denoted like this $w\sqsubset x$. For example $ab \sqsubset abcca$.
Similarly a string w is a suffix of string x if $x=yw$. This is denoted like this $w \sqsupset x$. For example  
 $cca \sqsupset abcca$. For both it is required that y is a string in $\Sigma^*$ or $y\in\Sigma^*$. Also its implicated that the length of w is less than or equal to x or $|w| \leq |x|$.

A prorpper prefix or propper suffix of x will be shorter than x or $|w| < |x|$. the empty string is both a suffix and prefix for every string. 

![[Screenshot 2024-06-02 at 12.02.48.png]]

## Naive Methode
The naive method is the method most will think of when trying to pattern match with a string. Its simply to go throug every character in th string T and look for the occurence of the pattern P. In other words. The naive methode finds all valid shift using a loop that checks the condition $P[1:m]=T[s+1:s+m]$ for each of the $n-m+1$ possible values of s

The running time for this methode is $O((n-m+1)m)$. This is also a tight bound in the worst case. We get this running time by looking at the worst case scenario which is when ever character in the string T is the same for exampl "aaaaaaaaaaa" or $a^n$ if we now look for a pattern of lets say "aaaa" or more general $a^m$ we would need to go through every character in the string T and compare every character. We will shift the pattern from position 0 to $m-n$. So there are $n-m+1$ shifts and $m$ comparisons and thus the worst case running time is $\Theta((n-m+1)m)$ in the case of $m=n/2$(rounded down) the running time is $\Theta(n^2)$ 
![[Screenshot 2024-06-02 at 13.00.30.png]]
## Rabin-Karp
Rabin-Karp is a string matching algorithm that performs well in practice. The algorithm uses $\Theta(m)$ preprocessing time and its worst case running time is $\Theta((n-m+1)m)$. based on certain assumption its average running time is better.

How does Rabin-Karp work. As always we start with the alphabet $\Sigma$ lets go with the first 10 characters and give them numbers from 0 to 9. Now if we have a pettern of for example length 3. This pattern will have a value that can be calculated with a function. We now go through the string and calculate the "hash" value for every shift. But we do not compare the values/characters. We only see if we have found the right substring if the calculated value matches the value from our pattern. We do this because there could be false positives, meaning other patterns that give the same value as our desired pattern.

To move the pattern over the string T we employ a method that makes it very efficient. Given a text $T[1:n]$ of length n, let $t_s$ denote the value of the length m substring $T[s+1:s+m]$ ,That means the value that we compare to the value of our pattern string. if we now want to move to $t_{s+1}$ to move our "window" one digit to the right to calculate the hash of the next number we can use this method. 
$$
t_{s+1}=10(t_s-10^{m-1}T[s+1])+T[s+m+1]
$$
![[Screenshot 2024-06-02 at 16.56.29.png]]
$t_{s+1}$ is the next hash value we want to compare to our pattern. $t_s$ is the current value. We then subtract $10^{m-1}$ from the current value, m is the length of the pattern.
We can repeat this again and again until we are done. 

In a simpler variant we do not calculate a hash for each pattern but just compare the values of each Pattern. We will still use the function from above.

We can compute the values for $t$ in $\theta(n-m+1)$ time and we can comput p in $\Theta(m)$ time. So we can find all of the occurrences of the pattern $P[1:m]$ in the text $T[1:n]$ with $\Theta(m)$ preprocessing time and $\Theta(n-m+1)$ matching time.

## Finite Automata
![[Screenshot 2024-06-02 at 18.09.32.png]]
![[Screenshot 2024-06-02 at 18.09.46.png]]
th finite automaton begins in the start state $q_0$ and reads the characters of the input string one at the time. After it reads a character it makes a transition if a is read for example it transitions from state q to state a. When ever the current state q is a member of A we are in an accepting state.

A finite automaton M uses a final-state function $\phi$. The function is set up in such a way that $\phi(w)$ is the state M ends up in after reading string $w$. In other words when we end up in an accepting state we now that the last last characters we have read are the desired pattern. 

To finite automata for string matching we start with a preprocessing step. The preprocessing step create a string matching automata specific to the pattern p. The automato then searches the text for occurences of P. In order to specify the string matching automaton corresponding to the pattern $P[1:m]$ we need to define an auxiliary function $\sigma$ called the suffix function corresponding to the pattern P. The function $\sigma$ maps $\Sigma^*$ to {0, 1, ..., m} such that $\sigma(x)$ is the length of the longest prefix of P that is also a suffix of x
$$
\sigma(x)=max\{k:P[:k]\sqsupset x\}
$$
The suffix function is used to check how much of the pattern P matches the string we have gotten from our DFA example walk through([[suffix Function example]])

**Computing the transition function**
![[Screenshot 2024-06-03 at 10.35.09.png]]
![[Screenshot 2024-06-03 at 10.35.22.png]]
For the stringmatching automaton to work we need the transition function for the pattern P that we are trying to find. THe nested loops beginning on lines 1 and 2 consider all states q and all character a, lines 3/6 set $\delta(q,a)$ to be the largest k suxh that $P[:k] \sqsupset P[:q]a$. The cpde starts with the largest conceivable value of k, which is q+1 unless q=m in which case k cannot be larger than m. It the decreases k until $P[:k]$ is a suffix of $P[:q]a$, which must eventually occur since $P[:0]=\varepsilon$ is a suffix of every string

The running time of is $O(m^3|\Sigma|)$ because the outer loops contribute a factor of $m|\Sigma|$, the inner while loop can run atmost m+1 times and the test for whether $P[:k]$ is a suffix of $P[:q]a$ on line 4 can require comparing up to m characters. This can be improved by some clever computing to $O(m|\Sigma|)$ (more details [[transition function]])

## Knuth-Morris-Pratt
KMP uses an auxilary fuinction $\pi$ which precomputes from the pattern in $\Theta(m)$ time and is stored in array $\pi[1:m]$. Using the array $\pi$ the algorithm can effectively compute the transition function $\delta$ (amortized). The index q in $\pi$ ($\pi[q]$) contains the information needed to compute 
$\delta(q,a)$. 

To get the prefix function array $\pi[q]$ we go throug the Pattern array $P[i]$ and find the propper pre and suf-fixes that are identical for each substring of the pattern. If we find on we insert the starting point of that into $\pi$   

To compute the prefix function and the array $\pi[q]$ we go through all the sub strings of the the pattern P. We then find  the longest matching proper prefix and suffix and put that length into $\pi[q]$ look drawing below.

![[IMG_1430.jpg]]

We can now use this Prefix table when going throug the string. We start just like the naive approach by comparing every character until we rncounter a miss match. When we encounter a miss match at index i we look at the prefix table to see how to shift now. For example if we encunter a miss match at index $P[4]$ we look at the prefix table and see that we have to shift the pattern so that index 2 is in the position where we found the miss match. This is done until we find a string and/ or finish.
![[IMG_7539B72E5DEF-1.jpeg]]

The running time of COMPUTE-PREFIX-FUNCTION is $\Theta(m)$ which can be found using the aggreagate method of amortized analysis. The tricky part is to show that the while loop of lines 5-6 executes O(m) times altogether. Lets start with some observations about k. Line 3 starts k at 0 and the only way taht k increases is by the increment operation in line 8, which executes at most once per iteration for the loop of lines 4-9. Thus the total increase in k is at most m-1. second since $k<q$ upon entering the for loop and each iteration of the loop increments q. we always have $k<q$. Therefor the assignments in lines 2 and 9 ensure that $\pi[q]<q$ for all $q=1,2,...,m$ which means that each iteration of the while loop decreases k. third k never becomes negative. Putting these facts together we see that the total decreas in k from the while loop is bounded from above by the total increase in k over all iterations for the for loop which is m-1. Thus the while loop iterates at most m-1 times in all and the runtime is $\Theta(m)$.

Compared to FINITE-AUTOMATON-MATCHER we can decrease the preprocessing time from $O(m|\Sigma|)$ to $\Theta(m)$ while keeping the matching time bounded by $\Theta(n)$ 
## Notes
![[AvanAlgoLecture8-9.pdf]]

