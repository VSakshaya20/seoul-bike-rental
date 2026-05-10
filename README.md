# RENT-A-BIKE: Studying the Factors Associated with Bike Rental Demand

This project was developed as part of ISSS602 — Data Analytics Lab coursework for our Master of IT in Business programme at Singapore Management University.

A statistical modelling project that examines how atmospheric and temporal factors are associated with hourly bike rental demand in Seoul, South Korea, using Poisson and Negative Binomial regression models.

## Overview

Bike-sharing systems support sustainable urban mobility by reducing traffic congestion and encouraging short-distance travel. This project analyses Seoul Public Bike rental demand and identifies the key factors associated with variation in hourly bike rentals across one year of observations.

The study focuses on both weather-related and time-related variables, and compares two count-data modelling approaches to determine which is more appropriate for the dataset: Poisson regression and Negative Binomial regression.

## Objectives

The project was designed to:

- Identify atmospheric and temporal variables that have a statistically significant relationship with bike rental demand.
- Determine the direction of these relationships and interpret their practical meaning.
- Provide insights that can support bike supply planning, maintenance, and operational decisions for the Seoul Metropolitan Government.

## Dataset

The analysis uses a dataset derived from prior research on Seoul bike rental demand and covers one year of hourly public bike rental data from December 2017 to November 2018.

After removing records where the bike-sharing system was not functioning, 8,465 observations were retained for analysis.

## Variables Used

### Response variable
- `Rented_bike_count`: hourly count of rented bikes

### Atmospheric variables
- `Rainfall`
- `Snowfall`
- `Solar_radiation`
- `Visibility`
- `Windspeed`
- `THI` (Temperature-Humidity Index)

### Temporal variables
- `Holiday`
- `Seasons`
- `Weekday_Weekend`

## Methodology

The project applies Generalized Linear Models for count data, specifically:

- **Poisson Regression**, which assumes the mean and variance are equal
- **Negative Binomial Regression**, which is better suited when the variance exceeds the mean, i.e. when overdispersion is present

A correlation review was also performed before modelling. Due to a strong positive correlation between `dew_point_temp` and `THI`, `dew_point_temp` was excluded to reduce multicollinearity and improve model stability.

Model performance was compared using:

- Akaike Information Criterion (AIC)
- Bayesian Information Criterion (BIC)

## Key Findings

- The Negative Binomial model outperformed the Poisson model, with much lower AIC and BIC values, indicating a better fit for the bike rental count data.
- The data showed clear overdispersion: the mean rented bike count was 729.16, while the variance was 412,613.52, which strongly supports the use of the Negative Binomial model over Poisson regression.
- All selected atmospheric and temporal predictors were statistically significant at the 5% level in the final Negative Binomial model.

### Temporal insights
- Bike rentals were about 30% lower on holidays than on non-holidays.
- Bike rentals were about 20% higher on weekdays than on weekends, suggesting stronger commuting-related demand on working days.
- Compared with winter, expected rentals were highest in autumn, followed by spring and summer.

### Atmospheric insights
- Rainfall and snowfall were negatively associated with bike rental demand.
- Solar radiation, visibility, windspeed, and THI showed positive associations with bike rental demand.

## Interpretation

The results suggest that Seoul’s bike-sharing usage is shaped by both commuting behavior and weather conditions. Weekday peaks reflect practical transport use, while lower rentals on holidays indicate reduced commuter activity.

Favourable weather conditions are associated with greater bike usage, while rain and snow reduce demand. These findings can help guide bike deployment, maintenance planning, and service availability under different conditions.

## Tools Used

- SAS Viya
- SAS Visual Analytics
- Generalized Linear Modelling
- Exploratory Data Analysis
- Regression model comparison using AIC and BIC 

## Why this project matters

This project demonstrates the application of statistical modelling to a real-world urban mobility problem. It shows how count-data methods can be used to generate operational insights from public transportation usage data.

It also highlights skills in data preparation, variable engineering, model selection, interpretation of coefficients, and translating statistical findings into practical recommendations.

## Team Members

- Akshaya Vijayakumar Sivakami
- Nazia Faisalkhan Faruqui
- Venes Bolo Aurellano 
