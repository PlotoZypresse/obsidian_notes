## Norms in Machine Learning

Norms in machine learning are mathematical tools used to measure the size or length of vectors. They play a crucial role in regularization, optimization, and error measurement.

### 1. **Definition of a Norm**
- A norm is a function that assigns a strictly positive length or size to each vector in a vector space, except for the zero vector, which is assigned a length of zero.

### 2. **General Formula for p-Norm**
- The p-norm (also known as Lp norm) of a vector is defined as:
  $$ \| \mathbf{x} \|_p = \left( \sum_{i=1}^{n} |x_i|^p \right)^{\frac{1}{p}} $$
  for \( 1 \leq p < \infty \), where \( \mathbf{x} \) is a vector in a vector space, and \( n \) is the dimension of the vector.

### 3. **Commonly Used Norms**
- **L1 Norm (Manhattan Distance)**: 
  $$ \| \mathbf{x} \|_1 = \sum_{i=1}^{n} |x_i| $$
- **L2 Norm (Euclidean Distance)**: 
  $$ \| \mathbf{x} \|_2 = \sqrt{\sum_{i=1}^{n} x_i^2} $$
- **Infinity Norm (Max Norm)**: 
  $$ \| \mathbf{x} \|_{\infty} = \max_i |x_i| $$

### 4. **Norms in Optimization**
- Norms define the size of corrections in optimization problems, influencing how models converge to a solution.

### 5. **Norms in Regularization**
- L1 and L2 regularization use norms to penalize the magnitude of coefficients, aiding in reducing overfitting and improving model generalization.

### 6. **Vector Norms vs. Matrix Norms**
- Vector norms measure the magnitude of vectors, while matrix norms extend this concept to matrices, crucial in algorithm behavior analysis.

### 7. **Applications in Machine Learning**
- Norms are integral to various algorithms and processes like support vector machines, principal component analysis, and neural networks.

