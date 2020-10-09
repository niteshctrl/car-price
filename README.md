# Predict Used Car Price

# Table of Contents:

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

#### Percentile description of the cleaned data:
![Description](https://github.com/niteshctrl/car-price/blob/master/images/3.png)

* Observe abrupt increase in values of selling_price and km_driven at tail signifying presence of outliers.

#### Distribution of 'year' in which the cars were purchased
![Distn of year](https://github.com/niteshctrl/car-price/blob/master/images/4.png)

* Most of the cars in the dataset were purchased post 2010 period.

#### Distribution of 'selling Price' of cars
![Dist Selling Price](https://github.com/niteshctrl/car-price/blob/master/images/5.png)
* This is highly skewed data and might probably damage the regressor model.
* Most of the cars have been sold for under ₹2M with the most costly selling going as high as ₹8M. Probably, some premium car.
* 75th percentile is at ₹ 6lakh or ₹ 600,000.
* Mean and median prices being ₹ 473000 and ₹ 350000 respectively.

#### Distribution of log values of 'selling_price'
![log Distribution](https://github.com/niteshctrl/car-price/blob/master/images/6.png)
* This looks much better than the previous one and we will be using this for our modeling.

#### Distribtion of 'km_driven'
![km_driven distribution](https://github.com/niteshctrl/car-price/blob/master/images/7.png)
#### Distribution of 'km_driven' with removed data points
![km_driven with removed points](https://github.com/niteshctrl/car-price/blob/master/images/8.png)
* The log trick didn't work here as in the case of 'selling_price'.
* Removal of data above 95 quantile makes the data less skewed and better for modelling.
* Mean distance driven = 69250 km
* Median distance driven = 60000 km


