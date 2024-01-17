# Support Vector Machines (SVMs)

Support Vector Machines (SVMs) are a set of supervised learning methods used for classification, regression, and outliers detection. They are particularly well-known for their ability to create maximum margin classifiers, which is their distinctive feature.

## Overview of SVMs

- SVMs construct a hyperplane or a set of hyperplanes in a high-dimensional space, which can be used for classification or regression.
- The core idea is to find the maximum marginal hyperplane (MMH) that best divides the dataset into classes.

## Key Concepts

### 1. Hyperplane
- A decision plane that separates different classes in the feature space.
- In two-dimensional space, this hyperplane is a line dividing a plane into two parts where each class lays on either side.

### 2. Margins
- The margin is defined as the gap between the two lines on the closest class points. This is often called the "street".
- SVMs look for the largest margin.

### 3. Support Vectors
- Support vectors are the data points nearest to the hyperplane; the points of a dataset that, if removed, would alter the position of the dividing hyperplane.

## Types of SVM

### 1. Linear SVM
- Used for linearly separable data, where a single line can separate the classes.

### 2. Non-linear SVM
- For non-linearly separable data, SVMs use the kernel trick to transform the input space to a higher-dimensional space.

## The Kernel Trick

- The kernel trick involves mapping data into a higher-dimensional space where a linear separator can be found.
- Common kernels: Polynomial, Radial Basis Function (RBF), Sigmoid.

## SVM for Regression (SVR)

- SVMs can also be used for regression. SVR performs linear regression in a higher-dimensional feature space using the kernel trick.

## Advantages

- **Effectiveness**: Particularly powerful in high dimensional spaces.
- **Versatility**: Different Kernel functions can be specified for the decision function.

## Limitations

- **Scalability**: Not suitable for large datasets.
- **Sensitivity**: Sensitive to the tuning of parameters and the choice of kernel.

## Applications

- **Classification**: Especially in applications where the distinction between classes is very clear.
- **Regression**: In scenarios where a linear regression model doesn’t fit well.

## Conclusion

SVMs are a robust and versatile class of machine learning algorithms, especially useful for small- to medium-sized datasets with complex feature spaces.

## References

- “Support Vector Machines for Pattern Classification” by Shigeo Abe.
- “Learning with Kernels” by Bernhard Schölkopf and Alexander J. Smola.

---

Note: This note offers a concise overview of Support Vector Machines. For detailed study and practical applications, the references above are highly recommended.
