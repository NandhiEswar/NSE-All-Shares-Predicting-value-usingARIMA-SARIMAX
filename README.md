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

Y
t
=
c
+
ϕ
1
Y
t
−
1
+
ϕ
2
Y
t
−
2
+
.
.
.
+
ϕ
p
Y
t
−
p
+
θ
1
ϵ
t
−
1
+
θ
2
ϵ
t
−
2
+
.
.
.
+
θ
q
ϵ
t
−
q
+
ϵ
t
Y 
t
​	
 =c+ϕ 
1
​	
 Y 
t−1
​	
 +ϕ 
2
​	
 Y 
t−2
​	
 +...+ϕ 
p
​	
 Y 
t−p
​	
 +θ 
1
​	
 ϵ 
t−1
​	
 +θ 
2
​	
 ϵ 
t−2
​	
 +...+θ 
q
​	
 ϵ 
t−q
​	
 +ϵ 
t
​	
 
Where:

Y
t
Y 
t
​	
  is the value at time 
t
t,
c
c is a constant,
ϕ
ϕ are the AR parameters,
θ
θ are the MA parameters,
ϵ
ϵ is white noise (error term).
Stationarity
For ARIMA to be effective, the time series must be stationary. This means that its statistical properties (mean, variance) do not change over time. The differencing operation, often referred to as the "difference function," helps achieve this by subtracting the previous observation from the current observation:

Y
t
′
=
Y
t
−
Y
t
−
1
Y 
t
′
​	
 =Y 
t
​	
 −Y 
t−1
​	
 
This process is repeated 
d
d times if necessary.

2. SARIMAX (Seasonal AutoRegressive Integrated Moving Average with eXogenous regressors)

Overview
SARIMAX extends ARIMA by adding seasonal components and the ability to include exogenous variables (external predictors). This makes it suitable for time series data that exhibit seasonal patterns.

Mathematical Representation
The SARIMAX model is represented as SARIMAX(p, d, q)(P, D, Q, s), where:

p, d, q: Non-seasonal parameters (as defined in ARIMA).
P, D, Q: Seasonal parameters.
s: Length of the seasonal cycle.
The SARIMAX model can be expressed as:

Y
t
=
c
+
∑
i
=
1
p
ϕ
i
Y
t
−
i
+
∑
j
=
1
q
θ
j
ϵ
t
−
j
+
∑
k
=
1
P
Φ
k
Y
t
−
k
⋅
s
+
∑
l
=
1
Q
Θ
l
ϵ
t
−
l
⋅
s
+
ϵ
t
Y 
t
​	
 =c+ 
i=1
∑
p
​	
 ϕ 
i
​	
 Y 
t−i
​	
 + 
j=1
∑
q
​	
 θ 
j
​	
 ϵ 
t−j
​	
 + 
k=1
∑
P
​	
 Φ 
k
​	
 Y 
t−k⋅s
​	
 + 
l=1
∑
Q
​	
 Θ 
l
​	
 ϵ 
t−l⋅s
​	
 +ϵ 
t
​	
 
Where:

The terms involving 
Φ
Φ and 
Θ
Θ account for the seasonal components.
Seasonal Differencing
To achieve stationarity in seasonal time series, seasonal differencing is used:

Y
t
′
=
Y
t
−
Y
t
−
s
Y 
t
′
​	
 =Y 
t
​	
 −Y 
t−s
​	
 
This accounts for the seasonality by removing periodic fluctuations.

Conclusion

ARIMA and SARIMAX models are powerful tools for time series forecasting, allowing for both trend and seasonal analysis. Ensuring stationarity through differencing is crucial for the effectiveness of these models.
