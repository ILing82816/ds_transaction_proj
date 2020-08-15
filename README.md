# Data Science Customer Annual Salary Estimator: Project Overview
* Created a tool that estimates data science customer annual salary (Accuracy 96\%) to help companies segment customers into income brackets.
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
 

## Model Building
First, I normalized the data. I also split the data into train and tests sets with a test size of 20%.  
I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.  
I tried three different models:  
* **Linear Regression** - Baseline for the model
* **Long Short-term Memory (LSTM)** - Because the history of oil price would affect current oil price, I thought a memorable model like long short-term memory would be effective.
* **Prophet** - Again, with the time series data, I thought that this would be a good fit. Also, prophet can predict not only one period but more.   

## Model performance
Depend on the trend of oil price in the future, investors decide the strategies of investment. Although the Linear Regression model far outperformed the other approaches on the test and validation sets, the Prophet model is more practical.
* **Prophet:** MAE = 14.56   
![alt text](https://github.com/ILing82816/ds_oil_price_proj/blob/master/Figure/prediction_prophet.png "prophet")   
* **Linear Regression:** MAE = 0.82  
![alt text](https://github.com/ILing82816/ds_oil_price_proj/blob/master/Figure/prediction_linear.png "linear")  
* **Long Short-term Memory (LSTM):** MAE = 1.08  
![alt text](https://github.com/ILing82816/ds_oil_price_proj/blob/master/Figure/prediction_LSTM.png "LSTM")

## Productionization
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the tutorial in the reference section above. The API endpoint takes in a request with the day of prediction and returns a list of estimated WTI Price.
