1. **Overfitting**: This occurs when a machine learning model is too complex and fits the training data too closely. As a result, it captures not only the underlying patterns but also the noise in the training data. This leads to high performance on the training set but poor performance on new, unseen data. Overfitting is characterized by low bias but high variance. The model is overly sensitive to the fluctuations in the training data, failing to generalize well to new data.

2. **Underfitting**: This happens when a model is too simple to capture the complexities and patterns in the data. It occurs when the model has high bias and low variance. In underfitting, the model doesn't perform well even on the training data, indicating that it has missed the essential trends in the data.

3. **[[Bias and Variance]] Trade-off**: The key to a successful machine learning model is finding the right balance between bias and variance. High bias can lead to underfitting, where the model oversimplifies the problem. High variance can lead to overfitting, where the model is too complex and captures noise in the data as if it were a valid pattern. The goal is to create a model that has just enough complexity to capture the true patterns in the data without being swayed by the noise or peculiarities of the training set.

4. **Strategies to Address Overfitting and Underfitting**:
   - **For Overfitting**: Simplify the model, use regularization techniques, increase training data, or use cross-validation techniques.
   - **For Underfitting**: Increase model complexity, add more features, or use a more sophisticated machine learning algorithm.

