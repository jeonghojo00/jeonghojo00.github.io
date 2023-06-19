---
layout: post
title: 'House Price prediction'
date: 2021-04-30 00:00:00 -0500
categories: [machine learning, regression]
tags: [machine learning, data analytics, regression, gradient boosting, eda]
---

# Housing Price Prediction
[Code](https://https://github.com/jeonghojo00/MachineLearning/blob/main/Regression/House_Prices_Advanced_Regression_Techniques.ipynb)

## Description and Deliverables
### Description
Ask a home buyer to describe their dream house, and they probably won't begin with the height of the basement ceiling or the proximity to an east-west railroad. But this playground competition's dataset proves that much more influences price negotiations than the number of bedrooms or a white-picket fence.

With 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa, this competition challenges you to predict the final price of each home.

### Main Questions to Answer and Hypothesis
- Can we predict the housing price and how accurate?
    - Assuming that the housing prices have patterns based on features, we may be able to predict the housing price. 
- What are the key factors influencing housing price?
    - When the houses are built and sold may be a good indicator because the house prices tend to deevalate after certain years since buit. 
    - Housing area may have an impact too.

## Data Analysis
I decided to explore and analyze data by data types. Main the EDA will have 3 parts
1. Handle missing values
2. Correlation analysis

### 1. Missing values
#### 1. Check Missing Values
features |missings |missings_percent |
-----|-----|-----| 
PoolQC |1453 |99.520548 |
MiscFeature |1406 |96.301370 |
Alley |1369 |93.767123 |
Fence |1179 |80.753425 |
FireplaceQu |690 |47.260274 |
LotFrontage |259 |17.739726 |
GarageType |81 |5.547945 |
GarageYrBlt |81 |5.547945 |
GarageFinish |81 |5.547945 |
GarageQual |81 |5.547945 |
GarageCond |81 |5.547945 |
BsmtExposure |38 |2.602740 |
BsmtFinType2 |38 |2.602740 |
BsmtFinType1 |37 |2.534247 |
BsmtCond |37 |2.534247 |
BsmtQual |37 |2.534247 |
MasVnrArea |8 |0.547945 |
MasVnrType |8 |0.547945 |
Electrical |1 |0.068493 |
- 19 columns have missing values of 81 columns
- Total 6965 missing values: Missing values consist of 6.3% of all data points
![Missing Values](/assets/images/house_price/houseprice_missingvalues.jpg)

#### 2. Handle Missing Values
- Drop columns with missing value rate higher than threshold
- Conduct imputation with mean of median
    - If normally distributed, replace NaN with mean
    ![Imputation Mean](/assets/images/house_price/houseprice_impute_mean.jpg)
    - If skewed, replace NaN with median
    ![Imputation Median](/assets/images/house_price/houseprice_impute_median.jpg)

### 2. Correlation with target price
![Correlation](/assets/images/house_price/houseprice_correlation.jpg)
- the graphs show that all the numeric features are positively correlated with house prices

## Regression Models and Results
model |MAE |MSE | RMSE| R2|
-----|-----|-----|-----|-----|
Linear Regression | 20240.2978 | 1343191715.6307 | 34637.0925 | 0.7978
Decision Tree Regressor | 25992.1466 | 1620293886.4781 | 39594.8290 | 0.7395
Random Forest Regressor | 17336.1356 | 873377933.0433 | 28866.6801 | 0.86383
Gradient Boosting | 15925.6580 | 706838477.7589 |   26014.4197 | 0.8879
Support Vector Machine Regressor | 55570.2082 | 6630089672.3575 | 80882.7555 | 0.0537

Based on the provided results, the gradient boosting model performed the best among the evaluated models. It achieved the lowest MAE, MSE, and RMSE, as well as the highest R2 score.

Gradient boosting is an ensemble learning technique that combines multiple weak learners (decision trees in this case) to create a stronger model. It builds the model in an iterative manner, where each new tree is trained to correct the errors made by the previous trees. This approach allows gradient boosting to effectively capture complex relationships and interactions within the data.