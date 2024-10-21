# NSE-All-Shares-Predicting-value-usingARIMA-SARIMAX
This repository contains a comprehensive analysis and implementation of time series forecasting for the National Stock Exchange (NSE) All Shares index using ARIMA and SARIMAX models. The goal is to predict future values of the index based on historical data, providing insights into potential market trends.
ARIMA and SARIMAX

1. ARIMA (AutoRegressive Integrated Moving Average)

Overview
ARIMA is a popular statistical model used for time series forecasting. It combines three components:

AR (AutoRegressive): Uses the dependency between an observation and a number of lagged observations (previous time steps).
I (Integrated): Represents the differencing of raw observations to make the time series stationary.
MA (Moving Average): Uses the dependency between an observation and a residual error from a moving average model applied to lagged observations.
Mathematical Representation
The ARIMA model is represented as ARIMA(p, d, q), where:

p: Order of the autoregressive part
d: Degree of differencing
q: Order of the moving average part
The general form of the ARIMA model can be expressed as:

$$
Y_t = c + \phi_1 Y_{t-1} + \phi_2 Y_{t-2} + ... + \phi_p Y_{t-p} + \theta_1 \epsilon_{t-1} + \theta_2 \epsilon_{t-2} + ... + \theta_q \epsilon_{t-q} + \epsilon_t
$$
​	
Where:
- \( Y_t \) is the value at time \( t \),
- \( c \) is a constant,
- \( \phi \) are the AR parameters,
- \( \theta \) are the MA parameters,
- \( \epsilon \) is white noise (error term).

Stationarity
For ARIMA to be effective, the time series must be stationary. This means that its statistical properties (mean, variance) do not change over time. The differencing operation, often referred to as the "difference function," helps achieve this by subtracting the previous observation from the current observation:

$$
Y'_t = Y_t - Y_{t-1}
$$

 
This process is repeated \( d \) times if necessary.


2. SARIMAX (Seasonal AutoRegressive Integrated Moving Average with eXogenous regressors)

### Overview
SARIMAX extends ARIMA by adding seasonal components and the ability to include exogenous variables (external predictors). This makes it suitable for time series data that exhibit seasonal patterns.

The SARIMAX model is represented as \( \text{SARIMAX}(p, d, q)(P, D, Q, s) \), where:
- **p, d, q**: Non-seasonal parameters (as defined in ARIMA).
- **P, D, Q**: Seasonal parameters.
- **s**: Length of the seasonal cycle.

The SARIMAX model can be expressed as:

$$
Y_t = c + \sum_{i=1}^{p} \phi_i Y_{t-i} + \sum_{j=1}^{q} \theta_j \epsilon_{t-j} + \sum_{k=1}^{P} \Phi_k Y_{t-k \cdot s} + \sum_{l=1}^{Q} \Theta_l \epsilon_{t-l \cdot s} + \epsilon_t
$$

Where:
Where the terms involving \( \Phi \) and \( \Theta \) account for the seasonal components. To achieve stationarity in seasonal time series, seasonal differencing is used:


$$
Y'_t = Y_t - Y_{t-s}
$$
​	
 
This accounts for the seasonality by removing periodic fluctuations.

Conclusion

ARIMA and SARIMAX models are powerful tools for time series forecasting, allowing for both trend and seasonal analysis. Ensuring stationarity through differencing is crucial for the effectiveness of these models.

## Overview

The analysis involves:

* Analyzing the Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) to determine appropriate model parameters.
* Fitting ARIMA and SARIMAX models to the differenced price data.
* Evaluating model performance using Mean Squared Error (MSE) and R-squared values.
##Autocorrelation and Partial Autocorrelation

ACF Values:
```markdown

```[1.0, 0.26179462, 0.11839793, 0.1109589, 0.12213969, 0.13264605,
 0.1126691, 0.09946351, 0.05312527, 0.1038283, 0.08697549, 0.0481756,
 0.06320687, 0.0430556, 0.07369887, 0.0165915, 0.05894618, 0.05199751,
 0.03460312, 0.01246014, -0.01364457, -0.00347308, -0.02774139, -0.00302039,
 -0.02520741, -0.01822235, 0.01085024, -0.02061389, 0.0183588, -0.01151293,
 -0.00367243, 0.00442698, -0.00371038, -0.01230855, 0.02847172, 0.04255121,
 0.03399034, 0.02829015, 0.00209405, 0.03483796, 0.00873389]
```

PACF Values:

```markdown
[1.0, 0.26193799, 0.05359329, 0.07291839, 0.07791967, 0.0799416,
 0.04940522, 0.04093098, -0.00848942, 0.0677755, 0.02200109, -0.00893245,
 0.02566624, -0.00454194, 0.03946601, -0.03739493, 0.03957783, 0.01305921,
 -0.00199065, -0.02211353, -0.03270929, -0.01462688, -0.03840061, -0.0019558,
 -0.02599983, -0.00349149, 0.0199767, -0.02009847, 0.03477457, -0.01059519,
 0.00282011, 0.01385557, -0.00394655, -0.01034384, 0.04622673, 0.02885167,
 0.02921025, 0.01205769, -0.01221488, 0.03382178, -0.0240496]

```

## ARIMA Model Results

Best Model: ARIMA(1, 0, 2)
* Log Likelihood: -13618.529
* AIC: 27247.058
* BIC: 27274.612
* HQIC: 27257.221

Ljung-Box Test:

* Q-statistic: 0.03, Prob(Q): 0.86
Model Performance
* Mean Squared Error (MSE): 6346.222
* R-squared: 0.900

## SARIMAX Model Results

Model: SARIMAX(2, 1, 1)x(1, 0, [], 5)
*og Likelihood: 19.325
* AIC: -28.650
* BIC: -31.718
* HQIC: -35.384

Ljung-Box Test:

* Q-statistic: 0.06, Prob(Q): 0.81

## I used some techniques to prove stationarity and find the p, d, q values for the ARIMA model, specifically using order=(1, 0, 1) and seasonal_order=(1, 0, 1, 5). I utilized auto_arima to determine the optimal ARIMA and SARIMAX parameters, and I employed custom functions for hyperparameter tuning.

