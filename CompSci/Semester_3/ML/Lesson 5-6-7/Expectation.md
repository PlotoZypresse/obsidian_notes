## Expectation in Probability Theory

Expectation, also known as Expected Value, is a fundamental concept in probability and statistics, representing the average or mean value of a random variable.

### 1. **Definition of Expectation**
- The Expectation of a random variable is the long-run average value of repetitions of the experiment it represents.
- It is denoted as $E(X)$ for a random variable $X$.

### 2. **Calculation of Expectation**
- For a discrete random variable:
  $$ E(X) = \sum_{i} x_i \cdot P(x_i) $$
  where $x_i$ are the possible values of $X$ and $P(x_i)$ is the probability of $x_i$.
- For a continuous random variable:
  $$ E(X) = \int_{-\infty}^{\infty} x \cdot f(x) \, dx $$
  where $f(x)$ is the probability density function of $X$.

### 3. **Properties of Expectation**
- **Linearity**: Expectation is linear, meaning $E(aX + bY) = aE(X) + bE(Y)$ for any two random variables $X$ and $Y$, and constants $a$ and $b$.
- Expectation does not necessarily correspond to a value the random variable can take.

### 4. **Examples**
- In a dice roll, the expected value of the outcome is $\frac{1}{6}(1 + 2 + 3 + 4 + 5 + 6) = 3.5$.
- For a random variable representing the flip of a fair coin, where heads is 1 and tails is 0, the expected value is $0.5(0) + 0.5(1) = 0.5$.

### 5. **Applications**
- Expectation is used in a wide range of areas including economics, finance, insurance, and many fields of science, to predict the average outcome of random events.

---

Understanding the concept of Expectation is crucial for interpreting the average
