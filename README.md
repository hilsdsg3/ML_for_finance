<h1 align="center"> Finance, Machine Learning, and GCP </h1> <br>
<p align="center">
  <a href="https://gitpoint.co/">
    <img alt="" width="450">
  </a>
</p>


## Table of Contents

- [Introduction](#introduction)
- [Machine Learning Factors](#machine_learning_factors)
- [Forecasting](#forecasting)
- [Time_Series](#time_series)
- [Machine_Learning_Model](#machine_learning_model)
- [Google_Cloud_Platform_Machine_Learning](gcp_ml)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

This is an ongoing project of the intersection between machine learning, finance, and the Google Cloud Platform. I will touch on each of the bulleted topics. I have accompanying Jupyter notebook. There is a lot of content in the [Jupyter notebook](https://github.com/hilsdsg3/ML_for_finance/blob/master/repo_nb.ipynb) so it is best to select the Table of Contents like below and select a topic.

<p align="center"><img width=50% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/table_of_contents.png"></p>


### Machine_Learning_Factors

Endogenous factors :
* Depends on trading data
* Technical strategy model
* Price data - price trends and volatility
* Order book - size of orders at the bid and ask price
* Volume data - traded amount of shares

Exogenous factors :
* Depends on fundamental / macro data
* Event driven strategy model
* Earnings data
* Supply or customer shock

### Forecasting
It is a process of making predictions of the future based on past trends and it can be made with either quantitative and/or qualitative methods. 
Forecasting can either be achieved by casual regression where the model relationship between at least two variables : explanatory and response.
Time series is another type of forecasting and is a simple average of all past data as a forecast.

There is a difference between regression that uses variables to explain the response and time series forecast which uses past data to predict the future.

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/forecasting.png"></p>

<p align="center"><img width=80% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/animated_forecast.gif"></p>

### Time_Series

A time series is a series of continuous data points or sequence indexed in successive equally spaced points in time of discrete-time data.

An important concept is stationary time series data. Time series data is used for creating a model to perform strategy analysis or price prediction. In order to create such a model a stable mean and variance must be found from the entire time series. This mean and variance in a stationary time series is said to be independent of time. Pricing and other time series data is not usually stationary but there are tools to help with this.

For example with US GDP data it has an exponential trend. From math we probably will need to take two derivatives of the data to get a stable mean and variance. Also to verify that it indeed would be stationary we can run a Augmented Dickey-Fuller test. [Python notebook link](https://hilsdsg3.github.io/ML_for_finance/)

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/GDP.png"></p>

The result with the US GDP data after differencing twice is an ADF value of -15 vs the 5% critical characteristic of -2.873, therefore the time series is stationary.   

Another important concept of time series is autocorrelation which is the correlation of data point with different periods in the past. An autocorrelation model is an autoregression (AR) model. 

The result from the Augmented-Dickey Fuller, ACF, and correlation graph data that GDP is stationary and non-correlated if the data is differenced twice. 

One other concept is the moving average (MA) concept which takes the previous error terms into account. A good model uses the optimal number of error terms , q, to consider. Combining AR and MA values would result in the following equation , ARMA. ARIMA is the integration of the two models and the model uses three terms ; p,d,q. p is the lag, d is the difference predictor, and q is period for sudden changes.  

<p align="left">
<img src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/ARMA_1st.svg"/>
</p>
<p align="left">
<img src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/ARMA_2nd.svg"/>
</p>
<p align="left">
<img src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/ARMA_3rd.svg"/>
</p>

There are two ways of evaluating ARIMA models for stationarity ; plotting the residuals and Ljung-Box test.


### Machine_Learning_Model
The general decision tree for narrowing which type of machine learning model could be more probable is in the following. For example, your best bet would be using matrix factorization to recommend an item.

<p align="center"><img width=80% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/model_matrix.png"></p>

Building a model with BigQuery ML

- Questions of financial modeling

What data do I have ?
What do others have ? Public or private
Does the freshness of my data matter a little or a lot ?
What assumptions is my model taking ? Retested very often
Is there a combination of things I could model ?

Generalization of machine learning models means how well the model fits the data and is usually measured by Root-Mean-Square-Model (RSME) or MSE.

Validation data and training data have totally independent to prevent the model learning on the validation data. Because sometimes there is only a limited amount of data, one strategy is cross-validation. By using cross-validation one can obtain a more stable model averaging the RSME across all sets of validation data like in the testing window above in the forecasting section.

Overfitting and underfitting is also important when creating a model. In the red line on the following graph, it does not follow the trends in the stock data. The overfit blue line does following the trend but the training model probably will not be generalizable on the forecast accuracy. The green line fit the trends of the stock data an is most likely generalizable.       

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/overfit_underfit.png"></p>

## GCP_ML

TensorFlow is an open-source, high performance library for numerical computation that uses directed graphs. A tensor is a n-dimensional array like a 1D, 2D, 3D .... arrays.
tf.constant() # cannot be modified
tf.variable() # CAN be modified

TensorFlow can compute the derivative of a function with respect to any parameter and the computation is recorded with GradientTape. 

For basic to medium machine learning models, use the top layer of abstraction. This is all that is needed.

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/TensorFlow_abstration_layers.png"></p>

TensorFlow has many helpful functions.
For instance, linear regression of y = slope * x + intercept where y = 1.5 x + 20. The full result is in the Jupyter notebook but the mean square result was 0.001.
```
	X	Y	Y_hat	diff_Y
0	0.0	20.0	19.9	-0.07
1	1.0	21.5	21.4	-0.06
2	2.0	23.0	23.0	-0.05
3	3.0	24.5	24.5	-0.03
4	4.0	26.0	26.0	-0.02
5	5.0	27.5	27.5	-0.01
6	6.0	29.0	29.0	-0.00
7	7.0	30.5	30.5	0.01
8	8.0	32.0	32.0	0.02
9	9.0	33.5	33.5	0.03
```



