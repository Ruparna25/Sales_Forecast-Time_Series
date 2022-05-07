# Sales-Forecast---Time-Series-Forecast
##Overview

Forecasting is perhaps the most common application of machine learning in the real world. Sales forecasting is an important problem in the e-commerce industry. Forecasting the sales of items helps businesses make better and informed decisions. 
Here we are working on the sales data of a grocery store from the country of Ecuador. The model aims at accurately predicting the unit sales for thousand of items sold across all the stores. High accuracy in the results is important because if the model predicts a little over, the stores get overstocked with perishable goods, and if it predicts a little under, the items quickly sell out, with disappointed customers.

##Dataset

This dataset has been taken from Kaggle competition held by the Corporación Favorita organization. The training data includes dates, stores, and product information, whether that item was being promoted, as well as the sales numbers. In addition to this there were some other supporting files containing data related to holiday events across the year and oil prices for the country over years. This information can help us build a robust model for forecasting that considers the trend, seasonality from the historical data of four years. This is a multivariate time series problem.
###Trend derived from the sales data –
a.	Trend captured by taking moving average over window of 365 days -
