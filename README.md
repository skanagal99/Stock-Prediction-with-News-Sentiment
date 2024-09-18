# Stock Market Sentiment Analysis and Prediction

This project explores the relationship between market sentiment and stock price movements. We analyze historical stock prices and financial news data, using sentiment analysis techniques to extract sentiment from text. A machine learning model is then trained to predict stock price trends based on these sentiment scores and historical stock performance.

### Data
Stock Price Data: Contains information on stock prices, including Open, High, Low, Close, Volume, and stock-specific details like Ticker, Industry, and Country.
Sentiment Data: Consists of financial news headlines and snippets for various dates, initially labeled with binary sentiment values. Instead of using the pre-labeled sentiment, custom sentiment analysis was performed using VADER to generate sentiment scores.
Process Overview
### 1. Data Exploration
Loaded two datasets: stock prices and sentiment data.
Explored key characteristics, such as date alignment and the presence of missing values, to ensure data quality.
### 2. Data Cleaning and Preprocessing
Converted date columns to datetime format, handling timezone inconsistencies.
Cleaned the sentiment data by merging multiple text snippets (Top1 to Top25) into a single string per day.
Calculated daily sentiment scores using the VADER sentiment analyzer, producing compound sentiment scores ranging from -1 (very negative) to 1 (very positive).
### 3. Feature Engineering
Merged stock price data with daily sentiment scores on the Date column.
Created additional features, including:
Price Change Percentage: The percentage change in stock price from the previous day.
Lagged Sentiment: Used previous days' sentiment scores to capture lagged effects of news on stock prices.
Volatility: Calculated as the difference between the high and low prices divided by the opening price to represent daily price swings.
Moving Averages: Added 5-day and 10-day moving averages of stock prices to capture recent trends.
### 4. Modeling
Defined the target variable as Price Movement, which indicates whether the stock price increased or decreased based on daily price changes.
Split the data into training and testing sets (80/20 split).
Trained a Random Forest Classifier to predict stock price movement using sentiment scores and other stock-related features.
### 5. Evaluation
Evaluated the model using accuracy, precision, recall, and F1-score.
The model achieved an accuracy score of 47%, with nearly balanced performance across precision and recall for both classes (up and down price movements).
The F1-scores for the positive and negative classes were 0.46 and 0.48, respectively, indicating limited predictive power.
### Key Findings
The model struggled to capture meaningful relationships between sentiment data and stock price movements, as evidenced by the low accuracy and F1-scores.
While sentiment plays a role in stock market dynamics, the model's poor performance suggests that more advanced feature engineering or alternative models might be required to capture this relationship effectively.
Potential improvements could include adding more advanced features, trying different machine learning models (e.g., XGBoost, LightGBM), and conducting hyperparameter tuning.
### Future Work
Feature Enhancement: Include more financial indicators (e.g., RSI, Bollinger Bands), longer-term trends, and additional lagged features to better capture the time-series nature of the data.
Advanced Modeling: Explore more sophisticated models, such as Gradient Boosting algorithms or neural networks, to improve predictive performance.
Hyperparameter Tuning: Use Grid Search or Random Search to find the optimal parameters for the model.
Data Augmentation: Incorporate more data, such as additional news sources, social media sentiment, or other financial indicators.
