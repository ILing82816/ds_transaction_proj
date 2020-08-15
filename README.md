# Data Science Customer Annual Salary Estimator: Project Overview
* Created a tool that estimates data science customer annual salary (RSE 0.96) to help companies segment customers into income brackets.
* Engineered features: handling outliers, normalization, categorical encodings, feature generation, scaling, extracting date.
* Optimized Linear Regression, Decision Tree, and Random Forest tuning parameters to reach the best model.

## Code and Resources Used
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn   
**Program Task:** https://www.insidesherpa.com/virtual-internships/ZLJCsrpkHo9pZBJNY  


## Data Cleaning
I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:
* Derived weekday and hour data of each transaction
* Added column for the ratio of transaction
* Interacted two variables account, customer_id
* Splited customer & merchant lat_long into individual columns
* Filtered out transactions for those who don't reside in Australia
* Droped the outlier and Checked Normalization

## EDA
I gathered some interesting overall insights about the data. Below are a few highlights from the figures.  
Purchase Transaction Amount:  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_18_2.png)   
Customers' Monthly Transaction Volumn:  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_19_1.png)  
Average Transaction Volumn by weekday:  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_21_1.png)  
Customers' location:  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/customer_map.png)  
Correlation with other features:  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_5_1.png)
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_7_1.png)
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_8_1.png)  
According to the above scatter plots, we can see age, the amount of purchase monthly, and ratio of purchase have correlation with Salary. 

## Model Building
First, I normalized and scaled the data. I also split the data into train and tests sets with a test size of 20%.  
I tried three different models and evaluated them using R Square Error.  
I tried three different models:  
* **Linear Regression** - Baseline for the model
* **Decision Tree** - Because of the sparse data from the many categorical variables, I thought a decision tree model would be effective.
* **Random Forest** - Again, with the sparse data, I thought that this would be a good fit. Also, random forest would be helpful when your model is complex, easy to overfit.   

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets.
* **Random Forest:** RSE = 0.83   
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_38_1.png)   
* **Linear Regression:** RSE = 0.80  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_26_1.png)  
* **Decision Tree:** RSE = 0.96  
![alt text](https://github.com/ILing82816/ds_transaction_proj/blob/master/Figure/output_33_1.png)  
It is perform better by using Random Forest model. Using the r square to evaluate the model, and getting 0.96. However, as we can seen, it is a little big overfitting. In my opinion, ANZ can identify the customers' income level by their ratio of purchase and the amount of purchase.
