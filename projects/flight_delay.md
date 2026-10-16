---
layout: default
title: "Flight Delay Prediction: Is Bad Weather Really to Blame?"
description: "PySpark and Spark MLlib classification of departure delays across 4.5 million U.S. flights, comparing weather and operational factors."
---

[← Back to Data Science Projects](https://timondm0704.github.io/Data%20Science%20Projects/)

## Flight Delay Prediction: Is Bad Weather Really to Blame?

*MS Applied Data Analytics, Boston University (2022) · Term project, MET CS 777 Big Data Analytics*

### Skills Demonstrated

*PySpark · Spark SQL · Spark MLlib Pipelines · Logistic Regression · Linear SVM · Decision Tree · One-Hot Encoding · Feature Selection · Cross-Validation · Hyperparameter Tuning · Model Evaluation (F1, AUC)*

---

### Overview

When a flight leaves late, airlines often point to bad weather. But how much of the delay is really the weather? To find out, I analyzed 4.5 million U.S. domestic flights from 2019, with 30 variables combining flight records from the Bureau of Transportation Statistics, daily weather observations from NOAA, and airport, airline, and staffing information. My goal was to find the best model for predicting whether a flight departs at least 15 minutes late, and to test how much weather contributes compared with factors airlines control.

Exploring the data with Spark SQL challenged my expectations. The months with the most departure delays were June, July, and August, not winter as I had assumed. Even on the days with the most extreme weather, outcomes were mixed: on the day with the heaviest snowfall, some flights were delayed and others left on time. This suggested weather alone could not explain delays.

To test this formally, I built an end-to-end PySpark pipeline that encodes carrier and airport as one-hot features, combines them with aircraft, staffing, and weather variables, and trains three classifiers: logistic regression, a linear support vector machine, and a decision tree. Data were split 70/30 into training and test sets. I then created two reduced feature sets, one with weather conditions only (precipitation, snowfall, snow depth, temperature, wind) and one with only factors under human control (such as seats per aircraft, flight attendants and ground staff per passenger, aircraft age, carrier, and airport), and trained all three models on each. Logistic regression was also tuned with 3-fold cross-validation over 12 combinations of regularization settings.

Weather-only models were no more predictive than models built on operational factors, and the full feature set performed best, with logistic regression reaching an area under the ROC curve (AUC) of 0.60. Bad weather plays a limited role on its own. Delays are better explained by weather and operations together: an airport unprepared for a storm, or air traffic control restrictions on a clear day. The results also carried a methodological lesson. Every model reached 0.81 accuracy, exactly the share of on-time flights, because with only about 19% of flights delayed, the models learned to predict "on time" almost always. Accuracy alone was misleading here, and future work would address the class imbalance (class weights or resampling), add departure time of day and historical delay rates, and try tree ensembles such as gradient-boosted trees.

---

### Figures

![Departure delays by month](https://timondm0704.github.io/images/flights_delay_by_month.png)  
*Figure 1. Number of delayed departures by month in 2019. Summer months had the most delays.*

![Flight outcomes on extreme weather days](https://timondm0704.github.io/images/flights_extreme_weather.png)  
*Figure 2. Delayed and on-time departures on the days with the maximum precipitation, snowfall, snow depth, and wind speed.*

![Model comparison](https://timondm0704.github.io/images/flights_model_results.png)  
*Figure 3. F1 score, AUC, and accuracy for logistic regression, SVM, and decision tree models across feature sets.*

---

[← Back to Data Science Projects](https://timondm0704.github.io/Data%20Science%20Projects/)
