## Performance Evaluation in Machine Learning

Performance evaluation is a critical step in developing and deploying machine learning models. It involves assessing a model's effectiveness in making predictions or classifications. Key concepts include:

### 1. **Evaluation Metrics**

- **Accuracy**: The proportion of correct predictions among the total number of cases examined. Particularly useful for balanced classification problems.
- **Precision and Recall**: Precision measures the ratio of true positives to all predicted positives, while recall (or sensitivity) measures the ratio of true positives to all actual positives. These metrics are crucial in scenarios where false positives and false negatives have different implications. [[Sensitivity and Specificity]]
- **F1 Score**: The harmonic mean of precision and recall, given by the formula ​$$ F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}} $$A higher F1 score indicates a balance between precision and recall, which is particularly important in situations where an even trade-off between false positives and false negatives is desired.
- **Mean Squared Error (MSE)**: Common in regression tasks, MSE measures the average squared difference between the estimated values and the actual value. ![[Screenshot 2024-01-14 at 09.57.55.png]]

### 2. **Validation Methods**

- **Holdout Method**: Splitting the dataset into a training set and a testing set (e.g., 80/20 split).
- **Cross-Validation**: Dividing the dataset into multiple smaller sets; the model is trained on several subsets and validated on the remaining ones. K-fold cross-validation is a popular variant. [[Cross Validation]]

### 3. **Overfitting and Underfitting**
[[Over and Underfitting]]
- **Overfitting**: Occurs when the model performs well on training data but poorly on unseen data. It indicates that the model has learned the details and noise in the training data to an extent that it negatively impacts the performance on new data.
- **Underfitting**: Happens when the model is too simple to capture the complexity of the dataset, leading to poor performance on both training and testing data.

### 4. **Confusion Matrix**
[[Confusion Matrix]]
- A table used to describe the performance of a classification model on a set of test data for which the true values are known. It compares the actual target values with those predicted by the model, providing insights into not only the errors being made but also the types of errors.

### 5. **ROC Curve and AUC**
[[ROC and AUC]]
- The Receiver Operating Characteristic (ROC) curve is a graphical plot that illustrates the diagnostic ability of a binary classifier. The Area Under the Curve (AUC) represents measure of separability. A higher AUC value indicates better model performance.

### 6. **Model Selection**

- Involves comparing different models and selecting the one with the best performance based on the evaluation metrics. It's essential to balance model complexity and accuracy to avoid overfitting and underfitting.