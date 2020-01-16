# Telco Customer Churn

It is a known fact in Business, to maintain an existing customer is more efficient than to get a new customer. To maintain is to find out what factors can affect a customer churn. By analyzing the effects, businesses can customize smart marketing strategies to incentivize the right customer with the right product. 

For this customer classification churn project, I analyzed a telecom customer data of size **955KB (7043 X 21)** sourced from the Kaggle datasets.  The project has 2 Notebooks, an *EDA* (exploratory data analysis) notebook that draws out the effects of the independent features, their distributions, and effects on each other, and a *Modelling* notebook that focuses on using different classification models, comparing the performances, hypertuning the models to derive better predictions, and finding out the feature importances from each of the model. 

## EDA
Here's a sample snapshot of the dataset features and types
![image](https://user-images.githubusercontent.com/7806480/71709041-22d38800-2e49-11ea-99f7-40bbae16a348.png)

Most of the features are Categorical in the data set. As such general desriptive statiscs like mean , median can be only applied for Tenure, and the charges. 

Based on the customer traits and the features of the service plan following observations were drawn
1. Most of the clients are not senior citizen. But among the Senior citizens there is more churning, with most of them under a monthly service plan. This could be due to financial reasons. 
![image](https://user-images.githubusercontent.com/7806480/71720164-d4d47980-2e74-11ea-9bdb-01eb5d12c942.png)

2. Customers with partners and/or dependants prefer a yearly contracts and have less churning. Customer with immediate family(working class) would not prefer to keep changing service operator.  
![image](https://user-images.githubusercontent.com/7806480/71720208-ffbecd80-2e74-11ea-8828-fb95de1a4a45.png)

3. 69% of churned customers have opted for an Fiber optice service as compared to 24.5% of the churned customers with DSL services. This can be a lacking internet service provision with Fiber optic either due to infrastructure availability or poor bandwidths. 
![image](https://user-images.githubusercontent.com/7806480/71720735-da32c380-2e76-11ea-87c1-c9902ced508c.png)

4. Total charges is linearly related to Monthly charges and Tenure.
![image](https://user-images.githubusercontent.com/7806480/71720867-3a296a00-2e77-11ea-8803-87696d19ddf2.png)

5. Customers with a higher monthly charges but with a lifetime of less than one year have higher chances of Churning out.

## Modelling 

First the data is preprocessed and few features are engineered based on the EDA. The modified data is put through 3 models developed using 
* Logistic Regression (This is a binary classification problem, to predict whether a customer churns(1) or does not churn (0). A logistitc regression would be the simplest to work with) 
* KNN (This is a simple parametric model and this can be considered as a baseline too) 
* Random forest (Random forest would be defintely helpful to evaluate if the required features are getting the importance).

### Data preprocessing
Tenure (in months) is replaced to Tenure_in_yrs, as the average tenure of non churning customers was observed to be more than an year.
Similarly monthly charges has been replaced to be in 100's of $ changing the range from 0-1. Similarly total charges is also changed to 1000's of dollars. 
In the function __*transform_categorical_data*__, all the dichotomous features are converted with *LabelEncoder()* and for other categorical variables pandas *get_dummies()* is used. 
Dropping of the customer id, the size of the data for modelling is 7043 X 24 as compared to 7043 X 21. 

### Feature Engineering
To reduce the number of features, customers with a *family*  (either partner or dependants) was created, as there is no additional features to indicate specifically for only partner / dependants .
This can be also performed with streaming TV, streaming Movies to be modified to a general streaming services if one of them doesnt have a significant impact on the target.

### Models metrics

Before we proceed to building the models, lets define the important metrics needed. For this project I focused on accuracy and verified different models performance with AUC score. 

### Evaluating the models
Three supervised algorithms are considered for this classficiation - logistics regression (parametric approach), KNN and Randomd forest (as non parametric approach)
- Running the logistic regression model without any hypertuning gives us an accuracy of 79.7% with auc at 84%. The training and test score of this model are close to each other. There may be an underfitting occuring over here. Hypertuning this model didnot change the acuracy much. (Accuracy 79.9%) 
- KNN model gives a hight training score of 97% with testing score at 75.5%. Even the auc score is only 74.7%
- Random forest gives a similar performance of prediction i.e., auc score of 80%  and 77.5% accuracy. With hypertuning of this model these results came same as logistic regression (80.4% accuracy, 84% auc score) 

Between Random forest and Logistic Regression the model analysing the feature importance of each model can help us to understand which model inteprets the data better. 




