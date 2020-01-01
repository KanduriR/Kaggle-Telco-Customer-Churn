# Telco Customer Churn

It is a known fact in Business, to maintain an existing customer is more efficient than to get a new customer.  To maintain is to find out what factors can affect a customer churn. By analyzing the effects, businesses can customize smart marketing strategies to incentivize the right customer with the right product. 
For this customer classification churn project, I analyzed a telecom customer data of size 955KB sourced from the Kaggle datasets.  The data has about 7043 customer entries, and 21 features (including the output). This is a supervised classification problem where the label is 'Churn'.  The project has 2 Notebooks, an EDA (exploratory data analysis) notebook that draws out the effects of the independent features, their distributions, and effects on each other, and a Modelling notebook that focuses on using different classification models, comparing the performances, hypertuning the models to derive better predictions, and finding out the feature importances from each of the model. 

## EDA
Each data entry have some features to describe characteristics of the customer itself - 
 * Gender 
 * Senior citizen 
 * Partners
 * Dependents
 
In addition each entry, had further details about the features of the service plan taken.
* Tenute - (months the customer is with the company)
* Phoneservice (Yes/No)
* Multiplelines (if a Phonservice is taken) (Yes/No/No Phoneservice)
* Internetservice (indicating type of internet source - DSL/Fiber optice/None)
* Additional features that can be opted provided there is internet service 
    * Online security
    * Online backup
    * Device protection
    * Tech support
    * StreamingTV
    * streaming Movies
* Contract (Monthly/ Yearly/ 2 years)
* Paperlessbilling (Yes/No)
* Payment Method
* Monthly charges
* Total charges

Most of the features are Categorical in the data set. As such general desriptive statiscs like mean , median can be only applied for Tenure, and the charges. 

Based on the customer traits and the features of the service plan following observations were drawn
1. Senior citizens have more churning, with most of them under a monthly service plan. 
2. Customers with partners and/or dependants prefer a yearly contracts and have less churning.
3. 69% of churned customers have opted for an Fiber optice service as compared to 24.5% of the churned customers with DSL services. This indicates a lacking internet service provision with Fiber optic either due to infrastructure availability or poor bandwidths. 
4. Total charges is a linearly related to Monthly charges and Tenure.
5. Customers with a higher monthly charges but with a lifetime of less than one year have higher chances of Churning out.

## Modelling 

This notebook includes some of the data modification and feature engineering methods. The modified data is put through 3 models developed using  
* Logistic Regression (This is a binary classification problem, to predict whether a customer churns(1) or does not churn (0). A logistitc regression would be the simplest to work with) 
* KNN (This is a simple parametric model and this can be considered as a baseline too) 
* Random forest (Random forest would be defintely helpful to evaluate if the required features are getting the importance).

### Data preprocessing

### Feature Engineering

### Models metrics

### Evaluating the models

### Hypertuning


