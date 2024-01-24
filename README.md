# HousePrices_AdvancedRegression
Prediction of Housing Prices at Ames, Iowa

# Business Understanding
Price of a house depends on various attributes of the house including but not limited to area of the house, number of floors, number of bedrooms, materials used to build the house, location, proximity to various services, etc. The data provided (from this [Kaggle Dataset](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)) contains most of these aspects of resedential homes in Ames, Iowa which can be used to determine the selling price of a house. This is precisely the endeavour of the current undertaking.

# Data Understading
Initial inspection of the dataset shows that there are multiple columns with `NaN` values which necessitate data cleaning and missing value handling. There are also categorical columns such as `MSSubClass` which have categorical values as numeric labels, so they must be carefully and correctly handled as categorical columns and the labels must not be used as numerical variables.

There are also multiple categorical variables with object type categories but belonging to a qualitative rating, so they can be converted to numerical ratings because those ratings themself have a value that can be quantified, so they must also be converted accordingly. 

`Condition1` and `Condition2` columns have represent proximity to various conditions, but they represent the same attribute and `Condition2` column is only populated for houses with multiple conditions. Therefore these variables can be converted using one-hot encoding but since `Condition2` may have many Null values, a single encoding must be made to capture presence/absence of conditions from both these columns.

The understanding mentioned above is not exhaustive and more detailed analysis will be done on each feature at a later stage to process it and use it correctly in model building.

# Analysis Steps:
- Data is cleaned as per data understanding
- EDA performed to better identify trends in the data
- Data preprocessing and dimensionality reduction performed using PCA
- 4 Regression models were built and their cross validation scores were compared
- Final results communicated
  
# Model Comparisons

|Model | Cross Validation (Average RMSE) | Final RMSE Train| 
|------|---------------------------------|-----------------|
| Linear reg | 42883.62 | 32308.64 |
| Ridge  | 39558.08 | 32310.11 |
| Lasso  | 42883.51 | 32308.64 |
| K-nearest neighbour | 42440.54 | 35302.41 |

# Final Conclusions
- The best model among the explored regression models is Ridge linear regression model with a cross validation RMSE of approximately 39,500. 

- Both simple linear regression and Lasso linear regression give the exact same outputs for RMSE suggesting that the L1 penalization isn't ideal, this is because the dimensionality reduction has already been done using PCA and the L1 penalization isn't dropping any extra features. 

- The KNN Regressor is the worst performer among the ones explored.

- Other models and hyperparameter tuning can potentially give better outputs. 
