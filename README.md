# Linear Time Series Assignment

## Overview
This project focuses on the analysis and forecasting of a time series dataset, specifically the **industrial production indices** for ornamental and construction stones, industrial limestone, gypsum, chalk, and slate. These indices are critical in monitoring changes in industrial activity in France and contribute to macroeconomic indicators like the GDP flash estimate.

The primary objective of the project is to perform time series decomposition, unit root tests, model selection, and forecasting. The analysis includes **Augmented Dickey-Fuller (ADF) Test**, **Kwiatkowski-Phillips-Schmidt-Shin (KPSS) Test**, **ARIMA model selection**, and **Granger Causality Testing**. The project also explores the computation of confidence intervals and regions using prediction errors, along with residual analysis.

## Table of Contents
1. [Introduction](#introduction)
2. [Methodology](#methodology)
   - [Time Series Decomposition](#time-series-decomposition)
   - [Stationarity Testing (ADF and KPSS)](#stationarity-testing)
   - [Model Selection (ARIMA)](#model-selection)
   - [Forecasting](#forecasting)
   - [Granger Causality Test](#granger-causality-test)
3. [Results and Discussion](#results-and-discussion)
4. [Appendix](#appendix)
   - [Proof for 95% Confidence Interval](#proof-for-95-confidence-interval)
   - [Hypothesis Testing on Residuals](#hypothesis-testing-on-residuals)
   - [Code in R](#code-in-r)

## Introduction
The time series chosen for this analysis represents the monthly industrial production indices from 1990 to 2018. The series is seasonally adjusted, allowing us to focus on trends and stationarity analysis. The series is key for business cycle tracking and is an important macroeconomic indicator.

## Methodology

### Time Series Decomposition
The series is decomposed into its trend component using the `decompose()` function in R. This helps us identify the underlying increasing trend over the 28 years.

### Stationarity Testing
Two main tests were used to check stationarity:
- **Augmented Dickey-Fuller (ADF) Test**: Initially, the ADF test shows that the series is not stationary, confirmed by the presence of autocorrelated residuals. After differencing the series once, stationarity is achieved.
- **KPSS Test**: This test also shows that the original series is not stationary, but confirms that the differentiated series is stationary.

### Model Selection (ARIMA)
After achieving stationarity, ARIMA models were fitted. Using the ACF and PACF plots, the best-fit model selected is **ARIMA(0,1,1)** for the differentiated series. The validity of the model is checked using the Ljung-Box test to ensure no autocorrelation in the residuals.

### Forecasting
The project forecasts future values using the ARIMA model, along with the computation of **95% prediction intervals**. Both univariate and bivariate confidence regions are computed for the forecasts.

### Granger Causality Test
The Granger Causality Test is employed to check if another time series, \( Y_t \), can help improve the prediction of \( X_t \) at time \( T+1 \). The test involves fitting Vector Auto Regressive (VAR) models and performing Wald tests to determine causality.

## Results and Discussion
The results show that the differentiated series follows an **ARIMA(0,1,1)** model, with residuals showing no autocorrelation, indicating a good fit. The project highlights the role of proper differentiation and residual testing in achieving accurate forecasts. Granger causality analysis suggests that incorporating additional time series data could further improve predictive accuracy.

## Appendix

### Proof for 95% Confidence Interval
Detailed proof is provided for calculating univariate and bivariate 95% confidence intervals based on the assumption that residuals follow a normal distribution.

### Hypothesis Testing on Residuals
Residuals were tested for normality using **Shapiro-Wilk** and **Jarque-Bera tests**. Results show deviations from normality, as indicated by the Q-Q plots.

### Code in R
The entire analysis was performed using **R**. Key libraries include:
- `zoo` for time series handling
- `tseries` for time series analysis
- `fUnitRoots` for stationarity testing

You can find the code used for time series decomposition, stationarity tests, ARIMA modeling, and forecasting in the Appendix.

### Dataset
The data for these indices can be accessed from the following link: [CVS-CJO index of industrial production](https://www.insee.fr/fr/statistiques/serie/010767595#Tableau)

### Authors
- Kanupriya Jain
- Soumodeep Hoodaty

