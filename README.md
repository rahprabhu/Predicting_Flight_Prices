# Predicting Flight Prices

## Background


In this project, I will be working with a dataset on flight prices for routes across major Indian cities from February through June 2019. The dataset contains information on the flight such as the airline, the route, arrival/departure time, flight date, duration, and of course the price. The goal of the project is to use the features provided to predict the price of flight. 

## Analysis Steps

### Data Cleaning, EDA, Feature Transformation
The dataframe is fairly clean as far as not having too many missing values, so most of the cleaning and transformation goes toward handling date fields and categorical fields. The categorical features are transformed to be compatible with the regression models using techniques like **One-Hot Encoding** and **Label Encoding**. Throughout the cleaning and transformation process, I also leverage Matplotlib and Seaborn to visually answer questions about the dataset, such as:
  - How does the average price compare across airlines?
  - How do flight prices vary throughout the day?
  - What are the most frequent routes traveled?
  - On average, which city is most expensive to fly out of?
 
<br>

### Feature Selection, Regression Modeling, and Model Evaluation
Once the dataset is cleaned and transformed, I then performed feature selection using **Mutual Information** for regression. Using this feature selection technique enabled me to drop features that provide little to no information gain and show a low dependency with Price. After feature selection, I then create 3 tree-based regression models to predict the price of flights: **Random Forest**, **Gradient Boosting Regression**, and **XGBoost**. Below are the error metrics and R squared values for the 3 models. Keep in mind that the currency for flights in this dataset is the Indian rupee.

![image](https://user-images.githubusercontent.com/100224330/172486825-dba1182a-3bcf-4599-b6a7-4d7e4b981a4d.png)

Despite the results being very similar across the 3 models, I ultimately selected the XGBoost Regression as the best model. Below is a prediction error plot and residual error plot for the XGBoost model.

![image](https://user-images.githubusercontent.com/100224330/172487099-cbb1386e-4ca6-422b-b10d-16f58d81e89c.png)
![image](https://user-images.githubusercontent.com/100224330/172487114-16f20ef3-43c4-4cb6-bd1e-8624217d1de0.png)

To further evaluate the XGBoost, I once again leverage Matplotlib and Seaborn, but this time to visualize the most important features and the error (RMSE) of the model grouped by some of the variables in the dataset, such as Airline, # of stops, and time of day for departure. Some key findings from this analysis include:
  - Whether the flight was with Jet Airways, the duration, and the # of stops were the 3 most important features in the XGBoost model.
  - Our RMSE increases with average ticket price by airline, with Jet Airways being the airline with the greatest RMSE.
  - Predicting the price of 1 stop flights was the most difficult type of flight to predict compared to non-stop, and 2 or 3 stop flights.
  - There is not a significant difference in RMSE across times of day when grouping departure hours into early morning, late morning, afternoon, evening, and late night.
<br>

## Potential Ways to Improve / Ideas for Additional Data
  - Dimensionality Reduction techniques: Using PCA or LDA to try and reduce the dimensionality and sparsity of the data to capture most of the variance within a smaller subspace.
  - Remove outliers: either price outliers, or duration outliers. If we remove flights that are unusually expensive or flights that are extremely long due to extended layovers, maybe we can see improved predictions.
  - Add data on when the flight was booked: Most often, flights tend to be more expensive the closer to the departure date that they are booked, so we could be able to explain more of the variance in prices if we knew when the tickets were booked.
  - Add data on where the flight was booked: Was the flight booked through the airline or 3rd party? People often search through 3rd party websites and services for cheaper tickets, so having info on how/where the flight was booked might be helpful.
