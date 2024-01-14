

Conditional probability is a fundamental concept in probability theory that deals with the probability of an event given that another event has occurred.

### 1. **Definition of Conditional Probability**
- The probability of an event A, given that event B has occurred, is denoted and calculated as:
  $$ P(A|B) = \frac{P(A \cap B)}{P(B)} $$
  provided that $P(B) > 0$ .

### 2. **Interpretation**
- $P(A|B)$  is read as "the probability of A given B". It reflects how the probability of event A changes when we know that event B has occurred.

### 3. **Importance in Probability Theory**
- Conditional probability allows for updating probabilities as new information becomes available and is foundational for Bayesian statistics.

### 4. **Independence**
- Two events A and B are independent if and only if $P(A|B) = P(A)$ or $P(B|A) = P(B)$. This means the occurrence of B does not affect the probability of A, and vice versa.

### 5. **Examples**
- If a deck of cards has 52 cards, and 4 are aces, the probability of drawing an ace (event A) is $\frac{4}{52}$. If one card is drawn and not replaced, and it is not an ace, the probability of drawing an ace on the second draw (event B) is now $\frac{4}{51}$ because the sample space has reduced to 51.

### 6. **Applications**
- Conditional probability is widely used in various fields such as finance, engineering, medicine, and weather forecasting, where it helps in decision making under uncertainty.
![[Screenshot 2024-01-14 at 17.09.01.png]]
---

Understanding conditional probability is crucial for interpreting and predicting outcomes in probabilistic models and real-world scenarios where events are often interdependent.
