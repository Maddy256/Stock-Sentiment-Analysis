 # INTRODUCTION :
 The aim of this project is to develop a sentiment analysis model that predicts the movement 
of stock prices by analyzing textual data from various sources such as news articles, social 
media posts, and other financial news and opinions. The insights from the sentiment 
analysis can serve as valuable indicators for investor sentiment and market sentiment, 
aiding in making informed trading decisions.
 
 ## OBJECTIVE :
 The primary objective of this project is to develop a machine learning model 
that can analyze sentiment from textual data and predict stock price 
movements. The project will involve the following steps:
 * Data Collection
 * Data extraction (Web scrapping)
 * Data Preprocessing
 * Sentiment Analysis
 * Model Training and Evaluation
 * Prediction and Visualization
# FLOW OF PROJECT
 ## PRIMARY ANALYSIS : 
Firstly i have imported the yahoo finance library and an object for MICROSOFT 
is created . The ‘HISTORY’ method is called to retrieve historical data of past 10 
years .The data includes daily open, high, low, close prices, volume, and 
dividends. 
### OUTPUT:



 
 Now ,I have done small analysis of the Close Price of stocks which i will 
be scrapping the data of, namely Microsoft(MSFT), 
Nvidia(NVDA),Apple(AAPL)



## DATA COLLECTION:
 I used the selenium to web scrap the dyanamic website of Financial 
times for the news headlines news data , this process includes:
 **1. Creating web driver from selenium :**


Then the code for web scrapping : 


 ## ISSUE:
 News is not present after certain pages
 ## SOLUTION:
 I have added the print statement so that i can make sure that once the 
news on the page number x ends then we need to end the loop 
manually (a keyboard interrupt) , otherwise it will continue to search till 
the 800 pages (even if they dont have any data) . You can see what i 
mean by going the cell inputs.
 It shows data available till the time data is available and page ends 
when the page is ended. After the output continuously shows page 
ends that means no more data is available

## Cleaning the headlines data:
 * merging the headline for the same date into one.
 * deleted the headlines where date is not defined.
 Now i have gathered the stock price data, from 
yfinance, put the labels on each day (1 if the present 
day price is greater than previous day, else 0) and 
merged it with the headlines data, based on the date , 
so that i get the label (what was the stock price 
behaviour) and the corresponding headline for a 
particular date , in my final database , which can be 
used for training.
 Here is the final db: with text vs label


 
