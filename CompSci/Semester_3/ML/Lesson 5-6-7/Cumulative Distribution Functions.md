## Cumulative Distribution Functions (CDFs)

Cumulative Distribution Functions are fundamental in probability theory and statistics, providing a comprehensive description of the distribution of a random variable.

### 1. **Definition of Cumulative Distribution Function**
- A CDF, denoted as $F(x)$ for a random variable $X$, is a function that gives the probability that $X$ will take a value less than or equal to $x$.
- Mathematically, for a continuous random variable, it is defined as:
  $$ F(x) = P(X \leq x) = \int_{-\infty}^{x} f(t) \, dt $$
  where $f(t)$ is the probability density function of $X$.
- For a discrete random variable, the CDF is the sum of probabilities up to and including $x$:
  $$ F(x) = P(X \leq x) = \sum_{t \leq x} P(X = t) $$

### 2. **Properties of CDFs**
- Non-decreasing: $F(x)$ never decreases as $x$ increases.
- Right-continuous: The right-hand limit of $F(x)$ at any point equals $F(x)$.
- Limits: $F(x)$ approaches 0 as $x$ approaches $-\infty$ and 1 as $x$ approaches $\infty$.

### 3. **Relation to PDF**
- For continuous random variables, the derivative of the CDF $F(x)$ with respect to $x$ is the PDF $f(x)$.

### 4. **Examples**
- In the case of a standard normal distribution, the CDF at $x$ gives the area under the normal curve to the left of $x$.

### 5. **Applications**
- CDFs are used to determine probabilities of a random variable falling within a particular range and to calculate percentiles and quantiles.

---

Understanding CDFs is crucial for interpreting the behavior of both continuous and discrete random variables, especially in statistical modeling and inferential analyses.
