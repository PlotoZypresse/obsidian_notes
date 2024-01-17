## Concentration Inequalities

Concentration inequalities are important tools in probability theory and statistics that provide bounds on how a random variable deviates from some value, typically its mean.

### 1. **Markov's Inequality**
- **Definition**: For any non-negative random variable $X$ and any $a > 0$, Markov's inequality gives an upper bound on the probability that $X$ is at least $a$ times its expected value.
  $$ P(X \geq a) \leq \frac{E(X)}{a} $$
- **Application**: Useful when little is known about the distribution of $X$ apart from its mean.

### 2. **Chebyshev's Inequality**
- **Definition**: For any random variable $X$ with finite expected value $\mu$ and finite non-zero variance $\sigma^2$, Chebyshev's inequality bounds the probability that $X$ deviates from its mean by more than $k$ standard deviations.
  $$ P(|X - \mu| \geq k\sigma) \leq \frac{1}{k^2} $$
  for any $k > 0$.
- **Application**: Widely used due to its applicability to any probability distribution with a finite variance.

### 3. **Hoeffding's Inequality**
- **Definition**: For independent random variables $X_1, X_2, \ldots, X_n$ that are bounded, Hoeffding's inequality provides an upper bound on the probability that the sum of these variables deviates from its expected value.
  $$ P\left(\sum_{i=1}^{n}X_i - E\left[\sum_{i=1}^{n}X_i\right] \geq t\right) \leq \exp\left(-\frac{2t^2}{\sum_{i=1}^{n}(b_i-a_i)^2}\right) $$
  where each $X_i$ lies in the interval $[a_i, b_i]$.
- **Application**: Useful in statistical learning theory, particularly in deriving bounds for learning algorithms.

---

Concentration inequalities are powerful tools for understanding the behavior of sums of random variables and for bounding tail probabilities, which are crucial in many areas of probability, statistics, and machine learning.
