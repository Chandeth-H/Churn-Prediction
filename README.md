# Churn-Prediction
**code**: _https://colab.research.google.com/drive/1Tg2EcbIAFULvCMbA-cpHGekgEX9UgYRn?authuser=1#scrollTo=hb9FKmx9HN3s_

## Introduction
This project focuses on predicting churn for a telecommunications company, leveraging data-driven insights to identify at-risk customers and implement targeted interventions. By analyzing customer data, including tenure, service charges, and demographic information, we aim to build a robust predictive model that accurately identifies customers who are likely to leave the service.
## Data Source
Dataset used in this project is taken from Kaggle with a total of 7043 entries and 21 columns.

![image](https://github.com/user-attachments/assets/52ab29ce-1167-457b-954b-86e1d6fc9cce)

## Analysis
So far, there's no missing value in our dataset and from what we see, most columns are object type and the column customerID will be dropped out since it's not useful in our modelling. 

### EDA
Next, we will do some analysis on our data.

![image](https://github.com/user-attachments/assets/977171c6-f04a-489c-8eda-b9224c4b95c5)

Based on this Churn Status Distribution graph, we can see that the target variable in our dataset, Churn, is imbalance with 73.5% of data is in "No Churn" status and only 26.5% is in "Churn" status. This imbalance will cause a huge impact on our models' accuracy.

![image](https://github.com/user-attachments/assets/a603cc66-6fd8-40df-b0d4-436165f9817e)

This Contract Type graph reveals a significant relationship between churn rates and contract type status. It shows that the majority of customer churn occurs among those with month-to-month contracts, followed by customers on one-year contracts, and least among those with two-year contracts. This trend suggests that customers on month-to-month contracts may experience greater flexibility but also a higher likelihood of disengagement.

Conversely, the lower churn rates among two-year contract holders indicate that longer commitments may foster a sense of loyalty and satisfaction, reducing the likelihood of customers opting to leave. This suggests that contract length plays a critical role in customer retention, highlighting the importance of offering attractive long-term contract options to enhance customer loyalty and minimize churn.

![image](https://github.com/user-attachments/assets/989fb00c-f2dc-486c-bfe9-8ce7f322743c)

The visualization of Payment Method indicates a notable correlation between churn rates and payment methods. Specifically, the highest churn occurs among customers who use electronic checks, followed by those who pay via mailed checks, bank transfers (automatic), and finally, credit cards (automatic).

This trend suggests that customers utilizing electronic checks may have a higher propensity to disengage from the service, potentially due to perceived inconvenience or dissatisfaction with the payment process. In contrast, customers who utilize credit card payments show lower churn rates, which may indicate a preference for the convenience and reliability associated with automatic transactions.

### Tenure & Charge Insight

![image](https://github.com/user-attachments/assets/f05bcc09-ed44-41d4-9ae3-17335c29b477) 

The tenure mean of Non-churn is 37.57, while Churn is 17.98 which indicates that customers who stay longer are significantly less likely to churn, highlighting the importance of customer engagement and retention strategies for newer customers.

![image](https://github.com/user-attachments/assets/cffa9b50-6b85-42c7-a443-e5b09ebb1d99)  

The higher average monthly charges for churning customers suggest potential dissatisfaction or issues with perceived value, indicating a need for better service or pricing structures.

![image](https://github.com/user-attachments/assets/f1ed3675-1cfe-4ee0-87be-1a3a240db49a)

Higher total charges among non-churning customers indicate that loyal customers tend to have a longer relationship with the company, leading to increased total spending.

## Modelling

1. Data Preparation
- We utilized LabelEncoder to convert categorical object columns into integer format, facilitating model compatibility.
- The StandardScaler was applied to standardize the values across all numerical columns, ensuring that each feature contributes equally to model training.
- We employed RandomOverSampler to address class imbalance in the target variable, enhancing the model's ability to predict both classes effectively.
- The dataset was divided into training and testing subsets, with 75% allocated for training and 25% for testing to validate model performance.

2. Models

  We evaluated several models including Decision Tree, Random Forest, Gradient Boosting, and XGBoost. After thorough experimentation, the Random Forest model yielded the most   satisfactory results. Below are the performance metrics (Class 0 is Non-churn and Class 1 is Churn):

  ![image](https://github.com/user-attachments/assets/0c8766e7-ad3e-4540-ad3b-8afa42ee3c6f)

  ![image](https://github.com/user-attachments/assets/0aa471ab-efff-486d-9c75-030851da0957)

  - Precision:
  > Class 0: Precision of 0.94 indicates that when the model predicts class 0 (the negative class), 94% of those predictions are correct. This means the model is very reliable at     
  identifying non-churners.

  > Class 1: Precision of 0.85 means that when the model predicts class 1 (the positive class), 85% of those predictions are accurate. While still good, this indicates a slightly higher 
  rate of false positives compared to class 0.

  - Recall:
  > Class 0: Recall of 0.83 indicates that the model correctly identifies 83% of all actual class 0 instances. This means that some non-churning customers are being misclassified as 
  churners.

  > Class 1: A recall of 0.95 signifies that the model successfully identifies 95% of all actual churners (class 1). This high recall is crucial in churn prediction, as it indicates that 
  the model is effective at capturing most of the customers who are likely to leave.

  - F1-Score:
  > Class 0: The F1 score of 0.88 for class 0 balances precision and recall, indicating a strong performance overall. This score is particularly relevant when you want to find a balance 
  between precision and recall.

  > Class 1: The F1 score of 0.89 for class 1 also reflects a good balance, particularly given the model's high recall for this class, which is essential for effectively addressing 
  churn.

  - Support:
  > Class 0: The support of 1273 indicates the number of actual instances of class 0 in the test set.

  > Class 1: The support of 1309 shows the number of actual instances of class 1. Support provides context for the precision and recall values, as metrics are often more meaningful when 
  considering the number of instances.

  - Accuracy:
  > The overall accuracy of 0.89 indicates that 89% of the total predictions (for both classes) are correct. This is a strong accuracy rate, suggesting that the model performs well in 
  general.

  - With an AUC of 0.96, your model demonstrates outstanding predictive performance, effectively identifying customers at risk of churning while maintaining a low rate of false 
  positives.
  
In short, the Random Forest model demonstrated strong performance across all metrics, particularly in recall for class 1 (Churn), indicating its effectiveness in identifying positive cases.

## Conclusion

Overall, the classification report indicates that the model performs well, especially in identifying churners (class 1), which is critical for a churn prediction task. The high precision and recall for class 1 suggest that the model can effectively flag customers at risk of leaving, allowing the company to take proactive measures to retain them. However, there is room for improvement in precision for class 1, as some churners are being incorrectly classified as non-churners, highlighting an area for further tuning or model refinement.






