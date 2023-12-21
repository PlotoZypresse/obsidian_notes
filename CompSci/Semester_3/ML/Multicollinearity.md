#### Definition
- Multicollinearity occurs when two or more predictors (independent variables) in a regression model are highly correlated with each other. This means that one predictor variable can be linearly predicted from the others with a substantial degree of accuracy.

#### Consequences
- **Inflated Standard Errors**: Multicollinearity increases the standard errors of the coefficients. High standard errors can make it difficult to determine if a predictor variable is statistically significant.
- **Unreliable Coefficients**: It makes the model's estimates highly sensitive to changes in the model. Small changes in the model can lead to large changes in the coefficients, making them unstable and unreliable.
- **Reduced Predictive Power**: Although it doesn't affect the model's ability to predict or forecast, multicollinearity can make it harder to understand how each independent variable is affecting the dependent variable.

#### Detection
- **Correlation Matrix**: A simple way to detect multicollinearity is by looking at the correlation matrix of the independent variables. High correlation coefficients (near ±1) indicate potential problems.
- **Variance Inflation Factor (VIF)**: It quantifies how much the variance is inflated due to multicollinearity. VIF values greater than 5 or 10 indicate a problematic amount of collinearity.

#### Solutions
- **Removing Variables**: If two variables are highly correlated, consider removing one of them.
- **Combining Variables**: Sometimes, it is possible to combine two correlated variables into a single one.
- **[[L2 Ridge Regression]] (L2 Regularization)**: This technique can be used when you want to keep all variables in the model, as it adds a penalty to the regression model which can reduce the impact of multicollinearity.
- **Principal Component Analysis (PCA)**: PCA is a technique that transforms the original variables into a new set of uncorrelated variables.

#### Example
Imagine you are analyzing data on house prices. You have two variables: the number of bedrooms and the number of sleeping rooms. These two are likely to be highly correlated (as bedrooms are a subset of sleeping rooms), which could lead to multicollinearity in your regression model.

Multicollinearity is a common issue in real-world data analysis, especially in fields like economics, finance, and social sciences, where many variables can be interrelated. It's crucial to check for and address multicollinearity to ensure the reliability and interpretability of a regression model.