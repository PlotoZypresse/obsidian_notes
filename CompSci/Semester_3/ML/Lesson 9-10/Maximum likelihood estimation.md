## Maximum Likelihood Estimation (MLE)

Maximum Likelihood Estimation is a statistical method used for estimating the parameters of a probability distribution or a statistical model.

### 1. **Definition of MLE**
- MLE is a method that determines the values of the parameters of a model that make the observed data most probable. It maximizes the likelihood function, which measures the probability of observing the given sample data.

### 2. **The Likelihood Function**
- The likelihood function for a set of parameters $\theta$ given data $D$ is denoted as $L(\theta|D)$, which is typically the probability of observing $D$ given $\theta$.
- The MLE of $\theta$ is the value that maximizes $L(\theta|D)$.

### 3. **Process of MLE**
- Formulate the likelihood function based on the probabilistic model.
- Apply optimization techniques to find the parameter values that maximize this function.
- Commonly involves taking the logarithm of the likelihood function, known as the log-likelihood, which is easier to optimize.

### 4. **Properties of MLE**
- **Consistency**: MLE estimates converge to the true parameter values as the sample size increases.
- **Efficiency**: In large samples, MLE achieves the lowest possible variance among all unbiased estimators.

### 5. **Applications**
- Widely used in various statistical and machine learning models for parameter estimation, such as in regression models, classification algorithms, and more complex models like neural networks.

### 6. **Examples**
- Estimating the mean and variance of a normal distribution from a sample of data, or estimating the parameters of a logistic regression model in a classification task.

---

MLE is a powerful and popular method in statistics and machine learning for parameter estimation, offering a principled way to fit models to data.
