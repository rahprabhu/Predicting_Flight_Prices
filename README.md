# Predicting Flight Prices

## Background


In this project, I will be working with a dataset on flight prices for routes across major Indian cities from February through June 2019. The dataset contains information on the flight such as the airline, the route, arrival/departure time, flight date, duration, and of course the price. The goal of the project is to use the features provided to predict the price of flight. 

## Analysis Steps

### Data Cleaning, EDA, Feature Transformation
  Before creating any predictive models, I clean the dataframe using Pandas. The dataframe is fairly clean as far as not having too many missing values, so most of the cleaning and transformation goes toward handling date fields and categorical fields. The categorical features are transformed to be compatible with the regression models using techniques like **One-Hot Encoding** and **Label Encoding**. Throughout the cleaning and transformation process, I also leverage Matplotlib and Seaborn to visually answer questions about the dataset, such as:
  - How does the average price compare across airlines?
  - How do flight prices vary throughout the day?
  - What are the most frequent routes traveled?
  - On average, which city is most expensive to fly out of?
 
<br>

### Feature Selection, Regression Modeling, and Model Evaluation
Once the dataset is cleaned and transformed, I then performed feature selection using **Mutual Information** for regression. Using this feature selection technique enabled me to drop features that provide little to no information gain and show a low dependency with Price. After feature selection, I then create 3 tree-based regression models to predict the price of flights: **Random Forest**, **Gradient Boosting Regression**, and **XGBoost**. Below are the error metrics and R squared values for the 3 models. Keep in mind that the currency for flights in this dataset is the Indian rupee.

![image](https://user-images.githubusercontent.com/100224330/172294255-726b4648-74b7-4977-8a4c-06bc78ca2f8a.png)

Despite the results being very similar across the 3 models, I ultimately selected the XGBoost Regression as the best model. 
