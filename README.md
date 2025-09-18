# AirBnB_Scoring_Prediction_Based_On_Features

Goal: 
My question is "can we predit whether an Airbnb listing in NYC will receive a high review score (rating >= 4.9) based on specific features"? This is a binary classification problem, where listings are classified as either "high-rated" or "not high rated". The label will be "high_rating", which is a new binary column I'll create from "review_scores_rating". The listing will be labeled 1 if "review_scores_rating >= 4.9, or else 0. The features (initially, but subject to adjustments) are room_type, accommodates, bathrooms, bedrooms, beds, host_response rate, host_acceptance_rate, host_is_superhost, number_of_reviews, reviews_per_month,review_scores_cleanliness, and review_scores_checkin.

This is an important problem because knowing this information can benefit both the Airbnb and the hosts. Airbnb can use this model to flag potential red flag listings or promote listings with high predicted guest satisfaction. Hosts can gain insight into what features most contribute to the guest experience and thus adjust those features for improvement.


Analysis:
I evaluated multiple classification models including logistic regression, random forest, and gradient boosting, along with their tuned versions using GridSearchCV. Among the untuned models, the random forest outpuerformed logistic regression and gradient boosting across all metrics, getting an AUC of 0.71 compared to 0.65 for logistic regression and 0.74 for gradient boosting. However, after hyperparameter tuning, both random forest and gradient boosting improved to an AUC of 0.74 (with gradient boosting slightly outperforming in the ROC curve and recall score).

The tuned gradient boosting model had an accuracy of 0.70, precision of 0.67, recall of 0.51, and AUC of 0.74. The feature importance plot showed that only a small group of features carried most of the predictive power. THis suggests that we can reduce the feature selection in future iterations. The confusion matric also showed that while the model correctly predicted a good number of positives, false negatives were significant. There is definitely room for improving recall further.

To validate the model behavior, I tested predictions of specific listings from the test set. For example, the model outputs both a predicted class -- higher rating or not -- and also a probability score telling us the confidence. This allows us to understand borderline cases where the model is not confident. The default classification thredhold of 0.5 might not be optimal, and adjusting this thredhold can help tune the balance between precision and recall.

In conslusion, gradient boosting with hyperparameter tuning was the best performing model in this project. It was able to achieve the best balance between precision, AUC, and recall. The results also point to the importance of ensemble methods and model optimization for improving generalization and predictive power.
