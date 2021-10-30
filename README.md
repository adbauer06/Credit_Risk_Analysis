# Credit_Risk_Analysis

## Analysis Overview
The purpose of this project was to use several different machine learning algorithms to evaluate credit risk.  Metrics for each of the models was then evaluated to determine their effectiveness in predicting credit risk.

A dataset of credit card information from LendingClub was used for this analysis.  Because this data is unbalanced with good loans greatly outnumbering risky loans, the algorithms used needed to handle that imbalance so that both options were more accurately represented.

The following methods and algorithms were used:
- RandomOverSampler algorithm (Oversampling)
- SMOTE alogorithm (Oversampling)
- ClusterCentroids algorithm (Undersampling)
- SMOTEENN algorithm (combination of oversampling and undersampling)
- BalancedRandomForestClassifier (ensemble classifier)
- EasyEnsembleClassifier (ensemble classifier)

For each method:
1. The data was resampled using the algorithm
2. A logistic regression model was then trained with the resampled data
3. Predictions were determined
4. Accuracy score was calculated
5. A confusion matrix was generated
6. A classification report was generated

The following metrics were then evaluated and compared:
- Balanced accuracy score - The percentage of overall predictions that were correct for the entire dataset.
- Precision Score - This shows how many of the positive predictions are correct, or in this case, how many positively identified as high-risk are in indeed high-risk.
- Recall or sensitivity score - This shows how good a test is at identifying the positives, or in this case how good it is at identifying the high-risk credit requests.


## Analysis Results

### RandomOverSampler Algorithm
This algorithm works by using oversampling.  Random data from the minority class (high risk class) is selected and added to the dataset until the two classes are balanced. 

The results of using this algorithm are as follows (for identifying high risk):
- Balanced accuracy score: 0.66
- Precision score: 0.01
- Recall score: 0.74

Classification summary report - RandomOverSampler:

![classification_report_ros](Resources/classification_report_ros.png)

### SMOTE Algorithm  
This algorithm also works by using oversampling.  In this case, new data is generated and added to the minority class until the two classes are balanced.

The results of using this algorithm are as follows (for identifying high risk):
- Balanced accuracy score: 0.65
- Precision score: 0.01
- Recall score: 0.62

Classification summary report - SMOTE:

![classification_report_smote](Resources/classification_report_smote.png)

### ClusterCentroids algorithm
This algorithm uses undersampling.  The majority class is decreased in size to match the minority class by generating datapoints that represent clusters of data.

The results of using this algorithm are as follows (for identifying high risk):
- Balanced accuracy score: 0.54
- Precision score: 0.01
- Recall score: 0.69

Classification summary report - ClusterCentroids:

![classification_report_cc](https://github.com/adbauer06/Credit_Risk_Analysis/blob/main/Resources/classification_report_cc.PNG)

### SMOTEENN
This algorithm uses a combination of both oversampling and undersampling to equalize the two classes.

The results of using this algorithm are as follows (for identifying high risk):
- Balanced accuracy score:  0.64
- Precision score: 0.01
- Recall score: 0.72

Classification summary report - SMOTEENN:

![classification_report_smoteenn](Resources/classification_report_smoteenn.png)

### BalancedRandomForestClassifier

This algorithm uses a process of randomly sampling data and creating small decision trees to evaluate that data that are then combined to make predictions.

The results of using this algorithm are as follows (for identifying high risk):
- Balanced accuracy score: 0.79
- Precision score: 0.03
- Recall score: 0.70

Classification summary report - BalancedRandomForestClassifier:

![classification_report_brfc](https://github.com/adbauer06/Credit_Risk_Analysis/blob/main/Resources/classification_report_brfc.PNG)

### EasyEnsembleClassifier

This agorithm uses a process of running classifiers on random samples independently and then aggregating the results into a final prediction.

The results of using this algorithm are as follows (for identifying high risk):
- Balanced accuracy score: 0.93
- Precision score: 0.09
- Recall score: 0.92

Classification summary report - EasyEnsembleClassifier:

![ClassificationReportEec](https://github.com/adbauer06/Credit_Risk_Analysis/blob/main/Resources/ClassificationReportEec.PNG)


## Summary

Looking at the metrics for each of the models, the balanced accuracy score using the EasyEnsembleClassifier was the highest at 93%.  However, that score may not be the best indicator as it only reflects overall accuracy, and does not give a glimpse into how high-risk and low-risk classes individually perform.  The precision number for all models was quite low, however in this analysis, using the sensitivity (recall) metric would be more important, as it measures how many credit requests that are actually high-risk are correctly identified.  While most of the models had a sensitivity score in the 60s and 70s, the EasyEnsembleClassifier scored 92.  With greater than 90% of the high-risk credit requests being identified, I would recommend using this model for evaluating credit risk.
