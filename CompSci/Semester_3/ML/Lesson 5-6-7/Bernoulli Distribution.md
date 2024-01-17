## Bernoulli Distribution

The Bernoulli Distribution is one of the simplest discrete probability distributions in statistics, used to model random experiments that can have one of two outcomes.

### 1. **Definition of Bernoulli Distribution**
- A random variable $X$ follows a Bernoulli distribution if it takes the value 1 with probability $p$ and the value 0 with probability $1-p$, where $0 \leq p \leq 1$.
- The probability mass function (PMF) is given by:
  $$ P(X = x) = p^x(1-p)^{1-x} $$
  for $x \in \{0, 1\}$.

### 2. **Characteristics**
- **Binary Outcomes**: This distribution only accounts for two possible outcomes, often labeled as 'success' and 'failure'.
- **Mean and Variance**: The mean of a Bernoulli random variable is $p$, and the variance is $p(1-p)$.

### 3. **Applications**
- It is widely used in scenarios with binary outcomes, like flipping a coin (heads or tails), a light bulb being defective or not, and in basic models of binary response data in various fields.

### 4. **Relation to Other Distributions**
- The Bernoulli distribution is a special case of the Binomial distribution where there is only one trial, i.e., $n=1$ in a Binomial distribution.

### 5. **Examples**
- In a clinical trial, a patient either has a positive or negative response to a treatment, which can be modeled using a Bernoulli distribution.

---

The Bernoulli Distribution is fundamental in probability theory and statistics, particularly useful for modeling experiments with two possible outcomes.
