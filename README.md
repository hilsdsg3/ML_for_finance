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
- [Exploratory Data Analysis for ML](#exploratory_data_analysis_for_ml)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

This is an ongoing project of the intersection between machine learning, finance, and the Google Cloud Platform. I will touch on each of the bulleted topics. I have accompanying Jupyter notebook. There is alot of content in the [jupyter notebook](https://github.com/hilsdsg3/ML_for_finance/blob/master/repo_nb.ipynb) so it is best to select the Table of Contents like below and select a topic.

<p align="center"><img width=80% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/table_of_contents.png"></p>


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

### Exploratory_Data_Analysis_for_ML
The general decision tree for narrowing which type of machine learning model could be more probable is in the following. For example, your best bet would be using matrix factorization to recommend an item.

<p align="center"><img width=80% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/model_matrix.png"></p>

### Models

Building a model with BigQuery ML

- Questions of financial modeling

What data do I have ?
What do others have ? Public or private
Does the freshness of my data matter a little or a lot ?
What assumptions is my model taking ? Retested very often
Is there a combination of things I could model ?

- Case study : Modeling CPU Performance by vendor with BigQuery

Given raw inputs such s vendor, max_mhz, os .... can you predict the benchmark score. The prediction model setup is linear regression with BigQuery ML.

### Time Series

A time series is a series of continuous data points or sequence indexed in successive equally spaced points in time of discrete-time data.

An important concept is stationary time series data. Time series data is used for creating a model to perform strategy analysis or price prediction. In order to create such a model a stable mean and variance must be found from the entire time series. This mean and variance in a stationary time series is said to be independent of time. Pricing and other time series data is not usually stationary but there are tools to help with this.

For example with US GDP data it has an exponential trend. From math we probably will need to take two derivatives of the data to get a stable mean and variance. Also to verify that it indeed would be stationary we can run a Augmented Dickey-Fuller test. [Python notebook link](https://hilsdsg3.github.io/ML_for_finance/)

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/GDP.png"></p>

The result with the US GDP data after differencing twice is an ADF value of -15 vs the 5% critical characteristic of -2.873, therefore the tie series is stationary.   

Another important concept of time series is autocorrelation which is the correlation of data point with different piriods in the past.



