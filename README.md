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
