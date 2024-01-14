1. **Data Set and Data Points**:
    - A data set, denoted as $S$, is a collection of data points.
    - Each data point is a tuple $(x_i, y_i)$.
    - $x_i$ is an input observation (also known as a feature vector). It's the information you have.
    - $y_i$ is the corresponding output observation. It's what you want to predict or explain.
2. **Feature Space (X) and Label Space (Y)**:
    - The set of all possible input observations is called the feature space, $X$.
    - The set of all possible outputs is called the label space, $Y$.
3. **Labeling Function**:
    - There exists a function $f: X \rightarrow Y$ that maps each input to an output.
    - This function is unknown and what machine learning models try to approximate or learn.
4. **Independent and Identically Distributed (i.i.d.)**:
    - Each observation in the data set is assumed to be independent and identically distributed.
    - Independent: One data point doesn't influence another (like rolls of a dice in backgammon).
    - Identically Distributed: Each data point is drawn from the same distribution or process (using the same dice throughout the game).
5. **Machine Learning and the i.i.d. Assumption**:
    - Machine learning algorithms learn from the data assuming that it is i.i.d.
    - This assumption means that the way data was generated in the past (the examples it learns from) will be the same as how data will be generated in the future (the examples it will predict).
    - This is similar to how humans learn. For example, if you learn that touching a hot stove burns your hand, you assume that this will always be the case.

In summary, in machine learning, we collect a set of data points. Each point is an independent example of a certain input leading to a certain output. We assume all these examples come from the same underlying process. The goal of machine learning is to learn this process (the labeling function) so that given a new input, we can predict its output. The analogy of backgammon dice rolls illustrates the concept of independent and identically distributed samples - each roll is independent of the previous, and all rolls are assumed to come from the same pair of dice.


---
#reviewML 