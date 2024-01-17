## Variance

Variance is a fundamental concept in statistics and probability theory, measuring the spread or variability of a set of data or a random variable.

### 1. **Definition of Variance**
- Variance quantifies the degree to which each number in a dataset is different from the mean. It is symbolically represented as $\text{Var}(X)$ for a random variable $X$.

### 2. **Calculation of Variance**
- For a discrete random variable:
  $$ \text{Var}(X) = \sum_{i} (x_i - E(X))^2 \cdot P(x_i) $$
  where $x_i$ are the values of $X$, $E(X)$ is the expected value of $X$, and $P(x_i)$ is the probability of $x_i$.
- For a continuous random variable:
  $$ \text{Var}(X) = \int_{-\infty}^{\infty} (x - E(X))^2 \cdot f(x) \, dx $$
  where $f(x)$ is the probability density function of $X$.

### 3. **Properties of Variance**
- Variance is always non-negative because the squares are always positive or zero.
- The variance of a constant is zero.
- Variance is used to compute the standard deviation, as the standard deviation is the square root of the variance.

### 4. **Examples**
- In a dice roll, if the expected value is 3.5, the variance would be calculated using the probabilities and outcomes of each roll, showing how much each roll deviates from the mean.

### 5. **Applications**
- Variance is widely used in statistical analyses to assess data spread, risk in financial investments, quality control in manufacturing, and in any field that requires a measure of data dispersion.

---

Understanding Variance is crucial for assessing the reliability of statistical models, risk in financial portfolios, and the overall spread of data sets in various applications.
