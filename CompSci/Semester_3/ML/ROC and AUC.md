## ROC (Receiver Operating Characteristic)
ROC can be used in [[Classification]] to find a classification threshold for the given data using [[Confusion Matrix]]. This is done by creating [[Confusion Matrix]] for different thresholds. Instead of having multiple [[Confusion Matrix]] we can create an ROC graph for all the different thresholds. On the graph the y axis is the True Positive Rate([[Sensitivity and Specificity|Sensitivity]]) and the x axis has the False positive rate([[Sensitivity and Specificity|Specificity]]). The False Positive Rate on the x-axis is $1 - Specificity$, not Specificity itself. The ROC curve is a plot of the True Positive Rate (TPR) against the False Positive Rate (FPR) as the decision threshold for the classifier is varied. ROC analysis is beneficial for evaluating the performance of a binary classifier.![[Screenshot 2023-12-19 at 15.55.00.png]]
## AUC
AUC or area under curve can be used to compare different methods and to find the better one. AUC is the area under the ROC curve. 

**Interpretation**:
- An AUC of 1.0 represents a perfect classifier; it perfectly separates the two classes.
- An AUC of 0.5 suggests no discriminative power, equivalent to random guessing.
- The closer the AUC to 1, the better the classifier is at predicting true positives and true negatives.![[Screenshot 2023-12-19 at 15.58.41.png]]