---
layout: post
title: "Credit Card Fraud Detection"
subtitle: "Detect credit card fraud"
date: 2020-01-26 23:45:13 -0400
background: '/img/posts/credit-card/Credit-card-fraud.jpg'
---

## Project Summary
Financial fraud is a major concern in banking and financial services and costs millions of dollars every year. Credit card fraud continues to rise due to highly imbalanced dataset and non-stationary nature of data. It is estimated that some organization have losses up to 5% due to fraud and recent studies point that fraud activities have risen and expected to increase in future. Losses to financial institution can be avoided by detecting credit card fraud and alerting banks about potential fraudulent transactions.

The first step in building a model is to get the dataset. One of the main issues with credit card fraud detection is unavailability of real dataset. Since the credit card data will have sensitive details about the customer, there are not many datasets available due to privacy issues. Another challenge with credit card dataset is that it is highly imbalanced where there are more legitimate transactions and few fraudulent transactions. Millions of transactions are processed every day and the size of the dataset will be huge. Feature selection technique is applied to use only required features and machine learning algorithm using Random Forest Classifier is used to evaluate and effectively predict fraudulent transactions.    

## Problem Statement
In financial industry, fraud is a major threat which leads in financial loss. Credit card fraud results in millions of dollars loss to the banks and/or financial institution. Fraudsters find new ways to conduct fraud in credit card transaction. Losses to financial institution can be avoided by detecting credit card fraud and alerting banks about potential fraudulent transactions.

## Proposal
By using credit card fraud dataset, firstly I will perform some graph analysis to understand some trends in the dataset. The dataset may be imbalanced which might result in false positive or false negative fraud detection. Hence may need to perform scaling on the dataset. I will be using machine learning algorithms to detect the fraudulent transactions.

### Dataset
The dataset is selected from Kaggle.
Credit card fraud data - [Data source](https://www.kaggle.com/mlg-ulb/creditcardfraud)

#### Data Variables:
Columns V1 to V28 are result of Principal Component Analysis (PCA) which has been done due to data compliance.
Amount is the Transaction amount 
Class 0 indicates non-fraud and 1 indicates fraud
Time is the time elapsed between each transaction

Data pre-processing was performed to check for null-values and Exploratory Data Analysis (EDA) was performed. 

Bar plot of count of fraud vs non-fraud transactions in the dataset

    
![png](/img/posts/credit-card/output_11_1.png)
    


Histogram of transaction times in fradulent and non-fradulent transactions


   
![png](/img/posts/credit-card/output_13_1.png)
    


From above, fradulent transaction shows couple of peak times but it can be observed that time of the trasaction cannot be considered much in the analysis to determine if the transaction is fraudlent or not. 


The above can be cross verified by applying feature selection technique. For this study, variance threshold feature selection technique is used. Variance threshold is calculated based on probability density function of a particular distribution. If a feature has 95% or more variability, it is very close to zero and the feature may not help in the model prediction and those features are removed. Time was not selected in the outcome. The number of features from 28 to 23. The dataset is split into train and test where 80% is train dataset and 20% is test dataset.

Metric selection plays important part in validating the model. In this study, AUC (Area Under the Curve) is used. This is one of the good metrics to evaluate the score of classifiers since the calculation is based on the complete ROC (Receiver Operating Characteristic) curve and all possible classification threshold are implied. ROC-AUC validates that the method has good performance and identifies if transaction is risky or not.


## Results:
In order to ensure there is no overfitting of data, cross validation needs to be performed. Cross validation ROC-AUC score is determined for different models and Random forest classifier score is 94.38. In random forest, each tree is trained by randomly sampling the subset of training dataset. Training is fast with large datasets and many features as each tree is trained independently of others. The model is evaluated using the test dataset and AUROC is 95.82.

The results can be evaluated by confusion matrix. Confusion matrix shows the correct and incorrect prediction for each transaction type. First row, first column indicates the number of legitimate transactions that were predicted correctly. First row, second column indicates how many legitimate transactions were predicted as fraud. Similarly, second row indicates the fraudulent transactions that were erroneously predicted as legitimate. Hence, higher the diagonal values of confusion matrix, better would be the correct predictions.



    
![png](/img/posts/credit-card/output_58_1.png)
    

Project code is present in Github - [Project Link](https://github.com/santosh0924/Credit-Card-Fraud-Detection)