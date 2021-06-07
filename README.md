## Capstone 2: Predicting Stock Price based on Twitter Sentiments of Stocks

<img width="760" alt="Screen Shot 2021-06-06 at 5 58 09 PM" src="https://user-images.githubusercontent.com/78486516/121067253-ae102600-c77f-11eb-9811-a1ef0f7703ac.png">


### Data
This dataset used is a part of the paper published in 2020 IEEE International Conference on Big Data Special Session and is available in Kaggle. This dataset contains tweets that are written about Amazon, Apple, Google, Microsoft, and Tesla by using their appropriate share tickers. This dataset contains over 3 million unique tweets with their information.

<a href="https://www.kaggle.com/omermetinn/tweets-about-the-top-companies-from-2015-to-2020" target="_blank">Kaggle</a>

The pricing data about these stocks that included closing price, high, low, daily volume was obtained from 

<a href="https://www.finance.yahoo.com/" target="_blank">yahoo finance</a>

### Method

checked if there was any correlation between the volume of tweets with the volume of stock traded. 

The figure below shows the relationship between trade volume and tweet volume for Apple.

<img width="760" alt="tweetvol and trade vol" src="Images\tweetvol and trade vol.png">

The calculated values for other stocks is given in the table below.

<img width="760" alt="Stock vol to tweet vol" src="Images\Stock vol to tweet vol.png">

It looks like the volume of tweets has a positive correlation with the trade volume. However, the strength of the correlation is relatively low. Additionally, it is not certain that volume of tweets is always correlated with the share price as demonstrated in Microsoft's case where the p-value exceeded the predetermined threshold of 0.05. The significance of values observed above the threshold means the relationship is not statistically significant.

Next,analyzed how the sentiment of the tweets impact the stock price. I categorized the tweet sentiments as either positive, negative or neutral using VADER Sentiment analyzer.
The figure below shows the correlation and the p-value for Apple.

<img width="760" alt="stockPrice to stockSentiment" src="Images\stockPrice to stockSentiment.png">


The calculated values for other stocks is given in the table below.

<img width="760" alt="tweet sentiments to stockprice" src="Images\tweet sentiments to stockprice.png">

There seems to be a stronger correlation between the sentiment of the tweets and the share price of the company as compared to the previous hypothesis.

I then performed a time series analysis to see if twitter sentiments can be used to predict stock prices. The analysis of time series is based on the assumption that successive values in the data file represent consecutive measurements taken at equal time intervals. I built the following models

* ARIMA
* Facebook Prophet
* Vector Autoregression (VAR)

### Scoring Metric
Root Mean Square Error (RMSE)was used to compare the performance of various models. The expectation here is that twitter sentiment used along with stock data should give us a lower RMSE score, than when calculated with the univariate models ARIMA and Facebook Prophet.

### Model Performance
The RMSE values from the three models are as follows.

<img width="760" alt="modelResults" src="Images\modelResults.png">


### Conclusion

I used time-series data and built univariate and multivariate models for our analysis. Though I found some correlation between stock price and tweet sentiments, when it comes to predicting the stock price this relationship remained inconclusive as seen from our model results.

### Further Improvements

* Use Deep learning models like LSTM. We can tinker with the LSTM architecture and hyperparameters to improve the model accuracy.
* Instead of using a pre-trained VADER Sentiment Analyzer, we can train our own model by first creating training data. A custom trained model should give better sentiment results as it will get trained on the stock market news language.
* There is some research that shows using GAN(Generative Adversarial Network), Reinforcement Learning can also be used to predict stock prices better.


