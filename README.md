<h1 align="center"> Finance, Machine Learning, and GCP </h1> <br>
<p align="center">
  <a href="https://gitpoint.co/">
    <img alt="" width="450">
  </a>
</p>



<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Introduction](#introduction)
- [Machine Learning Factors](#Machine_learning_factors)
- [Demo](#demo)
- [Contributors](#contributors)
- [Backers](#backers-)
- [Sponsors](#sponsors-)
- [Acknowledgments](#acknowledgments)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

This is an ongoing project of the intersection between machine learning, finance, and the Google Cloud Platform. I will touch on each of the bulleted topics. 

### Machine Learning Factors

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
Time series is another type of forcasting and is a simple average of all past data as a forecast.

There is a difference between regression that uses variables to explain the response AD time series forecast which uses past data to predict the future.

<p align="center"><img width=60% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/forecasting.png"></p>

<p align="center"><img width=80% src="https://github.com/hilsdsg3/ML_for_finance/blob/master/metadata/animated_forecast.gif"></p>

### Exploratory Data analysis
The general decision tree for narrowing which type of model could be more probable is in the following. For example, your best bet would be using matrix factorization to recommend an item.

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


## Contributors

Please take a look at the [contributing guidelines](./CONTRIBUTING.md) for a detailed process on how to build your application as well as troubleshooting information.

## Backers [![Backers on Open Collective](https://opencollective.com/git-point/backers/badge.svg)](#backers)





<a href="https://opencollective.com/git-point/sponsor/0/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/1/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/2/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/3/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/4/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/5/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/6/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/7/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/8/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/git-point/sponsor/9/website" target="_blank"><img src="https://opencollective.com/git-point/sponsor/9/avatar.svg"></a>

## Acknowledgments

Thanks to [JetBrains](https://www.jetbrains.com) for supporting us with a [free Open Source License](https://www.jetbrains.com/buy/opensource).

