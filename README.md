# Predict Used Car Price

## Introduction
### Problem Statement:

Predict selling price of used cars

### Data details:
This dataset contains information about used cars listed on www.cardekho.com The columns in the given dataset are as follows:
1. name
2. year
3. selling_price
4. km_driven
5. fuel
6. seller_type
7. transmission
8. Owner

### Metric Used:
> * Coefficient of Determination(Def: Proportion of the variance in the dependent variable that is predictable from the independent variable)

## Exploratory Data Analysis:
#### Data View and Cleaning
![Data View](https://github.com/niteshctrl/car-price/blob/master/images/1.png)

* There are 4340 rows with 8 columns each.
* There were no NULL Values and 763 duplicate rows.
* De-duplication left 3577 rows in the dataset.

* Observed abrupt increase in values of 'selling_price' and 'km_driven' after 95 percentiles signifying presence of outliers. The 99th percentile value of 'selling_price' is 2.6M while its max value is 8.9M.

* Most of the cars in the dataset were purchased post 2010 period.

#### Distribution of 'selling Price' of cars
* This shows highly skewed data and might not be suitable for the regressor model.
* Most of the cars have been sold for under ₹2M with the most costly selling going as high as ₹8M. Probably, some premium car.
* Mean and median prices being ₹ 473000 and ₹ 350000 respectively.

> Taking log values of the 'selling_price' minimized the skewness
* This looked much better than the previous one and we will be using this for our modeling.

#### Distribtion of 'km_driven'

* The log transformstion didn't work here as in the case of 'selling_price'.
* Removal of data above 95 quantile made the data less skewed and better for modelling.

## Featurization

This was the trickiest part of the entire project. Here the task is to featurize the various categorical variables in the data into a processable format.
Below are the mentioned features with their transformations:
1. Names: Target Encoding
2. Year : No transformation
3. Selling Price(Dependent Variable) : Log of the corresponding values 
4. Fuel : Ordinal Encoding
5. Seller Type : Ordinal Encoding
6. Transmission : Ordinal Encoding
7. Owner : Ordinal Encoding

A correlation Heatmap after the transformations showed that 'selling_price' is most correlated with 'name', 'transmission', 'year' and then 'fuel' but 'log_selling_price' is with 'year', 'name' , 'fuel' and then 'transmission'.


## Model Exploration

Models tried were:
1. Linear Regression : R-squared = -1.22
2. SVM Regressor : R-squared = 0.6150
3. Random Forest : R-squared = 0.8665
4. Gradient Boosted Decision Trees : R-squared = 0.6892

## Conclusion

> * The best output came from **Random Forest** with a R-squared value of **0.8665**.
> * I used RandomizedSearch for Hyperpaprameter tuning with default 5-fold CV technique. The best parameters came out to be n_estimators = 700 and criterion='mae'.
