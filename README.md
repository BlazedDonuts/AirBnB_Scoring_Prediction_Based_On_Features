# AirBnB_Scoring_Prediction_Based_On_Features

Goal: 


Analysis:
I evaluated multiple classification models including logistic regression, random forest, and gradient boosting, along with their tuned versions using GridSearchCV. Among the untuned models, the random forest outpuerformed logistic regression and gradient boosting across all metrics, getting an AUC of 0.71 compared to 0.65 for logistic regression and 0.74 for gradient boosting. However, after hyperparameter tuning, both random forest and gradient boosting improved to an AUC of 0.74 (with gradient boosting slightly outperforming in the ROC curve and recall score).

The tuned gradient boosting model had an accuracy of 0.70, precision of 0.67, recall of 0.51, and AUC of 0.74. The feature importance plot showed that only a small group of features carried most of the predictive power. THis suggests that we can reduce the feature selection in future iterations. The confusion matric also showed that while the model correctly predicted a good number of positives, false negatives were significant. There is definitely room for improving recall further.

To validate the model behavior, I tested predictions of specific listings from the test set. For example, the model outputs both a predicted class -- higher rating or not -- and also a probability score telling us the confidence. This allows us to understand borderline cases where the model is not confident. The default classification thredhold of 0.5 might not be optimal, and adjusting this thredhold can help tune the balance between precision and recall.

In conslusion, gradient boosting with hyperparameter tuning was the best performing model in this project. It was able to achieve the best balance between precision, AUC, and recall. The results also point to the importance of ensemble methods and model optimization for improving generalization and predictive power.
