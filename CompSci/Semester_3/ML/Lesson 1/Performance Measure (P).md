
1. **Loss Function**:
    - The loss function, $L: Y \times Y \rightarrow \mathbb{R}^+$, measures the accuracy of predictions.
    - **Zero-One Loss for Classification**: $\ell(y,y') := \mathbb{I}(y \neq y')$, which counts how often the predicted class ($y'$) is not equal to the actual class ($y$).
    - **Squared Error for Regression**: $\ell(y,y') := (y-y')^2$, measuring the squared difference between the predicted and actual values.
2. **Learning Algorithm**:
    - A learning algorithm $A(\cdot)$ takes a dataset $S$ and produces a hypothesis $h_S$.
    - $h_S = A(S)$ represents the learning process, where $h_S$ is the hypothesis generated from the dataset $S$.
3. **Generalization Error**:
    - The generalization error for a hypothesis $h$ is defined as $L_{(D,f)}(h) := \mathbb{P}_{x \sim D}[f(x) \neq h(x)]$.
    - This is the probability that the hypothesis $h$ will predict differently than the true labeling function $f$ for data drawn from the distribution $D$.

---
#reviewML 