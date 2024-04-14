# Predicting-the-number-of-rings-in-an-abalone

The dataset has been sourced from the UCI Machine Learning Repository : https://archive.ics.uci.edu/dataset/1/abalone

Predicting the age of abalone from physical measurements.  The age of abalone is determined by cutting the shell through the cone, staining it, and counting the number of rings through a microscope -- a boring and time-consuming task.  Other measurements, which are easier to obtain, are used to predict the age.  Further information, such as weather patterns and location (hence food availability) may be required to solve the problem.

From the original data examples with missing values were removed (the majority having the predicted value missing), and the ranges of the continuous values have been scaled for use with an ANN (by dividing by 200).

Given is the attribute name, attribute type, the measurement unit and a brief description.  The number of rings is the value to predict: either as a continuous value or as a classification problem.

Name / Data Type / Measurement Unit / Description
-----------------------------
Sex / nominal / -- / M, F, and I (infant)
Length / continuous / mm / Longest shell measurement
Diameter	/ continuous / mm / perpendicular to length
Height / continuous / mm / with meat in shell
Whole weight / continuous / grams / whole abalone
Shucked weight / continuous	 / grams / weight of meat
Viscera weight / continuous / grams / gut weight (after bleeding)
Shell weight / continuous / grams / after being dried
Rings / integer / -- / +1.5 gives the age in years

The dataset has been divided among the train and test
train.csv - the training dataset; Rings is the integer target
test.csv - the test dataset; objective is to predict the value of Rings for each row. 

From operforming the initial analysis, 
Sex is the only categorical column 
![image](https://github.com/aakriti-nag/Predicting-the-number-of-rings-in-a-abalone/assets/166777298/ac1251a7-da41-4900-b9e1-ecf8a3a3c1df)

The target variable 'Rings' from the train dataset has values ranging from 1 to 29. 
![image](https://github.com/aakriti-nag/Predicting-the-number-of-rings-in-a-abalone/assets/166777298/3e790969-4775-427a-b094-9ae6b0fd7772)

Considering, sex was the only categorical column, it was converted to numeric using LabelEncoder(), thus Female - 0, Infant - 1, Male-2.

For scaling, and understanding the distribution of the data, performed both outlier detection and log transofrmation. Outlier detection was chosen instead cause performing, log transformation and later calculation RMSLE affected the values, and got the best values when removed the outliers. 
![image](https://github.com/aakriti-nag/Predicting-the-number-of-rings-in-a-abalone/assets/166777298/4ec8b833-951c-46d9-8e55-14da84233771)

Performed multple regression methods to best the best values for RMSLE with, 
1. Linear regresssion
2. Decision Tree Regression
3. XGBoost Regressor
4. Random Forest Regressor

XGBoost performed best, and after performing hyperparameter tuning with L1, L2 reguralization, and cross validation, and also trying with GridSearchCV the best parameters were chosen to perform the final XGBoost model, and resulting the RMSLE value of 0.14, concluded the prediction. 

The RMSLE is Root Mean Squared Logarithmic Error, which is calculated as: sqrt(1/𝑛(log(1+𝑦̂𝑖)−log(1+𝑦𝑖))^2) where:

𝑛 is the total number of observations in the test set,
𝑦̂𝑖 is the predicted value of the target for instance (i),
𝑦𝑖 is the actual value of the target for instance (i), and,
log is the natural logarithm.

And the best features was found to be : 
![image](https://github.com/aakriti-nag/Predicting-the-number-of-rings-in-a-abalone/assets/166777298/e852e556-3909-43d9-8da6-eede44cef499)






