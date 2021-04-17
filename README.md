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




