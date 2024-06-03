
The equation shown is an example of using amortized analysis with a potential function. Let's break down the steps to understand why $D_0$ appears in the final expression.

The total amortized cost of $n$ operations is given by:

$$
\sum_{i=1}^{n} \hat{c_i} = \sum_{i=1}^{n} \left( c_i + \Phi(D_i) - \Phi(D_{i-1}) \right)
$$

This equation states that the amortized cost $\hat{c_i}$ of each operation is the actual cost $c_i$ plus the change in the potential function $\Phi$ due to the operation.

Now, let's consider the right-hand side of the equation:

$$
\sum_{i=1}^{n} \left( c_i + \Phi(D_i) - \Phi(D_{i-1}) \right)
$$

This sum can be split into two separate sums:

$$
\sum_{i=1}^{n} c_i + \sum_{i=1}^{n} \left( \Phi(D_i) - \Phi(D_{i-1}) \right)
$$

The second sum, $\sum_{i=1}^{n} \left( \Phi(D_i) - \Phi(D_{i-1}) \right)$, represents the total change in the potential function over all operations.

Notice that this sum is a telescoping series, meaning that most terms will cancel out. Let's write out the terms explicitly to see this:

$$
(\Phi(D_1) - \Phi(D_0)) + (\Phi(D_2) - \Phi(D_1)) + (\Phi(D_3) - \Phi(D_2)) + \cdots + (\Phi(D_n) - \Phi(D_{n-1}))
$$

In this series, every term $\Phi(D_i)$ for $i = 1, 2, \ldots, n-1$ appears twice: once as $+\Phi(D_i)$ and once as $-\Phi(D_i)$. Thus, all intermediate terms cancel out, leaving only the first and the last terms:

$$
\Phi(D_n) - \Phi(D_0)
$$

Substituting this result back into our original equation gives:

$$
\sum_{i=1}^{n} \hat{c_i} = \sum_{i=1}^{n} c_i + (\Phi(D_n) - \Phi(D_0))
$$

This is why $D_0$ appears in the final expression. The telescoping nature of the series simplifies the sum of the potential changes to just the difference between the potential function evaluated at the final state and the initial state.