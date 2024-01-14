## k-Nearest Neighbors (k-NN)

The k-Nearest Neighbors (k-NN) algorithm is a simple, yet effective machine learning algorithm used for both classification and regression tasks. It is a type of instance-based learning or lazy learning.

### 1. **Basic Principle**
- k-NN works by finding the k closest training examples in the feature space to a new sample and predicting the output based on these nearest neighbors.

### 2. **Classification and Regression**
- **Classification**: The output is a class membership. The class which is the most frequent among the k nearest neighbors is chosen as the prediction.
- **Regression**: The output is the property value for the object. This value is the average of the values of its k nearest neighbors.

### 3. **Choosing the Right k**
- Selecting the optimal value of k is crucial. A smaller k means that noise will have a higher influence on the result, while a larger k makes the computation costlier and may result in over-smoothing the model.

### 4. **Distance Measures**
- Distance metrics are crucial in k-NN to identify the closest neighbors. The choice of metric can significantly impact the performance of the algorithm.

  - **Euclidean Distance**: The most common distance metric, representing the straight line distance between two points. It's calculated as:
    $$ d(\mathbf{p}, \mathbf{q}) = \sqrt{\sum_{i=1}^{n} (q_i - p_i)^2} $$
    where \( \mathbf{p} \) and \( \mathbf{q} \) are two points in Euclidean n-space.

  - **Manhattan Distance (L1 Norm)**: Calculates the sum of the absolute differences of their Cartesian coordinates. Often used in grid-like path planning.
    $$ d(\mathbf{p}, \mathbf{q}) = \sum_{i=1}^{n} |q_i - p_i| $$

  - **Hamming Distance**: Measures the distance between two strings of equal length by counting the number of positions at which the corresponding symbols are different. Primarily used for categorical data.
    $$ d(\mathbf{p}, \mathbf{q}) = \sum_{i=1}^{n} \mathbb{1}(p_i \neq q_i) $$
    where \( \mathbb{1} \) is the indicator function, which is 1 if \( p_i \neq q_i \) and 0 otherwise.


### 5. **Features of k-NN**
- **No Training Phase**: k-NN does not learn a discriminative function from the training data but memorizes the training dataset instead.
- **Sensitivity to Feature Scaling**: Features need to be normalized so that one feature does not dominate the distance measures.
- **Handling Non-Linear Data**: k-NN can handle non-linear data effectively.

### 6. **Advantages**
- Simple to understand and implement.
- No assumption about the data distribution, suitable for real-world, non-linear data.

### 7. **Disadvantages**
- Not efficient on large datasets.
- High memory requirement as it stores all of the training data.
- Sensitive to irrelevant or redundant features, as all features contribute equally to the distance computation.

---

k-NN is a versatile algorithm that can be used for various types of data. It's especially useful in scenarios where the decision boundary is very irregular.

---
#reviewML