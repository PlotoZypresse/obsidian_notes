Least Squares is a fundamental method in statistics and machine learning, particularly used in regression analysis. The method is used to find the best-fitting line or curve to a given set of data by minimizing the sum of the squares of the differences between the observed and predicted values.

### Concept of Least Squares

1. **Objective**: The goal of the least squares method is to find the best-fitting model to the observed data. It does this by minimizing the sum of the squared differences between observed values and the values predicted by the model.
2. **Mathematical Formulation**:
    - Suppose you have a dataset with observations $(x1,y1),(x2,y2),...,(xn,yn)(x1​,y1​),(x2​,y2​),...,(xn​,yn​)$, where xixi​ are the independent variables and yiyi​ are the dependent variables.
    - The least squares method seeks to find the coefficients ββ of a function f(x,β)f(x,β) (often a linear function for linear regression) that minimizes the sum of squared residuals (errors): \[ $\text{Minimize } S = \sum_{i=1}^{n} [y_i - f(x_i, \beta)]^2$

### Application in [[Linear Regression]]

- **Linear Model**: In the case of linear regression, the model is a linear function of the form $y=β0+β1xy=β0​+β1​x$
- **Least Squares Solution**: The least squares method computes the best values of $β0$ and $β1$​ such that the line $y=β0+β1xy=β0​+β1​x$ minimizes the sum of squared differences between the actual and predicted values of $y$.

---
#reviewML

