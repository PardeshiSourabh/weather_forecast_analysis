# OnPoint Weather Forecast - Machine Learning for Time Series Analysis of Weather Forecast Anomaly Data

## ABOUT THE DATASET

OnPoint Weather is a global weather dataset for business available for any latitutde/longitude point and geographic area such as ZIP codes. OnPoint Weather provides a continuum of hourly and daily weather from the year 2000 to current time and a forward forecast of 45 days.
Weather has a significant impact on businesses and accounts for hundreds of billions in lost revenue annually. OnPoint Weather allows businesses to quantify weather impacts and develop strategies to optimize for weather to improve business performance.
The Dataset can be found at https://console.cloud.google.com/marketplace/details/weathersource-com/weather-forecast

## Analysis Tool: BigQuery
BigQuery is a fully-managed data warehouse on RESTful web service that enables scalable, cost-effective and fast analysis of big data working in conjunction with Google Cloud Storage. It is a serverless Software as a Service (SaaS) that may be used complementarily with MapReduce. It also has built-in machine learning capabilities.
More details about BigQuery can be found at https://cloud.google.com/bigquery

## Datalab equipped with the BigQuery API

Cloud Datalab is a powerful interactive tool created to explore, analyze, transform, and visualize data and build machine learning models on Google Cloud Platform. It runs on Compute Engine and connects to multiple cloud services easily so you can focus on your data science tasks. We use this feature with the BigQuery API for a seamless execution of our machine learning project
![Datalab](data/datalab_bq.png)

## DATA PREPROCESSING

We are using Weather Source's OnPoint Climatology Data, which is essentially the statistics of weather over time. Climatology data can be useful in two ways - It allows users to compare weather to what should be ‘normal’ weather for a place and time. This allows for finding 'Anomalies' in the weather, that is, whether parameters like Temperature, Humidity, Air Pressure etc are 'Departing from Normal' . Often it’s the departure from normal that has the biggest influence on consumers and the greater the departure from normal the greater it's effect on customers and consequently, the Business.
For this Project, we are considering United States climatology data for Hourly and Daily weather statistics.
Data Columns:

Postal Code  
Country Code  
Valid date/time (UTC)  
Day of Year (UTC)  
Hour of the day (UTC)  
Valid date/time (Local Time)  
Daylight Saving Time Offset (Minutes)  
Air Temperature (F)  
Wet Bulb Temperature (F)  
Dew Point Temperature (F)  
Feels Like Temperature (F)  
Wind Chill Temperature (F)  
Heat Index Temperature (F)  
Relative Humidity (percent)  
Specific Humidity (grams/kilogram)  
Surface Pressure (millibars)  
Pressure Tendency (millibars)  
Mean Sea Level Pressure (millibars)  
Wind Speed at 10 meter height (mph)  
Wind Direction at 10 meter height (degrees)  
Wind Speed at 80 meter height (mph)  
Wind Direction at 80 meter height (degrees)  
Wind Speed at 100 meter height (mph)  
Wind Direction at 100 meter height (degrees)  
Total Precipitation Amount (in)  
Total Snowfall Amount (in)  
Cloud Cover (percent)  
Solar Radiation (watts/m^2)  

## RESEARCH QUESTION
What patterns can we observe in weather forecast errors which we can analyze and debug? Optimizing these predictions by avoiding such errors in data can possibly save weather forecast companies billions of dollars in revenue.

## ARIMA

ARIMA stands for Autoregressive Integrated Moving Average. In statistics and econometrics, and in particular in time series analysis, an autoregressive integrated moving average (ARIMA) model is a generalization of an autoregressive moving average (ARMA) model. Both of these models are fitted to time series data either to better understand the data or to predict future points in the series (forecasting). ARIMA models are applied in some cases where data show evidence of non-stationarity, where an initial differencing step (corresponding to the "integrated" part of the model) can be applied one or more times to eliminate the non-stationarity.

Here is a mathematical definition of ARIMA from Wikipedia
![ARIMA](data/arima_def.png)

The AR part of ARIMA indicates that the evolving variable of interest is regressed on its own lagged (i.e., prior) values. The MA part indicates that the regression error is actually a linear combination of error terms whose values occurred contemporaneously and at various times in the past. The I (for "integrated") indicates that the data values have been replaced with the difference between their values and the previous values (and this differencing process may have been performed more than once). The purpose of each of these features is to make the model fit the data as well as possible.

Non-seasonal ARIMA models are generally denoted ARIMA(p,d,q) where parameters p, d, and q are non-negative integers, p is the order (number of time lags) of the autoregressive model, d is the degree of differencing (the number of times the data have had past values subtracted), and q is the order of the moving-average model. Seasonal ARIMA models are usually denoted ARIMA(p,d,q)(P,D,Q)m, where m refers to the number of periods in each season, and the uppercase P,D,Q refer to the autoregressive, differencing, and moving average terms for the seasonal part of the ARIMA model.[4][5]

## Dashboards
The key takeaway from this plot is that all indices are affected globally. Sudden changes in temperature affects all of these regions at the same time which also signifies that these indices are correlated. Although, the funny thing about weather forecasts is that yesterdays weather may or may not affect todays weather. This is an important fact to be noted when dealing with Time Series.

![AvgTemp](charts/EDA_Page_1.jpg)
![AvgTempPct](charts/EDA_Page_2.jpg)
![Dashboard](charts/EDA_Page_3.jpg)

## REFERENCES
[1] Understanding, modeling and predicting weather and climate extremes: Challenges and opportunities
JanaSillmann Thordis Thorarinsdottir Noel Keenlyside Nathalie Schaller Lisa V. Alexander Gabriel Hegerl Sonia I.Seneviratne Robert Vautard Xuebin Zhang Francis W.Zwiersi
https://www.sciencedirect.com/science/article/pii/S2212094717300440

[2] Predicting uncertainty in forecasts of weather and climate
T N Palmer
https://iopscience.iop.org/article/10.1088/0034-4885/63/2/201

[3] On the reliability of seasonal climate forecasts
A. Weisheimer 1,2 and T. N. Palmer 1

[4] Time Series Forecasting System. SAS Institute. Retrieved 19 May 2015.

[5] Hyndman, Rob J; Athanasopoulos, George. 8.9 Seasonal ARIMA models. Forecasting: principles and practice. oTexts. Retrieved 19 May 2015.
