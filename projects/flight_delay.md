---
layout: default
title: "Flight Delay Prediction: Is Bad Weather Really to Blame?"
section: Data Science Projects
description: "PySpark and Spark MLlib classification of departure delays across 4.5 million U.S. flights, comparing weather and operational factors."
---

[← Back to Data Science Projects]({{ "/Data%20Science%20Projects/" | relative_url }})

## Flight Delay Prediction: Is Bad Weather Really to Blame?

### Skills Demonstrated

*PySpark · Spark SQL · Spark MLlib Pipelines · Logistic Regression · Linear SVM · Decision Tree · One-Hot Encoding · Feature Selection · Cross-Validation · Hyperparameter Tuning · Model Evaluation (F1, AUC)*

---

### Overview

Inclement weather is often blamed when a flight leaves late. But how much of the delay is really the weather But how much of the delay is really the weather? To find out, I analyzed 4.5 million U.S. domestic flights from 2019, with 30 variables combining flight records from the Bureau of Transportation Statistics, daily weather observations from NOAA, and airport, airline, and staffing information. My goal was to find the best model for predicting whether a flight departs at least 15 minutes late, and to test how much weather contributes compared with factors airlines control.

Exploring the data with Spark SQL challenged my expectations. The months with the most departure delays were June, July, and August, not winter as I had assumed.

![Departure delays by month]({{ "/images/flights_delay_by_month.png" | relative_url }})
<br><small><em>Figure 1. Number of delayed departures by month in 2019. Summer months had the most delays.</em></small>

Even on the days with the most extreme weather, outcomes were mixed: on the day with the heaviest snowfall, some flights were delayed and others left on time. This suggested weather alone could not explain delays.

![Flight outcomes on extreme weather days]({{ "/images/flights_extreme_weather.png" | relative_url }})
<br><small><em>Figure 2. Outcomes for a sample of 20 flights on each of the days with the maximum precipitation, snowfall, snow depth, and wind speed. About 19% of all flights in the dataset were delayed.</em></small>

To test this formally, I built an end-to-end PySpark pipeline that encodes carrier and airport as one-hot features, combines them with aircraft, staffing, and weather variables, and trains three classifiers: logistic regression, a linear support vector machine, and a decision tree. Data were split 70/30 into training and test sets. I then created two reduced feature sets, one with weather conditions only (precipitation, snowfall, snow depth, temperature, wind) and one with only factors under human control (such as seats per aircraft, flight attendants and ground staff per passenger, aircraft age, carrier, and airport), and trained all three models on each. Logistic regression was also tuned with 3-fold cross-validation over 12 combinations of regularization settings.

Because the data were imbalanced, I compared models using F1 score and area under the ROC curve (AUC), rather than accuracy. Weather-only models did not outperform models built on operational factors, and the full feature set performed best: logistic regression reached an area under the ROC curve (AUC) of 0.60, compared with 0.50–0.58 for the other models, and cross-validation tuning did not improve it. Inclement weather plays a limited role on its own. Delays are better explained by weather and operations together: an airport unprepared for a storm, or air traffic control restrictions on a clear day.

Looking back, the main limitation was class imbalance: only about 19% of flights were delayed, so the models had difficulty learning to identify the delayed class. Future work would address this with class weights or resampling, add features such as departure time of day and historical delay rates, and try tree ensembles such as gradient-boosted trees.

---

[← Back to Data Science Projects]({{ "/Data%20Science%20Projects/" | relative_url }})
