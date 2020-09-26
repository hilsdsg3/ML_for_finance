<h1 align="center"> Finance, Machine Learning, and GCP </h1> <br>
<p align="center">
  <a href="https://gitpoint.co/">
    <img alt="" width="450">
  </a>
</p>

<br>
<br>

## Table of Contents

- [Introduction](#introduction)
- [Machine Learning Factors](#machine_learning_factors)
- [Forecasting](#forecasting)
- [Time_Series](#time_series)
- [Machine_Learning_Model](#machine_learning_model)
- [Fundamentals_of_a_trading_strategy](fundamentals_of_a_trading_strategy)

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
The following diagram is the general decision tree for narrowing which type of machine learning model. It displays which model may be more probable. For example, a simple recommender your best bet would be using matrix factorization.

<p align="center"><img width=80% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/model_matrix.png"></p>

Another concept of good machine learning models is generalization which means how well the model fits the training data and is usually measured by Root-Mean-Square-Error (RSME) or Mean-Square-Error (MSE).

Testing data and training data have to be fully independent to prevent the model learning on the testing data. Because sometimes there is only a limited amount of data, one strategy is cross-validation. By using cross-validation one can obtain a more stable model averaging the RSME across all sets of validation data like in the testing window above in the forecasting section.

Overfitting and underfitting is also important when creating a model. In the red line on the following graph, it does not follow the trends in the stock data. The overfit blue line does following the trend but the training model probably will not be generalizable on the forecast accuracy. The green line fit the trends of the stock data an is most likely generalizable.       

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/overfit_underfit.png"></p>

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

The following diagram shows a linear model. The output equation is the vectorized form of w * x.  
<p align="left"><img width=60% src="https://github.com/hilsdsg3/Machine_Learning_Fundamentels/blob/master/meta_data/Perceptron_diagram_detail4.png"></p>

A slightly more complex model is the non-linear model with a hidden layer where all interactions are valid between the inputs, activation layer, and hidden layers.
<p align="left"><img width=60% src="https://github.com/hilsdsg3/Machine_Learning_Fundamentels/blob/master/meta_data/Non-linear_diagram.png"></p>

### Fundamentals_of_a_trading_strategy

One can describe and algorithmic trading model by entries and exits. The traders that develop these models are objective, metric-driven, and focused on risk-management.

Trade entry rules based on performance are endogenous rules for example :
```
Buy a stock when price decreases below 200.
Buy a stock at a 10 day low.
Buy a stock if the volume exceeds the previous day's volume and the closing price is lower than the daily average.
```

Exogenous rules mean other the price or volume :
```
Buy a stock if another stock price falls below 5%.
Buy a stock if the unemployment rate decreases.
Buy a stock if the reported quarterly sales increased or profits
exceed analyst expectations.
```

Some trade exit rules are profit-exit, stop-loss, and a time-out.
```
Profit-exit : 
LONG - Make 50 basis points.
Buy :  $100.00
Equation :=  Sell / Buy - 1 = 0.50 % = 50bp
----------
Sell : $100.50


Profit-exit AND stop-loss: 
SHORT - Make 500 basis points AND 200 basis loss tolerance.
Sell :  $150.00
Equation := 1 - (Buy/Sell) = Profit
Equation := 1 - (Buy/Sell) = -Loss tolerance
---------
Buy : $142.5 for 500 basis point profit
Buy : $153 for 200 basis point profit


Profit-exit AND dynamic-stop-loss: 
LONG - Make 400 basis points AND 200 basis loss tolerance.
Buy :  $1100.00
Equation :=  Sell / Buy - 1 = Profit
Limit :=  Sell / 1100 - 1 = 4%
stop-loss :=  Sell / 1130 - 1 = -2%
---------
Limit :=      Sell = $1144
stop-loss :=  Sell = $1107.4
```

***A Trading system has 4 components***
- Trading strategy - Decide which markets, devolop the logic, define parameters
- Backtesting system - Analyze the strategy performance on historical data and remove biases
- Execution system : Link to a brokerage and minimize the tranaction cost
(cost of trading, commision, and slippage)
- Risk management system : Create pre and post trade checks to avoid losses

### Develop_a_basic_trading_strategy

*** Example Parameters of an ML trading strategy
- Fundamental - P/E ratios, EPS, Cash flows
- Technical - Momentum, mean reversion, correlated/cointegrated
- Combined - Fundamental and technical indicators

Development of a momentum trading model
1. Define the problem - price prediction, return p/l, buy/sell signal, portfolio optimization, efficient execution
2. Collect the Data - 
3. Create the features
4. Split the Data
5. Machine Learning model selection
6. Backtest on Unseen data - auquan toolbox

Sample problem :
1. Problem definition - Create a prediction model of trade price difference between two assets. basis = Prices of Stock - Price of Future = St - Ft
Define parameters - 
1a. Target expected value in the next 5 min
Y = future expected value of basis = average(basis(t1)...(t5))
1b. - Objective : Create a model so that predicted value is as close as possible to Y
1c. Evaluation Criteria : RMSE. We'll also use Total PnL as an evaluation condition.
1d. Features : Current and future bid/ask price and volume,
Current VWAP = BidPrice * AskVol + AskPrice * BidVol/(AskVol + BidVol)

2. Collect data - EDA (Check for accuracy, alignment, dividends, stocks split, rolls). Beware timing of when the dividends was incorporated in the price is key. If the timing is off , you may have training data which fits well to the model but test data which performs poorly.



3. 


























