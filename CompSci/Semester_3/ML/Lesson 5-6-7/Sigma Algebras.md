## Sigma Algebras (σ-Algebras) in Probability Theory

A sigma algebra is a mathematical concept in probability theory and measure theory, forming a fundamental part of the definition of a probability space.

### 1. **Definition of a Sigma Algebra**
- A sigma algebra (σ-algebra) on a set X is a collection of subsets of X that includes the empty set, is closed under complementation, and is closed under countable unions.

### 2. **Properties of a Sigma Algebra**
- **Includes the Empty Set**: The empty set is always a member of a σ-algebra.
- **Closed under Complementation**: If a set A is in the σ-algebra, then its complement (not A) is also in the σ-algebra.
- **Closed under Countable Unions**: If a sequence of sets \( A_1, A_2, A_3, \ldots \) is in the σ-algebra, then their union \( \bigcup_{i=1}^{\infty} A_i \) is also in the σ-algebra.

### 3. **Significance in Probability Theory**
- In probability theory, a σ-algebra on a sample space is used to define the events for which probabilities can be assigned. It ensures that probabilities are well-defined and that operations like union, intersection, and complementation of events behave consistently.

### 4. **Examples**
- In a simple coin-flip experiment, a σ-algebra could include the following subsets of the sample space {Heads, Tails}: { }, {Heads}, {Tails}, {Heads, Tails}. These subsets satisfy the properties of a σ-algebra.

### 5. **Relation to Measurable Functions**
- A function between two measurable spaces (where the spaces are equipped with a σ-algebra) is called a measurable function if the pre-image of any measurable set is also measurable. This concept is crucial in defining random variables in probability theory.

---

Sigma algebras provide the necessary structure to define probability measures and work with random variables, making them a key component in the rigorous mathematical study of probability.
