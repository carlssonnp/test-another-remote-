1. Generally, AUC stands for area under the curve, but when used in Machine learning, it stands for area under the precision-recall curve or the area under the ROC curve. In our case, it's the latter. AUC ROC is the area under the curve of the pase positive rate and the true positive rate. An arbitrary AUC would be the 45 degree line, so we always want to improve on that to show that our model can perform better than 50-50 chance.

2. The confusion matrix is a simple 2-2 matrix showing True Positives, False Positives, True Negatives, and False Negatives.

3. True Positive Rate is the proportiion of positives that are correctly classified over all positives. False positive rate is the proportion of obs I classified as positive while they are really negative divided by all obs that are negative. FPR and TPR compose the ROC AUC, with FPR typically on the y axis and TPR on the x axis.

4. AUC ranges from 0 to 1. We want models with AUC values that are closer to 1 and prefer a model closer to 1 over a model that has an ROC that is closer to 0.

5. Gini, like AUC, ranges from 0 to 1, 1 being the best predictive score. IT is calculated by Gini = 2*AUC-1

6. Gini is a function of AUC and ranges from 0 to 1, but the meaning of the value 0 is different for gini, as it represents a random 50-50 baseline. In either case, we want the highest gini or AUC

7. Interpretability?