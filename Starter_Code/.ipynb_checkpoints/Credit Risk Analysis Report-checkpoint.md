# Module 12 Credit Risk Analysis Report

## Overview and Purpose

This analysis means to address the challenge in classifying credit risk and the inherent imbalance in the data that must be used for classification.
The imbalance arises from the substantial majority of healthy loans in comparison to the fewer number of high-risk loans. To solve this, we'll employ techniques to train and evaluate models dealing with these imbalanced classes. Using a dataset of past lending transactions, the objective is to construct a model capable of determining the creditworthiness of borrowers. First we'll create a Logistic Regression model with the original data. Then, we'll resample the data and create another Logistics Regression model. Last, we'll compare both models and determine which model works better.

## Target Variable and Features within the Dataset

### Dependent Variable - Represented as y
Loan Status - This is the variable we are seeking to determine using the machine learning models.
0 = Healthy Loan | 1 = High-Risk Loan
The value_count of this variable was as follows:
0    75036
1     2500
This uneven split confirms we are dealing with imbalanced classes. 

### Independent Variables - Represented as X
Loan Size | Interest Rate | Borrower Income | Debt-to-Income
Number of Accounts | Derogatory Marks | Total Debt

## Machine Learning Stages
### Import the Modules needed
- Import the train_test_learn module from the sklearn library 
- Import the LogisticRegression module from the skLearn library
- Import the RandomOverSampler module form the imbalanced-learn library
- Import the balanced_accuracy_score, accuracy_score, confusion_matrix and classification_report modules from the sklearn library
- Import the classification_report_imbalanced library from the imbalanced-learn library
### Split the data
- Read our data from the csv file into a Pandas DataFrame
- Separate the target variable and the features
- Split the data into training and testing datasets using a random_state=1
### Create a Logistic Regression Model with the Original Data
- Instantiate the Logistic Regression model using a random_state=1
- Fit the model using training data
- Make a prediction using the testing data
- Evaluate the model’s performance by calculating accuracy score, generating confusion matrix and printing classification reports
### Predict a Logistic Regression Model with Resampled Training Data
- Instantiate the random_oversampler model using a random_state=1
- Fit the original training data to the random_oversampler model
- Count the distinct values of the resampled target variable, ensuring an equal number of data points this time
- Create another Logistic Regression Model using the resampled data (Instantiate-Fit-Predict)
- Evaluate the resampled model's performance. (Calculate accuracy score, generate confusion matrix, print classification reports)

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * The balanced accuracy score of this model is 95%. This tells us it does a pretty good job at classifying healthy and high-risk loans. However, the confusion matrix shows there is a high amount of false positives (102) and false negatives (56) so there may be some room to improve the model. 
  * Precision for healthy and high-risk loans is 100% and 85% respectively. 
  * Recall for healthy and high-risk loans is 99% and 91% respectively.

* Machine Learning Model 2:
  * The balanced accuracy score of this model using resampled data is 99%. This is higher than Machine Learning Model 1 which tells us this model is even better at classifying healthy and high-risk loans. Additionally, The confusion matrix shows a much lower number of false negatives (4) but a slightly higher number of false positives (116) than the previous model. I consider this a slight improvement overall as there is less errors in the dataset.
  * Recall is 99% for both healthy and high-risk loans. This is another improvement from Machine Learning Model 1.
  * Precision is still 100% for healthy loans and has dropped slightly to 84% for high-risk loans. This slight drop seems insignificant considering the improvement in recall.

## Summary

* Machine Learning Model 1 will predict a very high number of false negatives. This could lead to many credit-worthy applicants being denied unfairly.
* Machine Learning Model 2 will predict a very low number of false negatives. This is a much more favorable outcome for both lenders and consumers.
* Based on this, Machine Learning Model 2 performs better, assuming its more important to predict 0's (healthy loans) than it is to predict 1's (high-risk loans)
* Which Machine Learning Model to use may depend on the financial institution and whether or not they can take the added risk of false positives being predicted. For example, a big financial institution may favor Machine Learning Model 2 which will lead to more high-risk loans being issued. Conversely, a small financial institution may favor Machine Learning Model 1 which will lead to more false negatives but also less high-risk loans being issued.

