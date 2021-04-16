# Classification-Project-Loan-Status-Prediction



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


### Feature Importance
1. From Logit model:

| Feature  | Coefficient  |   
|---|:-:|
| Principal  | -0.03  |   
| Terms  | -0.06  |   
| Age  | 0.06  |   
| Gender  | 0.06  |   
| Weekend  | -0.34  |   
| Bachelor  | 0.01  | 
| High School or Below  | -0.01  | 
| College  | 0.00  | 

* As highlighted in the EDA, weekend feature has the strongest predictive power




