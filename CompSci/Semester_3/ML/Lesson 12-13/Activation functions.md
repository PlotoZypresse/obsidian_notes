# Activation Functions in Neural Networks

Activation functions in neural networks are critical components that decide whether a neuron should be activated or not. They introduce non-linearity into the network, enabling it to learn complex patterns in the data.

## Purpose of Activation Functions

1. **Non-linearity**: Without non-linear activation functions, a neural network, regardless of its depth, would behave like a single-layer perceptron because summing these linear transformations would still result in a linear transformation.
2. **Control Signal**: Activation functions control the amplitude of the output signal of a neuron and can limit it to a certain range, like [0,1] or [-1,1].

## Types of Activation Functions

### 1. Sigmoid or Logistic
- **Formula**: $f(x) = \frac{1}{1 + e^{-x}}$
- **Characteristics**: Smooth gradient, output values bound between 0 and 1.
- **Usage**: Historically popular, especially for binary classification.
- **Drawbacks**: Prone to vanishing gradient problem, not zero-centered.

### 2. Hyperbolic Tangent (Tanh)
- **Formula**: $f(x) = \tanh(x) = \frac{2}{1 + e^{-2x}} - 1$
- **Characteristics**: Similar to sigmoid but output values are zero-centered, ranging from -1 to 1.
- **Usage**: Often preferred over sigmoid in hidden layers.
- **Drawbacks**: Like sigmoid, can suffer from vanishing gradients in deep networks.
### 3. Rectified Linear Unit (ReLU)

- **Formula**: $f(x) = \max(0, x)$
- **Characteristics**: Provides a range [0, ∞), allowing for faster and effective training.
- **Usage**: Commonly used in modern neural networks, especially in deep networks.
- **Drawbacks**: Can suffer from "dying ReLU" problem where neurons stop firing during training.

### 4. Leaky ReLU

- **Formula**: $f(x) = x$ if $x > 0$, else $0.01x$
- **Characteristics**: Similar to ReLU but allows a small, non-zero gradient when the unit is not active.
- **Usage**: Used to address the dying ReLU problem.
- **Drawbacks**: The coefficient for negative values needs to be chosen carefully.

### 5. Softmax

- **Formula**: $f(x_i) = \frac{e^{x_i}}{\sum_{k} e^{x_k}}$
- **Characteristics**: Converts output to a probability distribution, where the sum of the output values is 1.
- **Usage**: Typically used in the output layer of a classifier to obtain probabilities for each class.

## Choosing an Activation Function

- The choice depends on the specific task and the network architecture.
- ReLU and its variants are generally a good starting point for hidden layers in deep networks.
- Sigmoid and Softmax are more common in the output layer for binary and multi-class classification tasks, respectively.

## Conclusion

Activation functions introduce the necessary non-linearity in neural networks, allowing them to learn complex patterns. The choice of activation function can significantly affect the performance and learning capabilities of the network.