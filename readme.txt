Predicting Bitcoin Price Variations using Bayesian Regression

Reference paper: http://arxiv.org/pdf/1410.1231.pdf

This project is about predicting the price variations of bitcoin, a virtual cryptographic currency. These predictions could be used as the foundation of a bitcoin trading strategy using Bayesian regression.

Datasets
I have done some cleaning of the data on the original raw data can be found here: http://api.bitcoincharts.com/v1/csv/. The datasets from this site have three attributes: (1) time in epoch, (2) price in USD per bitcoin, and (3) bitcoin amount in a transaction (buy/sell). However, only the first two attributes are relevant to this project.
To make the data to have evenly space records, all the records are taken within a 20 second window and replaced it by a single record as the average of all the transaction prices in that window. Not every 20 second window had a record; therefore those missing entries were filled using the prices of the previous 20 observations and assuming a Gaussian distribution. The raw data that has been cleaned is given in the file dataset.csv.
Finally, as discussed in the paper, the data was divided into a total of 9 different datasets. The whole dataset is partitioned into three equally sized (50 price variations in each) subsets: train1, train2, and test. The train sets are used for training a linear model, while the test set is for evaluation of the model. There are three csv files associated with each subset of data: *_90.csv, *_180.csv, and *_360.csv. In _90.csv, for example, each line represents a vector of length 90 where the elements are 30 minute worth of bitcoin price variations (since we have 20 second intervals) and a price variation in the 91st column. Similarly, the *_180.csv represents 60 minutes of prices and *_360.csv represents 120 minutes of prices.


