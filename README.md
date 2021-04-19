# Classification Project: Loan Status Prediction

## Overview
* Applied the major Classification models to identify whether a loan is paid off or goes in collection 
* Achieved an out-of-sample Accuracy of 79% with Support Vector Machine Classifier


## Table of Contents
<div >

1.  [Introduction](#1)<br>
2.  [Data](#2) <br>
3.  [Exploratory Data Analysis](#3) <br>
4.  [Methodology](#4) <br>
5.  [Results](#5) <br>
6.  [Conclusions](#6) <br>
    </div>

## Introduction <a id="1"></a>
In Credit Risk Modeling, supervised Machine Learning and in particular Classification algorithms have proved to be incredible tools for banks, as they have significantly improved the ability in identifing good and bad debtors. In this project I apply all of the major Classification models to predict whether a loan will be paid off or will go in collection.

## Data <a id="2"></a>
The dataset is provided by IBM, as part of the Data Science Professional Certificate. The dataset is already splitted into train and validation set; the train set is splitted again during the analysis to set the optimal parameters through Cross-validation. The train set consists of 346 observations (the customers) and eight varibles, the first of which will be the target variable, while the test set contains 54 observations. The features are:

* Loan status (target variable): whether a loan is paid off or in collection
* Principal: basic principal loan amount in dollars
* Terms: origination terms which can be weekly (7 days), biweekly (15 days) or monthly (30 days)
* Effective date: when the loan got originated and took effect
* Due date: Since it's one time payoff schedule, each loan has one single due date
* Age: age of applicant
* Education: Education of applicant (High School or below, Bachelor, College, Master or above)
* Gender: Gender of applicant

## Exploratory Data Analysis <a id="3"></a>
After converting effective date in the weekday clients receive the loan:

<p align="center">
     <img src="https://user-images.githubusercontent.com/78954578/115154619-23168780-a07c-11eb-9e49-353191d79e4e.jpg" width="380" height="380">
     </p>
It seems that receiving the loan during to weekend is associated with the loan status, since most of the loans go in collection if obtained on Saturday or Sunday. I then create a new variable, "weekend", which is a dummy variable.

### Data Visualization
* Numerical variables
   * Histograms 
     <p align="center">
     <img src="https://user-images.githubusercontent.com/78954578/115154863-50176a00-a07d-11eb-8a60-8317e78e4eb5.jpg" width="720" height="280">
     </p>
     <em>Principal</em> distribution is highly concentrated on the 1000 value, while <em>age</em> could be distributed as a normal (slightly positive skewed) and <em>dayofweek</em> shows a bimodal distribution

   * Box plots
     <p align="center">
     <img src="https://user-images.githubusercontent.com/78954578/115155049-565a1600-a07e-11eb-84ff-e4cc481c75e0.jpg" width="720" height="280">
     </p>
     The outliers in the <em>Principal</em> and age distributions can be better visualized.
   
   * Correlation matrix
     <p align="center">
     <img src="https://user-images.githubusercontent.com/78954578/115186425-fac17400-a0e1-11eb-9305-dead06d51c0c.jpg" width="350" height="350">
     </p>
     Numerical featurea are very low correlated


* Categorical Variable

|  | |
:-------------------------:|:-------------------------:
![terms barplot](https://user-images.githubusercontent.com/78954578/115155189-134c7280-a07f-11eb-911e-4dee6e061558.jpg) | ![education barplot](https://user-images.githubusercontent.com/78954578/115155251-4f7fd300-a07f-11eb-843c-8d7d73c823d4.jpg)
![gender barplot](https://user-images.githubusercontent.com/78954578/115155256-5a3a6800-a07f-11eb-86a5-ab3b1a2cd61f.jpg)  | ![weekend barplot](https://user-images.githubusercontent.com/78954578/115155375-febcaa00-a07f-11eb-9c00-ce82ad92a32f.jpg)

Modes in the dataset are respectively: monthly term, high school and college as level of education, male and weekend as days in which applicants obtain the loan

* Target variable
<p align="center">
     <img src="https://user-images.githubusercontent.com/78954578/115187277-504a5080-a0e3-11eb-8b19-f45ecb919225.jpg" width="350" height="350">
     </p>
As usual in Credit Risk modeling, positive cases are significantly higher than negative ones

## Methodology <a id="4"></a>

I fit to the data all of the major Classifiers:

*	Logistic regression
*	Naive Bayes 
*	K Nearest Neighbrs
*	Support Vector Machine
*	Decision Tree
*	Random Forest
*	Gradient Boosting
*	XGBoost

For all the algorithms above, I evaluate the performance out-of-sample with both confusion matrix and ROC curve measuring:

*	Accuracy
*	Sensitivity (Recall)
*	Specificity
*	Precision
*	F1 Score
*	AUC

Finally, I inspect feature importances with the models from which can be extracted insights, i.e. Logistic Regression, Decision Tree and Ensemble Methods.

## Results <a id="5"></a>
### Logistic Regression

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![logit conf matrix](https://user-images.githubusercontent.com/78954578/115061341-5d9beb00-9ee9-11eb-8aeb-450850a4cc6f.jpg) | ![logit roc ](https://user-images.githubusercontent.com/78954578/115059652-21678b00-9ee7-11eb-9ffd-c17de0cbfb1c.jpg)

| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,74  |   
| Sensitivity (Recall)  | 0,97  |   
| Specificity  | 0,07  |   
| Precision  | 0,75  |   
| F1 Score  | 0,84  |   
| AUC  | 0,77  |   

* Almost perfect to predict paidoff loans, but very poor ability to predict loans in collection

### Naive Bayes Classifier

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![naive conf matrix](https://user-images.githubusercontent.com/78954578/115066514-ef0e5b80-9eef-11eb-993b-f6f435728f82.jpg) | ![naive roc](https://user-images.githubusercontent.com/78954578/115066541-f6ce0000-9eef-11eb-8dad-7474fedde481.jpg)


| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,67  |   
| Sensitivity (Recall)  | 0,65  |   
| Specificity  | 0,71  |   
| Precision  | 0,86  |   
| F1 Score  | 0,74  |   
| AUC  | 0,77  |   

* Lower accuracy than logit, increase of the ability to predict loans in collection, but sensitivity decreases

### K Nearest Neighbors
(Identified K=7 with Cross-validation on the train set, using Accuracy as metric)

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![knn conf matrix](https://user-images.githubusercontent.com/78954578/115109667-6affb680-9f77-11eb-8ce2-935edb0a92d3.jpg) | ![knn roc](https://user-images.githubusercontent.com/78954578/115109672-74891e80-9f77-11eb-9458-73f60d76f654.jpg)


| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,67  |   
| Sensitivity (Recall)  | 0,85  |   
| Specificity  | 0,14  |   
| Precision  | 0,74  |   
| F1 Score  | 0,79  |   
| AUC  | 0,71  |   

* Similarly to logit, very low specificity, but worse in predicting positives

### Support Vector Machine
(implemented with radial basis as kernel function)

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![svm conf matrix](https://user-images.githubusercontent.com/78954578/115112770-6216e100-9f87-11eb-8a54-d3479571154e.jpg) | ![svm roc](https://user-images.githubusercontent.com/78954578/115112774-68a55880-9f87-11eb-9c78-dc36bec76ccc.jpg)



| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,79  |   
| Sensitivity (Recall)  | 0,97  |   
| Specificity  | 0,29  |   
| Precision  | 0,79  |   
| F1 Score  | 0,87  |   
| AUC  | 0,81  |   

* Same Sensitivity score of logit, but better performance in predicting negatives

### Decision Tree
(Entropy is selected as splitting criteria)

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![dectree conf matrix](https://user-images.githubusercontent.com/78954578/115122321-94d8cd80-9fb7-11eb-9d85-209a27276e09.jpg) | ![dectree roc](https://user-images.githubusercontent.com/78954578/115122325-9bffdb80-9fb7-11eb-972d-27af1157bf83.jpg)


| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,72  |   
| Sensitivity (Recall)  | 0,80  |   
| Specificity  | 0,50  |   
| Precision  | 0,82  |   
| F1 Score  | 0,81  |   
| AUC  | 0,65  |   

* Not the best Accuracy, but until now the best balance between Sensitivity and Specificity

### Random Forest
(Entropy is selected as splitting criteria, number of trees set to 50)

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![random forest conf ](https://user-images.githubusercontent.com/78954578/115137873-e3728000-a028-11eb-91cf-f3329374e36e.jpg) | ![random forest roc](https://user-images.githubusercontent.com/78954578/115137884-eb322480-a028-11eb-89c8-241a5a1f9231.jpg)


| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,72  |   
| Sensitivity (Recall)  | 0,82  |   
| Specificity  | 0,43  |   
| Precision  | 0,80  |   
| F1 Score  | 0,81  |   
| AUC  | 0,70  |   

* Same Accuracy of Decision Tree, but better Area under Curve

### Gradient Boosting

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![grad boosting conf matrix](https://user-images.githubusercontent.com/78954578/115143641-db2a3d00-a048-11eb-91e9-3b3c69e7eacd.jpg) | ![grad boosting roc](https://user-images.githubusercontent.com/78954578/115143647-e67d6880-a048-11eb-9ca0-04f99df6fc14.jpg)


| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,70  |   
| Sensitivity (Recall)  | 0,85  |   
| Specificity  | 0,28  |   
| Precision  | 0,77  |   
| F1 Score  | 0,80  |   
| AUC  | 0,79  |   

* Increased AUC than Decision Tree, but worse Accuracy and Specificity

### XGBoost

| Confusion Matrix         |  ROC Curve |
:-------------------------:|:-------------------------:
![xgboost conf matrix](https://user-images.githubusercontent.com/78954578/115143792-af5b8700-a049-11eb-8fd2-0a7b35e3d879.jpg) | ![xgboost roc](https://user-images.githubusercontent.com/78954578/115143799-b6829500-a049-11eb-8a3c-4bcc2c449c57.jpg)



| Metrics  | Value  |   
|---|:-:|
| Accuracy  | 0,77  |   
| Sensitivity (Recall)  | 0,87  |   
| Specificity  | 0,50  |   
| Precision  | 0,85  |   
| F1 Score  | 0,83  |   
| AUC  | 0,77  |   

* Increased Accuracy than Decision Tree, but worse Specificity

### ROC Curve Comparison


<p align="center">
     <img src="https://user-images.githubusercontent.com/78954578/115143815-c8fcce80-a049-11eb-96d3-ed34c39db710.jpg" width="500" height="500">
     </p>


### Feature Importance

Highlithing the importance of the features used, in terms of coefficients value for the Logit model, and of impurity reduction for Decision Tree and other ensemble methods

| Feature               | Logit  |  Decision Tree  |  Random Forest  |  Gradient Boosting  |  XGBoost  |
|-----------------------|:------:|:---------------:|:---------------:|:-------------------:|:---------:|
| Principal             | -0,03  |     0,04        |      0,04       |     0,02            |    0,02   |
| Terms                 | -0,06  |     0,06        |      0,07       |     0,09            |    0,05   |
| Age                   |  0,06  |     0,40        |      0,48       |     0,23            |    0,04   |
| Gender                |  0,06  |     0,07        |      0,03       |     0,03            |    0,06   |
| Weekend               | -0,34  |     0,33        |      0,29       |     0,55            |    0,71   | 
| Bachelor              |  0,01  |     0,01        |      0,01       |     0,02            |    0,03   |
| High School or Below  | -0,01  |     0,03        |      0,02       |     0,03            |    0,03   |
| College               |  0,00  |     0,05        |      0,02       |     0,02            |    0,05   |

* As highlighted in the EDA, weekend feature has a strong predictive power in all of the models implemented
* Decision Tree, Random Forest and Gradient Boosting also identify age as a key feature; however, as well there doesn't seem to be a relationship between the loan status and the age of clients, I'd take this insight as a simple statistical association.


## Conclusions <a id="6"></a>
*	Achieved an Accuracy of 79% with Support Vector Machine Classifier
*	Models from which we could obtain insights confirm that weekend is a key feature, at least in this dataset, to classify good and bad loans, as highlightted in the EDA
*	Models in general are not efficient in predicting negatives: the highest Specificity is achieved by Naive Bayes Classifier, but the cost is the lowest Accuracy of all modes; for the other ones, Specificity highest score is 50%




