# Credit-Card-Classification
Classification Models on Credit Card Fraud Detection Dataset

A. The Dataset

From Machine Learning Group of Universite Libre de Bruxelles, the next dataset provides untitled features that determine if a certain transaction is fraudulent. The dataset consists of 31 features with 284,807 instances. The features set consists of V1-V28, time, amounts, and “Class”. The “Class” feature consists of 1 and 0’s. “1” means the instance associated is marked as fraudulent while “0” represents as genuine transactions. Displaying the number of fraudulent transactions versus the genuine transactions uncovers a large disparity between the two.

![fraud_data](https://github.com/user-attachments/assets/86a0f832-84ca-42c8-8185-67f367c4c515)

Fig. 3. Genuine vs. Fraudulent Transactions

B. Classification Modeling with an Imbalanced Dataset
and its Effects

Figure 3 displays an imbalanced dataset and would
cause high bias if a classification model was fitted without
balancing. Using Logistic Regression, the most basic
classification model that was taught in class, the data was
fitted to the model to provide an example of what occurs.
To show the effects of using imbalanced data in a model, a
confusion matrix visualization can be used. A confusion
matrix displays the number of false positives, false
negatives, true positives, true negatives.
In the case of credit card fraud:
1. False Positive (0,1): Means the model predicted a fraudulent
transaction but it was genuine.
2. False Negative (1,0): Means the model predicted a genuine
transaction but was fraudulent.
 3. True Positive (1,1): Means the model predicted a fraudulent
transaction which was indeed fraudulent.
4. True Negative (0,0): Means the model predicted a genuine
transaction which was indeed genuine.

![confusion_matrix_imbalanced](https://github.com/user-attachments/assets/5783e9da-4a31-4d5c-adaa-9c3ecec3c9ec)

Fig. 4. Confusion Matrix of a Logistic Regression Model with
Imbalanced Data
TABLE I
Evaluation of Logistic Regression Model Before SMOT
Accuracy: 0.99927
Precision: 0.87755
Recall: 0.63235
F1-score: 0.73504

With imbalanced data, there's both high precision and
recall scores. High precision and recall cause many false
negatives in the model. This would not be good in detecting
fraudulent charges. In Figure 4, there are 50 false negatives
and 86 true positives meaning there is about a 33% chance
that the model would flag a transaction as genuine when it
should be considered fraudulent. Thus, modeling with
imbalanced data causes high bias in the dominant feature.
To combat high bias in an imbalanced dataset, there are
multiple pre-processing techniques that balance the data
and eliminate high bias.

C. Data Pre-processing to Prevent Bias
After determining that the dataset is imbalanced the
“Imbalanced-learn” package can be utilized to balance the
data and prevent bias in the dataset when fitting a
classification model. One such technique is Synthetic
Minority Over-Sampling or SMOTE. SMOTE creates
synthetic minority class samples. After resampling the
dataset, the number of fraudulent and genuine transactions
become equal as shown in Figure 5 below.

![fraud_data_balanced](https://github.com/user-attachments/assets/fb4d5ff7-b639-423a-9542-05acc7eac75d)

Fig. 5. Balanced Data After Using SMOTE

D. Confusion Matrix After Balancing Dataset
Applying a balanced dataset, we can ensure there
won’t be bias towards the majority in a dataset. In this case
it would be the genuine transactions. After fitting the
Logistic Regression model with the new balanced dataset,
the confusion matrix produces better False Negative results
but worse False Positive Negatives.

![confusion_matrix_log_balanced](https://github.com/user-attachments/assets/86e23f57-24a3-4048-bd58-2bda77e3d886)

Fig. 6. Confusion Matrix of a Logistic Regression Model After Using SMOTE on the Dataset

TABLE II
Evaluation of Logistic Regression Model After SMOT
Accuracy: 0.97346
Precision: 0.05323
Recall: 0.93382
F1-score: 0.10071

With only 9 False Negatives, this model is a significant
improvement over the one with imbalanced data.

E. Comparing Other Models
Since Logistic Regression with balanced data
produced a high number of False Positives, other models
were sought out to improve the confusion matrix without
sacrificing too much accuracy. Another method that was
utilized to predict whether a transaction is fraudulent or not
was Decision Tree Classification. In a Decision Tree,
leaves represent a class label and branches represent
conjunctions of features that lead to those labels. The
outcome of using this model provided slightly better results
with a slightly higher False Negative number with a
significantly lower False Positive number.

![confusion_matrix_tree_balanced](https://github.com/user-attachments/assets/b64a8484-2410-4632-9272-06afb0023c69)

Fig. 7. Confusion Matrix of a Decision Tree Classification After
Using SMOTE on the Dataset
5
TABLE III
Evaluation of Decision Tree Classification After SMOT
Accuracy: 0.99751
Precision: 0.36396
Recall: 0.75735
F1-score: 0.49165

![curve_tree](https://github.com/user-attachments/assets/bd713af4-6462-4a75-88a6-0cbe9e033d46)

Fig. 8. Precision Recall Curve of Decision Tree Classifier
Because the goal is to detect fraudulent transactions with
great accuracy, searching for a model with better results
became necessary. The model selected was a Random
Forest Classifier. This classification model surprising
performed the best out of the three. With a 99% accuracy
and low False positives and negatives, Random Forest
Classification predicted fraudulent transactions with the
greatest accuracy and lowest error.

![confusion_matrix_forest_balanced](https://github.com/user-attachments/assets/4ada521e-8051-44d0-9084-de1f82c47ff6)

Fig. 9. Confusion Matrix of a Random Forest Classification After
Using SMOTE on the Dataset
With only 16 False Negatives and 21 False Positives,
Random Forest Classification beats Decision Trees and
Logistic Regression without sacrificing accuracy. 
