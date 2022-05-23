# Sales_Forecast-Time-Series-Forecast
### Overview

Forecasting is perhaps the most common application of machine learning in the real world. Sales forecasting is an important problem in the e-commerce industry. Forecasting the sales of items helps businesses make better and informed decisions. 
Here we are working on the sales data of a grocery store from the country of Ecuador. The model aims at accurately predicting the unit sales for thousand of items sold across all the stores. High accuracy in the results is important because if the model predicts a little over, the stores get overstocked with perishable goods, and if it predicts a little under, the items quickly sell out, with disappointed customers.

### Dataset

This dataset has been taken from Kaggle competition held by the Corporación Favorita organization. The training data includes dates, stores, and product information, whether that item was being promoted, as well as the sales numbers. In addition to this there were some other supporting files containing data related to holiday events across the year and oil prices for the country over years. This information can help us build a robust model for forecasting that considers the trend, seasonality from the historical data of four years. This is a multivariate time series problem.

**Trend derived from the Sales data**
* Trend captured by taking moving average over window of 365 days -

![image](https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/year_window.png)

**Seasonality captured from the Sales data**

Seasonality derived from the sales data

* Impact of different kinds of seasonality derived from the dataset –

![image](https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/Periodgram.png)

**Autocorrelation Plot for the Sales data**

![image](https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/ACF.png)

**Partial Autocorrelation for the Sales data**

![image](https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/PACF.png)

### Design

Based on the above plots we extracted the features like week, month, quarter, year to capture the time series trend along with other important features. Different lag features were added to capture the autocorrelation (commonly called serial dependence), is the correlation between a time series current value with past values. Also, moving average of different windows are used as feature to capture data trend. All these features were combined with the features already present in the dataset to train the model. 

3 different models were trained to observe how each performs against the other – 
1.	**ARIMA**

Model trained on Moving Average calculated based on different window sizes - 7(weekly), 30(monthly) and 365(annual) days. 

2.	**LGBM**

For training the LGBM model, batch of data were used and these batches were identified based on the type of training window passed to the model. There were two types of windows defined one being the sliding window and another being the expanding window. Example of sliding window and expanding window is given below - 

![image](https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/window_lgbm.JPG)

3.	**LSTM**

Used TimeseriesGenerator class to create training sequence and test sequences. Used a 3-layered LSTM model with the last layer being a Dense Layer to predict the sales price for any given day. The model was trained by fit_generator function of TimeseriesGenerator class. Evaluation metrics used was MSE (Mean squared error).

### Performance

Below is the Performance data of different models tried -
1. **ARIMA**

RMSE obtained from each window size is shown below -

<img src='https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/ARIMA.png' width=500, height=300>

2. **LGBM**

RMSE scores for both sliding and expanding type of window training -

<img src='https://github.com/Ruparna25/Sales-Forecast---Time-Series-Forecast/blob/main/images/LGBM.png' width=400, height=300>


