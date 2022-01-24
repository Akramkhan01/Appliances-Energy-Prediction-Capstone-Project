# Appliances-Energy-Prediction-Capstone-Project

This project deals with predicting appliances energy consumption of a particular household in Belgium based on the temperature and humidity levels of different rooms in the building and the weather reports in the area over a period of 4.5 months.

The data set is at 10 min for about 4.5 months. The house temperature and humidity conditions were monitored with a ZigBee wireless sensor network. Each wireless node transmitted the temperature and humidity conditions around 3.3 min. Then, the wireless data was averaged for 10 minutes periods. The energy data was logged every 10 minutes with m-bus energy meters. Weather from the nearest airport weather station (Chievres Airport, Belgium) was downloaded from a public data set from Reliable Prognosis (rp5.ru) and merged together with the experimental data sets using the date and time column. Two random variables have been included in the data set for testing the regression models and to filter out non-predictive attributes (parameters).

# Dataset Link
http://archive.ics.uci.edu/ml/datasets/Appliances+energy+prediction

# Dataset Information
Number of instances: 19,735

Number of attributes: 29

# Attribute Information:

date: year-month-day hour:minute:second

T1: Temperature in kitchen area, in Celsius

RH_1: Humidity in kitchen area, in %

T2: Temperature in living room area, in Celsius

RH_2: Humidity in living room area, in %

T3: Temperature in laundry room area

RH_3: Humidity in laundry room area, in %

T4: Temperature in office room, in Celsius

RH_4: Humidity in office room, in %

T5: Temperature in bathroom, in Celsius

RH_5: Humidity in bathroom, in %

T6: Temperature outside the building (north side), in Celsius

RH_6: Humidity outside the building (north side), in %

T7: Temperature in ironing room, in Celsius

RH_7: Humidity in ironing room, in %

T8: Temperature in teenager room 2, in Celsius

RH_8: Humidity in teenager room 2, in %

T9: Temperature in parents’ room, in Celsius

RH_9: Humidity in parents’ room, in %

T_out: Temperature outside (from Chievres weather station), in Celsius

Pressure: (from Chievres weather station), in mm Hg

RH_out: Humidity outside (from Chievres weather station), in %

Wind speed: (from Chievres weather station), in m/s

Visibility: (from Chievres weather station), in km

T_dewpoint: (from Chievres weather station), Â°C

rv1: Random variable 1, non-dimensional

rv2: Random variable 2, non-dimensional

Lights: energy use of light fixtures in the house in Wh

Appliances: energy use in Wh (Target Variable)

Where indicated, hourly data (then interpolated) from the nearest airport weather station (Chievres Airport, Belgium) was downloaded from a public data set from Reliable Prognosis, rp5.ru. Permission was obtained from Reliable Prognosis for the distribution of the 4.5 months of weather data.

# Problem Statement

We should predict Appliance energy consumption for a house based on factors like temperature, humidity & pressure .

In order to achieve this, we need to develop a supervised learning model using regression algorithms. Regression algorithms are used as data consist of continuous features and there is no identification of appliances in the dataset.

# Descriptive Statistical Analysis:

Descriptive statistics are brief descriptive coefficients that summarize a given data set, Descriptive statistics are broken down into measures of central tendency and measures of variability (spread). Measures of central tendency include the mean, median, and mode, while measures of variability include standard deviation, variance, minimum and maximum variables.

# Observations (Temp Feature)
![Capture temp](https://user-images.githubusercontent.com/78207836/150788015-c80666a0-e57e-4f98-88b9-a3f4949dffd8.JPG)

1.The average outside temperature over a period of 4.5 months is around 7.5 degrees. It ranges from -6 - 28 degrees.

2.While the average temperature inside the building has been around 20 degrees for all the rooms. It ranges from 14 - 30 degrees.

3.This implies Warming appliances have been used to keep the insides of the building warm. There must be some sort of direct correlation between temperature and consumption of energy inside the house.

Observations (Humidity Features)
![Capture humid](https://user-images.githubusercontent.com/78207836/150788187-9cb0d9ee-2c09-4b9f-b2da-5b85f08a4fb6.JPG)

1.Average humidity outside the building has been higher than the average humidity inside.

2.Average humidity at the weather station is significantly higher compared to outside humidity near the building.

3.Average humidity in the bathroom is significantly higher compared to other rooms due to obvious reasons.

Heatmap Corelation Between Features:
![download (29)](https://user-images.githubusercontent.com/78207836/150788311-4d026120-e0cc-47aa-b439-aaf6d028f29e.png)

Observations from Heatmap correlation plot:
a. Features related to temperature Almost all the temperature measures in different rooms are highly linearly correlated with each other. However, there is little to no correlation between temperature features and target variables.

b. Features related to humidity Almost all the humidity measures in different rooms are highly linearly correlated with each other. However, there is little to no correlation between humidity features and target variables.

c. Weather data

Dewpoint shows a higher correlation with most of the temperature and humidity level features than any other weather parameters. However, its correlation with the target variable is low. Pressure, wind speed, and visibility show little correlation with temperature and humidity features as well as the target variable.

# PCA on Temperature features:

![download (30)](https://user-images.githubusercontent.com/78207836/150788739-40d1c7ed-4511-433a-b259-3b8f3a7db948.png)

First two components seem to explain more than 91 % of variance in data.

# PCA on Humidity features:
![download (31)](https://user-images.githubusercontent.com/78207836/150788817-295c253b-1fa0-4fc9-9880-68b720d930a3.png)

Similar to temperature first two components seem to explain more than 91 % of variance in data.

# Results:

![Capture](https://user-images.githubusercontent.com/78207836/150788912-d661da72-3093-4240-ab5b-1c34973b916b.JPG)

# Model Result Trained With PCA Features
![download (34)](https://user-images.githubusercontent.com/78207836/150789154-aa9f86a6-0979-49ee-89da-47da3185ba50.png)
![Capture 2](https://user-images.githubusercontent.com/78207836/150789272-766cf780-9d07-4208-80c8-8b4fe3c64190.JPG)

# Model Result Trained without PCA Features
![download (35)](https://user-images.githubusercontent.com/78207836/150789348-6f6e2923-c670-4a45-bd94-4ecf33549151.png)

# Feature Importances:
![download (37)](https://user-images.githubusercontent.com/78207836/150789440-7fa6e70b-b31c-4a80-9f5a-d9f96d292edc.png)

Feature Importances With PCA Features

![download (38)](https://user-images.githubusercontent.com/78207836/150789511-ecc31ada-3d76-4921-bfbe-142af6501318.png)

Feature Importances Without PCA Features

# Conclusion:

1 The humidity and temperature feature has little to no linear correlation with the target variable.

2 The time zone of the day plays an important role in deciding the power consumption of appliances.

3 The best Algorithm to use for this dataset is Extra Trees Regressor (tree-based algorithm).

4 PCA helped us to reduce our feature set dimension considerably without affecting the performance of our models significantly.

5 The untuned model was able to explain 75.50% of the variance (R2 score = 0.7550) on the test set, while the tuned model was able to explain 75.84% of the variance (R2 score = 0.7584).

6 The least RMSE score on the test data set is found to be around 0.5 by the Extra trees regressor model, which is considered good compared to other models.

7 Tree-based models are by far the best model while dealing with a data set that has most of its features have
 no linear correlation with the target variable. For similar reasons, linear
 models such as linear regression, Ridge, and Lasso perform the worst.





