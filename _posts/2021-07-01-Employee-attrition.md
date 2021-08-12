---
layout: post
title: "Employee Attrition Prediction"
subtitle: "Predict employee turnover"
date: 2020-01-26 23:45:13 -0400
background: '/img/posts/employee/employee_attr.png'
---
## Project Summary
Employee attrition is the departure of employees from organization over time. Employee attrition can be voluntary or involuntary. Involuntary attrition is result of organization’s action where the employee is let go due to various reasons like performance. Voluntary attrition is when employee leaves the organization based on their discretion. Employee attrition that is voluntary can be due to various reasons like personal, job mismatch, retirement. Employee attrition is common in all organizations and if it is not managed properly, it can result in key members leaving the organization which in turn would result in decreased productivity.  The organization then have to hire and train new people which results in increased cost and is time consuming process. 

The project proposal is to predict employee attrition based on which companies can take certain actions to reduce attrition. As part of this project, company’s HR dataset will be analyzed to predict if an employee is likely to leave the organization. The dataset is first preprocessed to remove unnecessary variables. Data visualization is performed using Exploratory Data Analysis (EDA). There are many features in the dataset, and they will be analyzed using EDA to look at some factors that affect attrition. The features required for machine learning model is selected and dataset is split into train and test. Machine learning models like Random Forest, Linear Regression will be applied, and performance will be evaluated. The model with best score is selected and tuned to improve performance. The tuned model is evaluated for prediction results. 

## Problem Statement
Employee attrition is the decrease in size of workforce. Employee can leave the organization due to various reasons. There are many factors like age, salary, workplace challenges, work life balance, etc., which lead to whether an employee decides to stay with organization or not. Human resource is the important factor and considerable time is spent to recruit employees. 

As per the reports, the national average attrition rate in US was 27% in 2018 and 36% in 2019. Employee attrition is increasing over the years and a survey in US indicates that in 2030, there could be $430 billion loss annually due to low talent retention. Organizations always focus to have their professional employees stay to maintain productivity and to reduce cost involved in hiring and training new people. There can be impact on project schedule due to recruiting and training of new employees. 

There can be different human resource problems which cannot be determined using specific scientific formula. Hence, machine learning is the best way to solve this problem. The ‘IBM HR’ data from Kaggle is used for analysis to predict employee attrition. Machine learning algorithms are used, scores of few models are compared and best model is selected. 

### Dataset
The dataset is selected from Kaggle.
IBM HR dataset - [Data source](https://www.kaggle.com/pavansubhasht/ibm-hr-analytics-attrition-dataset)

## Data Exploration
The ‘IBM HR Analytics Employee Attrition & Performance’ dataset is selected from Kaggle. The dataset is explored to look at different variables. The dataset has 35 variables.

Attrition – is the predictor variable that contains value Yes and No. ‘Yes’ indicates employee attrition and ‘No’ indicates employee staying with the company.  

The dataset has 1,470 records. It was first explored to check for null values. There are no null values in any of the variables. Some of the variables were removed from further processing as it does not add much value in attrition prediction. The features removed are - EmployeeCount, Over18, StandardHours, EmployeeNumber.

## Exploratory Data Analysis

The predictor variable ‘Attrition is visualized to check for records. 
![png](/img/posts/employee/output_10_1.png)
    
As shown above, dataset has 237 Attrition records and 1233 records non-attrition records. Hence, the dataset is highly imbalanced.  

Data visualization of OverTime to Attrition is plotted. 

![png](/img/posts/employee/output_13_0.png)

As shown above, Attrition due to over time is more  

YearSinceLastPromotion variable is then visualized. As shown below, Employees who are recently promoted are likely to stay in the company. 

![png](/img/posts/employee/output_14_0.png)

Age feature is visualized as shown in below.
 ![png](/img/posts/employee/output_17_0.png)

As seen, attrition is more between age group 25 to 35.

Density plot of Attrition with regards to MonthlyIncome is shown below. It shows that attrition is more for monthly income between $2000 to $4000. 

 ![png](/img/posts/employee/output_19_0.png)

 Figure below shows that attrition is more when number of companies worked is less. Hence, employee is most likely to leave organization during early stages in their career. 

![png](/img/posts/employee/output_20_1.png)

Attrition related to EducationField is shown below. It shows that attrition is more in Life Sciences and Medical. It is least in Human Resources. 

![png](/img/posts/employee/output_22_1.png)

Feature selection is performed using SelectKBest technique. For this process, the best 20 features from the dataset are selected. Figure below shows the features selected for processing. 

![png](/img/posts/employee/picture1.png)


## Model Selection and Evaluation
The variables with text data are converted to numerical values using Label Encoder. The dataset is split into train and test. 80% of the data was selected for training and 20% was selected for testing. Stratify option is used when splitting train and test data so that the proportion example is present in train and test data. Since the dataset variables have different range of values, it is important to get them to common value range. Hence, normalization is performed using StandardScaler. The metric used for machine learning model is ROC AUC (receiver operating characteristic curve). The train data is fit with different machine learning models. 

The models used are Random Forest, Decision Tree Classifier, SGD classifier and Logistic Regression. Logistic Regression model has the best ROC-AUC score of 80%. 

Hence, Logistic Regression is selected for further performance tuning. Logistic Regression model is tuned with hyper parameters using Grid Search CV. The parameters selected are C = 0.1, penalty = l2 and solver = newton-cg. The Grid SearchCV on Logistic Regression classifier increased the ROC-AUC score to 81%. 

## Results
The project proposal shows that employee attrition can be predicted using machine learning model. Different models like Logistic Regression, Decision Tree Classifier, SGD classifier, Random Forest was evaluated. Logistic Regression model has best score. The model was evaluated using test data and score of tuned model is 78.90%.  

Figure below shows the confusion matrix where bottom right is True Positive, top left is True Negative, top right is False Positive and bottom left is False Negative.  

![png](/img/posts/employee/output_40_1.png)

True positive rate is 79% which indicates attrition was predicted correctly when the data indicated attrition. True negative rate is 88% which indicates model correctly predicted employee would stay with company when data indicated non-attrition. False positive rate is 21% which indicates the percentage of employee that were predicted as who would leave the company but was actually employee who stayed. False negative rate is 11.63% which indicates the percentage of employee that were predicted as who would stay but they actually left.

Organizations can use this tool to determine employee attrition and focus on the reasons that affect attrition. With this, employee can stay longer with the organization which reduces additional cost to the company and reduce potential delay in organization commitments. 


Project code is present in Github - [Project Link](https://github.com/santosh0924/Employee-Attrition-Prediction)