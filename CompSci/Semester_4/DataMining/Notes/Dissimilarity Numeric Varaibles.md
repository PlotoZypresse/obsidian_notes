![[Screenshot 2024-06-07 at 12.05.24.png]]
1. **Distance Measure**:
    - This is a way to quantify how different or similar two observations (data points) are in a dataset. It's particularly useful for numerical data.

2. **Properties of a Distance Measure**:
    - In mathematics, a distance measure (or dissimilarity measure) must satisfy certain properties to be considered valid. These properties are:

    **a. Non-negativity**:
        - ( $d(x_1, x_2) \geq 0$) for all ( $x_1$ ) and ( $x_2$ ).
        - This means that the distance between any two points is always zero or positive; it can never be negative.

    **b. Identity of Indiscernibles**:
        - ($d(x_1, x_2) = 0$) if and only if ( $x_1 = x_2$).
        - This means the distance between two distinct points is zero only if they are actually the same point.

    **c. Symmetry**:
        - \( $d(x_1, x_2) = d(x_2, x_1$) \) for all \( $x_1$ \) and \( $x_2$ \).
        - This means the distance from \( $x_1$ \) to \( $x_2$ \) is the same as from \( $x_2$ \) to \( $x_1$ \).

3. **Metric**:
    - A distance measure is called a metric if it also satisfies an additional property called the **triangular inequality**.

    **d. Triangular Inequality**:
        - \( $d(x_1, x_2) \leq d(x_1, x_3) + d(x_3, x_2)$ \) for all \( $x_1, x_2,$ \) and \( $x_3$ \).
        - This property states that the direct distance between two points \( $x_1$\) and \( $x_2$ \) is always less than or equal to the sum of the distances of an intermediate point \( $x_3$ \).

    - The triangular inequality is crucial for many data analysis and mining algorithms because it helps in efficient computation and ensures the consistency of the distance measure.

**Example Illustration**:
- The image includes a simple illustration of three points \( $x_1$ \), \( $x_2$ \), and \( $x_3$ \) in a space. The distance \( $d(x_1, x_2)$ \) directly connects \($x_1$ \) and \( $x_2$ \). According to the triangular inequality, this direct distance should be less than or equal to the sum of the distances \( $d(x_1, x_3) + d(x_3, x_2)$ \).

By adhering to these properties, a distance measure ensures that it behaves in a predictable and logical manner, which is essential for various analytical tasks in data science and machine learning.
[[Data_Representation.pdf]]