                                        Forecasting Monthly Sales using ARIMA and SARIMA
This project focuses on forecasting monthly sales data using classical ARIMA (AutoRegressive Integrated Moving Average) and SARIMA (Seasonal ARIMA) models.
It demonstrates how to transform a non-stationary, seasonal dataset into a stationary form suitable for time series modeling and forecasting.

 Objective
        To analyze, model, and forecast a monthly sales dataset using ARIMA and SARIMA models by:
              •	Understanding data trends and seasonality.
              •	Making the data stationary through differencing.
              •	Identifying AR and MA terms via ACF and PACF plots.
              •	Building and comparing ARIMA and SARIMA models for better predictive performance.

       Step 1: Data Cleaning
              •	Imported the sales dataset and checked for null or invalid entries.
              •	Converted the time column into a DateTime index for proper time-based operations.
              •	Ensured the data was aggregated at a monthly frequency.

      Step 2: Data Visualization
              •	Visualized the sales data to observe clear seasonal patterns repeating every 12 months.
              •	Plotted rolling mean and standard deviation to assess trend and variance.
              •	Performed time series decomposition into trend, seasonality, and residuals.

      Step 3: Differencing (Integrated Step)
      The data exhibited strong annual seasonality, with a cycle of 12 months.
      To make the series stationary:
              •	Applied first-order differencing for trend removal.
              •	Applied seasonal differencing (lag = 12) to handle yearly seasonality.
Created a new column:
df['seasonal_first_difference'] = df['Sales'] - df['Sales'].shift(12)


       Step 4: Model Identification
            🔸 Auto-Regressive (AR) Model
                    •	Identified using Partial Autocorrelation Function (PACF) plot.
                    •	PACF “cuts off” after the order p, meaning significant correlations end beyond lag p.
                    •	The number of non-zero PACF values gives the AR order.
            🔸 Moving Average (MA) Model
                    •	Identified using Autocorrelation Function (ACF) plot.
                    •	ACF “tapers off,” and significant spikes indicate q, the MA order.
Model Parameters
Parameter	Meaning
p	AR (Auto-Regressive) lags
d	Differencing order
q	MA (Moving Average) lags

        Step 5: Model Building
                •	Fitted several ARIMA(p, d, q) models to identify the best configuration.
                •	Extended the model to SARIMA(p, d, q)(P, D, Q, s) to capture seasonal cycles.
                •	Used AIC and BIC values for model comparison.
Example SARIMA configuration:
SARIMA(1, 1, 1)(1, 1, 1, 12)

        Step 6: Forecasting
                •	Generated forecasts for future months based on the trained model.
                •	Compared predicted values vs. actual values using visual plots and error metrics.
                •	Evaluated accuracy using RMSE and residual diagnostics.

        Results and Insights
                •	The SARIMA model effectively captured the yearly seasonality.
                •	Forecast plots showed close alignment with actual values, indicating strong predictive power.
                •	Seasonal differencing (12-month lag) was critical for stationarity.
                •	ARIMA performed well, but SARIMA outperformed it due to seasonal structure.



