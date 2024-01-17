## Probability Theory Cheat Sheet

### 1. **Probability of an Event**
   $$ P(A) $$
   - The likelihood of event A occurring.


## Calculating P(A) - Probability of an Event

### 1. **Basic Probability for Discrete Events**
   $$ P(A) = \frac{\text{Number of favorable outcomes}}{\text{Total number of outcomes}} $$
   - Used when each outcome in a sample space is equally likely, such as rolling a die or flipping a coin.

### 2. **Probability for Continuous Events**
   $$ P(a \leq X \leq b) = \int_{a}^{b} f(x) \, dx $$
   - Used for continuous random variables, where \( f(x) \) is the probability density function, and \( a \) and \( b \) define the range of interest.

### 3. **Using Probability Mass Function (PMF)**
   - For discrete random variables, where each outcome has a specific probability:
   $$ P(X = x_i) = p(x_i) $$
   - Here, \( p(x_i) \) is the PMF which gives the probability that the random variable \( X \) takes the value \( x_i \).

### 4. **Using Probability Density Function (PDF)**
   - For continuous random variables:
   $$ P(a \leq X \leq b) = \int_{a}^{b} f(x) \, dx $$
   - The probability that \( X \) lies in the interval \([a, b]\) is the integral of the PDF \( f(x) \) over that interval.

---

The calculation of \( P(A) \) depends on the nature of the event \( A \) and the underlying sample space. It's crucial to understand the context and the type of random variable (discrete or continuous) when applying these formulas

### 2. **Conditional Probability**
   $$ P(A|B) = \frac{P(A \cap B)}{P(B)} $$
   - The probability of event A given that B has occurred.

### 3. **Bayes' Theorem**
   $$ P(A|B) = \frac{P(B|A) \times P(A)}{P(B)} $$
   - Updates the probability of A after obtaining new evidence B.

### 4. **Law of Total Probability**
   $$ P(A) = \sum_{i} P(A|B_i) \times P(B_i) $$
   - The probability of A across a complete set of disjoint events B_i.

### 5. **Independence of Events**
   $$ P(A \cap B) = P(A) \times P(B) $$
   - True if the occurrence of A does not affect the probability of B.

### 6. **Expected Value (Mean) of a Random Variable**
   - Discrete: $$ E(X) = \sum x_i \times P(x_i) $$
   - Continuous: $$ E(X) = \int_{-\infty}^{\infty} x \times f(x) \, dx $$
   - The average or expected outcome of a random variable X.

### 7. **Variance of a Random Variable**
   - Discrete: $$ \text{Var}(X) = \sum (x_i - \mu)^2 \times P(x_i) $$
   - Continuous: $$ \text{Var}(X) = \int_{-\infty}^{\infty} (x - \mu)^2 \times f(x) \, dx $$
   - Measures the spread of the values of X around the mean $\mu$.

### 8. **Standard Deviation**
   $$ \sigma = \sqrt{\text{Var}(X)} $$
   - The square root of the variance, indicating the average distance of the data from the mean.

### 9. **Binomial Distribution**
   $$ P(X = k) = \binom{n}{k} p^k (1-p)^{n-k} $$
   - Probability of k successes in n independent Bernoulli trials with success probability p.

### 10. **Normal Distribution Probability Density Function**
   $$ f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{ -\frac{(x-\mu)^2}{2\sigma^2} } $$
   - Describes the distribution of a continuous random variable with mean $\mu$ and variance $\sigma^2$.

---

This cheat sheet covers essential formulas in probability theory, useful for quick reference and basic analysis in various statistical and probabilistic contexts.
