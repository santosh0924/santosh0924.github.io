---
layout: post
title: "Hotel booking demand and cancellation with Predictive Analytics"
subtitle: "Predict if hotel booking will be cancelled"
date: 2020-01-26 23:45:13 -0400
background: '/img/posts/hotel/hotel-booking.jpg'
---


## Project Summary
Hotel booking cancellation is a major revenue issue for hotels. Booking cancellations not only has impact on hotel revenue and affect pricing but can also impact overbooking situations and could affect hotel’s online social reputation. The objective is to build model that can classify booking as cancelled or not using Machine learning. Machine Learning is a branch of Artificial Intelligence (AI) where applications are developed to learn from data to improve accuracy without any programming done to do so. The data is obtained from Hotel Booking Demand Datasets for the analysis. The dataset is from real bookings in European market. The data obtained in raw form is cleaned and formatted. Visualization tools are used to create images that provides important insights about the dataset. For instance, cancellation before certain number of days will be looked as it is important to so that hotels can arrangements well ahead of time. With the help of machine learning algorithms, different models are trained and performance score of each model is determined. The model that has the best score is selected for fine tuning.

From all the models tested, it is discovered that the best performing model is Random Forest. The tuned model has around 87% accuracy in predicting hotel cancellation. By using the prediction, hotels can act on high cancellation probability and associated revenue losses. Hotels can manage their business accordingly. Better net demand forecasts can be made, overbooking, cancellation policies can be improved and the revenue can be increased. There are not many models available to predict hotel cancellations. Hence, it is recommended for business to use this model and grow their business.

### Dataset
The dataset is selected from Kaggle. 
Hotels booking data - [Data source](https://www.kaggle.com/jessemostipak/hotel-booking-demand)

By looking at the values in the dataset, it can be seen that some columns have missing values. The columns where some values are missing are - 'children', 'country', 'agent', 'company'. The missing values will need be replaced. 

## Exploratory Data Analysis 
Data distribution of Cancelled vs Not cancelled

    
![png](/img/posts/hotel/output_6_1.png)
    

By hotel type

![png](/img/posts/hotel/output_7_1.png)

Cancellation of Hotels and Resort


    
![png](/img/posts/hotel/output_8_0.png)
    

Cancelled to arrival days
    


    
![png](/img/posts/hotel/output_12_1.png)
    

Cancelled booking by market segment

![png](/img/posts/hotel/output_13_0.png)

Correlation of features and cancellation     


    
![png](/img/posts/hotel/output_14_0.png)
    

## Modeling
Libraries or packages that is needed for the machine learning model is installed. The dataset is be first cleaned to remove any missing values or replace any missing values. Using EDA, correlation of features and cancellation is understood.
The overall process is as follows –
The dataset is split into training and test sets and feature scaling is applied. Baseline model is created. Training and prediction of multiple models are done and is compared against baseline model to choose the best model using accuracy. Hyperparameters tuning is done using GridSearchCV. Model is retrained using hyperparameters and prediction is made.
The first step towards model selection is the selection of performance metric. Since the dataset is not highly imbalanced, I have used Accuracy as a metric.
I have used Baseline model accuracy as base and compared it with different models – Logistic Regression, KNN, SVM and Random Forest. Below are the accuracy scores.

The data will be split into train and test. 80% of the data is train data and 20% is test data. In order to determine the best model, train dataset will be used. The test data will then be used for model evaluation. This is supervised classification problem as the goal is to predict if reservation will be cancelled or not.
The Random Forest model is tuned with hyper parameters using Grid Search and retrained to see if improves the accuracy score. The Grid SearchCV on random forest classifier has improved the accuracy score.

## Results
Based on the accuracy scores, Random Forest model is selected and the parameters are tuned which makes it more efficient. A model is selected so that it behaves well with current data and predict the hotel booking demand and cancellation for any future data.
Below is the confusion matrix. Top left is the true negative, top right is the false positive, bottom left is the false negative and bottom right is the true positive. 

![png](/img/posts/hotel/output_30_1.png)

Project code is present in Github - [Project Link](https://github.com/santosh0924/Hotel-Booking-Demand-and-Cancellation-with-Predictive-Analytics)