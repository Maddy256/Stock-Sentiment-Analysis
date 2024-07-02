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


![Screenshot_3-7-2024_34447_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/2f7272c2-54a7-4353-b748-fa12a9b39a61)
 
 Now ,I have done small analysis of the Close Price of stocks which i will 
be scrapping the data of, namely Microsoft(MSFT), 
Nvidia(NVDA),Apple(AAPL)

![Screenshot_3-7-2024_3457_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/5c8fea3c-b6f7-4999-8ed8-5f30e03391a6)


## DATA COLLECTION:
 I used the selenium to web scrap the dyanamic website of Financial 
times for the news headlines news data , this process includes:
 **1. Creating web driver from selenium :**

![Screenshot_3-7-2024_34525_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/cee2bca3-c2df-4ac9-b114-587a74bc3a0c)


Then the code for web scrapping : 
![Screenshot_3-7-2024_34536_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/2ccf8c9d-7b18-4f3e-adf2-ab5fcbd6d0c4)
![Screenshot_3-7-2024_34554_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/562137f9-b996-46da-96c3-58dd48ec2490)
![Screenshot_3-7-2024_3469_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/210461a4-1370-4ee0-96e4-dd84bc0d862d)

![Screenshot_3-7-2024_34628_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/0c42a035-1fbb-49ce-a805-d4219b35ce99)
# Issue and the Solution
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

![Screenshot_3-7-2024_34644_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/03cc9caf-d370-4602-8192-c6de5140bf4b)

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
 Here is the final db: with text vs labe

![Screenshot_3-7-2024_3478_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/f7f1d7d8-3412-45ef-b99e-f5600816f58f)


![Screenshot_3-7-2024_34721_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/7ebc82be-3e31-499d-8b1b-bf15035520d7)
Now implementing bag of words approach :
![Screenshot_3-7-2024_34738_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/a8be1a66-fd0e-4e05-9de4-036e54dc5432)
Calculated the sentiment score via NLP and vader sentiment 
analyser: 
![Screenshot_3-7-2024_34751_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/5e762d3a-3554-4f97-846d-a1ad76ae9546)


![Screenshot_3-7-2024_3482_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/e3f4648d-71e7-475e-8a98-b488d2ffc0b4)
 ## Training the Model
 Now our data is ready for training based on the compound 
sentiment score of the headline and the stock label, using this 
we train a random forest classifier (supervised) ,and then test 
it (initially we split it using test train classifer) .
 I trained with compound score as the features. 
![Screenshot_3-7-2024_34814_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/cb3660db-a7da-446e-810f-bce7722c53fb)
![Screenshot_3-7-2024_34826_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/eb203125-9f71-4880-a479-8d95ae2a5a43)
## The Confusion Matrix :
 I got an accuracy of 55.17%



![Screenshot_3-7-2024_34838_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/97269412-86d3-48f5-bee6-54c226491e0a)
## NOW THE MODEL IS READY FOR USE : 
FEED SENTIMENT - GET THE LABEL OF INCREASE / 
DECREASE
 We will test it by performing the trades by our portfolio on 
Tesla (TSLA) stocks.
 ## First Step:
 Getting the tesla stock headlines on which our model will work 
and predict the increase/ decrease of the tesla stocks:
 Following the same procedure for web scrap as above , we get 
the news and the model predicts the labels
![Screenshot_3-7-2024_34852_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/b896b23e-bca5-4bec-a8b2-cc9e04f44805)
![Screenshot_3-7-2024_3491_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/e734a446-8261-4378-be3e-dfae450a3b88)
## OUTPUT:
![Screenshot_3-7-2024_34914_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/4a1310dc-45b2-4df2-aabb-fdd0703afbf0)
## Now I have defined a strategy
![Screenshot_3-7-2024_34925_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/b682e0da-4a05-4727-b724-f9be9341c913)

![Screenshot_3-7-2024_34941_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/522e310d-3a90-46ad-8351-5de83a06a668)

![Screenshot_3-7-2024_34950_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/daa31868-8b02-4edf-991e-3e6267a71705)
 * It maintains a position variable to track whether the 
strategy is currently holding a position or not.
 * The strategy interprets a label shift from 0 to 1 as a 
buying opportunity, initiating a buy action if the 
strategy currently holds no position.
 * Upon detecting a buy signal, it records the 
corresponding closing price as the buy price and stores 
the date of the buy signal.
 * If a buy signal is detected and the strategy wasn't in a 
position, it calculates the number of stocks that can be 
bought based on the available investment amount and 
the closing price, initiating a buy action.
 I have taken my initial portfolio value to be $10,000



![Screenshot_3-7-2024_3502_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/fb8c795a-3fed-45ee-a229-48402545ec1d)

![Screenshot_3-7-2024_35014_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/990db1d2-8ac4-40a5-aa23-50973ef62b08)

The graph of portfolio is shown at the last:
![Screenshot_3-7-2024_35026_](https://github.com/Maddy256/Stock-Sentiment-Analysis/assets/118598865/0e03335c-58c0-4f21-ad9c-61bd0eb33d16)








 
