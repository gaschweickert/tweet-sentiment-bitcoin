# Bitcoin Price Prediction Using Tweet Sentiment and Historical Data

### Overview
This project replicates and extends the methodology from "Bitcoin Price Prediction using Transfer Learning on Financial Micro-blogs" (Davchev et al.). It utilizes Twitter sentiment analysis and historical Bitcoin price data to forecast next-day Bitcoin prices using XGBoost regression.
Data Sources

Twitter Dataset: 14,876,179 Bitcoin-related tweets from Kaggle
Historical Bitcoin Prices: 700 days of price data (2017-01-31 to 2018-12-31) from Coinmarketcap.com

### Methodology

Data Preprocessing:

Twitter data: Removed null values, URLs, mentions; standardized date formats
Price data: Converted dates and values to appropriate types


Sentiment Analysis:

Model: cardiffnlp/twitter-roberta-base-sentiment (Hugging Face)
Approach: Random sub-sampling of 5 tweets per day, averaged positive sentiment scores


Feature Engineering:

Moving windows (3, 7, 30 days) for mean and standard deviation of:

Trading volume, market cap, open/close/high/low prices, sentiment scores




Model:

XGBoost Regression (PySpark implementation)
Hyperparameter tuning: Grid search with custom TrainValidationSplit


Infrastructure:

Amazon EMR for distributed computing
Amazon S3 for data storage



### Results

Test set (140 days) performance:

MAE: 223.25
RMSE: 301.46
R²: 0.94



### Key Findings

Most important features: Current day's open price and trading volume
Shorter sliding window spans generally more informative
Current day's sentiment most important among sentiment features

### Future Work

Implement relevance-based tweet selection
Expand hyperparameter search space
Increase tweet sample size
Experiment with different pre-trained language models
Implement real-time prediction capabilities

### Technologies

PySpark
XGBoost
Hugging Face Transformers
Amazon EMR
Amazon S3
