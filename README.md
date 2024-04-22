# SC1015 Mini-Project - Estimating Time of Food Delivery

## About
This is a mini project for SC1015 - Introduction to Data Science and Artificial Intelligence (DSAI) which focuses on food delivery time.

## Contributors
SONG YICK QI - Data Cleaning & Preparation, Machine Learning, Readme, Presentation

LIEW WEI JIE - Data Cleaning & Preparation, EDA, Machine Learning, Readme, Presentation

LEE JIA QIAN VALERIE - Data Preparation,Readme, Presentation


## Motivations
- Increase in usage of food delivery services compared to pre-pandemic, source from deliveroo: https://deliveroo.com.sg/more/news-articles/consumer-survey
- 2023, Many consumers pointed out that the problem lay in the apps promising to deliver within a certain number of minutes but never giving an exact or even tentative time by when it should arrive. Source from Deccan Chronicle: https://www.deccanchronicle.com/nation/current-affairs/020623/late-deliveries-customer-complaints-food-delivery-hyderabad.html
- 2020, Late delivery was the top delivery issue that required customer service contact, source from PR Newswire: https://www.prnewswire.com/news-releases/new-study-finds-late-delivery-impacts-50-of-on-demand-food-delivery-customers-but-nearly-two-thirds-miss-phone-calls-to-alert-them-301122001.html
- Advantages of a more precise food delivery time: Builds customer confidence, leading, improved customer experience which eventually leads to increased sales, source from CEO of Fenix Commerce, Akhilesh Srivastava’s linkedin account: https://www.linkedin.com/pulse/what-does-take-provide-estimated-delivery-dates-akhilesh-srivastava/

## Problem Definition
- Are we able to create a model that predicts the delivery time? 
- Which features are of higher importance for the predictions?
- Are we able to improve the model through feature selection?
- Which / What models would be best for predicting the food delivery time?

## Models Used
- Linear Regression: `sklearn.linear_model.LinearRegression`
- Decision Tree Regression: `sklearn.tree.DecisionTreeRegressor`
- Random Forest Regression: `sklearn.ensemble.RandomForestRegressor`
- Gradient Boosting Regression: `xgboost.XGBRegressor`

## Reading Order
1. Data_Cleaning.ipynb
2. MissForest_Imputation.ipynb
3. EDA.ipynb
4. files with prefix "Machine_Learning_", except Machine_Learning_Final.ipynb
5. Machine_Learning_Final.ipynb

## Walkthrough
1. **Data Cleaning and Preparation**
    - Conversion to appropriate data types
    - Visualisation of missing value - `Missingno`
    - Removal of irrelevant columns
    - Handling NaN values
      - Dropping Na values
      - Data imputation - Using Mean, Median, Mode
2. **Feature Engineering**
    - `Distance` - Using Coordinates of the restaurant and the delivery location
    - `Day` - Using `OrderDate`
    - `OrderPeriod` - Using `TimeOrdered`
3. **Data imputation using `MissForest`**
    - Label Encoding
    - `MissForest`
4. **Exploratory Data Analysis** 
    - Numerical Features and Correlation 
    - Numerical Against Categorical 
    - Outlier Removal - Z-score and IQR
    - Categorical count
    - Time-Series
5. **Machine Learning - Regression**
    - Encoding categorical variables using `LabelEncoder` and `OneHotEncoder` from `sklearn.preprocessor`
    - Standardisation of the values across columns using `sklearn.preprocessor.StandardScaler`
    - Model fitting on the dataset using `GridSearchCV`, trying out linear regression, decision tree regression, random forest regression, and XGB regression, with different hyperparameters
    - Predicting TimeTaken using the models trained on the test set

## Conclusion
Using `XGBRegressor` we are able to predict the delivery time with an R2 score of 0.83. 

We performed analysis on the visualisations and observed the following:
  - Features that positively correlate to delivery time:
    - Age ~ We could not find a reason to explain the correlation
    - Distance
  - Features that negatively correlate to delivery time:
    - Ratings of driver
  - Important features for prediction: 
    - Multiple Delivery ~ Multiple Delivery attributed to high delivery time. This shows the concept of supply and demand between riders and delivery orders. 
    - Ratings ~ the time taken for the client to receive their order is significant for their user experiences, and hence affecting their ratings given to the deliverer.
    - Road Condition ~ Traffic conditions attributed to higher delivery time.
  - Time-Series observations:
    - Delivery time is significantly affectted by multiple devlieries as observed on the time-series graph. Explanation as above ^.
    - Road conditions explanation as above ^
    - Recommendation of improvement to customers, restaurant, and delivery riders.

Models and Feature selection:
Selection of features based on visualisation indeed improved results of linear regression. However,  this method of feature selection does not improve the results of other models. E.g. RandomForrestRegressor, XGBoost. (Explain how feature selection work for the other regressor)
(Which model is best for the prediction and why)
(Recommendation to improve delivery time/ Recommendations to improve model)


## What did We Learn From this Project?
  - Visualisation of missing values using `missingno`
  - Imputation of missing values, with machine learning - `MissForest`
  - Standardisation of columns
  - Encoding of categorical data
  - Cross-validation on regression models
  - Abovementioned regression methods

## References
https://www.kaggle.com/code/residentmario/using-missingno-to-diagnose-data-sparsity

https://www.kaggle.com/code/lmorgan95/missforest-the-best-imputation-algorithm

https://medium.com/@min0taur0/stop-filling-your-datasets-in-the-wrong-way-the-missforest-method-16f9464a2718  

https://gretel.ai/blog/comprehensive-data-cleaning-for-ai-and-ml 

https://towardsdatascience.com/7-ways-to-handle-missing-values-in-machine-learning-1a6326adf79e



