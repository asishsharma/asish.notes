# Financial data 

## WQU MScFe 600 Financial data 
Transcript : 
	[google docs link](https://docs.google.com/document/d/1svws_6bzvnXL-Z8n4ItP044kr2jo-hbCZD5ctM3QMZY/edit)
	local pdf link: 

### Jupyter notebooks 
> [!Note] Best practices
> The text here is quite long. Use the outline in tag pane to navigate

#### M1. Macroeconomics
##### 1.1 Financial data best practices

###### Required reading: 

Ozenbas, Deniz et al. "Liquidity and the Impact of Information Shocks." Liquidity Markets and Trading in Action: An Interdisciplinary Perspective, edited by Deniz Ozenbas, Michael S. Pagano, Robert A. Schwartz, and Bruce W. Weber, Springer, 2022, pp. 51–69, [https://link.springer.com/book/10.1007/978-3-030-74817-3](https://link.springer.com/book/10.1007/978-3-030-74817-3)

- Notes: 
	- try writing your summary of what you read in the reading here. 

  

FINANCIAL DATA BEST PRACTICES

In Financial Markets, we examined how the world of financial engineering is influenced by concepts like credit risk, financing, volatility, correlation, liquidity, regulation, leverage, non-linearity, model failure, and financial crisis. In Financial Data, we will revisit all of these concepts by introducing data to help us populate models that can interpret, predict, and even prescribe solutions to the challenges financial engineers face.

  

In this module, we will examine what constitutes financial data: where it comes from, the factors that affect data, the types of data, how to handle missing or extreme cases, and the foundations of data preparation for machine learning.In this lesson, we'll focus on a half dozen lessons we can make about data, based on understanding the macroeconomy, central banks, and one of the key financial concepts from the last course--liquidity.

  

###### 1.1.1. Economics

  

Asset prices are greatly influenced by what happens in the macroeconomy. A thriving business cycle invites equity investments, increases in personal spending, and perhaps actions taken by the central bank. In the first module of Financial Markets, you saw examples where depositors were earning a specific interest rate.  At the same time, lenders (or borrowers) earned a different interest rate.  Depositing money in a bank will surely earn less interest than the interest you would pay on a loan from the same bank!

  

One of the biggest influences on markets in general, and interest rates in particular, is news.  

News can be thought of as expected or unexpected. Recall that efficient markets may have incorporated much of the expected news already. For example, suppose Netflix declares a \$2.00 dividend. If this is indeed the amount that gets announced, then it comes as no surprise and should not affect Netflix's stock price. However, suppose there is unexpected news.

-Netflix had stronger than anticipated growth due to underestimated popularity with certain shows, causing a larger than expected number of subscribers in Korea. The dividend is \$2.40. The stock price will likely rally.

-On the other hand, suppose Netflix had higher than expected costs for producing original content, causing net profits to drop. The dividend is only $1.80. The stock price will likely tumble.


Unexpected news can be good or bad, that is, it may result in higher prices or lower prices, depending on the situation. For example, consider bad news. It can increase credit risk, threaten financing cash flows, create volatility, disrupt correlation, aggravate leverage, induce non-linearities, challenge model assumptions, stress models by incurring added costs for liquidity, promote model failure, and even bring about financial crises. Of course, one piece of bad news may not do all that, but what if the bad news affected many businesses--such as higher than expected interest rates?

Let's examine how interest rates work. Investing in business affects interest rates, but simultaneously, interest rates affect business investments. Most relationships in finance are complex because they can be multi-directional. It's not just that A affects B and B affects A. It's that A affects B and C; B affects A and C; C affects A and B; and so on. Your required reading for this lesson, Ozenbas Chapter 3 Section 1, will help you understand the complex interaction of business investment and interest rates.

This gives us our first lesson about the type of data. If we just collect interest rates and have no sense of monetary policy or money supply or economic decisions, we lose data that both affects interest rates and in turn are affected by those same rates. Indeed, we may want to collect associated data so that we can examine if that other variable (e.g., Fed decisions) affect our variable of interest. Indeed, we will do this later in the course with conditional averages, or run conditional regressions.

###### 1.1.2. Federal Reserve

Recall from Financial Markets that we read about central banks.  The Federal Reserve is the central bank in the United States. The Fed's output is vast: It includes decisions, research, and printed and spoken market commentaries. These findings are heavily watched and analyzed, as they significantly affect markets. For example, eight times a year, the Federal Reserve has regularly scheduled releases of decisions about interest rates. These meetings result in decisions about interest rates released to the market. Like any other information, this is news that can be expected or unexpected.  If the news is expected, then that information is already priced in the market.  If the news is unexpected, then there are likely to be information shocks that cause market volatility.  In addition, the Fed selects 8 other dates at which they release the minutes of the meetings. These releases contain qualitative rather than quantitative data. These releases can also affect not only interest rates, but stock trading as well, as they indicate the opinions and intended actions of the Fed. For example, in 2019, the Fed decided to cut interest rates three times. This led to a 29% decrease in the S&P 500 during the 4th quarter of 2019.

This gives us our second lesson about data. If we collected data during 2018 and then attempted to extrapolate, we would miss out on key events that affect data. Oftentimes, we need to understand key events that affect our data, as we might consider a data sample as information between those events.

For example, if you construct a sample of equity data, you could collect daily equity closes, but when it comes to analyzing them, you could consider:
1) no grouping 
2) 1 group per equity dividend announcement
3) groups based on the level of the Fed Reserve rate
4) 1 group per Fed fund meeting

To get data from the Federal Reserve, please visit https://fred.stlouisfed.org/docs/api/api_key.html
From there, you can request a free API key.

While the data collected may be the same, there is a recognition that the data as a whole (example 1) may have different properties and can be better analyzed based on an intrinsic property of the company (example 2, earnings) or based on an extrinsic property, like monetary policy (examples 3 and 4). Understanding that our data experiences changes means that we will want to understand markets as systems. It also means we may want to collect and analyze data that is qualitative (e.g., Fed statements).

> [!Note] API Key
> Asish FRED API key:: `40ae5aa25e085f60ac616195d9b31908`. Used Google account to generate it from FRED website. 
```pre-python

import pandas_datareader as pdr  # access fred
```
```python
# extract api key: put your key in between the angle brackets <>
myKey = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
fred_api_key = "<ENTER YOUR API KEY HERE>"

# Using code from FRED API: Get US Economic Data using Python
def get_fred_data(param_list, start_date, end_date):
    df = pdr.DataReader(param_list, "fred", start_date, end_date)
    return df.reset_index()

# Let's see what the Fed Funds rate was since 2000
series = "FEDFUNDS"
# get data for series
df = get_fred_data(param_list=[series], start_date="2000-01-01", end_date="2022-05-03")
df

```
- output
	- ![](https://i.imgur.com/UVtB8jc.png| 1/10)
	- 

###### 1.1.3. Types of Financial Markets

Even the type of financial market influences the data.
Read about the various types of financial markets in the required reading.

If we use prices, we may be using data only where actual trades occurred.
If we use quotations, then we have a richer set of data because this includes information in the limit order book.  The limit order book includes
1. bid price: the best (i.e., highest) price at which a buyer is willing to pay. This is the top of the book.
2. bid size: the amount the best bid is willing to purchase at that price.
3. ask price: the best (i.e., lowest) price at which a seller is willing to trade. This is also the top of the book on the offer side. Note that the ask price is also known as the offer price.
4. ask  size: the number of shares the best offer is willing to sell at that price.
As we saw in the previous course, the difference between the bid and ask price is known as the bid-ask spread.  

In Financial Markets, we stated that illiquid markets have a high bid-ask spread. If is high relative to the level of the securities' prices.  You can see examples of this in neighborhoods where there are vacant storefronts. In the commercial real estate world, retail businesses are willing to pay \\$x for a 1-year rental (the bid price). Landlords, however, would like to receive \$y for the same rental. The bid-ask spread, y - x, could be quite large indeed. The two sides could be 10%, 20%, 30%, or even more away from each other.  With neither side willing to budge, the market remains illiquid. As a result, the properties remain vacant.

If no new rentals occurred within 2 years, how would you collect data to analyze the market?
Trade data, where actual trades occurred, would be two years out of date.  
Quote data, where you have recent bids and offers, would be more applicable, since they are more recent. But where is this quote data? Commercial real estate is NOT exchange traded. Commercial real estate does not trade on an over-the-counter market. Therefore, either side does not have a  detailed, accurate, and comprehensive history of bids, offers, and such. In short, there is no publicly accessible limit order book of real estate. These markets could be auction markets or dealer markets, where information is much more difficult to obtain. Indeed, each landlord may deal directly with each prospective tenant.  Alternatively, there may be a middleman (i.e., real estate broker) who ironically makes the market more illiquid by inserting big transaction costs (brokerage fees) that drive the two sides even further apart. In securities markets, there are even dark pools where some details are hidden and others are visible to make markets more equitable by hiding information from advantaged traders, like high-frequency traders.

This gives us the third point of financial data: know your source! Exchange-traded data is often the best because it tends to be complete, detailed, available with not only trade information but also quote information. In the case of cryptocurrencies, there can literally be billions of pieces of information, given the top of book, depth of book, type of trade, and many other fields. Considering  the fact that it trades high-frequency, there can be thousands of points per second of trading.
Quote data does not reflect where prices occur but does show the supply and demand of participants at a given time. Quote data is one of the most comprehensive types of data because it gives a two-sided view of the market.

```python
import yfinance as yf
```
```python
data = yf.download(tickers="NFLX", period="1d", interval="5m")
# Print data
data
```
- output
	- ![](https://i.imgur.com/uueK189.png)

###### 1.1.4. Information Shocks

Indeed, we may want to collect many types of data because we get a fuller picture when we capture data from different markets and sources. Often, we will want to understand that the market experiences shocks, and having different types of data can reveal how significant those shocks are. The required reading for this module walks you through a case study about the Federal Reserve. The Fed's Chairman, Jerome Powell, made statements in October 2018 that affected equity prices for the remainder of 2018 Q4 (i.e., the fourth quarter of 2018). In short, equity prices dropped 29% over this period. Please note that we are not saying that a simple action (Fed decisions) caused these events.  Rather, we are recognizing that finance is an empirical science, rather than a controlled experiment. 

In finance, we perform observational studies and use the enriched analysis to understand the results. Often, results do not simply continue trending or directly mean revert because the conditions continually change. As you do the reading, please study the graphs of federal funds rates, the ten-year U.S. Treasury note, and the S&P 500 stock market level to see how macroeconomic policy affects financial markets and vice versa.

This gives us the fourth point of financial data: financial series jump. Many of the models we will study in this program simplify the behavior of asset prices by assuming they are continuous (like  Brownian motion). In reality, nearly every asset, index, or economic ratio has a tendency to jump. Jumps are not "outliers" or "market corrections" per se, but rather an illustration of how markets consist of a multitude of human decision-makers who tend to react and overreact, causing extreme moves and reversals in markets. We may use models that assume jumps aren't allowed, but it is always prudent to see if the assumptions of those models can be relaxed to accommodate jumps. 

###### 1.1.5. High Frequency
Indeed, some of the data collected may actually contain so much information and noise that it is hard to see the forest for the trees.

This leads us to the fifth point: understanding the frequency of data.
Some series exist at exceptionally high frequencies--limit order books for cryptocurrencies, which can have millions of points each day. Some series are much slower moving, such as corporate bonds, which may trade only a few times per year. Imagine having to run a correlation on series such as these: Do you slow down a fast-moving series, or do you somehow interpolate a slower-moving series? You will see that the financial problem you face will be solved on a time scale--high frequency, intraday, daily, weekly, monthly, periodically. Choose your data accordingly.

Indeed, we will run regressions later in the program that use financial series whose data you could get intraday, along with economic indicators whose values only change quarterly. Learning to combine time series that start out with different frequencies is a key part of financial engineering because we cannot control the experiments, but we can somehow transform data to be modeled.

###### 1.1.6. Liquid Securities

In this section, we'll emphasize one more aspect about financial data. Not all securities are as liquid as other securities. In general, it is better to get data from liquid securities than from illiquid securities. To review, we can consider five characteristics that liquid securities have.
1) A relatively small bid-ask spread
2) Frequent trading
3) Considerable volume
4) Small market impact
5) Units tend to be indistinguishable
  
In the example from the reading, from 9:30-11:30, Flushing Financial stock traded 25 times. During that same time, Microsoft traded 25,250 times! The daily volume for Flushing Financial was 67,250. The volume of Microsoft's daily volume was 44 million!  
In relative terms, Microsoft traded 100 times as often and 655 times as much volume!  
Shares of an S&P 500 stock that trades on an exchange tends to be liquid because it likely meets all five characteristics. Real estate, on the other hand, fails to meet most of these, particularly number 5, because no two properties are identical.

In our simple example of analyzing interest rates, we may want to build a term structure of rates. It would be preferable to use, say, 7 liquid securities (like 7 U.S.-issued treasury notes and bonds), and interpolate to get dozens of points, rather than use 60 illiquid securities.  In other words, only one U.S. bond is liquid--the "active" one, also known as the "on-the-run" or the "current" one.  Meanwhile, there are dozens of 30-year bonds that have been issued; one was issued three months ago, one six months ago, one nine months ago, etc. These bonds are not as liquid as the active one! Why? They don't trade as much because some investors buy and hold. For example, a pension fund manager may buy a 30-year bond and hold it in her portfolio, never to trade it again. The coupon payments the manager receives twice a year can pay retirees their pension. In 30 years time, the principal is repaid, and the process can be repeated. Since these bonds are unlikely to default, they are a way to earn coupon interest over a long period of time.


This gives us the sixth and final point of financial data: try not to combine illiquid and liquid data! Liquid data tends to contain more rapidly changing information.  Illiquid data does not. Think of an illiquid security as having a great standard error around the data value itself. The price from a liquid security is informative, as there was trading there. The price from an illiquid security may not give a good sense of the impact of liquidity.

###### 1.1.7. Conclusion

This lesson introduced the macroeconomic view of data as it affects interest rates. It also covered the role of liquidity in markets, as measured by the bid-ask spread.   The next lesson will drill down into the specific types of data we want to collect.

**References**

* Herrera, Ariel. “FRED API: Get US Economic Data Using Python - Towards Dev.” *Medium*, 30 Mar. 2022, https://towardsdev.com/fred-api-get-us-economic-data-using-python-e51ac8e7b1cc


##### 1.2. Types of financial data 

###### Required reading
1.  Sanger, William, and Thierry Warin. "High Frequency and Unstructured Data in Finance: An Exploratory Study of Twitter. _Journal of Global Research in Computer Science_, vol. 7, no. 4, April 2016, pp. 6–16, [https://www.rroij.com/open-access/high-frequency-and-unstructured-data-in-finance-an-exploratory-study-oftwitter-.php?aid=70514](https://www.rroij.com/open-access/high-frequency-and-unstructured-data-in-finance-an-exploratory-study-oftwitter-.php?aid=70514)
    
    -   **Required pages:** 6 - 8  
    -   **Estimated reading time:** 15 minutes
    - Notes: 
        - not read. lets see if its needed in quizzes.



|  |  |
|:---|:---|
|**Reading Time** |  40 minutes |
|**Prior Knowledge** | Equities, Bonds, Credit Risk, Fundamental Analysis, Technical Analysis  |
|**Keywords** | Structured Data, Unstructured Data, Alternative Data |


---

*The previous  lesson introduced the macroeconomic view of data as it affects interest rates.  It also covered the role of liquidity in markets, as measured by the bid-ask spread.   This lesson will drill down into the specific types of data we want to collect: structured, unstructured, and semi-structured data.  It will also address 10 question you can ask about the data you collect.*

###### 1.2.1. Types of Data for Equities



In this first section, think of all the types of data that you can collect pertaining to equity markets. Note that each of these fields has associated with it an observation time.
1. Prices. Price data tends to be continuous and strictly positive.

2. Issuance. Issuance data tends to be continuous and positive, reflecting a number of outstanding shares.


3. Quotes. Quote data refers to a lot of information. At any given time, there is a picture of the limit order book. This includes prices, sizes, and sides (buy or sell) for many different price levels. If any market maker adds, deletes, or changes a price, size, or side, then the quote data is updated. Indeed, there can be thousands and thousands of quotes per second if market makers are aggressively updating their trade blotter thanks to high-frequency algorithms.

4. Industry Classifications. This data is largely categorical and does not change over time. An exception would be if a company entered into a new industry.

5. Index Memberships. This data is effectively binary (in or out of a membership) and largely time invariant between index rebalances. However, periodically some indices do get redefined, at which points names are deleted from the index (+1 becomes 0) and some names are added to the index (0 becomes +1). Indeed, a classic equity trading strategy is predicting the additions and deletions to an index like the Russell 5000. Typically, stocks that are added tend to have a short-term gain (due to many participants buying the stock so they can track the index). Likewise, stocks that are deleted from the index tend to have a short-term loss due to many participants selling the stock since they no longer need it to track the index.

6. Returns. These are derived from consecutive prices to produce daily returns. While these may use logs or percent, the key is ensuring that the returns are measured using key levels--like official closes.  

7. Volatilities(realized, implied ATM, implied OTM). These should be strictly positive, but also need to take into account that their sizes reflect the period to which they apply -- daily volatilities, in other words, are smaller than weekly volatilities, which are smaller than annual volatilities, etc.

8. Skew.  This is a difficult thing to measure because, as stock prices change, the particular strikes that are in the money and out of the money also change. Moneyness is the ratio of strike level to current stock price. So skew needs to track a moving target of moneyness and the option volatilities at those levels.

9. Financing Costs. This is also difficult because financing can be issue-specific. In other words, a given stock or a specific bond from an issuer can have a very high financing cost due to the supply being quite limited.  When items go "on special," they become very expensive to finance.

10. Portfolio Fees. This is an example of data that may contain hybrid data. The fees could be based on both trading activity and on assets under management. Fees may not seem important, but when backtests are run and all costs are included, the fees could turn an otherwise profitable strategy into an unprofitable one!

###### 1.2.2. Types of Data for Bonds and Other Assets

Similarly, there are lots of different data to get from bond markets.
1. Bond Yields (continuous, largely positive)
2. Bond Carry
3. Bond Financing
4. Bond Issuance
5. Bond Spreads
6. Issuer  
7. Credit Ratings (ordered categories, time variant)
8. Default Probabilities (0 to 1)
9. Recovery Rates (0 to 1)
10. Default Correlations (-1 to 1, but typically positive)

Notice that the last 3 variables are noticeably bounded.  Probabilities and recovery rates are effectively percentages that must lie within the range of 0 to 1 inclusive. Likewise, default correlations are in a band of minus 1 to plus 1. However, negative default correlations among assets in the same market are uncommon.  
```python
# Let's use the investpy package to get Argentinian bond data.
import investpy

data = investpy.get_bond_historical_data(
    bond="Argentina 3Y", from_date="01/01/2018", to_date="31/12/2021"
)
data.head()
```
- output
	- ![](https://i.imgur.com/2TPWT7c.png)

###### 1.2.3. Other Types of Data

Within any asset class, there are multitudes of fundamental and technical factors: price-to-earnings ratio, upper Bollinger band, etc. In fact, we could list hundreds of these factors! Why are there so many?
Consider the moving average.
You could have a 5-day moving average (MA)
You could have a 20-day moving average (MA).
You could have an indicator that determines if the 20-day MA is above, equal, or below the 5-day MA.
You could have an exponentially weighted moving average.
With this short example, we could vary the length (5-day versus 20-day), the calculation (simple MA versus exponential MA), or the relationship (the crossover).


In addition to traditional data, there is also the availability of alternative data. This includes
1. headlines
2. news articles
3. analyst recommendations
4. social media content
5. social media traffic (e.g., number of tweets)
6. reviews

This data tends to be non-numeric, non-rectangular, and very much in need of processing before it can be useful.

###### 1.2.4. Structured Data

Broadly speaking, there are two types of data.
Typically, structured data is rectangular. It can be organized into rows and columns. Rows reflect observation times. Columns represent variables.
For example, you could have a 1000 by 50 matrix of stock prices. One thousand rows represents approximately 4 years worth of daily closes (i.e., business days). Fifty columns represent the 50 stocks within an exchange-traded fund.  
This data can easily be stored thanks to a friendly structure.
One row gives you a snapshot of the portfolio at a particular moment in time--known as a cross-section.
One column gives you a "movie" of a stock over four years--known as a time series.

In this example, the difference between observations is effectively the same--one business day (even though they may range from one calendar day for weekdays to three calendar days for the weekend, or even four calendar days for three-day weekends).

It is also possible to have structured data where the observation times form an irregular time series. For example, if these 1000 points reflect intraday observation times, then the time itself could be a variable.

In Python, structured data can be handled by a variety of data structures, but pandas data frames are often the best choice.

###### 1.2.5. Unstructured Data
Most financial data is numeric, but of course there is also non-numerical data. These data types include social media posts, review sites, photographs, audio, and video files.  If you are pricing weather derivatives, perhaps satellite photos of weather are considered key data. If you are monitoring particular companies, perhaps the sentiment from Facebook, Twitter, or other social media sites reflect the short-term optimism about the stock. Likewise, you might examine customer reviews on Yelp or Instagram for photographs from satisfied users to determine product adoption, popularity and brand loyalty, and customer churning. Indeed, much of machine learning takes inputs from this type of data and builds models known as sentiment analysis. Unstructured data is not as easy to store as structured data, due to the unconventional, non-rectangular format.  

In Python, unstructured data can be handled by dictionaries and lists, which can allow for flexible keys, data types, and data lengths.

###### 1.2.6. Semistructured Data
Data forms a spectrum ranging from unstructured to structured. We can consider a category in between. For example, emails are semi-structured: They have well-defined fields but are unstructured within given fields.  

In Python, semi-structured data can be handled by a combination of data structures. It is difficult to give a specific rule, but Python certainly has a variety of data structures to handle this.

###### 1.2.7. Know Your Data

In finance, when you deal with customers, there's an acronym, KYC: Know Your Customer.
In financial engineering, when you deal with data, we can create an analogous acronym, KYD: Know Your Data.

Here are 10 questions you can ask about the data you collect and intend to use for financial models.

1. Does the data have predefined fields?
2. Is the data scaled?
3. is the data bounded?
4. Is the data observable?
5. Does the data comes from a trade, a limit order book, or neither?
6. Is the data quantitative, qualitative, or a hybrid?
7. Is it continuous or categorical?
8. If it is non-numerical, are there language issues?
9. Was the data collected at the frequency with which it was produced?
10. Was the data cleaned or checked from the vendor?


Let's review these.
1. When data has predefined fields, the data structure is easier to identify and maintain. When data lacks predefined fields, a looser data structure is needed.

2. Some data is best left in its raw form, while other data may need to be scaled. Scaling could be as simple as a log transformation or a volume-weighting applied to the price to produce a Volume Weighted Average Price, or VWAP.  

3. If data is bounded, then we should acknowledge the lowest possible value and the largest possible value the data could have. If we measured probabilities, then we would expect no value to be negative and no value to be greater than 1. Suppose missing values were coded with -99. Clearly, we would need to recognize this as a missing value and not as data. This is often the mistake with importing data.

4. Many financial data series are directly observable-- like stock prices, stock volumes, bond issuance, etc.  Ironically, not all data is directly observable. For example, number of defaults may not be made available, as some data is proprietary. Some data may only be visible based on a given model--for example, default probabilities are not directly observable in the market but are values implied or outputted by credit risk models. The choice of credit risk model will very much affect the default probability we see. The same is true for certain types of volatility--they are not directly observable.

5. Be sure to distinguish trade data--values at which buyers and sellers transacted--versus quote data, which are bids, asks, and their sizes. When the bid-ask spread is wide, the midquote, which is the average of the bid and ask, may not be a good representative of the price.

6. Clearly, qualitative data needs to be processed and interpreted, either through text mining, sentiment analysis, or some other means.

7.  Much of financial data series are actually categorical. For example, credit spreads are categorical and ordered as well. Others are merely categorical, such as industry classifications. It is easy to confuse the two types when the categories are listed as numbers.  

8. Non-standard data is complicated by the fact that it may be in different languages. Sentiment analysis needs to account for the parts of language, such as metaphors, figures of speech, expressions, idioms, multiple negations, sarcasms, and even emojis.

9. For exchanges, there is often a wealth of data provided--closing prices, top of book, and various depths of book data bundles. If you are an infrequent trader, say in your own retirement account, you may be inundated by high-frequency data, which provides too much information and would require enormous processing just to make sense at a scale that is more appropriate to the trading decisions you would make. Conversely, daily data would be inappropriate for a market maker.  Market makers are subject to intraday volatility because they have to make two-sided markets throughout the day.  The volatility at the daily level is too low a frequency to capture what could be a significant event.

10. If you assume data is cleaned from the vendor, then you invite the vendor's gaps, omissions, oversights, misprints, mixups, transpositions into your data, as well as errors in transferring and importing from their side to yours.  
One way to clean data is to have redundant sources.  Imagine you had four sources to tell you a stock's price.  Any discrepancies can be identified and handled manually; even better, rules and filters can be applied so that data seems to agree with itself.





###### 1.2.8. Conclusion
This lesson outlined the types of data for the major asset classes--stocks and bonds--and categorized different types of structured and unstructured data. It concluded by addressing 10 questions you can ask about your data. In the next lesson, we look at working with securities data. 

**References**

- Del Canto, Alvaro Bartolome. “Investpy - Financial Data Extraction from Investing.Com with Python.” *Investpy*, GitHub, https://investpy.readthedocs.io/_info/installation.html. Accessed 4 May 2022.

##### 1.3 Working with Securities data
###### Required reading
Required readings for this program are open access, which means you should be able to access them at no cost. The link provided in the citation will take you directly to the reading or to a page where you can download it.

1.  Cheng, Peng et al. "Massive Data Analytics for Macroeconomic Nowcasting." _Data Science for Economics and Finance_, edited by Sergio Consoli, Diego Reforgiato Recupero, and Michaela Saisana, Springer, 2021, pp. 145–167, [https://link.springer.com/chapter/10.1007/978-3-030-66891-4_7](https://link.springer.com/chapter/10.1007/978-3-030-66891-4_7).  
    
    -   **Required pages:** 145–149
    -   **Estimated reading time:** 20 minutes
2.  Ghirelli, Corinna et al. "New Data Sources for Central Banks." _Data Science for Economics and Finance_, edited by Sergio Consoli, Diego Reforgiato Recupero, and Michaela Saisana, Springer, 2021, pp. 169–194, [https://link.springer.com/chapter/10.1007/978-3-030-66891-4_8](https://link.springer.com/chapter/10.1007/978-3-030-66891-4_8).
    
    -   **Required pages:** 169–173
    -   **Estimated reading time:** 20 minutes




|  |  |
|:---|:---|
|**Reading Time** |  40 minutes |
|**Prior Knowledge** | Equities, Bonds & Maturity Date, Options & Expiration Date, Bid Price / Offer Price, Quantity Bid/Offered  |
|**Keywords** | Primary Sources, Financial Platforms, Data Vendors, Ticker, CUSIP, SEDOL, Adjusted Close, ISIN |

---

*The previous lesson outlined the types of data for the major asset classes, stocks and bonds, and categorized different types of structured and unstructured data. It concluded by addressing 10 questions you can ask about your data. In this next lesson, we examine some of the real-world issues facing financial data: its sources, identifiers, timestamps and trading days, and other complexities.*

###### 1.3.1. Data Sources

In the previous lesson, we discussed the importance of the vendor.
Our first consideration is the quality of the data the vendor provides.
Informally speaking, there are four types of providers of data:

A. Primary Sources
These include exchanges and credit agencies, like rating agencies, credit cards, and credit bureaus.
Exchanges and credit agencies are the locations where the data originates based on transactions, trading, payments, or lack thereof. Here are examples of some exchanges and credit institutions:

* Stock Exchanges: NYSE, NASDAQ, Shangha, Shenzhen, Euronext, Nigerian, Nairobi, Stock Exchange of Mauritius, etc.
* Option Exchanges: Chicago Board Option Exchange
* Commodity Exchanges: Chicago Mercantile Exchange, London Metal Exchange
* Forex Exchanges: London, New York, Sydney, Tokyo 
* Cryptocurrency Exchanges: Bitcoin, Coinbase, Binance, Gemini, FTX  
* Credit Agencies: S and P, Moody's, Fitch, Transunion, Equifax, Experian, Visa, Mastercard
    

B. Financial Platforms
These companies provide trading platforms, news, analytics, and communications. While they may provide data, they are typically redistributors of data from exchanges, OTC markets, and other financial sources. The data can be analyzed from inside their platform or through an API.

* Bloomberg
* Thomson-Reuters
* Factset

C. Data Vendors
These companies tend to focus on data and analytics. They tend to have their data accessible through APIs. Their revenue typically comes from selling or streaming data to clients.

* BarChart
* RavenPack
* Capital IQ
* CRISP
* Datastream
* Morningstar
* Exante Data
* Xignite
* Refinitiv
* Short Trends
* dxFeed

D. Free Sites
Finally, there are free sites, whether public services, government sites, or user groups, that pool and provide access to free data for educational purposes or individuals. Some of these limit the amount of data that can be accessed.

* Quandl
* Alpha Vantage
* FRED: Federal Reserve Economic Database
* Yahoo finance
* Google finance


The emphasis here is not so much knowing which vendor is in which category, but how they may offer the data. 
	Exchanges can often provide complete data, including quote and trade data. 
	A free site like Yahoo finance may only be able to provide end-of-day data based on trades and not quotes. 
	Some vendors may clean the data; 
	others present the data as they collected it and leave it to customers to address errors. 
	Some data may be in a format known as FIX: Financial Information eXchange Protocol. 
	Other data may simply be in comma-separated values, tab-delimited formats, etc.

Data itself is a commodity, and exchanges, markets, and vendors make money providing this data, whether historical, daily, or real-time, to clients who need to make quick, if not real-time, decisions with it.

```python
# Using the `pandas_datareader` package, we'll get Netflix stock information from Yahoo Finance
import pandas_datareader as pdr

# Request data via Yahoo public API
data = pdr.get_data_yahoo("NFLX")
# Display Info
print(data.info())
```
- output
	- ![](https://i.imgur.com/3qgLvWb.png)

```
# If we wanted 1 day's worth of Bitcoin data, we can use the following
import yfinance as yf

BTC = yf.Ticker("BTC-USD")
BtcData = BTC.history(period="5D")
BtcData.tail(2)
```
- output
	- ![](https://i.imgur.com/jfN1eZc.png)

###### 1.3.2. Data Descriptors

How do you refer to data related to specific securities? Most securities have identifiers. In the previous example, we referred to Netflix by its ticker, NFLX, on the stock exchange.  Depending on the asset class, different types of identifiers are used. In previous lessons, we discussed bonds, stocks, cryptocurrencies, mutual funds, ETFs, options, securitized products, and real estate, among others. Let's start with stocks.

Tickers are the most popularly known identifiers. You will see tickers listed on screens during television shows or podcasts, in newspapers and online stories, as the ticker may tend to have some resemblance to the name or type of company. Everyone knows Facebook as FB (even though it is now Meta), Apple as AAPL, and IBM as, well, IBM! The ticker is not only an identifier but a way to remember the company. For example, Papa John's is a food company that specializes in pizza. Its ticker is PZZA. Thermogenesis Corporation is an energy company with the ticker KOOL. Southwest Airlines' ticker is LUV.  WideOpenWest has ticker WOW. Research has shown that the ticker can actually affect the performance!

In 2006, researchers showed that if the ticker is easy to pronounce, it tends to outperform the market. [Boutin]
In a 10+ year study, researchers at Pomona College showed that stocks with clever tickers outperform stocks with plain tickers [Smith]. Who would think that the resemblance of a ticker to a fun or easily remembered word could affect the company's performance? In a future course, we'll cover topics related to behavioral finance and discuss the idea of familiarity bias.  

Tickers are important but tend to be applied to stocks and ETFs. Bonds, for example, do not have tickers. Let's look at some other ways securities are identified.

CUSIP: Typically, when you see all uppercase, the identifier is an acronym.  CUSIP is an acronym for 'Committee on Uniform Security Identification Procedures'. Used in North America, it is a nine-digit alphanumeric code that uniquely identifies not only a security but also information about its type and issuer. The first 6 alphanumeric characters identify the issuer. The next two characters identify the type of security. The last digit is a check that the code is created correctly. CIN is a CUSIP for securities in foreign markets. These are extra digits, where the first letters represent the issuing country. The acronym refers to the CUSIP International Numbering System.

SEDOL is also an acronym: Stock Exchange Daily Official List. When a company is listed on an exchange, it has a SEDOL. If it gets delisted, it loses its SEDOL. Consider the case of Hertz Rental Cars. Hertz was the number one rental company in the world. Hertz ran into financial difficulties. It suffered further during the COVID-19 pandemic, which affected both business and leisure travel. In May 2020, Hertz filed for Chapter 11 bankruptcy. Later that year in October 2020, Hertz was delisted from the NYSE. At that time, the SEDOL changed representing a listing no longer on the NYSE but on NASDAQ. Any data collected on Hertz must recognize the switch from one exchange to another.

ISIN is the International Securities Identification Number. ISIN uses 12-digit identifiers. The first 2 characters are alphabetic identifying the country. The next 9 alphanumeric characters identify the security. ISINs are more universal. For example, futures tend not to have CUSIPs but have ISINs. Foreign Exchange rates have identifiable tickers (e.g., GBP/USD) but are referred to internationally by their ISINs.

The securities we've described are fungible. Fungible securities are interchangeable. For example, 100 shares of AAPL common stock are like any other 100 shares of AAPL common stock. Most financial securities are fungible. Note that fungible need not mean identical. Gold is considered fungible, so long as it does not have serial numbers or marks that uniquely identify it. (U.S. dollar bills have serial numbers but are still considered fungible.) Likewise, Bitcoin is fungible. You can pay someone a Bitcoin, and they can send you a different one back. They are considered interchangeable, just like paper currency in any country.  

When we get to items that are more specific or unique, we have infungible securities. Real estate is not a fungible commodity. It is not interchangeable. Real estate is infungible. Even two houses that are the same size, material, and location are not interchangeable, in part because they are in different physical locations, with different views, light, neighbors, properties, etc. Similarly, works of art are not fungible. An original painting or sculpture is not like any other. Securities that are infungible will be very difficult to identify because they are, by nature, unique.  

For example, Zillow may show a property that was \\$100,000, and then a year later, it is \\$500,000. Did the house really increase five-fold? No. Zillow represents the value of whatever the real estate is at the address.  Originally, the land was undeveloped; it was a vacant lot. It was bought by a builder for \\$100,000. The builder constructed a house that was then sold for $500,000. The land itself has value ("undeveloped") and any structures (homes, buildings) add value through "developments" on the land. Zillow relies on a deed or property record, often filed at the local level, to refer to the property. With millions of properties, it is difficult to uniquely identify a property and likely impossible (and unnecessary) to have an internationally standardized system.  

Moving to precious jewelry, diamonds are infungible. In the U.S., some diamonds are graded by the Gemological Institute of America (GIA) and have an engraved serial number. This makes diamonds like gold with a serial number--not interchangeable and thus infungible. Diamonds without this engraving are more fungible. However, there are risks that it is not properly appraised for clarity, carats, and even if it is man-made or natural.

When you want to analyze the behavior of securities, think about the data you are collecting, and ask yourself if it is a specific, one-of-a-kind asset (home, art, some jewelry) or a fungible, easily interchangeable asset (stock, bond, ETF). Use identifiers if they help.



###### 1.3.3. Time Zones, Trading Days, and 24/7

"Get me the closing price" is something you will hear as a financial engineer. But what is "the" closing price?
The answer sounds like a quantum physics one--depending on where you are, the close will be different, based on your location and time zone.

Clearly, if we are in Lagos, Nigeria, trading Dangote Cement, we can expect its official close at the close of the Nigerian Stock Market--2:30 PM local time, or GMT+1. If we are in Sydney, Australia, trading the Australian stock BHP, then we observe the market at its closing time, 4:00 PM Sydney time: GMT + 10 hours.

Suppose we want to correlate the returns of these two companies using closing prices. We have to remember that their official exchange closes are about nine hours apart! Here is a table of times the markets open and close:

 GMT    Sydney, Australia   Lagos, Nigeria    Event
 00:00       10:00            01:00           Sydney Stock Exchange opens
 06:00       16:00            07:00           Sydney Stock Exchange closes     
 09:00       19:00            10:00           Nigeria Stock Exchange opens
 13:30       23:30            14:30           Nigeria Stock Exchange closes
  

Depending on the objective of the analysis, one could use
* Plan A: GMT=06:00. Get the data at Sydney's close, but the Nigerian exchange is not open!
* Plan B: GMT=13:30. Get the data at the Nigerian exchange's close, but the Sydney exchange has already closed.
The advantage of Plan B is that the date will reflect the closing prices of both exchanges. Even though Sydney closed, that is the last observable price for that trading day.
Keep in mind that data is not available until at least GMT=13:30 when the Nigerian exchange closes.
If you were to build a trading strategy using this closing correlation and decided to buy Dangote, it would have to be for the following trading day. Indeed, novices will often lose a sense of the timestamp. If you were to build a strategy that buys Dangote based on the correlation, we would reverse cause and effect.

The difficulties are more subtle if we look at the same security that trades in different parts of the world.
Consider a credit derivative that was discussed in Financial Markets, say a 5-year Credit Default Swap on IBM.
You can purchase this CDS from a Tokyo-based bank, a London-based bank, or a New York-based bank, among other locations. Each of these banks is geographically located in a different part of the world. Depending on the time of year (thanks to daylight savings), Tokyo is 12 hours ahead of New York, and London is 5 hours ahead of New York. Each one of these locations has an official close. For securities that are not housed in a specific location (like a 5-year cds), there can be "different closes" because the CDSs are not exchange traded, but over the counter. As there are OTC markets worldwide, the notion of close is relative to a geographical location.  

Reflecting on section 1, think about the quality of your data vendor. Are they providing the timezone, market, currency, etc., of the CDS value? If not, there is uncertainty about where the data originates.

What if we have an exchange, but it never closes? For example, Bitcoin may use GMT - 5 hours as the official close. But for a market that trades 24/7, is this price really more important than the price each day at GMT?

When data lives in different geographical regions, or simply on exchanges with different closing hours, be sure to align properly so that the trading date reflects the close on that date.


###### 1.3.4.  Mixing Up Fields

Following up from the last section, depending on the location of the data, the currency can be different. So in our CDS example, you can find data denominated in yen, pound sterling, or U.S. dollars.  Oftentimes, people collect the data and think of it as a number separate from the units. This would be easily distinguished for yen-denominated and dollar-denominated, but not so for when the currencies have an exchange rate closer to 1. Be sure when you compare levels that you are comparing numbers representing the same quantity. One way to fix this problem would be to compute returns instead of using levels. Another way would be to have a common currency for all quoted prices. This would involve having appropriate FX conversions.

Collecting data as numbers without paying attention to the units can lead to disastrous results. Be sure to keep fields correctly labeled.  

For example, imagine if you mixed up price and quantity.
Suppose, for example, you were supposed to sell some stock: say 1 share at 610,000 yen.
That is, the quantity is 1, and the price is 610,000.
Suppose there is a mix up of the data, and you send an order to sell 610,000 at 1 yen!

Indeed, this very mistake happened in December 2005 to a well-known global bank. The bank had an operational risk of data whereby they mixed up price and quantity. The bank anxiously tried to cancel the order, but the Tokyo Stock Exchange did not allow cancellations. The stock was sold at a bargain, a fraction of its true worth. Ironically, the amount being sold was more than the amount actually issued! Nevertheless, when the damage was done, it cost the bank US \$225 million dollars, nearly a quarter of a billion dollars, which makes for a very expensive typo. The bank was large and profitable enough in other businesses that it did not result in their demise. [CBS]

This is no small matter and emphasizes a distinction between programming and financial engineering.
The programmer will apply test cases and have validation suites, such as asserting that prices must be positive.

The financial engineer, however, will put these in the context of financial markets, and likely would ensure that the program reject the trade before it ever gets to the exchange. Indeed, it would have been better
to reject the trade outright. What quality checks could have been done on the data? The financial engineer could ask:
1. Should the offer price be 600,000 yen different from the last traded price?  
2. Should the offer price be different from the daily volume weighted average price (VWAP)?
3. Should the quantity offered be more than the bank had on hand?
4. Should the quantity offered be more than the total amount in issuance?
All these questions have the same answer: NO. The financial engineer uses financial common sense to assert that the inputs do not make sense given the financial state of the system and rightfully rejects the order. This would have saved hundreds of millions of dollars.

We will see in the next lesson that there could be quality data checks throughout the handling of data to ensure that these types of errors avoid massive costs. The problem isn't merely saving money but also protecting the reputation and trustworthiness of operations of these financial institutions.



###### 1.3.5.  Complexities

In addition to differing units, timestamps, and currencies, financial data tends to have its own set of complexities.
For example, stocks can split, whereby the number of outstanding shares increase and the share price decreases. For example, a company with 100,000,000 shares at \$200 per share could have a 2-for-1 split so that there are now 200,000,000 shares at \\$100 per share. Similarly, a company could have a reverse split--those 100,000,000 shares at \\$200 could become 50,000,000 shares at \\$400 per share. In either case, market capitalization always remains the same. The idea behind splitting is that it makes stocks more affordable. When stocks split, the histories actually have to be adjusted so that the stock doesn't have a 50% drop in price.

In addition, equities receive dividends, which affect the prices, so equity prices also need to be adjusted for the income they receive as dividends.  Often, you will see stock prices adjusted for splits and dividends.  For example, importing data from Yahoo finance, the most suitable column is the "Adjusted Close" column, rather than the Close column.

When we upgrade from individual securities to ETFs, we have extra complexities. A sector ETF has members, whose names and weights change over time. So in addition to tracking the price and volume history of ETFs, we may want to track additions, deletions, and re-weightings.  

Keep in mind that ignoring deletions creates a survivorship bias. Suppose you did a five-year study on an equity index like SP500. You start in 2022, and look back, say 15 years, and only use those companies that existed for that 15-year period. Companies that started out in 2007 but failed to survive would be excluded from the study. So the study looks only at stocks that survived the 15-year period. This survivorship bias means that our results will appear better than they really were because there are some companies that went bankrupt bringing the average return down.

Leaving the world of equities, there's a complexity regarding time. Bonds mature. On-the-run active bonds roll. Options expire. Suppose you have a specific 10-year bond issued in the U.S. If you collect this for a number of years, you are following a bond whose time to maturity keeps decreasing.  After 10 years, the bond matures.  
Yet, it is possible to find decades and decades of history of 10-year notes.  How? We use a generic 10-year CUSIP.
What makes this generic? Suppose a new 10-year note is issued every three months. Then, every three months, the generic switches from the old issue to the new issue. So long as 10-year notes are regularly issued, we can continue to roll out of the old issue into the new one. This is what generic series do. This works for future contracts as well. Since futures expire, we simply use generic versions to track.

Options are more complex because they don't roll like futures contracts. In the next section, we'll see why options in fact are the most difficult.


###### 1.3.6.  Choices within an Asset Class
Choices refer to the extent of selections there are in an asset class.  Suppose you like to trade a security related to the company Apple.

There is one common stock for Apple, and the most liquid place to trade it is on the NASDAQ (though it trades on some foreign exchanges like Buenos Aires and Berlin)

Yet, if you wanted to buy bonds, there are dozens of choices--different maturities with various coupons.  

Furthermore, if you wanted to buy options, there are hundreds of choices--calls or puts, different strike levels, different expirations, different types of exercise, and even different payoffs (vanilla or exotics). The choices are staggering.

When there are more securities in a class (IBM Bonds or IBM calls), the liquidity is going to spread out. Therefore, the data is harder to collect, organize, and analyze.  

In general, equity data is the easiest data to manage, in part because of the small number of securities. ETFs are a bit harder because they involve members and weightings that change quite frequently. Then, bonds are harder still because of both the great number of them, the complex features (e.g., callable bonds, convertible bonds), and the maturity dates winding down.  Options are probably the most difficult security data to work with because of the vast number of them and their dependence on the underlying securities.  

Options can change in value because the underlying changes, volatility changes, interest rates change, or any combination of these. For example, option prices decreasing in price could simply reflect the fact that they are getting closer to their expiration dates and not necessarily due to a decrease in volatility.



###### 1.3.7. Conclusion
Financial data has its own set of idiosyncrasies and complexities: different frequencies, units, time zones, currencies, some of which represent executable prices and others that are mere quotes. This lesson gave a broad introduction to these issues. In the next lesson, we'll add unstructured data and compare how these data management issues lead the way to getting data ready for machine learning.
 

**References**

* Boutin, Chard. "Stock Performance Tied to Ease of Pronouncing Company’s Name."
https://www.princeton.edu/news/2006/05/29/study-stock-performance-tied-ease-pronouncing-companys-name

* [CBS News]. "Stock Trade Typo Costs Firm $225M." December 9, 2005.
https://www.cbsnews.com/news/stock-trade-typo-costs-firm-225m/
    
    
* Smith, Gary. Stocks with Clever Ticker Symbols Outperform Plain Names, New Pomona College Study Confirms.
https://www.pomona.edu/news/2019/09/27-stocks-clever-ticker-symbols-outperform-plain-names-new-pomona-college-study-confirms




##### 1.4. From a financial engineering view to a ML view
###### Required Readings

Required readings for this program are open access, which means you should be able to access them at no cost. The link provided in the citation will take you directly to the reading or to a page where you can download it.

1.  Akansu, Ali. "The Flash Crash: A Review."_Journal of Capital Market Studies_, vol. 1, no. 1, 2017, pp. 89–100, [https://www.emerald.com/insight/content/doi/10.1108/JCMS-10-2017-001/full/html](https://www.emerald.com/insight/content/doi/10.1108/JCMS-10-2017-001/full/html)
    -   **Required pages:** Whole article
    -   **Estimated reading time:** 45 minutes
2.  Ishwarappa, and J. Anuradha. “A Brief Introduction on Big Data 5Vs Characteristics and Hadoop Technology.” _Procedia Computer Science_, vol. 48, 2015, pp. 319–24. Crossref, [https://doi.org/10.1016/j.procs.2015.04.188](https://doi.org/10.1016/j.procs.2015.04.188)
    -   **Required pages:** Whole article
    -   **Estimated reading time:** 45 minutes



|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Structured Data, Unstructured Data  |
|**Keywords** | Flash Crash, Data Volume, Data Variety, Data Velocity, Data Veracity, Data Value |


---

*When you are in a shopping mall or airport terminal, you walk up to the information kiosk to find a map that says “You are here.”  If we were to do so in the world of data, what would the map look like?  As financial engineers, where are we in the vast world of data? There is time series data, survey data, economic data, alternative data, big data. This lesson will attempt to answer that by examining data from the financial engineering perspective to the machine learning perspective. We’ll begin by looking at desirable features of data.*

###### 1.4.1. Data Quality

As financial engineers, we think of data as information provided by markets. Those markets could be securities exchanges, over-the-counter markets, credit agencies, central banks, economic institutions, etc. The data can be provided by the exchanges themselves, broker-dealers with whom we trade, the agencies who make and sell the credit models, central banks, and economic institutions through their API portals. There are also third-party companies that use data to build factor models, or other value-added models that score or rank stocks, securities, factors, and sectors to assist in financial decision-making.
Regardless of the source, there are four features of data equality we always seek:

a.	Accuracy <br>
b.	Completeness <br>
c.	Consistency <br>
d.	Timeliness <br>

Suppose we were making a lending decision to a consumer.  How would we know the credit risks to determine a suitable credit limit, interest rate, and repayment terms? All four of the principles would apply. Here’s how the four features would apply.

1.1 Accuracy
First, we’d like to ensure that the data we have is about the person to whom we intend to loan funds. We’d want to make sure we have the correct individual and would rely on reference data pointing to the person (a national ID number).  Just as securities have their primary keys like CUSIPs or SEDOLs, people should have unique identification. We would want to make sure we don’t mix up people with the same name or even family members with the same name who live at the same address.    

1.2 Completeness
Second, we would want a complete history. Imagine if we only pulled credit reports say within the last 10 years for homes and other collateralized loans, but not for ordinary credit cards. We would have only a partial picture.  Completeness means that the lender has to perform due diligence to discover all information. Of course, regulation may prohibit a lender from getting information that is not allowed. For example, some credit prohibits a person’s age or gender as a criterion for getting a loan.  These protected classes ensure fairness in lending.  Completeness must abide within the confines of what information is allowed, and find full histories.

1.3 Consistency
Third, we would like the data that is provided from different sources to agree. As there are multiple companies that collect and provide credit ratings, we may want to pull from two or agencies to see if the data is consistent. Indeed, using multiple credit agencies we can correct for any discrepancies.

1.4 Timeliness
Fourth, we would like the data to be timely. Suppose a customer applied for six different credit cards all within one morning. We would need to make sure our credit checks reflect real-time lending. Even data that is one day old would not show the extra credit or outstanding balance an individual may have. Such a system could be gamed, and ill-intentioned borrowers can get an inordinate amount of loans all within a short window of time, achieving a balance far beyond what would be accepted if they applied for these loans over a longer period of time. Indeed, the burden on many analytics providers now is that data analytics are performed in real-time. This requires not only the ability to handle real-time requests, but also the ability to run analyses that take a short time so that decisions can be made quickly. For example, many credit cards offer an opportunity for a credit increase and are able to provide an answer in under a minute.   

The computational and modeling burdens these demands place on the analysis require a thorough understanding of the data. In the next section, we’ll start by reviewing structured data.

###### 1.4.2. Structured Data

In the last section, we discussed four principles of quality data. Let’s apply these to structured data, the topic of our previous lesson.  

**2.1 Accuracy**
We’ve been taught “garbage in, garbage out” as a reminder to incorporate accuracy. Clearly, if we have data that is well structured, but highly inaccurate, we have garbage coming out. Note that this is not merely useless. It is dangerous! Models that produce outputs that "seem" correct may be used for pricing and hedging and cause untold amounts of financial damage. Recall the operating hazard of mismatching price and quantity, resulting in a \$225 million dollar trading error. Had the model simply produced no output or warning messages, no trade would be executed and no money would be lost. Useless means a model has no use. Dangerous means a model can lose big time.  

**2.2 Completeness**
What about completeness? Suppose we were measuring volatility. Imagine we included the week of the flash crash, but only looked at a frequency that misses the event, say weekly data. Would our data be complete? If we had decisions in place, such as stop-losses, then those could trigger when using live market prices, which we would not know with a volatility measure based on weekly returns. As you progress in your coursework through econometrics, stochastic modeling, and machine learning, you will be exposed to different frequencies of data. Volatility will look different at different time scales. Having a complete set of data will depend on your application.  


 **2.3 Consistency**
Likewise, consistency is key. Is data that comes from different sources the same? For example, suppose you had been closely monitoring the equity market in the U.S. On April 23, 2018, the news agency Associated Press had their Twitter account hacked.  The tweet read “Breaking: Two Explosions in the White House and Barack Obama is injured.” The Dow Jones Industrial Average plunged -0.33%, and the S&P500 fell -1.21%. In dollar amounts, \\$136 billion of market cap evaporated (Domm).

However, there were no other tweets or headlines about the story. Could the Associated Press be that much quicker than all the other global news sources? Surely, such a story would have received wide media coverage. If we insisted on having consistent data sources, we would anticipate a second data source providing the same news. There was none because it was fake news due to a hacked account. The White House quickly confirmed there was no incident. Within six minutes, stocks returned to their normal levels. However, the turbulence for those 6 minutes was enough to wipe out more than $22 billion per minute! Most of the trading was performed by automated trading rules, which were likely to react first rather than “wait for confirmation” later.  

Consider a different example: credit scoring individuals applying for a loan. We can enforce consistency by comparing credit scores from different sources. For example, there are three major credit agencies that provide FICO scores for individuals. While the “true” value is never known, we can compare all 3 scores. Many lenders may use a median score as a means to resolve any discrepancies. Therefore, redundancy in data sources is a good practice.

**2.4 Timeliness**
The last point concerns the timeliness of data. Arguably, this is the most difficult issue in finance, because financial models built with data can easily become “miscalibrated”. Finance is not physics. In physics, the laws of the universe are largely invariant over time. Data we collected yesterday can be used to construct a model that would likely work just as well tomorrow as it does today. Finance, however, is not physics but social science. In social science, laws are replaced by “principles” or “rules” by which humans tend to behave and make decisions.  However, people change their behavior and their decision-making, so models that work one day in finance may not necessarily work the next–-either because a new calibration is needed or perhaps because the model as a whole is no longer appropriate.  
For example, several years ago, the app Google Maps suggested a shortcut for commuters driving to New York City over the George Washington Bridge. At first, only a few drivers followed this shortcut. But as Google Maps and other navigation apps had wider adoption, more and more drivers took this shortcut. It reached a point where the shortcut became just the opposite: traffic congestion. The town attempted to ban out-of-town drivers from using their roads. When people learn of shortcuts, tricks, and secrets, they can change their behavior in a way that effectively eliminates the short cut (Foderaro). 

In market terms, if there is arbitrage (‘extra time’), as market participants learn and exploit it, it goes away: a restoration of market efficiency. As financial engineers, the price we pay is a constant and healthy amount of skepticism: How can we know that the data we collected continues to accurately represent the way the system works today?  

```python
# The FX market is open 24 hours a day, 5 days a week.
# Let's get the most recent FX data: Japanese Yen to Eurodollars
import yfinance as yf

data = yf.download(tickers="JPYAUD=X", period="1d", interval="15m")
data
```
- output
	- ![](https://i.imgur.com/CMf8PYX.png)

###### 1.4.3. Unstructured Data

As we move to unstructured data, we see that the same principles apply.  Let’s discuss what makes data unstructured.  Unlike structured data, unstructured data lacks a predefined format.  It tends to be qualitative, but can be numeric.  It is disjoint, disorganized, complex.  The key distinction is that the data isn’t easily placed into a tabular format that relational databases expect.  Rules of thumb in the industry estimate that approximately 80% of all data is unstructured.    
a.	Business Documents
b.	Product Photos or Barcodes
c.	Audio Clips
d.	Videos
e.	Reviews
f.	Social Media
g.	Customer Feedback
h.	Web pages
Some data may lie in between structured and unstructured.  Emails are considered semi-structured because they contain some known fields: sender, recipient, header, and message.  However, within the message field, the data is unstructured and cannot easily be parsed using traditional methods.   

###### 1.4.4. Alternative Data
Finance has often referred to unstructured data as alternative data. Let’s look at some examples. Suppose you are pricing weather derivatives. How do you construct hedges? For example, [one bank uses NASA satellite imagery for pricing and hedging weather derivatives](https://www.artemis.bm/news/mitsui-sumitomo-to-use-nasa-satellites-for-weather-derivative-sales/).  
Consider sentiment analysis for social media. Social media contains many unstructured data fields we discussed in the previous section. Those data need to be captured, from which a rigorous sentiment analysis can be performed.  Please read the paper by Hansen on alternative data and sentiment analysis.

**4.1 Properties of Alternative Data**
What are the properties of alternative data?  We can list at least half a dozen:

1.   They tend to be unstructured
2.   They tend to be less commonly used in traditional finance 
3. Many of the sources (but not all) come from non-financial markets
4. Many of the data contain rare or extreme events
5. Many contain non-textual information, such as audio, video, or imagery
6. They may be the exclusive source of this information



**4.2  Quality of Alternative Data**
The same principles of accuracy, consistency, completeness, and timeliness apply to unstructured data. However, these can be harder to assert if there is only one source. As an example, an artist with some extra time on his hands decided to trick Google Maps. He collected 99 iPhones, put them in a wagon, and walked them up and down the street in Berlin in front of the Google headquarters. With many phones moving that slowly, Google Maps reported a massive traffic jam--though there were no cars on the road! (Somos)

Fake reviews abound. A food writer, also with a lot of extra time, created a "fake restaurant" and wrote fake reviews of it. Despite there being no physical restaurant there, the restaurant became TripAdvisor's No. 1 ranked restaurant in London! (Bender)
We could look at these events as pranks played by artists.  But the Flash Crash is no different--trades entered by a spoofer who caused a trillion dollars of market swings.  Read the Akansu paper “The Flash Crash: A Review.”
We’ll conclude this section with a review of the data.

**4.3 Assessing Alternative Data**
Consider some questions to ask about alternative data.
Who generates the data?
Who collects the data?  
How is it recorded?
Who has access to the data?
How can it be verified?


```python
# Let's look at a few fundamentals on Uber.
ticker = "UBER"
UberFundamentals = yf.Ticker(ticker)
print(UberFundamentals.info.keys())
print(UberFundamentals.info["freeCashflow"])
print(UberFundamentals.info["priceToBook"])
```
- output
	- ![](https://i.imgur.com/3FFLyXf.png)

###### 1.4.5. The Big Data: [[The 5 V's]] 

In the field of data science, machine learning has provided best practices of data for more than 20 years. There is a well-known “Big 5 Vs." (Some papers point to dozens and dozens of Vs!) We’ll discuss these five features. (Please see the Ishwarappa paper for more details.)

* **Volume**: Volume is the amount of data. Streams and streams of data pour in.

* **Variety**: Variety refers to the different sources and forms. In our previous sections, we saw that data can be structured, semi-structured, or unstructured.

* **Velocity**: Velocity refers to the rate at which data is created in real time. Exchange data can be as fast as fractions of a millisecond! Other financial data may not be available more than once a day or even quarterly in the case of economic indicators.

* **Veracity**: Veracity refers to the confidence in the data source.  Think fake news accounts and spoofed trades.

* **Value**: Value refers to the insights available in the data.  

###### 1.4.6. Conclusion 

Data science has influenced every field due to its universal nature of addressing data collection, visualization, modeling, and presentation. Financial engineering is no exception. As financial engineers, we’ll examine machine learning problems through a financial lens and follow the best practices for data that have been recommended in both fields.

**References**

*   Bender, Andrew. TripAdvisor Gets Totally Punked when Fake Restaurant is Ranked No. 1. *Forbes*, December 8, 2017.  
https://www.forbes.com/sites/andrewbender/2017/12/08/tripadvisor-gets-totally-punked-when-fake-restaurant-is-ranked-no-1/?sh=2d5d01282c23

* Domm, Patti. “False Rumor of Explosion at White House Causes Stocks to Briefly Plunge; AP Confirms Its Twitter Feed Was Hacked.” *CNBC*, 24 Apr. 2013, www.cnbc.com/id/100646197.

* Foderaro, Lisa. “Navigation Apps Are Turning Quiet Neighborhoods Into Traffic Nightmares.” *The New York Times*, 24 Dec. 2017, www.nytimes.com/2017/12/24/nyregion/traffic-apps-gps-neighborhoods.html.

*   Somos, Christy. German Artist Uses 99 Smartphones to Fool Google Maps with Fake Traffic Jam. *Sci-Tech News*, February 4, 2020.
https://www.ctvnews.ca/sci-tech/german-artist-uses-99-smartphones-to-fool-google-maps-with-fake-traffic-jam-1.4797313?cache=yes%3FclipId%3D89619%2Fexpert-advice-5-ways-to-get-rid-of-annoying-fruit-flies-1.2492904


#### M2. Equities and crypto in python

##### 2.1. Analyzing prices of stocks,bitcoin, and bonds

###### Required readings
1.  Bionic Turtle. "FRM: Why We Use Log Returns in Finance." _YouTube_, 3 Feb. 2009, [https://www.youtube.com/watch?v=PtoUlt3V0CI](https://www.youtube.com/watch?v=PtoUlt3V0CI).
    
    -   **Required pages:** Whole video
    -   **Estimated reading time:** 6 minutes
2.  Damodaran, Aswath. "Corporate Finance B40.2302 Lecture Notes: Packet 1." [http://people.stern.nyu.edu/adamodar/pdfiles/cfovhds/cfpacket1spr19.pdf](http://people.stern.nyu.edu/adamodar/pdfiles/cfovhds/cfpacket1spr19.pdf)
    
    -   **Required pages:** Slide number 74–76
    -   **Estimated reading time:** 10 minutes

|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Basic Python, Algebra|
|**Keywords** | Stock, Bitcoin, Bond Prices, ETFs, Simple Returns, Analyzing and Charting Data in Python |

---


*For the first lesson of this module, we will recap some of the concepts you learned during the Financial Markets class. We will examine stocks, bonds, and cryptocurrency prices during this lesson. Finally, we will also demonstrate how to pull price data from Python and do some basic price analysis of equities, Bitcoin, and bond data.*
```python
import datetime

import numpy as np
import pandas_datareader.data as web
from IPython.display import VimeoVideo
```

###### 2.1.1.Pull Equities Data from Amazon and Ford, along with Bitcoin Data
The following code pulls the last five years of equity price data from Ford and Amazon along with the daily Bitcoin prices over the same time period. The reason we chose Ford and Amazon here is to give examples from different sectors. While Amazon has been around for a while now, it still represents a newer, popular tech stock while Ford is very much a part of the old guard, trading publicly since 1956.

```python
# start = datetime.date.today() - datetime.timedelta(days=5*365)
# end = datetime.date.today()
start = datetime.date(2016, 11, 16)
end = datetime.date(2021, 11, 18)
df = web.DataReader(["AMZN", "F", "BTC-USD"], "yahoo", start, end)["Adj Close"]
```

2.1.1.1 Taking a look at the data
Unless you're extremely familiar with the dataset you're working with, it's almost always a good idea to take a look at the first few rows of the data to get an idea on how it looks. We can accomplish this using the *head()* method. You can pass a numerical parameter in this (for example, 10) and it will return the top 10 rows of the data set. By default, it returns the first five.
```python
df.head()
```
- output: 
	- ![](https://i.imgur.com/xqYcgyQ.png)

Right off the bat, we can see in Figure 1 that it was a smart idea to take a look at this data first. Can you guess why we have null values here?

The answer is simple—equities only trade Monday through Friday, which means there’s no price data available on the weekends. Bitcoin does not have this same characteristic as it trades seven days a week, which is why 2016-11-19 and 2016-11-20 are populated in this case. 

2.1.1.2 Digging a little deeper into the data
We can use the pandas `describe()` method to show summary stats of our data. We can see that Bitcoin has a much higher number of observations (count) than our two stocks, which, as just discussed, is because of stocks not being traded on weekends. The other summary stats are relatively basic, like mean and standard deviation along with showing minimum, maximum, and a few quantiles. This might be something you are interested in, but it is hard to compare these investments with this data alone since each asset had a different starting price five years ago. For a better comparison, we will have to examine returns in more depth in an upcoming lesson.
```python
df.describe()
```
- output
	- ![](https://i.imgur.com/FuEqAO1.png)

In the following video, we will recap what's been done so far and show how to pull price data using Python's built-in libraries.

```python
VimeoVideo("706651332", h="84a123c14c", width=600)
```
[Access video transcript here](https://drive.google.com/file/d/1c6-7UwtiIlRk8kjvp5_76gsTgCdoFUG7/view?usp=sharing)

2.1.1.3 Charting prices over 2020
If we ever want to get a quick plot of the DataFrame's data, we can use the aptly named plot() method. As shown below to chart the 2020 returns of these 3 assets
```python
df["2020-01-01":"2020-12-31"].plot();
```
- output: 
	- ![](https://i.imgur.com/wOX1nBQ.png)

The above code and chart demonstrate how we can easily pass in a date range to the plot method in order to chart a subset of the data. If no date range is supplied, by default, the plot will encapsulate the entire data set. Once again, the following chart illustrates why using price alone is not ideal for comparing two assets. The scale of Bitcoin’s price versus a low-price stock like Ford makes it very hard to compare the two when deciding which stock is better to invest in.



###### 2.1.2. Calculating Return on Investment
If we invested \$1,000 into each of these assets five years ago, how much money would we have today? To answer this question, we first need to determine how many shares of each stock we could buy with \\$1,000 at the start of our date range. For the purposes of this exercise, we will use 11/21/2016 as our starting point because it’s the first weekday of our data set. 

From our data above, we can see the starting prices of AMZN, F, and Bitcoin were \$780, \$9.604, and \$739.248 respectively. Now, we need to divide \$1,000 by each of these numbers to see how many shares we will have:

AMZN = 1000/780 = 1.282 shares
F = 1000/9.604 = 104.123 shares
Bitcoin = 1000/739.248 = 1.353 shares
It’s a relatively recent phenomenon that retail brokers offer fractional shares, but this tends to be the case nowadays for most commonly used brokers. For this exercise, we will assume we can have fractional shares.

Now, to determine how much money we would have today, we look at the most recent date in our data set (11/18/2021), get the prices of each asset, and multiply our number of shares by this number. We can find this by looking at the bottom of our data set in Figure 4 using the `tail()` method:
```python
np.round(df.tail(3), 3)
```
From here, we can get our final asset values:

- AMZN = 1.282 * 3696.06 = \\$4,738.35
- F = 104.123 * 19.56 = \\$2,036.65
- Bitcoin = 1.353 * 56942.14 = \\$77,042.72

Wow. All three of these assets have at least doubled the initial \$1,000 that was invested. Bitcoin is clearly the standout asset in this case, turning \$1,000 into a whopping \$77,042.72. While Bitcoin clearly outperformed the other two assets over the last five years, past performance does not necessarily indicate future performance. 

These assets were relatively easy to compare here since we started with \\$1,000 in each. If we had started with different values, we would need to calculate the returns for an apples-to-apples comparison. In a future lesson, we will go over simple and log returns, but for the purpose of simplicity, we will use simple returns:

Simple Returns Formula

$R_{simple} = \frac{p_1 - p_0}{p_0}$

where

$p_1 = \textrm{final value}$
$p_0 = \textrm{initial value}$
This will be easy in our case since \$1,000 is the initial value in all three situations:

- AMZN = (4738.35 - 1000)/1000 = 3.7384 = 373.84%
- F = (2036.65 - 1000)/1000 = 1.03665 = 103.67%
- Bitcoin = (77042.72 - 1000)/1000 = 76.04272 = 7,604.27%

Bitcoin’s return here is off the charts compared to the other two assets. Bitcoin is a relatively new—some would even say riskier—asset than the other two. Higher risk equals higher potential for rewards, and thus far, investing in Bitcoin has paid off handsomely. 

###### 2.1.3. Comparing Equities and Bitcoin to Bonds
Let's introduce one more asset class here—bonds. As you recall from the Financial Markets class, bonds not only have the return of principal but they also return a coupon, usually annually or quarterly. To simplify things, we will use an exchange traded fund (ETF), which tracks bonds. The ETF is the Vanguard Long-Term Bond Index Fund ETF or BLV for short. This fund intends to track the performance of the Bloomberg Barclays U.S. Long Government/Credit Float Adjusted Index. This index includes investment grade corporate, U.S. government, and international dollar-denominated bonds that have maturities greater than 10 years. At least 80% of the fund's total assets will be invested in bonds held in the index mentioned above (Vanguard).

The following code snippet will pull BLV data and join it with our current DataFrame, df
```python
df = df.join(web.DataReader(["BLV"], "yahoo", start, end)["Adj Close"])

df.tail()
```

- 2.1.3.1 Calculate log returns, remove unused columns, and drop nulls

We need to remove the nulls for the weekend dates
```python
df = df.dropna()
df["Amazon"] = np.log(df.AMZN) - np.log(df.AMZN.shift(1))
df["Ford"] = np.log(df.F) - np.log(df.F.shift(1))
df["Bitcoin"] = np.log(df["BTC-USD"]) - np.log(df["BTC-USD"].shift(1))
df = df.iloc[1:, 3:]

df.head()
```

- 2.1.3.2 Show summary stats for the returns
```python
df.describe()
```
 
2.1.3.3 Converting Daily Returns to Annual

```python
(df.describe()[["Bitcoin", "Ford"]])

((df[["Bitcoin", "Ford"]].mean() + 1).pow(365) - 1) * 100
```

We can run the same analysis on BLV as we did on the above stocks to get the total simple return over a five-year period using a slightly different method. This time, we’ll calculate the simple return and then just multiply that number by 1+ `returnRate`. 

BLV 5 year return = (103.02-73.463)/103.02 = 0.2869 = 28.69%

If we started with \$1,000, after five years, we would’ve ended up with (1+0.2869) * 1000 = \$1,286.90.

While this is still a positive return, it’s a much lower return than what we would’ve gotten with Ford, Amazon, or Bitcoin. This is to be expected for the most part as bonds return a quarterly/annual coupon along with returning the principal. For this reason, bonds (especially government bonds) are considered safer assets than stocks or cryptocurrencies. One major thing to consider is if a company goes bankrupt, you may not get your principal back in a bond. That being said, the same goes for stocks. Bondholders also have less credit risk than stockholders: If you own a bond in Ford and your friend owns Ford stock, but Ford declares bankruptcy tomorrow, the bondholder will be paid off first in the bankruptcy proceedings and the equity owner will only get what’s left over, making bonds a safer investment. 

The downside to this is that it's hard to achieve the level of total returns that a stock or cryptocurrency can achieve with a bond. There is a risk-reward tradeoff. Think back to the reading in this lesson for a moment. What we just discussed here is mentioned in the reading comparing a high-variance investment to a low-variance investment. What you choose is entirely up to your risk preferences. Always take into consideration the risk-reward tradeoff.

Most investors hold a mix of stocks/cryptocurrencies and bonds. A rule of thumb that’s commonly used to determine this mix is to subtract your age from 100; the resulting number is the percentage of assets that should be in risky assets, like stocks. In other words, a 26-year-old should be putting (100-26) = 74% of their assets in stocks and 26% in bonds. The reason for this is that, while you’re young, you have more time to wait out the potential down cycles in a market so you can be riskier with your money.

In this next video, we'll go over some Python DataFrame tricks to transform data more easily along with showing how to calculate returns and visualize the data for easy comparison.

```
VimeoVideo("706651387", h="a0b53c000e", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1MlwM_Ox9NvKBpM1nfmGdJa_Gh34XDRhE/view?usp=sharing)

###### 2.1.4. Conclusion

This lesson was a starting point for pulling in and analyzing price data in Python. In the next lesson, we will go into some more specifics on different types of stocks and compare them using similar methods.

**References**

- “BLV Long-Term Bond ETF.” *Vanguard*, https://institutional.vanguard.com/investments/product-details/fund/0927


##### 2.2. Identifying and applying risk metrics associated with financial markets


|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Stock indices, Log return calculations  |
|**Keywords** | Variance, Volatility, Standard Deviation, Moving Averages |

---
###### Required reading 
1.  "Measures of Spread: Range, Variance & Standard Deviation." _Khan Academy_. [https://www.khanacademy.org/math/statistics-probability/summarizing-quantitative-data/variance-standard-deviation-population/v/range-variance-and-standard-deviation-as-measures-of-dispersion](https://www.khanacademy.org/math/statistics-probability/summarizing-quantitative-data/variance-standard-deviation-population/v/range-variance-and-standard-deviation-as-measures-of-dispersion)
    -   **Required pages:** Whole video
    -   **Estimated reading time:** 12 minutes

*In the previous lesson, we examined the returns of different asset classes and performed some basic price analysis. In this lesson, we will expand on what we learned in the previous lesson with a few custom volatility metrics, along with how to program them in Python. We'll also focus on the risk, or volatility of returns, of financial assets.*

```python
import numpy as np
import pandas as pd
import pandas_datareader.data as web

pd.options.display.float_format = "{:,.3f}".format
import datetime
from datetime import date

import seaborn as sns
from IPython.display import VimeoVideo
from matplotlib import pyplot as plt
```

###### 2.2.1. Future Value of an Investment
The S&P 500 consists of 500 large-cap companies. The index calculates weights according to market capitalization. This weighting is different from that in the Dow Jones Industrial Average, which is price weighted. The companies that make up this index are chosen by a committee, but companies must fit specific criteria before being included (Standard & Poor's):

* Market capitalization must be greater than or equal to \\$13.1 billion.
* Annual dollar value traded to float-adjusted market capitalization is greater than 1.0.
* The minimum monthly trading volume is 250,000 shares in each of the six months leading up to the evaluation date.
* The company must be publicly listed on either the New York Stock Exchange (NYSE), including NYSE Arca or NYSE American, or NASDAQ (NASDAQ Global Select Market, NASDAQ Select Market or the NASDAQ Capital Market).
* The company should be from the U.S.
* Securities that are ineligible for inclusion in the index are limited partnerships, master limited partnerships and their investment trust units, OTC Bulletin Board issues, closed-end funds, exchange-traded funds, exchange-traded notes, royalty trusts, tracking stocks, preferred stock, unit trusts, equity warrants, convertible bonds, investment trusts, American depositary receipts, and American depositary shares.
* Since 2017, companies with dual share classes, like Standard & Poor's, are not added to the index.

This will be used as our proxy for large-cap stocks.

The Russell 2000 is an index that contains 2,000 small-cap companies and is frequently used as a benchmark by small-cap mutual funds for comparison purposes. The Russell 2000 is constructed to provide a barometer for small-cap stocks. It's reconstituted annually to ensure companies from the previous year don't get too large and distort the characteristics of small-caps (Maginn 118).

The Russell 2000 Index will be used as our proxy for small-cap companies.

One way to compare two investment opportunities is to determine the future value of an investment. There are always risks and many assumptions that need to be made when determining future value, especially for a risky investment like a stock. We will begin by using the average daily rate of return of each index to determine expected return. This is a simple way of thinking because it’s impossible to say the next 10 years will be the same as the past 10 years, but it is a starting point when comparing investments. We will delve further into more advanced comparison metrics as the course goes on. 

**The formula for compound interest is:**

$FV = PV (1+i)^n$, where

$FV = \textrm{Future value}$
$PV = \textrm{Present value}$
$i = \textrm{Periodic interest rate}$
$n = \textrm{Number of periods}$


**2.2.1.1 Pull 10 years daily price data for S&P 500 and Russell 2000**

We're going to dig deeper into specific equities asset classes and compare them as potential investments. We will start by comparing large cap to small cap stocks using S&P 500 and the Russell 2000 Index. 

Throughout this lesson we will build towards a function here which takes a date range and compares two series of returns.


```python
# start = datetime.date.today()-datetime.timedelta(365*10)
# end = datetime.date.today()
start = datetime.date(2011, 11, 25)
end = datetime.date(2021, 11, 22)

prices = web.DataReader(["^GSPC", "^RUT"], "yahoo", start, end)["Adj Close"]

# Rename column to make names more intuitive
prices = prices.rename(columns={"^GSPC": "SP500", "^RUT": "Russell2000"})
```

```python
prices.describe()
```

```python
prices.head()
```

Once again, we can see these datasets have different starting points so the only way we can do a fair comparison is by comparing returns

 **2.2.1.2 Calculate log returns, remove unused columns, and drop nulls**

No nulls here for the weekend dates. Since S&P 500 and the Russell 2000 Index are both stock indices, the weekends are automatically removed. 

```python
df = np.log(prices) - np.log(prices.shift(1))
df = df.iloc[1:, 0:]
```

```python
df.head()
```

**2.2.1.3 Calculating Future Value of each Index**

Once we get the daily returns in a DataFrame, df, we can use the mean() method in order to determine daily average returns. We calculate this over the last 10 years to determine our expected daily rate of return for our future value calculation. From here, we will assume a \$1,000 investment for present value and plug these numbers into the interest rate parameter. If we assume a 10-year investment time frame and 252 trading days a year, the periods will be 10*252 = 2520.

```python
df.mean() * 100
```

Assuming mean of daily returns is the daily expected return going forward

```python
(1 + df.mean()) ** (252 * 10) * 1000
```

With our future value calculations, we’re predicting a \$1,000 investment in the S&P 500 today would yield a \$4,053.57 future value and for the Russell 2000 a \$3,509.06 future value. 

While future value is important when comparing investments, we also need to be concerned about how volatile these investment opportunities are. In the next section, we will discuss three different volatility metrics along with how to program them in Python.

###### 2.2.2. Investment Opportunities: Volatility
2.2.2.1 Price Volatility: High-Low
We will be using the prices DataFrame again to show some simple ways to compare the volatility of certain investments. The first method is comparing the high and low of the index. For this, we use the max() and min() methods to get the high and low over the duration of the DataFrame by column. From here, we can subtract these from each other to get an idea of the potential volatility of each investment.

```
prices.max()
```

```
prices.min()
```

```
prices.max() - prices.min()
```

While some may find this useful, we definitely need to improve upon this metric to make it more useful when comparing different investments. How do you think we can do this? Let's try out two ideas.

The first is changing the time frame slightly. Above, we’re looking at the last 10 years of data. Perhaps it will be more useful to analyze more recent data. For this, we will look at the same metric over the last year:

```python
currYear = prices.loc[
    date.today() - datetime.timedelta(365) : date.today()  # noqa E203
]
currYear.max() - currYear.min()
```

Even when comparing data over the last 365 days, it seems hard to do a comparison of these two datasets since they have different starting points. One final adjustment to this volatility metric could be to standardize it by dividing by the current price of the index:

```python
(currYear.max() - currYear.min()) / prices.iloc[-1]
```

Now that we have the data standardized by the current price, this high/low metric actually shows the Russell 2000 to be the more volatile investment. This is pretty much in line with what you would expect since the S&P 500 is mostly big established companies while the Russell 2000 is filled with small caps. Accordingly, you would expect business to be more turbulent and the stock prices to be more volatile.



**2.2.2.2 Moving Averages** 

*2.2.2.2.1 50-Day Moving Average*
We are going to create a volatility metric that compares each day's price to the moving average. The 50- and 200-day averages are commonly used when comparing investments. For our metric, we will use the 50-day average. Here is an example of how we can chart the S&P 500 along with its 50-day moving average:

```python
prices["SP500 50 day_rolling_avg"] = prices.SP500.rolling(50).mean()

# set figure size
plt.figure(figsize=(12, 5))

# plot a simple time series plot
# using seaborn.lineplot()
sns.lineplot(x="Date", y="SP500", data=prices, label="Daily S&P 500 Prices")


# plot using rolling average
sns.lineplot(x="Date", y="SP500 50 day_rolling_avg", data=prices, label="Rollingavg")
```

*2.2.2.2.2 50-Day Rolling Distance* 
We can create a volatility metric here using this moving average. Let’s imagine we were taking the distance between the moving average line and each data point from the S&P 500 chart. We can use this as a proxy for volatility. We also would want to treat the negative differences the same as the positive differences; otherwise, they may cancel each other out. As such, we will use the absolute value of each point. We will divide these differences by the prices in order to standardize these values, and finally, we'll take the average of those values. This can be programmed in Python with this simple line:

```python
((abs(prices - prices.rolling(50).mean())) / prices).mean()
```

Even though this is a different metric than the high/low metric we previously calculated, it shows the same result: The Russell 2000 has been more volatile than the S&P 500 over the last 10 years.

In the first video of this lesson, we will recap the risk metrics we've written thus far and show how we can use them in Python.

```python
VimeoVideo("706651510", h="e6511ea8b5", width=600)
```

 [Access video transcript here](https://drive.google.com/file/d/1a48fxAGWt2gibIXJ7VJD_u2ASuBWIEeC/view?usp=sharing)

**2.2.2.3 Price Volatility: Standard Deviations**
Standard deviation is potentially the most popular volatility metric used when looking at an investment opportunity. It’s as simple as calling the std() method on a DataFrame.

```python
prices.std()
```

As mentioned before, calling this on the prices is not as intuitive as calling this on the returns since prices start at different points. For a better comparison, we will call this std() method on the daily returns of the last 10 years:

```python
df.std()
```

All three of our volatility metrics, albeit slightly similar, show us that the Russell 2000 Index has been more volatile over the last 10 years than the S&P 500.



**2.2.2.4 Writing a Comparison Function in Python**
To tie it all together, we're going to take the three volatility metrics we've used up to this point, along with average daily return, and write a function, which takes:

* `startTime` - `dateTime` format
* `endTime` - `dateTime` format
* `tickers` - a dictionary of values where the key is the yahoo ticker and the value is the display name i.e. {"^GSPC": "SP500", "^RUT": "Russell2000"}

By writing a function like this, it allows our research to be reproducible and applicable to many different parameters. In our case, it will be a date range and dictionary of tickers. If you were writing a serious application, you would need to have lots of error handling in this function, such as guaranteeing that parameters passed in are of the correct type. In our case, we will assume the data types of parameters are correct and that the date range is longer than 365 days. 

```python
def investCompare(startTime, endTime, tickers):
    # pull price data from yahoo -- (list(tickers.keys())) = ['^GSPC','^RUT']
    prices = web.DataReader(list(tickers.keys()), "yahoo", startTime, endTime)[
        "Adj Close"
    ]
    prices = prices.rename(columns=tickers)
    returns = np.log(prices) - np.log(prices.shift(1))
    returns = returns.iloc[1:, 0:]

    # pull data into separate DataFrame, 52weeks to just look at the last 365 days of data for calculating our high/low metric
    currYear = prices.loc[
        date.today() - datetime.timedelta(365) : date.today()  # noqa E203
    ]
    highLow = (currYear.max() - currYear.min()) / prices.iloc[-1]
    highLow = pd.DataFrame(highLow, columns=["HighMinusLow"])

    # Moving average volatility
    MA = pd.DataFrame(
        ((abs(prices - prices.rolling(50).mean())) / prices).mean(),
        columns=["MovingAverageVolatility"],
    )

    investments = pd.merge(highLow, MA, on="Symbols")
    investments = pd.merge(
        investments,
        pd.DataFrame(returns.std(), columns=["StandardDeviation"]),
        on="Symbols",
    )
    investments = pd.merge(
        investments,
        pd.DataFrame(100 * returns.mean(), columns=["Daily Return Percentage"]),
        on="Symbols",
    )

    return investments.round(3)
```

**2.2.2.5 Trying It Out**
We will start by calling our function with the two indices we've been examining thus far: the S&P 500 alongside the Russell 2000 Index. As we've seen, the three volatility metrics showed the Russell 2000 to be the more volatile investment. The average daily return is also higher for the S&P 500. Therefore, over the last 10 years not only has the S&P 500 returned better than the Russell 2000, but it was also less volatile. Keep in mind that these different volatility metrics all calculate in some way how turbulently the stock has behaved in the past. This exercise was intended to demonstrate different ways of calculating volatility and how you can be a bit creative with it. This doesn't mean that volatility is constant or easily predictable, behaving the same way going forward; this exercise only reflects the past.

```python
investCompare(
    datetime.date(2020, 1, 1),
    datetime.date.today(),
    {"^GSPC": "SP500", "^RUT": "Russell2000"},
)
```

This function gives us one clean space to compare investments in one line.

We also want to show that we made the function flexible in order to add symbols in the future. In the example below, we added Apple to the DataFrame in order to compare it to the other two indices. 

```python
investCompare(
    datetime.date(2020, 1, 1),
    datetime.date.today(),
    {"^GSPC": "SP500", "^RUT": "Russell2000", "AAPL": "Apple"},
)
```

These metrics show Apple to be a better investment in terms of daily return, but they also show that Apple is significantly more volatile than the two indices. This is expected, since the indices represent vast baskets of stock. With many stocks moving in different directions, you'd expect the indices to be less volatile than an individual stock, even a blue-chip stock like Apple.

In the next video, we will combine all of the risk metrics we've created so far and wrap them up tidily into a function that can be reused going forward.

```python
VimeoVideo("706651724", h="836ae485f0", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1na-nRzhNunGctPmXHUKAwAuASjxF3d3x/view?usp=sharing)

**2.2.2.6 Comparing Growth vs. Value stocks**
We can continue using the function we just wrote to examine and compare different categories of investments, starting here with growth vs. value stocks. As a proxy for growth stocks, we will use the Vanguard Growth ETF (VUG). VUG is one of the biggest growth ETFs with around \\$87 billion in assets under management. For value stocks, we will use the Vanguard Value ETF (VTV). VTV is the most prominent value ETF with \\$88 billion in assets under management. As you may imagine by now, Vanguard is a popular purveyor of ETFs and has some of the lowest expense ratios in the industry.

```python
investCompare(
    datetime.date(2020, 1, 1), datetime.date.today(), {"VUG": "Growth", "VTV": "Value"}
)
```

Running `investCompare` over the last two years for these ETFs shows that growth stocks have clearly outperformed value stocks in terms of returns—but not without increased volatility. We need to keep in mind that time frames have a large influence on our results here. Let's take a look at the data since 2010:

```python
investCompare(
    datetime.date(2010, 1, 1), datetime.date.today(), {"VUG": "Growth", "VTV": "Value"}
)
```

We do see quite similar results here, with the daily returns of the growth ETF coming down to earth a bit. Growth stocks tend to be more volatile in general, and the proof can be seen empirically here.

**2.2.2.7 Comparing Domestic vs. Foreign Stocks**
We will use the S&P 500 once again for U.S. stocks while finding an ETF for the foreign stocks. There are tons of options to choose from in this space. 

The first question you need to ask yourself is where do you want to invest? It could be emerging markets, Europe, China, etc. To make things simple, we will use one example that is specific to Europe, ETF: SPDR Portfolio Europe ETF (SPEU), and one example that is specific to China, ETF: SPDR S&P China ETF (GXC).

```python
investCompare(
    datetime.date(2020, 1, 1),
    datetime.date.today(),
    {"^GSPC": "SP500", "SPEU": "Europe ETF", "GXC": "China ETF"},
)
```

Since the start of 2020, U.S. stocks have had the best daily returns by a solid margin with lower volatility than Europe and China. Hindsight is 20/20, but this makes a clear case for U.S. equities being the best investment over the last two years. If we zoom out and look at the data since 2010, we'll see the following:

```python
investCompare(
    datetime.date(2010, 1, 1),
    datetime.date.today(),
    {"^GSPC": "SP500", "SPEU": "Europe ETF", "GXC": "China ETF"},
)
```

The above makes an even better case for U.S. equities over the last 10 years. That being said, this is no guarantee that the next 10 years will look the same. Past performance is no guarantee of future results.

###### 3. Conclusion

In this lesson, we compared returns of different investment opportunities, and we used Python to illustrate different ways of calculating the volatility of investments. Keep these lessons in mind as we delve deeper into the connection between volatility and return in the next lesson. Up next, we'll expand this analysis by also taking into account the returns of different investments.

**References**

- Standard & Poor's. *S&P U.S. Indices Methodology*, Standard & Poor's, Nov. 2021, https://www.spglobal.com/spdji/en/documents/methodologies/methodology-sp-us-indices.pdf

- Maginn, John L. *Managing Investment Portfolios Workbook: A Dynamic Process*. John Wiley & Sons, Inc., 2007.


##### 2.3. Comparing and contrasting returns of different asset classes

|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Basic Python  |
|**Keywords** | Log and simple returns, Variance, Standard Deviation, Correlation, Covariance, Sharpe Ratio, Semivariance |

---
###### Required reading 
1.  Bionic Turtle. "Three Approaches to Value at Risk (VaR) and Volatility (FRM T4-1)." _YouTube_, 14 Nov. 2018, [https://www.youtube.com/watch?v=qzOWm7PurHE](https://www.youtube.com/watch?v=qzOWm7PurHE).
    -   **Required pages:** Whole video
    -   **Estimated reading time:** 18 minutes

*This lesson will build upon the previous two lessons' focus on price to finally expand the conversation to returns. We go much more in depth into how to calculate returns and how to compare two investments using various risk measures.*

```python
import datetime

import numpy as np
import pandas_datareader.data as web
import seaborn as sns
from IPython.display import VimeoVideo
from matplotlib import pyplot as plt
```

###### 2.3.1. Obtaining and Transforming Financial Data 
Since this course has a more practical focus, we will start by pulling price data into Python and showing how to simply clean and transform the data so it's in a format that is easier to work with.  

We use the `pandas_datareader` library in order to pull financial data. We will pull data from the FRED (Federal Reserve Economic Data) Database. Keep in mind, we can use the `pandas_datareader` package to pull from many different sources, like OECD, Yahoo Finance, etc.

```python
start = datetime.date.today() - datetime.timedelta(days=5 * 365)
end = datetime.date.today()
df = web.DataReader(["sp500", "NASDAQCOM", "CBBTCUSD"], "fred", start, end)
```

We've retrieved the data from the two most popular U.S. indices, the NASDAQ and S&P 500, along with the daily Bitcoin prices from the last five years. Some basic data cleaning is done here by removing nulls (weekend data). Now, we have a DataFrame containing the dates and prices of four different assets. We need to compare returns instead of prices here for a couple of reasons: 

1. Return is a scale-free summary of an investment opportunity. 
2. Returns have statistical properties that are easier to work with. (This will be discussed more in a later lesson.)  

The next question is whether to use simple returns or log returns. Using the following variables, we can define the different types of return:

$p_1 = \textrm{final value}$
$p_0 = \textrm{initial value}$

**Simple Returns Formula**

$R_{simple} = \frac{p_1 - p_0}{p_0}$

For example, if we were calculating yearly returns and on day 1, the portfolio was worth \\$100 and at the end of the year it was worth \\$125, the simple return would be

(125-100)/100 = 0.25 = 25% gain



**Log Returns Formula**

$R_{log} = ln(p_1/p_0)$

For example, if our portfolio was worth \\$100 at the start of the year and \\$80 by the end of the year, the log return would be:

ln(80/100) = -0.223 = -22.3% loss

Log returns are used in this case because it is a common assumption in many financial models that returns are normally distributed, and log returns have good mathematical properties, which make them easier to work with considering this assumption.



###### 2.3.1.2 Calculate log returns, remove unused columns, and drop nulls

We need to remove the nulls for the weekend dates

```python
df = df.dropna()
df["SP500"] = np.log(df.sp500) - np.log(df.sp500.shift(1))
df["NASDAQ"] = np.log(df.NASDAQCOM) - np.log(df.NASDAQCOM.shift(1))
df["Bitcoin"] = np.log(df.CBBTCUSD) - np.log(df.CBBTCUSD.shift(1))
df = df.iloc[1:, 3:]
```

```python
df.head()
```

###### 2.3.1.3 Show summary stats for the index returns

```python
df.describe()
```

```python
df["2019-05-01":"2019-05-31"].plot();
```

###### 2.3.2. Variance and Standard Deviation 
Investors have to keep volatility in mind as well when choosing an investment. For example, a pension fund may need to be extra careful with its money and will want to ensure they aren’t getting into any extremely volatile investments. There are also hedge funds, which short stocks and even trade volatility with options. As you can see, whether you’re risk-seeking or risk-averse, the volatility (risk) of an investment is something you should care about.   

A simple measure of volatility is the variance. Variance is used to see how far away each data point in a set is away from the mean. Variance is calculated with the following steps:

Take the difference between each data point and the mean
Square each difference so that they're all positive values
Sum up the squared results
Divide this by the count of data points minus one
$\sigma^2 = \frac{\sum(x_i - \overline{x}^2)}{n-1}$

where

$\sigma^2 = \textrm{Sample Variance}$

$x_i = \textrm{value of one observation}$

$\overline{x} = \textrm{mean of all observations}$

$n = \textrm{number of observations}$

The larger the variance, the further spread out it is from the mean. Variance treats all deviations from the mean the same way, regardless of whether they are less than or greater than the mean. A variance of zero would indicate that each data point is the same.  

Standard deviation is easy to calculate once you have the variance. All you have to do is take the square root of the variance: 

$\sigma = \sqrt{\sigma^2}$	

where 

$\sigma = \textrm{standard deviation}$

Standard deviation is another commonly used statistical measure to quantify market volatility. You would expect newer growth stocks to have higher standard deviations and more established blue-chip stocks to have lower standard deviations of returns. We will illustrate this by comparing daily returns from the last five years of the S&P 500 and NASDAQ, as well as Bitcoin prices. While Bitcoin isn't necessarily a growth stock, it's still very new compared to the S&P 500 and NASDAQ, so you would expect to see bigger swings in the price when compared to those two stock indices.

This is illustrated below by taking the standard deviations of returns over the last five years. These results are as expected: Both the S&P 500 and NASDAQ have very similar daily standard deviations. Bitcoin, on the other hand, has almost five times the standard deviation of the two stock indices.

```python
df.std()
```

We can also visualize this by graphing returns in Python using the plot method in pandas in conjunction with standardized y-axis limits so that we can ensure we're comparing returns on the same scale:

```python
ax1 = df.plot(figsize=(15, 3), y="SP500", title="Figure 1: S&P 500 Daily Returns")
ax2 = df.plot(figsize=(15, 3), y="Bitcoin", title="Figure 2: Bitcoin Daily Returns")
```

```python
ax1.set_ylim(-0.5, 0.4)
ax2.set_ylim(-0.5, 0.4);
```

The above charts show clearly how much more volatile Bitcoin is compared to the S&P 500 and hence why the variance/standard deviation of returns is much higher.

Standard deviation is preferred over variance in most cases because variance is a squared result of the units of return. By taking the square root of this and thus obtaining standard deviation, the result is in the same unit as the underlying data, which in this case is returns. This makes it much easier to understand, intuitively.  

Keep in mind, a lower standard deviation is not necessarily preferable when considering investments. It all depends on the investor’s risk preferences. A higher risk means a higher potential for rewards. Understanding the investor’s perspective is key to determining what levels of risk an investor is comfortable with.  

In the first video of this lesson, we will compare different asset classes using standard deviation of returns.

```python
VimeoVideo("706652115", h="fc2f09065c", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1veRqEUCAxGXzHz423f9r2qQNxC_JK0ol/view?usp=sharing)

###### 2.3.3. Covariance and Correlation 
We are able to compare the performance of stocks that have different price levels by using returns and standard deviation. How can we look at the joint performance of two stocks? For this, we turn to covariance and correlation. We will start with covariance: 

$\frac{\sum(x_{i}-\overline{x})(y_{i}-\overline{y})}{N-1}$

where

$x_i = \textrm{value of one observation of x}$

$y_i = \textrm{value of one observation of y}$

$\overline{x} = \textrm{mean of x}$

$\overline{y} = \textrm{mean of y}$

$N = \textrm{number of observations}$


**Covariance** provides us some insight into how two variables move together. A positive covariance between stock returns would indicate that when one stock goes up, so does the other and vice versa. A negative covariance would mean that the two stocks move inversely, i.e., when one goes up, the other goes down.  

Looking at the covariance matrix below for our three assets, we can see that these assets have a positive relationship with each other. It's hard to understand much more than that with these numbers, given that the units are not standardized. 

###### 2.3.3.1 Using a Covariance Matrix
While covariance is useful for determining the direction of two variables jointly, we can turn to correlation for a more standardized version of this. For now, when discussing correlation, we will use the Pearson’s correlation coefficient. The other types of correlation will be discussed in a future lesson

```python
df.cov()
```

###### 2.3.3.2 Using the Pearson Correlation Coefficient Formula
The Pearson correlation coefficient is a measure of the strength of a linear relationship between two variables. The formula is as follows: 

$\rho_{X,Y} = \frac{cov(X,Y)}{\sigma_{X} \sigma_{Y}}$

where

$cov = \textrm{Covariance}$

$\sigma_{X} = \textrm{Standard Deviation of X}$

$\sigma_{Y} = \textrm{Standard Deviation of Y}$

Correlation is used in statistics to quantify the degree to which two variables move in a linear relation to each other. Correlation can range from –1 to 1 inclusive. A correlation of 1 means perfect correlation; the variables move exactly in tandem with one another. Perfect tandem for positive correlation means that if we know variable X increases, then variable Y also increases.  A correlation of –1 indicates perfect inverse correlation. This is also perfect tandem, but in the opposite direction.  Here, if we know variable X increases, then variable Y decreases. A correlation of 0 indicates there is no distinguishable relationship between two variables; therefore, it would be impossible to make predictions of one variable given the other. In this case, if we know variable X increases, then variable Y is equally likely to increase or decrease.

A benefit of correlation over covariance is that correlation is capped from –1 to 1 while covariance can be from –inf to inf. This makes covariance a harder statistic to understand intuitively. Correlation is also proportional, which will be shown in the video below.  

Keep in mind that a lot of models and financial concepts assume a constant correlation, but this is rarely the case. Correlation is changing over time and will likely even change if you adjust the time range from which you’re measuring correlation. 

When comparing the correlations of the assets we've been using so far, you can see it paints a clearer picture than the covariance did.

```python
round(df.corr(), 3)
```

All of the variables have a positive relationship, which we saw with the covariance matrix previously. Here, we can also see the strength of the relationships: The S&P 500 is strongly correlated with NASDAQ since we've obtained a 0.944 Pearson's correlation coefficient. The relationship between NASDAQ and Bitcoin is still positive but much weaker with a 0.192 Pearson's correlation coefficient. 

When we chart the returns between these variables, we can see evidence of the correlations above, visually:

```python
chart = sns.regplot(x="SP500", y="NASDAQ", data=df).set(
    title="Figure 3: Daily S&P 500 Returns vs NASDAQ Returns"
)

plt.axvline(0, 0, 1, dash_capstyle="butt", linestyle="--", color="grey")

plt.plot([min(df.SP500), max(df.SP500)], [0, 0], linestyle="--", color="grey")
```

This relationship shows nearly perfect correlation. 

```python
sns.regplot(x="SP500", y="Bitcoin", data=df).set(
    title="Figure 4: Daily S&P 500 Returns vs Bitcoin Returns"
)
```

```python
plt.axvline(0, 0, 1, dash_capstyle="butt", linestyle="--", color="grey")
```

```python
plt.plot([min(df.SP500), max(df.SP500)], [0, 0], linestyle="--", color="grey")
```

The relationship here is much more scattered even though the relationship is still slightly positive. These were charted using the seaborn `regplot` method, which also shows confidence intervals around the regression line, as seen above.  

In the next video, we will go over how to leverage Python libraries in order to easily calculate correlation and covariance given an array of returns.

```python
VimeoVideo("706652174", h="765b5c9c8a", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1_vKay5S09R01iw9-wgvDCE5KuwetOxUd/view?usp=sharing)

Are there any statistics we can use to quantify not just return but also risk? For this, we turn to the Sharpe ratio.

###### 2.3.3.3 The Sharpe Ratio 
The Sharpe ratio allows an investor to understand the relationship between the return of an investment in relation to its volatility. The formula is as follows: 

$\textrm{Sharpe Ratio} = \tfrac{R_p - R_f}{\sigma_p}$

where

$R_p = \textrm{Return of the portfolio}$

$R_f = \textrm{Risk-free Rate}$

$\sigma_p = \textrm{Standard Deviation of the Portfolio}$

In many cases with interest rates so low, investors will assume the risk-free rate to be 0, making the ratio: 

$\textrm{Sharpe Ratio} = \frac{R_p}{\sigma_p}$

Notice anything about the denominator? Yes, that’s right—we use the standard deviation here to represent risk.  

This measure is used as a way of scaling the return of an investment depending on how much risk is taken. In other words, the higher the standard deviation, the more the risk-weighted return is reduced. Let’s use the same example as above with S&P 500 and Bitcoin daily returns over the last five years.

Average daily return of S&P 500: **0.000617 = 6.17 bp**

Average daily return of Bitcoin: **0.003626 = 36.26 bp**

Using standard deviations from above and assuming the risk-free rate = 0, we can calculate the Sharpe ratio of these investments using: 

S&P 500: 0.000617/0.012115 = **0.0509** 

Bitcoin: 0.003626/0.050088 = **0.0724** 

According to the Sharpe ratio, over the last five years, Bitcoin has had a better risk-adjusted return. This is interesting because even though Bitcoin had a higher standard deviation of returns, the higher return was enough for the Sharpe ratio to deem it the better investment from a risk/return perspective.  

One major flaw with the Sharpe ratio is that it uses the standard deviation of returns in the denominator, which assumes that returns are normally distributed. This may not always—and is actually rarely—the case. This will be explored further in a future lesson.  

```python
Sharpe_Ratio_SP500 = df["SP500"].mean() / df["SP500"].std()
Sharpe_Ratio_SP500
```

```python
Sharpe_Ratio_Bitcoin = df["Bitcoin"].mean() / df["Bitcoin"].std()
Sharpe_Ratio_Bitcoin
```

How can we refine the Sharpe ratio to give an even better measure of risk-adjusted returns? Semivariance is the answer.

###### 2.3.4. Semivariance 
Semivariance, a.k.a. downside risk, is a more refined version of a standard deviation. Standard deviation looks at both the upside and downside risk of an investment. Most investors, unless you’re trading short, care much more about the downside risk than the upside risk. In other words, if you bought a stock and are looking at the Sharpe ratio, you wouldn’t want this number to be penalized for how far it moves to the upside. Most of the time, an investor will be much more concerned with the downside risk of a stock.  

$\textrm{Semivariance} = \tfrac{1}{n} * \sum_{r_i < \overline{r}}^{n} (r_i - \overline{r})^2$

where

$r_i = \textrm{value of one observation}$

$\overline{r} = \textrm{mean of all observations}$

$n = \textrm{number of observations}$

Semivariance can be thought of as the standard deviation when only looking at returns below 0. This can be used to estimate the average loss a portfolio could incur, assuming normal distributions of returns.  

Conversely, if we are short a security, we could still use semivariance, but this time, it would focus on the returns that are positive. If we are short, drops in the price create upside, so we would not want to penalize this volatility in our Sharpe ratio. However, if there are large deviations in the upward direction, then this will contribute to semivariance.

In short, semivariance uses either the positive or negative returns.


```python
df[df["SP500"] < df["SP500"].mean()]["SP500"].std()
```

```python
df[df["Bitcoin"] < df["Bitcoin"].mean()]["Bitcoin"].std()
```

###### 2.3.5. Conclusion

This lesson covered surface-level returns and volatility metrics to compare stocks. We also discussed downside risk measures and ways to jointly compare different financial assets. In the next lesson, we will delve into more advanced metrics modeled with different statistical distributions.


##### 2.4. Using statistical distributions to model stock returns
###### Required readings
-  Downey, Allen B. _Think Stats: Exploratory Data Analysis in Python_. Version 2.2, Green Tea Press, Needham, MA. [https://greenteapress.com/thinkstats2/thinkstats2.pdf](https://greenteapress.com/thinkstats2/thinkstats2.pdf)
    -   **Required pages:** Sections 5.2-5.4 (pp. 60–66)
    -   **Estimated reading time:** 15 minutes

|                     |                                                                          |     |
|:------------------- |:------------------------------------------------------------------------ | --- |
| **Reading Time**    | 30 minutes                                                               |     | 
| **Prior Knowledge** | Statistics, Cumulative distribution functions                            |     |
| **Keywords**        | Normal Distribution, Student T distribution, Normality Testing, P-values |     |

---


*We looked at various ways to measure risk and returns in the last lesson. Here, we take that a step further by using distributions to correctly model risk and returns.*


```python
import datetime

import numpy as np
import pandas as pd
import pandas_datareader.data as web
import seaborn as sns
from matplotlib import pyplot as plt
from scipy import stats
```

###### 2.4.1. How Are Stock Returns Distributed?
Many models and theories surrounding stocks assume a normal distribution. We will try to determine that here with a data-based analysis. Properties of a Gaussian distribution are as follows:

* Mean, median, and mode are all the same
* The data is symmetrical, meaning there are equal counts of observations on both sides of the mean.
* In normally distributed data, 68.25% of all cases fall within +/- one standard deviation from the mean, 95% of all cases fall within +/- two standard deviations from the mean, and 99.7% of all cases fall within +/- three standard deviations from the mean.

Let's start by pulling 20 years of daily price data for the S&P 500. We'll use similar methods we've used in the last few lessons to pull this data and will calculate the log returns here.

One quick way of doing this is to determine how many data points we have on either side of the mean here. We have a bit more than 5,000 data points. The below code takes the count of data points greater than the mean and divides it by the total number of data points. This will give us the percentage of data points greater than the mean.

```python
start = datetime.date.today() - datetime.timedelta(365 * 20)
end = datetime.date.today()
prices = web.DataReader(["^GSPC"], "yahoo", start, end)["Adj Close"]

# Rename column to make names more intuitive
prices = prices.rename(columns={"^GSPC": "SP500"})
df = np.log(prices) - np.log(prices.shift(1))
df = df.iloc[1:, 0:]
```

###### 2.4.1.1 Are returns symmetric?

One quick way of doing this is to determine how many data points we have on either side of the mean here. We have a bit more then 5,000 data points here. The below code takes the count of data points greater than the mean and divides it by the total data points. This will give us the percentage of data points greater than the mean

```python
(len(df[df.SP500 > df.SP500.mean()])) / (len(df))
```

We're getting about 52.7% of data points being greater than the mean, which shows we have a slightly positive skew to this dataset. We can't rule out symmetric returns based on this since it is only a sample of data and is reasonably close to the 50% mark. This makes it hard to say for certain whether S&P 500 returns are symmetric or not, but it is still a reasonable assumption to make here. Also, keep in mind there should be a slight bias towards positive returns anyways, if for no other reason than some drift from inflation.

###### 2.4.1.2 Is Volatility constant?

```python
vols = pd.DataFrame(df.SP500.rolling(50).std()).rename(columns={"SP500": "S&P 500 STD"})
# set figure size
plt.figure(figsize=(12, 5))
# plot using rolling average
sns.lineplot(
    x="Date",
    y="S&P 500 STD",
    data=vols,
    label="S&P 500 50 day standard deviation rolling avg",
)
```

Above, we calculate a rolling average of the standard deviation and then make a line chart of it. It can be clearly seen that volatility is anything but constant. This adds another layer of complexity to modeling stock returns, especially the many models which assume constant volatility 

###### 2.4.2. Are Stock Returns Normally Distributed?
The normal distribution is one of the most common distributions used in modeling random variables. Indeed, many phenomena in the natural and social sciences can be modeled by normal distribution. One of the great advantages of the normal distribution is its simplicity. We can completely describe a normal distribution through two numbers: one for the center of the distribution and one for the uncertainty about that center. The first number refers to the mean, and the second number refers to the standard deviation.

Once we have these two numbers, we can draw inferences, estimate percentiles, compute probabilities that a point falls within a region, and more. If our data is well-represented by the normal distribution, then we can confidently use the mean and standard deviation to report our portfolio expected returns and volatilities. If our data is not well represented by the normal distribution, then we need to find other distributions that are more suitable. Thus, when we have a distribution of stock returns, for example, we'll want to start this assessment by visualizing the returns to see if they appear to be normal. Of course, we can follow this up with more quantitative assessments by running statistical tests.

We can visualize the data using the `hist()` method. We pass in bins = 100 as a parameter to determine the amount of buckets to place the data in. The more bins you have, the more granular the data will look in a histogram. Increasing the bins too much may result in slightly noisy data, which will make it tougher to determine a normal distribution. The chart in Figure 3 looks like it could be normally distributed, but we need to be a little more scientific to determine if that's actually the case or not.

```python
df.hist(bins=100)
```

###### 2.4.2.1 Conducting a normality test

```python
stats.normaltest((np.array(df.SP500)))
```

We can use the `normaltest` method here to determine if the sample data could fit a normal distribution. This method uses D’Agostino and Pearson’s normality test, which combines skew and kurtosis to produce an omnibus test of normality.

The null hypothesis of this test is that the sample data fits a normal distribution. Let's assume we want to be 90% confident this data fits a normal distribution. We can compare this to the p-value to see if it's greater than 90%. In this case, the value, 2.43e-252, is extremely small, which leads us to reject the null hypothesis that this data fits a normal distribution.

###### 2.4.2.2 Testing Skewness and Kurtosis
As one added testing step, we can test the skewness and kurtosis of our distribution using the Jarque-Bera test. The test statistic will always be greater than zero. The further the test statistic is from zero, the more likely the sample data does not match a normal distribution.

Lucky for us, Python has another library for us to use here which really simplifies the analysis. From the `scipy.stats` library, we can use the `jarque_bera` method directly to our data to get test statistic 


```python
stats.jarque_bera((np.array(df.SP500))).pvalue
```

The p value of our data here shows once and for all that there is virtually zero chance our sample data is normally distributed

###### 2.4.2.3 Where Does Our Gaussian Distribution Break Down?
So according to the normality test, our data is not normally distributed despite the histogram looking like it may be. So, why is the data failing the normality test? The answer likely comes down to fat tails. Fat tails essentially means that extreme events +/-3 standard deviations away from the mean) are more likely than the normal distribution would imply.

Assuming a normal distribution with a mean of 0.00028 and standard deviation of 0.012, we can determine the probability of any return given that the returns fit a normal distribution.

To determine how many standard deviations away from the mean a specific number is, we need to use 

$\tfrac{X - \bar{X}}{\textrm{Sample standard deviation}}$

 Let's do this for the min and max of the sample data:

```python
dfMax = df.SP500.max()
dfMin = df.SP500.min()
print(
    "Min return of sample data is %.4f and the maximum return of sample data is %.4f"
    % (dfMin, dfMax)
)
```

```python
df.SP500.min()
```

```python
(df.SP500.min() - df.SP500.mean()) / df.SP500.std()
```

```python
(df.SP500.max() - df.SP500.mean()) / df.SP500.std()
```

Over the last 20 years, S&P 500 has had a maximum daily return of 10.96% and a minimum daily return of -12.77%. If we use the formula to determine standard deviations from the mean, we get -10.5 and 8.9 standard deviations away from the mean for the minimum and maximum, respectively. These standard deviations are humongous when compared to the normal distribution. We can see this analytically when we plug in the z score to the `norm.cdf` method to determine the probability this value could be in a normal distribution:

```python
stats.norm.cdf(-10.45)
```

This implies that the chance we could have a move as small as -12.77%, is 7.326261431744285e-26. This probability is so low that we would never expect an event like this to happen in our lifetime. We have multiple events like this, as illustrated by the minimum and maximum.

Going further with this idea, based on normal distribution z tables, we would expect 99.7% of our data points to be within +/- 3 standard deviations from the mean. Let's determine this for our sample data. First off, we need to find the cut-off values at +/- 3 standard deviations:

```python
(3 * df.SP500.std()) + df.SP500.mean()
```

```python
(-3 * df.SP500.std()) + df.SP500.mean()
```

The above two calculations would imply that 99.7% of all of our data points should be in between -0.0364 and 0.03699. Since we have 5,031 data points, we would expect about 15 of them to be outside of that range.

```python
df[(df["SP500"] > 0.03699) | (df["SP500"] < -0.0364)].tail()

len(df[(df["SP500"] > 0.05) | (df["SP500"] < -0.05)])
```

Not only do we get 85 values outside of our 3 standard deviation range, but we also get 36 values outside of +/- 5%, though you would almost never expect one of these events over 20 years, given a normal distribution.

In this next video, we go over how to leverage Python in order to test for normality of our data.

```python
from IPython.display import VimeoVideo

VimeoVideo("706653140", h="47eb01d16b", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1aJ1WcWvEEM5cUnJZm4lDdyOug1j2E9Rs/view?usp=sharing)

All this analysis does is basically prove that we have fat tails in our sample data, which is why the normal distribution is not suitable for modeling stock returns.



###### 2.4.3. Non-Gaussian Distributions

One potential alternative distribution we could use to forecast stock returns is the Student's t-distribution. This is very similar to a normal distribution except it has heavier tails. Theoretically, this sounds perfect for daily returns based on what we’ve seen up to this point.

Since we have 5,031 data points, we have 5,030 degrees of freedom. We can plug these numbers right into `stats.t.rvs` method to see a sample t-distribution and chart it:

```python
stats.t.rvs(df=5030, size=5000)

# generate t distribution with sample size 10000
x = stats.t.rvs(df=5030, size=10000)

# create plot of t distribution
plt.hist(x, density=True, edgecolor="black", bins=50)
```

We can also use the `ttest_ind` method to determine the probability that our returns came from the same sample distribution as in above figure



```python
t_stat, p = stats.ttest_ind(df["SP500"], stats.t.rvs(df=5030, size=5031))
print(f"t={t_stat}, p={p}")
```

Here, we get a p-value of 0.866, which means we would reject the null hypothesis at a 95% confidence level that these values come from the same data as the sample. There are two main things to point out here:

* While the p-value is less than 0.95, it’s still not too far off, and it's magnitudes closer to being true than the normal distribution we showed before. This indicates that this distribution is much better to use when modeling daily returns than the normal distribution. 
* This p-value is highly reliant on the sample data we have here. Every time we run that cell, we get different sample data, which also means different p-values. 

###### 2.4.4. Conclusion

In this lesson, we focused for the first time on comparing daily stock return data to normal distributions. We also touched on other potential distributions we could use to model this data. In the next module, we will take what we've learned thus far and apply it to a portfolio setting instead of just looking at individual assets in isolation

**References**

- D'Agostino, Ralph B. “An Omnibus Test of Normality for Moderate and Large Size Samples.” *Biometrika*, vol. 58, no. 2, 1971, pp. 341–348, https://doi.org/10.1093/biomet/58.2.341.



#### M3. Portfolios in Python

##### 3.1. Calculating portfolio risk/return statistics
1.  Damodaran, Aswath. "January 2019 Data Update 4: The Many Faces of Risk!" _YouTube_, 21 Jan. 2019, [https://www.youtube.com/watch?v=nI_vtGf5_Jc.](https://www.youtube.com/watch?v=nI_vtGf5_Jc.)
    -   **Required pages:** From minute 8:34 to 15:10
    -   **Estimated reading time:** 7 minutes
|  |  |
|:---|:---|
|**Reading Time** |  40 minutes |
|**Prior Knowledge** | Simple Stock Returns, Variance, Python, Linear Algebra, Matrix Multiplication  |
|**Keywords** | Portfolio Return, Variance, Sharpe Ratio |

---

*The previous module had a focus on the individual security. For this lesson, we take what we have learned previously and apply it to a portfolio setting using a basket of stocks/crypto.*

```python
import datetime
import math

import numpy as np
import pandas_datareader.data as web
from IPython.display import VimeoVideo
```
 
###### 3.1.1. Portfolio Returns
Up to this point in the course, we've spent our time analyzing individual securities. Today, we perform a similar analysis except using a portfolio of assets. We will first quickly recap how to determine return on investment for a single asset, General Electric (GE).

###### 3.1.1.1 Single Asset Return Recap
We will assume we bought 100 shares 10 years ago. To determine the cash return, we just need to use the following formula:

$r_f = (p_f - p_i) * 100$

start = datetime.date(2011, 11, 29)
end = datetime.date(2021, 11, 28)

```python
# start = datetime.date.today()-datetime.timedelta(365*10)
# end = datetime.date.today()
prices = web.DataReader(["GE"], "yahoo", start, end)["Adj Close"]
```

```
start = datetime.date.today() - datetime.timedelta(365 * 10)
end = datetime.date.today()
prices = web.DataReader(["GE"], "yahoo", start, end)["Adj Close"]
initialPrice = prices.GE[0]
finalPrice = prices.GE[-1]
cashReturn = (finalPrice - initialPrice) * 100
print(
    "With an initial investment of $%.2f, the cash return of this investment would be %.3f - %.3f * 100 = $%.3f"
    % (initialPrice * 100, finalPrice, initialPrice, cashReturn)
)
```
output: `With an initial investment of $13602.46, the cash return of this investment would be 75.860 - 136.025 * 100 = $-6016.463`

###### 3.1.1.2 How to Calculate Return with a Basket of Assets
We’ve now gone over returns of a single asset many times during this course. It’s time to apply similar logic to a basket of multiple assets. This will once again be best illustrated with an example. The following calculations can easily be extended to n number of securities, but to keep it simple, we will use two for our example. For this, we need to make some basic assumptions:

* 2 stocks
    * Meta—We will refer to it as its previous name from here on out: Facebook (FB) 
    * Chipotle (CMG)
* Bought 100 shares of each five years ago
* Goal: Calculate percentage return obtained by the portfolio at the end of the period

To start, we need to calculate the weights of each asset at the start of the period:

```python
# Define all initial variables
# start = datetime.date.today()-datetime.timedelta(365*5)
# end = datetime.date.today()
start = datetime.date(2016, 11, 29)
end = datetime.date(2021, 11, 28)
prices = web.DataReader(["FB", "CMG"], "yahoo", start, end)["Adj Close"]
initialFB = prices.FB[0]
initialCMG = prices.CMG[0]
finalFB = prices.FB[-1]
finalCMG = prices.CMG[-1]
FBWeight = initialFB / (initialFB + initialCMG)
CMGWeight = initialCMG / (initialFB + initialCMG)

print(
    "We have an initial investment in FB of $%.2f and in CMG $%.2f"
    % (initialFB * 100, initialCMG * 100)
)
```
output: `We have an initial investment in FB of $nan and in CMG $39511.00`

```
print(
    "This would make the weights %.2f and %.2f for FB and CMG respectively"
    % (FBWeight, CMGWeight)
)
```
o/p: `This would make the weights nan and nan for FB and CMG respectively`

###### 3.1.1.3 Final Returns


In order to calculate the final portfolio percentage returns, we need to find the returns of each asset individually, multiply the return by the weight in our portfolio, and then add them together. The formula to calculate this for two assets is:

$Portfolio_{Return} = w_1R_1 + w_2R_2$

```python
returnFB = 100 * (finalFB - initialFB) / initialFB
returnCMG = 100 * (finalCMG - initialCMG) / initialCMG

print(
    "This return over this period for Facebook is %.2f%% and %.2f%% for Chipotle"
    % (returnFB, returnCMG)
)
```
output: `This return over this period for Facebook is nan% and nan% for Chipotle`

```
print(
    "Multiplying these individual returns by their weights gives %.2f (FB) and %.2f (CMG)"
    % (returnFB * FBWeight, returnCMG * CMGWeight)
)
```
`Multiplying these individual returns by their weights gives nan (FB) and nan (CMG)`

Adding these weighted returns together gives us a portfolio return of 41.14+250.35 = 291.49% 

Our portfolio would have returned 291.49% over the last five years, assuming we invested in both assets on the same starting date and with our weights.

In the first video of this lesson, we show how to transition from calculating an individual security's returns to calculating the returns of a portfolio of assets.

```python
VimeoVideo("706655699", h="1a478ba2bf", width=600)
```
- Screenshots: 
- 
[Access video transcript here](https://drive.google.com/file/d/1XBLrPLm9xtBfS74KK2xve2TuU5Ci9ZOf/view?usp=sharing)

###### 3.1.2. Calculating Portfolio Variance
This was discussed at a high level during the Financial Markets course, but here, we will show how to calculate variance in Python with empirical data. While returns are important, investors are also concerned about risk or volatility. We will use variance of returns to determine risk. Once again, we will use an example, using the same data as before to drive the point home. A bit of linear algebra is needed, but luckily, we have Python to do the tough calculations for us. 

If we were to calculate this for two assets using pencil and paper, we could use the following formula:

$\textrm{Portfolio variance} = w_1^2\sigma_1^2 + w_2^2\sigma_2^2 + 2w_1w_2Cov_{1,2}$

Where:

* $w_1$ = the portfolio weight of the first asset

* $w_2$ = the portfolio weight of the second asset

* $\sigma_1$ = the standard deviation of the first asset

* $\sigma_2$ = the standard deviation of the second asset

* $Cov_{1,2} = \textrm{the covariance of the two assets, which can thus be expressed as } \rho_{(1,2)}\sigma_1\sigma_2, \textrm{where }\rho_{(1,2)} \textrm{is the correlation coefficient between the two assets}$



Luckily, Python makes it easy for us to expand the formula to n number of assets. This formula is better expressed in matrix notation since it's easier to apply this way in Python: 

$Portfolio Variance = Weights transposed * (covariance matrix) * weights$

###### 3.1.2.1 Defining Variables
Let's put those portfolio weights we calculated before into an array and also calculate the simple daily returns of our asset along with a covariance matrix of these daily returns. Keep in mind that we will multiply the daily returns covariance matrix by 252 to measure annual variance.



```python
weights = np.array([0.23, 0.77])
returns = prices.pct_change()
covariance = 252 * returns.cov()
```

After defining these, we simply need to take the dot product of the transposed weights with the dot product of the covariance matrix and weights to get the annual variance of our portfolio. Note: The t-method in numpy just transposes the array.

```python
variance = np.dot(weights.T, np.dot(covariance, weights))
```
```python
# Print the result

print(str(np.round(variance, 4) * 100) + "%")
```

We determine that the annual variance of our portfolio is 10.33%. Let’s compare this to the variance of each individual asset.

###### 3.1.2.2 Comparing Portfolio Variance to Individual Stock Variance
This shows the annual variance of a portfolio with FB and CMG weighted 23% and 77% respectively has shown a 10.33% annual variance over the last five years.

One extremely interesting byproduct of this result can be seen when calculating variance of the equities individually. One of the main pillars of modern portfolio theory is about how diversification reduces risk. We can see this clear as day by looking at each stock's variance over the same time period.

```python
returns.var() * 252
```

We can see in above that both stocks' variance is higher than that of our portfolio, and even though CMG has a 77% weighting and a 13.7% variance, our portfolio's variance is more than 3 percentage points lower. This is because, if assets are not perfectly correlated, there will be some diversification benefit to risk by investing in multiple securities.

###### 3.1.2.3 Calculating Standard Deviation of the Portfolio
Taking this a step further, since we know standard deviation is just the square root of variance, we can also calculate that here.

The below calculation shows the annual standard deviation of our portfolio to be about 32%:

```python
np.round(math.sqrt(variance) * 100, 2)
```

Just like with the last video where we moved from thinking about individual stocks to a basket of stocks, we do the same here in order to calculate variance and standard deviation of returns for a portfolio.

```python
VimeoVideo("706655745", h="8aa2f6d895", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1GJfJMRmDvKy1Hd8eUWL8VeGQcuwAsR-I/view?usp=sharing)

###### 3.1.3. Sharpe Ratio of Portfolio
Calculating the Sharpe ratio of a portfolio is pretty easy at this point since we have all the variables we need at our disposal. As a recap, the Sharpe ratio is just:

$\cfrac{Portfolio_{Return} - \textrm{risk-free rate}}{Portfolio_{StandardDev}}$

Since interest rates have been near 0 for a while now, we will assume 0 for the risk-free rate. Our formula is now: 

$\cfrac{\textrm{Portfolio}_{Return}}{\textrm{Portfolio}_{StandardDev}}$

We have calculated the total return of our portfolio over five years to be 291.49%. To get a single-year return, we can divide this number by 5 to get 58.298%. Considering our annual standard deviation is 32.01%, we can get the Sharpe ratio by dividing these two numbers to get 1.821 as the Sharpe ratio for our portfolio. In most cases, a Sharpe ratio over 1 is an exceptional risk/return metric. This makes sense considering how advantageous investments in Chipotle or Facebook would have been if you had invested in them five years ago.



###### 3.1.4. Performing Similar Analysis on Cryptocurrencies
We will use the two most popular cryptocurrencies to perform a similar analysis, and we will compare and contrast them to the equity results we have obtained. We'll perform the analysis over the same time frame (the last five years) for the two most popular cryptocurrencies: Bitcoin and Ethereum. This time, let's say we bought five Bitcoin and 100 Ethereum five years ago.

```python
# Define all initial variables
# start = datetime.date.today()-datetime.timedelta(365*5)
# end = datetime.date.today()
start = datetime.date(2016, 11, 29)
end = datetime.date(2021, 11, 28)
prices = web.DataReader(["BTC-USD", "ETH-USD"], "yahoo", start, end)["Adj Close"]
prices = prices.rename(columns={"BTC-USD": "Bitcoin", "ETH-USD": "Ethereum"})

initialBTC = 5 * prices.Bitcoin[0]
initialETH = 100 * prices.Ethereum[0]
finalBTC = 10 * prices.Bitcoin[-1]
finalETH = 100 * prices.Ethereum[-1]
BTCWeight = initialBTC / (initialBTC + initialETH)
ETHWeight = initialETH / (initialBTC + initialETH)

print(
    "This would make the weights %.2f and %.2f for Bitcoin and Ethereum respectively"
    % (BTCWeight, ETHWeight)
)
```

```python
returnBTC = 100 * (finalBTC - initialBTC) / initialBTC
returnETH = 100 * (finalETH - initialETH) / initialETH
```

```python
np.round(returnBTC, 3)
```

```python
np.round(returnETH, 3)
```

Now, our returns for the stock portfolio were high, but this takes it to another level: Bitcoin and Ethereum have shown unprecedented returns over the last five years. Bitcoin returned 15,616.76% and Ethereum has returned 54,280.23%. If we keep using our portfolio weights from before, our portfolio would have returned 22,647.01%

```python
np.round(returnBTC * BTCWeight + returnETH * ETHWeight, 3)
```

###### 3.1.4.1 Calculating Variance for Cryptos
Notice instead of multiplying by 252 like we did previously to annualize our variance, we use 365 here since cryptos trade seven days a week:

```python
weights = np.array([0.82, 0.18])
returns = prices.pct_change()
covariance = 365 * returns.cov()
variance = np.dot(weights.T, np.dot(covariance, weights))
print(str(np.round(variance, 3) * 100) + "%")
```

We get 63.6% variance for our portfolio, which translates to an annual standard deviation of 79.73%. Even though we were in relatively risky stocks, the standard deviation of that portfolio (32.14%) pales in comparison to this. Even though it's riskier, the crypto portfolio also returned a much higher rate. This illustrates a classic financial principle: With more risk, there is more potential return. Can you think of one simple way we can compare the portfolios taking into account risk AND return?

Yes, that's right, we can go back to the trusty Sharpe ratio.

###### 3.1.4.2 Sharpe Ratio Comparison
The Sharpe ratio of our stock portfolio was 1.821. If we run the same calculation on our crypto portfolio we get:

22647.01/5 = 4,529.40% as our annual percentage return. If we divide this by the standard deviation we get:

45.294/.7973 = 56.81 Sharpe Ratio

This is a truly outstanding Sharpe ratio, and it's obvious at this point that if you had invested in Bitcoin or Ethereum five years ago and held it today, you're in very good shape. While this would've been a great investment, hindsight is 20/20, and it must be said that just because the last five years had incredible returns, it does not mean the next five years will.

###### 3.1.5. Conclusion

During this lesson, we hint and imply that diversifying reduces risk in a portfolio. In the next lesson, we will prove it by quantifying the benefits of diversification.



##### 3.2. Displaying effects of diversification in a portfolio
1.  Downey, Allen B. _Think Stats: Exploratory Data Analysis in Python_. Version 2.2, Green Tea Press, Needham, MA. [https://greenteapress.com/thinkstats2/thinkstats2.pdf](https://greenteapress.com/thinkstats2/thinkstats2.pdf)
    -   **Required pages:** Chapter 7: (pp. 91-103)
    -   **Estimated reading time:** 30-40 minutes
|  |  |
|:---|:---|
|**Reading Time** |  40 minutes |
|**Prior Knowledge** | Stock Return Calculations, Variance, Standard Deviation  |
|**Keywords** | Variance - Correlation relationship, Covariance |

---

*In the previous lesson, we focused on comparing returns and volatilities of multiple assets. In this lesson, we focus further on how we can reduce volatility in our portfolio and the variables that have an impact on this*

```python
import datetime

import pandas as pd
import pandas_datareader.data as web
import seaborn as sns
from IPython.display import VimeoVideo
```

###### 3.2.1. Diversification
Diversification is an extremely important investing concept. It's the belief that you can reduce risk by spreading your capital across multiple investments, not just one. This can be multiple stocks, multiple asset classes, etc. The key is that you spread your wealth or, don't put all your eggs in one basket. Later in this lesson, we will discuss how we can optimize the diversification of our portfolio. For now, we will illustrate why it is so important.

We will use a practical example. Let's say the year is 2016 and you have inherited some wealth from a family member and are looking for where to put it. You were told by a family friend that you should spread out this money and not just put it into the same type of asset so you decide to buy 100 shares of JP Morgan (JPM) and 5 Bitcoin. Let's pull the data and calculate the returns of each along with the returns of our portfolio 

```python
start = datetime.date(2016, 11, 29)
end = datetime.date(2021, 11, 28)
# start = datetime.date.today()-datetime.timedelta(365*10)
# end = datetime.date.today()
prices = web.DataReader(["JPM", "BTC-USD"], "yahoo", start, end)["Adj Close"]
prices = prices.rename(columns={"BTC-USD": "BTC"})
prices = prices.dropna()
returns = prices.pct_change()

# observe data
returns.head()
```

###### 3.2.1.1 Determine Initial Investment

```python
# Determine weights
initialJPM = prices.JPM[0] * 100
initialBTC = prices.BTC[0] * 5
initialInvestment = initialJPM + initialBTC

weightJPM = initialJPM / (initialBTC + initialJPM)
weightBTC = 1 - weightJPM
print(
    "This would make the weights %.3f and %.3f for JPM and BTC respectively"
    % (weightJPM, weightBTC)
)
```

###### 3.2.1.2 Calculate Portfolio Daily Returns

We will use the existing weights we just calculated, but to make things simpler, we are going to assume a $10,000 investment in each of these assets along with our portfolio so that we can compare returns. In order to see the daily change in our portfolio, we need to add 1 to each return and then multiply each subsequent return by our previous position.

For example, in our portfolio below our first two returns are 0.015 and 0.018. 
We add one to these to get 1.015 and 1.018. 

Then, with our starting position of \\$10,000,  to get the portfolio value after one day we multiply 
\\$10,000 * 1.015 = \\$10,150. 

To get the portfolio value after the next day, we multiply \\$10,150 * 1.018 = \\$10,332.7

Let's apply the above logic to the last 5 years of data:

```python
returns["Portfolio"] = (returns.JPM * weightJPM) + (returns.BTC * weightBTC)
returns = returns + 1
returns.head()
```

```python
returns.iloc[0] = 10000
returns.head()
```

```python
returns.cumprod()
```

```python
portValues = returns.cumprod()
portValues["Date"] = portValues.index
```

We can chart the two assets we've invested in along with the value of our portfolio. First, we need to get the data into a more usable format for seaborn's `lineplot` method. We use the pandas `melt` method to make our table more horizontal:

```python
sns.lineplot(x="Date", y="value", hue="Symbols", data=portValues.melt(id_vars=["Date"]));
```

We can see in the above chart that our portfolio wouldn't have gained as much as our highest returning asset, Bitcoin, but it seems as if the peaks and valleys of the chart are reduced a bit by investing in more than one asset.

###### 3.2.1.3 Quantifying Diversification Benefits
How do you think we can measure how volatile our stocks are compared to our portfolio? One simple way is to take the standard deviation of the returns and compare it to the standard deviation of our portfolio returns. 

```python
returns.drop(index=returns.index[0], axis=0, inplace=True)
returns = returns - 1
returns.head()
```

```python
returns.std().round(3)
```

We can see from the standard deviations above that even though Bitcoin had the highest returns, it also had the highest standard deviation of returns by a significant margin. Herein lies one of the major benefits of diversification: by investing in multiple assets, we are able to reduce the volatility of our portfolio. It's not less than JP Morgan's standard deviation, but it is much closer to that than the high end, which is Bitcoin. In most cases, the more assets we invest in, the more we can reduce our risk or standard deviation

If we are managing a client's account and their first objective is to reduce risk, how do you think we can identify assets to do this effectively and efficiently?

In the first video of this lesson, we recap what we've learned so far regarding the benefits of diversification and how we can quantify this.


```python
VimeoVideo("706655791", h="668198086a", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1MrBC8e7yIG5YVHcicLBsukkrCOnErrLj/view?usp=sharing)

###### 3.2.2. Managing Portfolio Variance
###### 3.2.2.1 Portfolio Variance Formula
In order to try to minimize portfolio variance, a good starting point is the formula itself to calculate variance with a two-asset portfolio.


$\textrm{Portfolio Variance} = w_x^2 \sigma_x^2 + w_y^2 \sigma_y^2 + 2w_x w_y Cov_{x,y}$

where

* $w_x$ = portfolio weight of asset x
* $w_y$ = portfolio weight of asset y
* $\sigma_x$ = standard deviation of asset x
* $\sigma_y$ = standard deviation of asset y
* $Cov_{x,y}$ = Covariance of the two assets

Also, building off the previous lesson this means that

$\textrm{Portfolio Standard Deviation} = \sqrt{\textrm{Portfolio Variance}}$



With this information in mind, there are 3 things we can do to minimize variance.
1. We can pick assets with lower standard deviations of returns. This may seem obvious, but if we really want to reduce the variance of our portfolio, the simplest thing to do is just pick assets that have relatively low volatilities. 
2. Invest a higher percentage of your portfolio into your less risky asset(s). For our previous example with JPM and Bitcoin, we could further reduce our portfolio variance by investing a bigger portion of our funds into JPM since it had a lower standard deviation than Bitcoin. 

Sometimes, it's the case that an investor may still want to invest in a riskier asset like Bitcoin. This brings us to the third thing we can do to reduce variance.

3. Check for assets with a low covariance. If you look at the right side of our portfolio variance function, you'll notice we have the covariance of two assets as a function parameter. If we can reduce that, we can reduce the overall variance of our portfolio. 

This is an important point and should be expanded upon further.


###### 3.2.2.2 Covariance-Correlation Relationship
If you recall from a previous lesson, the formula for correlation is:

$\rho_{x,y} = \frac{Cov_{x,y}}{\sigma_x*\sigma_y}$

We can rearrange this to get the covariance formula:

$Cov_{x,y} = \rho_{x,y}\sigma_x\sigma_y$

Then, we can plug this back into our portfolio variance formula:

$\textrm{Portfolio Variance} = w_x^2 \sigma_x^2 + w_y^2 \sigma_y^2 + 2w_x w_y \rho_{x,y}\sigma_x\sigma_y$


These formulas are basically to show that we need to minimize correlations in order to minimize portfolio variance. Owning uncorrelated assets illustrates the efficient benefits of diversification. Let's write some reusable functions to sum up the work we did above and really display how this works with a few examples 

**3.2.2.2.1 Writing Functions - Reusable Code**
A common tenet in programming is to wrap any code you're going to need to use multiple times into a function. In our case, we've needed to calculate daily returns over a date range many times throughout this course. We will wrap the core code for this into a function called `getReturns`.

`getReturns` takes 3 arguments:
* `startTime` - `datetime`
* `endTime` - `datetime`
* `tickers` - dict of values where key is the yahoo ticker for a security and values are the displayed names in the output

```python
def getReturns(startTime, endTime, tickers):
    # pull price data from yahoo -- (list(tickers.keys())) = ['^GSPC','^RUT']
    prices = web.DataReader(list(tickers.keys()), "yahoo", startTime, endTime)[
        "Adj Close"
    ]
    prices = prices.rename(columns=tickers)
    prices = prices.dropna()
    return prices.pct_change()
```

We can test this function by running it with our existing data and then returning the first few rows:

```python
res = getReturns(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"JPM": "JPM", "BTC-USD": "Bitcoin"},
)
res.head()
```

Now that that's settled, onto the good stuff. We can now use our `getReturns` function to easily calculate correlations of different assets. Let's look at the correlations of the two assets we've used thus far along with introducing a Bond ETF. We will use the bond ETF, BLV, that we used in a previous lesson:

```python
getReturns(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"JPM": "JPM", "BTC-USD": "Bitcoin", "BLV": "BLV"},
).corr()
```

We can see that the BLV has a very small correlation with Bitcoin and even a negative correlation with JP Morgan.

We will expand upon this further and use our `getReturns` function in a new `compareRisk`.

`compareRisk` will take the same parameters of `getReturns` along with a list of weights so that we can calculate daily portfolio returns and volatility metrics


```python
def compareVariance(startTime, endTime, tickers, weights):
    returns = getReturns(startTime, endTime, tickers)
    tmp = weights * returns
    returns["Portfolio"] = tmp[tmp.columns[0]] + tmp[tmp.columns[1]]
    standardDev = returns.std()
    avgReturns = returns.mean()
    res = pd.concat([avgReturns * 100, standardDev], axis=1)
    res.columns = ["Daily Average Return Percentage", "Standard Deviation of Returns"]
    return res.round(3)
```

We can use this function to illustrate our previous example comparing JP Morgan to Bitcoin over the last five years. 

```python
compareVariance(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"JPM": "JPM", "BTC-USD": "Bitcoin"},
    [0.652, 0.348],
)
```

Like mentioned previously, one simple way to reduce variance could be to skew the weight of your investment more towards the less volatile side. In this case, we'll increase our weight in JPM from 0.652 to 0.8. By doing this, the volatility of our portfolio is the same as that of JPM, but we get double the returns of JPM since Bitcoin returns are still factored in.

```python
compareVariance(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"JPM": "JPM", "BTC-USD": "Bitcoin"},
    [0.8, 0.2],
)
```

To really bring this point home, let's compare three assets with similar average returns and show how correlation can affect portfolio variance. We will do this comparing JP Morgan to Ford and General Motors. We can see below that they all have very close average daily returns over the last five years.

```python
getReturns(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"JPM": "JPM", "F": "F", "GM": "GM"},
).mean()
```

When looking at the correlations, we see close to what we would expect. Ford and General Motors are quite highly correlated since they're both car manufacturers. While JP Morgan is still positively correlated with both, it's a good amount less than Ford and General Motors themselves.



```python
getReturns(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"JPM": "JPM", "F": "F", "GM": "GM"},
).corr()
```

If you had to own two of these stocks, what do you think would be the best combination in order to minimize the variance of our portfolio?

We look at Ford and General Motors together first. The standard deviation of returns for our portfolio is less than that of F or GM on their own which shows the benefits of diversification even with assets which are strongly correlated

```python
compareVariance(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"F": "F", "GM": "GM"},
    [0.5, 0.5],
)
```

Since Ford and JP Morgan are least correlated, we would expect the benefits of diversification to be strongest with a portfolio here and the results show us exactly that. Standard deviation of returns for our portfolio goes down even further while maintaining the same daily average return. Keep in mind that a well-diversified two-stock portfolio can have less volatility than either of its individual stocks!

```python
compareVariance(
    datetime.date(2016, 11, 29),
    datetime.date(2021, 11, 28),
    {"F": "F", "JPM": "JPM"},
    [0.5, 0.5],
)
```

In the next video, we recap the portfolio variance formula, go over different ways to reduce variance by manipulating the variables in this formula, and write a function for easy comparison of assets.

```python
VimeoVideo("706655839", h="5fa1cf9fae", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1EOjUT08zJp1t8noEFKh7SLG6rOamZpRM/view?usp=sharing)


###### 3.2.3. Conclusion

We've spent this lesson developing methods to compare returns and volatilities of different assets. We can use some of methods we have learned in order to help us pick different investments to fit our needs, whether that means maximizing returns, minimizing volatility, or some combination of the two. In the next lesson, we will explore exchange traded funds(ETFs) in greater detail along with showcasing the built-in diversification benefits you get by owning them.



##### 3.3.ANALYZING COSTS AND BENEFITS OF OWNING AN ETF
1.  Khan Academy. "Exchange Traded Funds (ETFs) | Finance and Capital Markets | Khan Academy." _YouTube_, 18 April 2011, [https://www.youtube.com/watch?v=SFdsY9Rdh6w](https://www.youtube.com/watch?v=SFdsY9Rdh6w).
    -   **Required pages:** Whole video
    -   **Estimated reading time:** 5 minutes

|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | ETFs, Stocks, Returns, Diversification  |
|**Keywords** | Expense Ratio, Survivorship Bias, Active vs. Passive Investing |

---

*In the last lesson, we showcased the benefits of diversification to a portfolio. Here, we will show how to effectively tap into those diversification benefits through owning an ETF.*

```python
import datetime

import matplotlib.pyplot as plt
import pandas_datareader.data as web
import seaborn as sns
```

###### 3.3.1. Analyzing Exchange Traded Funds (ETFs)

For this lesson, we will continue building upon the analytical tools we've learned in previous lessons to further examine exchange traded funds (ETFs). To this point, we have used ETFs a few times already like, when we used BLV as a proxy for bonds, but in this lesson we will go into further detail about ETFs and what makes them such an important investing tool. 

###### 3.3.1.1 ETF Benefits
* Diversification: exchange traded funds essentially have some form of diversification built in already. We went over the benefits of diversification in the last lesson and that is built into the DNA of what an ETF is. For example, you can invest in the SPDR S&P 500 ETF Trust(SPY) which tracks the S&P 500. This allows you to effectively invest in 500 companies at once instead of actually having to buy the stocks of 500 companies individually. You can reap the diversification benefits from this. Most ETFs even rebalance every quarter so you don't have to worry about that either.

* Survivorship Bias: There are a lot of ETFs, some of which follow strict rules on which companies can be included or not. Let's say we have an ETF called ABC. ABC requires companies to have over a \\$100mn market cap. This means that anytime one of the holding comapnies within ABC falls below \\$100 million, the ETF is forced to sell it and buy a new company. This introduces a clear bias to only hold onto companies that are doing well. This can be a huge benefit to investors in certain situations.

* Broader Predictions: ETFs allow you to make a prediction without being an expert in a certain industry - Let's say you expected the semiconductor market to do well over the next year but didn't know specifically which company to buy. ETFs simplify this thought process by allowing you to buy into one ETF, which contains shares of individual semiconductor stocks  


Let's explore these benefits in a bit more detail starting from the top.

###### 3.3.1.2 ETF Benefits: Diversification
Although you probably get the theme of these lessons by now, we will use a lesson to best illustrate the benefits of diversification through ETFs. Imagine the year is 2006 and your two friends Elaine and Jerry both conclude that banks and financial institutions will be fantastic long-term investments for the next 15+ years. Jerry is confident with his stock-picking skills, so he decides he's going to invest all of his money into a company he can't imagine in a million years could fail, Lehman Brothers. Elaine doesn't know as much about specific financial institutions and what to invest in, so she decides she will just invest her money into an ETF, XLF. XLF is the Financial Select Sector SPDR Fund; it contains exposure to the U.S. financials sector. It's cap-weighted, S&P 500-only portfolio, which means that it’s concentrated in large banks and avoids small-caps (XLF).

If you had to guess, who do you think had better performance since the start of 2006? You can probably see where this is going. If you're unaware, Lehman Brothers famously collapsed in 2008 and filed for the largest bankruptcy in U.S. history. This means Jerry likely lost his entire initial investment.


**Figure 1: Lehman Brothers Market Cap**
![](https://i.imgur.com/7IquqiD.png)


Source: Wiggins, Rosalind Z.; Piontek, Thomas; and Metrick, Andrew (2019) "The Lehman Brothers Bankruptcy A: Overview," *The Journal of Financial Crises*: Vol. 1 : Issue. 1, 39-62.,(https://elischolar.library.yale.edu/cgi/viewcontent.cgi?article=1000&context=journal-of-financial-crises)


Let's examine what happened to XLF during this time period and see how it held up:


```python
start = datetime.date(2006, 1, 1)
end = datetime.date(2021, 11, 28)
# end = datetime.date.today()
prices = web.DataReader(["XLF"], "yahoo", start, end)["Adj Close"]
prices = prices.dropna()

# set figure size
plt.figure(figsize=(12, 5))

# plot a simple time series plot
# using seaborn.lineplot()
sns.lineplot(x="Date", y="XLF", data=prices, label="Daily XLF 500 Prices")
```

Lehman Brothers collapse had a profound effect on the financial industry as seen in the above chart. They had lots of different exposure to different financial institutions and for a variety of reasons, the U.S. economy went into the worst recession since the Great Depression. If we just take a moment to look at the period from 2006 to the start of 2010 and compare the min and max of the data at this time, you can see that XLF lost 82.7% as its max drawdown. 

```python
drawdown = (
    prices["2006-01-01":"2010-01-01"].min() - prices["2006-01-01":"2010-01-01"].max()
) / prices["2006-01-01":"2010-01-01"].max()
100 * drawdown.round(3)
```

I'm sure near the start of 2010, Elaine would be distraught over her investment since XLF was performing horribly. As sad as she would be, Jerry would be more upset since his investing account is now worth \\$0 with no way to recoup his initial investment. Lucky for Elaine, she's a patient person so instead of taking a massive loss, she decided she would just wait and hold. Let's see her percentage return from the start of 2006 to today:

```python
(100 * (prices.XLF[-1] - prices.XLF[0]) / prices.XLF[0]).round(2)
```

By having the benefits of diversification through an ETF and by being patient, Elaine would've ended up with a 104.82% return since 2006. If she invested \\$10,000 dollars into the fund then while Jerry invested \\$10,000 into Lehman Brothers, he would be left with \\$0 while Elaine would be sitting on about $20,482. This is just one example of many illustrating the benefits of diversification through ETFs.

###### 3.3.1.3 ETF Benefits - Survivorship Bias
Many ETFs have to follow certain rules for which companies they can hold: this has a sort of built in survivorship bias, which can help investors. For example, consider the Dow Jones Industrial Average (DJIA), which is one of the oldest equity indices on Earth. This index was created by Charles Dow in 1896 with the following original components:

* American Cotton Oil 
* American Sugar 
* American Tobacco
* Chicago Gas 
* Distilling & Cattle Feeding 
* General Electric 
* Laclede Gas 
* National Lead 
* North American 
* Tennessee Coal Iron and RR 
* U.S. Leather 
* United States Rubber 

General Electric is likely the only one you have heard of out of these and is the only company from this list still with its original name. The rest of them have been dissolved or spun off into different companies. Considering this, you would expect the Dow Jones Industrial Average to be struggling, but that's not the case. DJIA hit an all-time low during the summer of 1890 where the index hit a price of 28.48. Fast forward to 2021 and the index is at \\$35,754.69 as of December 9th, 2021. This is clearly not an index in bad shape. This is because over time, as views change regarding what should constitute the DJIA, companies were removed and added. In fact, General Electric has been removed twice throughout it's history, finally in 2018 as it is no longer on the index today (S&P Dow Jones Indices).

Clearly, ETFs were not available during the Dow's inception as they've only become widely available over the past couple of decades, but you can still see why this survivorship bias can help you as an owner of an ETF.  

###### 3.3.1.4 Expense Ratios
One thing to consider before buying an ETF is the expense ratio. This is written as a percentage of the net asset value of each fund. The expense ratio is used to pay for many different things like the salaries of the managers, marketing, administration, distribution, and any other expenses. Typically, the expense ratio of ETFs is much lower than that of mutual funds, which is one of the reasons why ETFs have become so popular in recent years comparatively. 

**3.3.1.4.1 How can we calculate the expense ratio of an ETF**
We can use SPY as an example; it has a 0.094% expense ratio. Now, if you calculate returns like we have been, you may notice that the expense ratio is built into the price. This means that when you buy an ETF, you won't get a charge for the annual expense ratio; it will just be reflected in your returns. 

Let's use a hypothetical ETF to illustrate how the expense ratio is calculated. Assume we invest into hypothetical ETF, ABC with:
* \\$10,000 initial investment
* Cost of one share of the ABC is \\$5,000
* After one year, the underlying assets are worth \\$6,000 per share
* Expense ratio is 0.5%

How much money do we have in our account at the end of the year assuming the expense ratio wasn't taken out yet? 

We can calculate the cost per share using the final value at the end of the year -- \\$6,000


```
6000 * 0.005
```

This means at the current price we're losing \\$30 a year annually per share. Multiply this by two shares and our final portfolio value at the end of the year is:

```
(6000 - 30) * 2
```

Instead of having a portfolio value of \\$12,000 by the end of the year, it's worth \\$11,940 when taking into account the expense ratio. This may not seem like a lot, but not all expense ratios are created equally and we must take this into consideration before investing into an ETF. If a portfolio is unchanged at the end of the year, then it loses the expense ratio, since the return was 0 before expenses.

###### 3.3.1.5 Active versus Passive ETFs
When ETFs were initially invented, they were designed to allow investors to invest into funds that track indices like the S&P 500, Dow Jones Industrial Average, etc. These would be considered passive funds since their sole purpose was to track an underlying index.

This purpose has evolved over time, and today there are many ETFs you can invest in that track a portfolio manager instead of an index. For example, there is the ARK Innovation ETF (ARKK) with an expense ratio of 0.75%, which is on the high side compared to many passive ETFs. This fund tracks the investments by famous investor, Cathie Wood. These actively managed funds tend to have higher expense ratios than passive funds

###### 3.3.2. Conclusion
This lesson we went over the nuances of owning an ETF along with how we can take advantage of their built-in diversification benefits. In the next lesson of this module, we will cover situations where diversification fails and how we can quantify that


**References**

- XLF ETF Report. ETF.com, https://www.etf.com/XLF. Accessed 23 March 2022.

- S&P Dow Jones Indices. *Dow Jones Industrial Average - Historical Components. S&P Global*, https://www.spglobal.com/spdji/en/documents/education/spdji-djia-historical-component-changes.pdf. Accessed 23 March 2022.

- Wiggins, Rosalind Z.; Piontek, Thomas; and Metrick, Andrew (2019) "The Lehman Brothers Bankruptcy A: Overview," *The Journal of Financial Crises*: Vol. 1 : Issue. 1, 39-62. https://elischolar.library.yale.edu/journal-of-financial-crises/vol1/iss1/2




##### 3.4. Identifying and applying downside risk metrics associated with financial markets
> [!Warning] Requirement missing
> There is a data file btc-usd.pkl missing which is unable to be downloaded from jupyterlab. 
> Care when running code. 
> Codeblocks where package is required pics of output from jupyterlab will be posted.
1.  DataCamp. "Python Tutorial: Correlation of Two Time Series." _YouTube_, 1 March 2020, [https://www.youtube.com/watch?v=XVV6IVPUlKU](https://www.youtube.com/watch?v=XVV6IVPUlKU).
    -   **Required pages:** Whole video
    -   **Estimated reading time:** 3 minutes


|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Stock Indices, Log return calculations  |
|**Keywords** | Value at Risk, Expected Shortfall |

---

*This lesson will go over a fundamental risk concept, Value at Risk. This will allow us to estimate the maximum amount of money we can lose in a single day given a confidence level. This metric is employed at banks and financial institutions around the world in order to mitigate market risk. Using this and it's many variations will help us build a well-balanced portfolio to try to protect us from financial losses going forward*

```python
import datetime

import numpy as np
import pandas as pd
import pandas_datareader.data as web
import seaborn as sns
from IPython.display import VimeoVideo
from scipy import stats
```

###### 3.4.1. Value at Risk (VaR)

Value at Risk is one of the easiest risk metrics to interpret. So far, the metrics we have introduced quantify risk as a percentage, in the case of standard deviation, or in units, as the Sharpe ratio does. Value at Risk answers the fundamental question many investors have on their mind: How much can I lose on an investment in a worst-case scenario? This is measured in dollars for the purposes of this class.

Value at Risk measures the potential loss in value of an asset/portfolio over a defined time period. Basically, you will always need to specify the time period and confidence interval that accompanies a Value at Risk. For example, if the VaR of a portfolio is \\$1,000,000 over a yearly time period with a 99\% confidence interval, it would mean that the portfolio only has a 1\% chance of losing more than \\$1,000,000 for any given year. VaR has become ubiquitous over the years; every investment bank and risk management firm is employing some form of VaR to help keep a cap on the potential losses one can incur. The focus on VaR is very much about downside risk unlike something like standard deviation, which looks at both the upside and downside risk.

There are three basic methods for calculating VaR, each with their own advantages and disadvantages. These should build on some of the lessons from earlier, like variance and covariance. Keep in mind that there are countless variations of each basic method, but we will stick with these main three for now:

* Historical Method
* Parametric Method 
* Monte Carlo Simulation


###### 3.4.2. Historical Method

This is probably the simplest and most intuitive method of calculating Value at Risk. In short, historical returns are sorted from lowest to highest on an asset or portfolio. Let’s say you wanted to calculate the daily Value at Risk on an equity with a 95% confidence interval. Assuming we can look at the last thousand days of data for this stock, we would take the daily returns and sort them from lowest to highest. From here, we would take the return from the 5th percentile of the data. In this case, with 1,000 days of data, it would be the 50th (0.05\*1000) worst daily return from these thousand days. Let’s say the 50th worst day had a –4% return. From this, we can assume that the daily VaR for this stock with a 95% confidence interval is –4%. Building on that, if we were to invest \$1,000 in said stock, we would expect the worst daily loss to be:

(-\$0.04)\*1000 = -\$40,  with a 95% confidence interval

Considerations for this method:
* This method uses historical returns to measure VaR empirically, which means that there are no assumptions made about the distribution whereas many models assume the normal distribution.
* Each day for this method is given equal weight, which means if there is a trend in the volatility, you could be overstating or understating the VaR depending on whether the volatility trend is down or up, respectively. One refinement to combat this could be to place greater weight on more recent data.
* Past data does not necessarily indicate what will happen in the future. While the other methods also rely on historical data to a certain extent, this method is solely derived from past historical returns. There are many unforeseen events that can happen, which can change the course of a stock’s trajectory and cause the stock to trade differently than it did in the past.



###### 3.4.2.1 Implementing Value at Risk (VaR) - Historical Method

Calculating daily historical VaR can be done pretty simply in Python. The order of steps needed is as follows:
1. Calculate all daily returns.
2. Sort these returns from least to greatest.
3. Based on a given confidence level, return the corresponding percentile return. In other words, if we want to calculate daily VaR at a 95% confidence level and we are using 100 data points, the 5th smallest return of that sample would be considered our 95% VaR.

Let's visualize this first with a histogram using Bitcoin.

```python
start = datetime.date(2016, 1, 1)
end = datetime.date(2021, 11, 28)
# end = datetime.date.today()
try:
    prices = web.DataReader(["BTC-USD"], "yahoo", start, end)["Adj Close"]
except:  # noqa E722
    # If there are connectivity issues, use backup data
    prices = pd.read_pickle("data/btc-usd.pkl")

returns = prices.pct_change()
returns = returns.rename(columns={"BTC-USD": "Bitcoin"})
returns = returns.dropna()
```

```python
sns.histplot(data=returns)
```

It may be a little hard to see, but the graph shows a lot more to the left of 0 than to the right of 0, indicating there may have been some big losses over the last 5 years. Let's calculate the historical VaR from this data.

We need to can use numpy's *percentile* method in order to easily calculate this for us. Using this function allows us to skip the sorting step as it is already factored into the logic. We can define a function below in order to look at various confidence intervals. This function `getHistoricalVar` takes two arguments:
1. a series of daily returns
2. a confidence level, 95 for example, would correspond to 95% confidence

```python
def getHistoricalVar(returns, confidenceLevel):
    var = 100 * np.percentile(returns, 100 - confidenceLevel)
    print(
        "With %.2f%% percent confidence, we can say the most our portfolio will lose in a day is %.3f%% using historical VaR"
        % (confidenceLevel, var)
    )
```

```python
getHistoricalVar(returns.Bitcoin, 95)
```

```python
getHistoricalVar(returns.Bitcoin, 99)
```

It can be seen after running the function that the greater we make our confidence level, the lower the Value at Risk will be. This is a useful tool when determining how much a financial asset can lose over a certain time period.

Using the historical method, if we have -10% as the 95% confidence VaR, it can be interpreted that 95% of the time, our asset shouldn't return lower than -10% in a single day. 

You may be wondering now, since we only use a 95% confidence level, what happens on those 5% of days where losses exceed -10%. We can use another handy metric, Conditional Value at Risk (CVaR), to deal with these situations.

###### 3.4.3. Conditional Value at Risk (CVaR)
CVaR is also commonly known as expected shortfall. To calculate this, we look at all of the daily returns that are lower than our Value at Risk and take the average of those values. It's as simple as that. We can index into our Python returns series in order to calculate it. Once, again we will write a function in order to calculate this with various parameters.


```python
def getHistoricalCVar(returns, confidenceLevel):
    var = np.percentile(returns, 100 - confidenceLevel)
    cvar = returns[returns <= var].mean()
    print(
        "With %.2f%% percent confidence VaR, our Expected Shortfall is %.2f%% using historical VaR"
        % (confidenceLevel, 100 * cvar)
    )
```

```python
getHistoricalCVar(returns.Bitcoin, 95)
```

The above can be interpreted that in the 5% of days where returns are less than our VaR, we can expect our return to average about -9%. This is another helpful tool when assessing the risk of an asset. Since these functions are defined now, we can quickly compare the Bitcoin results to a bond index, BLV. 

```python
start = datetime.date(2016, 1, 1)
end = datetime.date(2021, 11, 28)
# end = datetime.date.today()
prices = web.DataReader(["BLV"], "yahoo", start, end)["Adj Close"]
returns = prices.pct_change()
returns = returns.dropna()
```

```python
getHistoricalVar(returns.BLV, 95)
```

```python
getHistoricalCVar(returns.BLV, 95)
```

While Bitcoin's 95% VaR and CVaR over the last five years is about -6% and -9% respectively, the bond index, BLV, has -.93% and -1.5% for the same metrics. This goes to show how much more downside risk an asset like Bitcoin holds when compared to bonds.

With the historical method, we're using only values that actually occurred in our dataset. This may not always be the scientific method because what happened over the last five years may not reflect what will happen over the next five years. We need to explore all of our options in order to best understand the risk profile of our investments. This leads us to a different way to calculate VaR. 

In the first video of this lesson, we recap the definition of VaR and how to calculate it using the historical method.

```python
VimeoVideo("706655901", h="21ae7573c3", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/1_3Tz0fJAiAq_XS5q7kDE6vu4lKwVSyH6/view?usp=sharing)

###### 3.4.4. Parametric Method
Since Value at Risk essentially is derived using probabilities to determine potential losses, we can use a probability distribution to compute VaR here. In the standard variation, a normal distribution of returns is assumed in the standard case. Just keep in mind that we can use other distributions to calculate this, as will be shown in the second example with a t-distribution. 

Example:

Assume you have an account with a mean value of \$10,000 and an annual standard deviation of \$500 and normally distributed returns. We can find that the critical value of a 95% confidence interval of a normal distribution is 1.96. Given these parameters, we can estimate with 95% probability that the most we can lose or gain in a year is:

$500*1.96 = \$980$



Considerations for this method:

* If returns are not normally distributed, you will likely be underestimating the true Value at Risk. For example, many stocks have more outliers than the normal distribution would assume; this means the computed Value at Risk will be lower than what it is in actuality.
* Variance and covariance between return streams must be considered when computing VaR for a portfolio. Even if returns are normally distributed, the VaR calculation can still be thrown off if the estimated variances and covariances are incorrect. This can be further amplified if variances and covariances are changing over time.
* Models that allow variance to change over time (heteroskedasticity), display a greater degree of accuracy. Engle has argued that Autoregressive Conditional Heteroskedasticity (ARCH) and Generalized Autoregressive Conditional Heteroskedasticity (GARCH) models provide better forecasts of variance and, by extension, better measures of Value at Risk (Engel 157-168)
* This method breaks down whenever a portfolio has assets with a non-linear payoff structure, e.g., options.


###### 3.4.4.1. Implementing VaR - Parametric Method with Normal Distribution
To calculate VaR using the parametric method is to assume a normal distribution for our returns and pass in the mean and standard deviation of our data into the `norm.ppf` method. This is a percent point function and allows us to pass in a confidence interval along with a mean and standard deviation to compute VaR. Even though we discussed that stock returns are non-normal in a previous lesson, this method of VaR calculation is arguably still a more valuable estimate than just using historical returns and will give us greater flexibility when doing Monte Carlo simulations in the near future.

Let's use the AAPL data back to 2010 in order to calculate this. 

```python
start = datetime.date(2010, 1, 1)
end = datetime.date(2021, 11, 28)
# end = datetime.date.today()
prices = web.DataReader(["AAPL"], "yahoo", start, end)["Adj Close"]
returns = prices.pct_change()
returns = returns.dropna()

mean = returns.AAPL.mean()
std = returns.AAPL.std()
(100 * stats.norm.ppf(0.05, mean, std)).round(3)
```

This method gives us a 95% confidence VaR of -2.78%. We can compare it to the historical method using our previous function.

```python
getHistoricalVar(returns.AAPL, 95)
```

It's quite interesting to note that, in this case, the parametric VaR gives a slightly more conservative estimate of daily VaR by having a lower expected return.

###### 3.4.4.2 Implementing VaR - Parametric Method with T-distribution
We just need to define our degrees of freedom for this method, but besides that, we can plug in the same parameters from above into the t-distribution function. We will use four degrees of freedom in this case. The higher you make the degrees of freedom, the more conservative VaR estimate you will have.



```python
# degrees of freedom
dof = 4
tVaR = np.sqrt((dof - 2) / dof) * stats.t.ppf(0.05, dof) * std - mean
(100 * tVaR).round(3)
```

We would expect the results to be similar, but it is quite remarkable that the 95% VaR using a t-distribution matches with what we had using a normal distribution.

In the final video of this lesson, we show once again how to calculate VaR using the parametric method in Python.



```python
VimeoVideo("706655936", h="435573b3f4", width=600)
```

[Access video transcript here](https://drive.google.com/file/d/12HhJ2V31itS9f-AGXGl92LeUNEAAixeK/view?usp=sharing)

###### 3.4.5. Monte Carlo Simulation

This method runs a series of simulations, usually in the thousands, where each return stream is represented as a random variable. This variable can be taken from any probability distribution, which is great because that means it doesn’t necessarily assume the normal distribution. There is a lot of flexibility in choosing what kind of distribution to use. All the variables are then dollar-weighted and simulated to see what the total portfolio value is at the end of each run. These simulation returns are then sorted lowest to highest, and we can easily look to see what the Value at Risk is using similar computations to the historical method, except this time, we’re using simulated returns instead of historical returns. For example, if you ran a series of 1,000 simulations, you would look at the 50th lowest value to determine the VaR for a 95% confidence interval.



Considerations for this method:
* Estimations will not be effective if the probability distributions used to determine the random variables are incorrect. Many use past data to get an idea of what the probability distribution should be; this method at least allows some subjectivity to doing this.
* You can estimate VaR more effectively for portfolios containing options with this method versus the parametric method since Monte Carlo doesn’t assume a normal distribution of returns.


###### 3.4.6. Conclusion

Throughout this lesson, we've examined different methods to calculate downside risk metrics like Value at Risk and expected shortfall. These should help shape your risk preferences before you buy assets for your portfolio.

**References**

- Engle, R., 2001, Garch 101: The Use of ARCH and GARCH models in Applied Econometrics, Journal of Economic Perspectives, v15, 157-168.



#### M4. Options in python
##### crt2
  
SCENARIO  
You are bullish on company ABC and company XYZ. Suppose you have $2 million to invest.  
You consider four different investment strategies in the form of portfolios:  
Note that we assume the variances of ABC and XYZ are similar (say within 20% of each other) AND positively correlated.

Portfolio A  
Buy $1 million worth of ABC stock using cash.  
Buy $1 million worth of XYZ stocks using cash.

Portfolio B  
Buy $2 million worth of ABC stock using $1 million and borrowing $1 million.  
Buy $2 million worth of XYZ stock using $1 million and borrowing $1 million.

Portfolio C  
Buy call options on ABC stock expiring in 1 month, with strike $5 higher than ABC’s stock price. The cost of all these ABC options is not more than $500,000.  
Buy call options on XYZ expiring in 1 month, with strike $5 higher than XYZ’s stock price.  
The cost of all these XYZ options is not more than $500,000.

Portfolio D  
Sell put options on ABC expiring in 1 month, with strike $5 lower than ABC’s stock price.  
Sell put options on XYZ expiring in 1 month, with strike $5 lower than XYZs’ stock price.

###### Question 1

Which portfolio(s) are affected by higher-than-expected covariance? Give at least 2 reasons.

- If the stocks have high covariance, then undoubtedly they have high correlation
- If the stocks have perfect negative correlation, they they will have perfect high covariance.
- If the stocks have high covariance, this will affect option prices. However, the particular strikes will depend on the amounts

###### Q2
What happens to the option portfolios if the correlation between ABC and XYZ is 0? Describe effects on return and risk.
- The call options have lower expected return
- The call options have lower expected risk
- The options go out of the money because there is no longer correlation.

3. Excluding Portfolio D, which portfolio(s) has the potential to make more than 100%? Give at least 2 reasons.
- If the stock triples, it makes more than 100% whether leveraged or unleveraged
- If the stock increases, the cost of the call premium can be much less than 100%
- No portfolio can make more than 100% due to Dodd Frank regulatory requirements

1. For proper risk management, which of the portfolios should be hedged? Give at least 2 reasons.
2. What happens when you have both high volatility AND high correlation? Provide at least 2 arguments.
3. Which of the portfolios have a non-linear payoff? Give at least 2 reasons.


##### 4.1 Option payoff and strategies
required readings: functions in python , [python essentials](https://python-programming.quantecon.org/python_essentials.html#iterating): basic, skippable

> [!Note] reading time: 30min

In the previous module, we examined stocks and cryptocurrencies.  In this module, we will examine the use of Python to compute and visualize option payoffs and prices, from single options to multi-option strategies.

```python
import math

from optionprice import Option
```

###### 4.1.1 Options
In this lesson, we'll use a Python package called `optionprice`.  This has a function called `Option`. As you recall from Module 4 of Financial Markets, there are two fields that describe the type of option:
1. The type of option: **call** or **put**. In the Option function, this is specified by the argument `kind`
2. The style of exercise: European or American. In the Option function, this is specified with the `European` argument set to `True` or `False`.

There are also six numerical values that allow us to value the option:
1. Strike Level: k
2. Stock Price: s0
3. Time to expiration (here, this is given in calendar days): t
4. Volatility: sigma (which is annualized)
5. Risk-Free rate: r (which is annualized)
6. Dividend-Yield: dv (which is annualized)


Let's import the package and create an ATM European call option. The function Option helps us to do that. Notice that we have to specify all eight of these fields as arguments to the Option function.

```python
myCall = Option(
    european=True, kind="call", s0=100, k=100, t=30, sigma=0.20, r=0.05, dv=0
)
print(myCall)
```
- output: 
		Type:           European
		Kind:           call
		Price initial:  100
		Price strike:   100
		Volatility:     20.0%
		Risk free rate: 5.0%
		Start Date:     2022-09-13
		Expire Date:    2022-10-13
		Time span:      30 days

```python
type(myCall)
```

Similarly, to create a put, we merely need to change the type to put.
```python
myPut = Option(european=True, kind="put", s0=100, k=100, t=30, sigma=0.20, r=0.05, dv=0)
print(myPut)
```
If we want a single attribute, we can just query it from the option.

```python
myCall.european
myCall.k
myCall.kind  # number 1 for calls, 2 for puts 
myCall.s0
myCall.sigma
myCall.r
```

###### 4.1.2. Getting the options price
As you first learn options, be sure to distinguish the price from the payoff. The option's payoff is known precisely at expiration. Indeed, the payoff only applies at an option's expiration. The option's price applies at every time from inception up until the payoff.
Clearly, pricing is a much more difficult undertaking than figuring out the payoff.

Let's learn to use pricing functions that are part of this Python module.
It is one thing to use a function to get an option's price.  
It's another to understand what that function does.
Keep in mind that there is an entire course, Derivative Pricing, that will provide the mathematics and intuition behind the pricing of these securities.
For now, let's just outline that there are two methods for pricing an option:
1. Analytic
2. Numeric

An analytic method uses mathematics, such as stochastic calculus, Fourier transforms, stochastic dominance, and other analytical methods, to develop a pricing equation.
A numeric method uses numerical or computational techniques, such as discretization (binomial trees, finite difference methods, finite element methods) or randomization (Monte Carlo sampling, agent-based models) to develop a numerical method through which the option price can be found.

Let's run one example of an analytical model called Black Scholes.
Let's run two examples of numerical models: binomial tree and Monte Carlo.

In the following code excerpt, we price our call three different ways:
1. Analytically with the Black Scholes model.
2. Numerically with a binomial tree.
3. Numerically with a Monte Carlo simulation.

```python
callBS = round(myCall.getPrice(), 4)
callBT = round(myCall.getPrice(method="BT", iteration=5000), 4)
callMC = round(myCall.getPrice(method="MC", iteration=500000), 4)
[callBS, callBT, callMC]
```

As we can see, the prices are fairly close. This is to be expected. If we use the methods properly, the prices should not vary depending on which method we use.  Keep in mind that the numeric methods (e.g., Monte Carlo simulation) require a sufficiently high number of iterations so that they can converge to the proper solutions.
Now that we've priced the call option, let's price the put using these three methods.
```python
putBS = round(myPut.getPrice(), 4)
putBT = round(myPut.getPrice(method="BT", iteration=5000), 4)
putMC = round(myPut.getPrice(method="MC", iteration=500000), 4)
[putBS, putBT, putMC]
```

Again, we have good agreement among the prices. Intentionally, we did not run a high number of iterations for the Monte Carlo method to illustrate how the results can be slightly off.

Whenever we compute option prices, we should get in the habit of checking our prices using put-call parity. Module 4 of Financial Markets showed us that:
$call - put = S - Ke^{-(rt)}$  
Let's check this for ourselves.  
Going forward, we'll use the option prices from the analytical form.
First, let's calculate the left-hand side of the put-call parity equation.
```python
c = callBS
p = putBS
round(c - p, 6)
```
```python
S = 100
K = 100
r = 0.05
t = 30 / 365
round(S - K * math.exp(-r * t), 6)
```
The difference is small, likely due to rounding and not an actual arbitrage.  Ensuring put-call parity holds means that our calculations have a consistency. Whenever you are asked to compute option prices, always check put-call parity. It avoids your making a careless mistake.
For any questions you see on CRTs or GWPs, be sure to apply put-call parity.
As you can see, it is computationally very easy.
Conceptually, it is quite intriguing.
It says that at any given time, a relationship among three different markets exists.
The 3 markets are:
1. options market: calls and puts
2. stock market: underlying stock
3. bond market: a risk-free bond whose term is the option's expiration 

Now that we've seen some option payoffs and prices, let's continue our applied treatment of options by examining some of the strategies.





\ 
###### 4.1.3 Option strategies
We've been using an option package called `optionprice` for creating options and examining their prices.  In fact, there are several Python packages available for handling options. We now turn to one called `opstrat` that is useful for illustrating option strategies.
```python
import opstrat as op
```
Let's graph the call option's payoff.  
Let's assume that we paid nothing for the option to see its payoff.
The function single_plotter will take the following arguments:
1. spot: current stock price
2. strike: strike level
3. op_type: option type, either "c" for call or "p" for put
4. tr_type: side of trade, either "b" for buying/long or "s" for selling/short
5. op_pr: option price
```python
op.single_plotter(spot=100, strike=100, op_type="c", tr_type="b", op_pr=0)
```
Remember, that the option's payoff you see in books tends to neglect the premium you paid. Once you buy an option, you can not lose any additional money. However, long option positions can lose money if the options expires OTM.

Since we bought the call, we paid the $2.49 premium. Let's redraw the payoff taking the premimum into account.
```python
op.single_plotter(spot=100, strike=100, op_type="c", tr_type="b", op_pr=callBS)
```
Clearly, the option is unprofitable not only if the stock price is below the strike level but also if the stock price is less than the sum of the strike and premium. So even if the option ends up ITM, we have to cover the cost of the premium to have a positive P&L.  

In fact, we can compute a break-even stock level for a call option. The **break-even stock level** is the price at which the option holder has a net payoff of 0.
$$Call Break-Even Stock Level = Strike + Option Premium$$
In our example, this is 
$$Call Break-Even Stock Level  = 100 + 2.49
                             = 102.49 $$

*The break-even is where the stock payoff crosses the x-axis.*
Let's see the seller's payoff.
```python
op.single_plotter(spot=100, strike=100, op_type="c", tr_type="s", op_pr=callBS)
```
Likewise, the seller's payoff for a call can be positive so long as the stock price exceeds the strike less the premium. To remind us that options are a zero-sum game, let's examine the two payoff diagrams together.
```python
op.single_plotter(spot=100, strike=100, op_type="c", tr_type="b", op_pr=callBS)
op.single_plotter(spot=100, strike=100, op_type="c", tr_type="s", op_pr=callBS)
```


###### 4.1.4 Zero Sum Games
Options are a zero sum game.  The buyer of the call has a payoff that is the mirror image of the seller's payoff.
Everywhere the long position is profitable (green), the seller is unprofitable (red).  
Everywhere the long position is unprofitable (red), the seller is profitable (green).

Notice the non-linearity in each graph.  
The strike is where the change in slope occurs.  
To one side of the strike, the payoff is a flat line.
To the other side of the strike, the payoff is 45 degrees from the x-axis.
For long positions, the slope is upwards.
For short positions, the slope is downwards.
Note that long calls have unlimited upside; therefore, short calls have unlimited downside.
As this graph reminds us, it is prudent to hedge all short calls.

For completion, let's compute the break-even for puts and then graph long and short puts.

Put Break Even Stock Level = Option Strike - Premium
                           = 100 - 2.08
                           = 97.92
The put break-even stock level is where the option payoff crosses the x-axis.

```python
op.single_plotter(spot=100, strike=100, op_type="p", tr_type="b", op_pr=putBS)
op.single_plotter(spot=100, strike=100, op_type="p", tr_type="s", op_pr=putBS)
```
We see the same story: 
The long and short payoffs are mirror images of each other, reflecting the zero-sum game of options.
At any given stock price, one side has a profit (shown in green) and the other side has a loss (shown in red).
Each graph is non-linear.  
The slopes are still 45 degrees; however, for the long position, the slope is negative,
and for the short position, the slope is positive.
Note: Even if the option is ITM, the buyer still needs to cover the cost of the premium for the option to be profitable. Also, it is relatively easy to lose 100%.

###### 4.1.5. Option Combinations
Another strategy involves trading volatility.  
Suppose we are unsure of the direction but believe that volatility will increase.
We can buy a call and a put at the same strike. This is an option straddle.
Remember, you don't have to get the direction of the underlying right.
```python
myCall = {"op_type": "c", "strike": 100, "tr_type": "b", "op_pr": 2.49}
myPut = {"op_type": "p", "strike": 100, "tr_type": "b", "op_pr": 2.09}
op_list = [myCall, myPut]
op.multi_plotter(spot=100, spot_range=10, op_list=op_list)
```
Notice the position is unprofitable unless the price moves about \$4.58 in either direction.
Option strategies that involve buying two options mean that the position has to cover the cost of two premiums.
Let's look at some less expensive ways to execute volatility strategies.
Instead of only buying two options, let's also sell two options.
Suppose we believe the stock will only move \$10.
We can sell a put at a strike of 90. We can sell a call at a strike of 110.
Let's price each one.
```python
myCall2 = Option(
    european=True, kind="call", s0=100, k=110, t=30, sigma=0.20, r=0.05, dv=0
)
myPut2 = Option(european=True, kind="put", s0=100, k=90, t=30, sigma=0.20, r=0.05, dv=0)
callBS2 = round(myCall2.getPrice(), 4)
putBS2 = round(myPut2.getPrice(), 4)
print([callBS2, putBS2])
```
Now we construct an option strategy with four options.
```python
myCall = {"op_type": "c", "strike": 100, "tr_type": "b", "op_pr": callBS}
myPut = {"op_type": "p", "strike": 100, "tr_type": "b", "op_pr": putBS}
myCall2 = {"op_type": "c", "strike": 110, "tr_type": "s", "op_pr": callBS2}
myPut2 = {"op_type": "p", "strike": 90, "tr_type": "s", "op_pr": putBS2}
op_list = [myCall, myPut, myCall2, myPut2]
op.multi_plotter(spot=100, spot_range=20, op_list=op_list)
```


###### 4.1.6. Comparing Volatility Strategies
Plan A:  Buy a straddle.   Cost: \$4.59.

Plan B:  Buy an iron butterfly. \$(4.59 - 0.20) =\$4.39

The iron butterfly involves a long straddle (buying a call and put at the same strike) and also a short straddle (selling an OTM put at a low strike and selling an OTM call at a high strike).
The iron butterfly gives up a potential upside for a rebate of the option premium.
Individually, we have 
1 short put at 90
1 long call at 100
1 long put at 100
1 short call at 110

The long iron butterfly trader is conservatively long volatility: even if volatility increases significantly, the long iron butterfly's P&L is capped at about \$5.  That's because the long call's gain past \$110 level is offset by the loss in the short call at strike 110.

The long straddle trader is aggressively long volatility: the more volatility, the more their P&L.

For example, if the final stock price is 115, then 
short put(90)   =  0
long put(100)   =  0
long call(100)  = 15
short call(110) = -5
Net Profit =     \$10

Indeed,\$10 is the maximum revenue. When the \\$4.39 cost is taken into consideration, the maximum P&L is \$10 - \$4.39 = \$5.61


###### 4.1.7. Saving
Graphs are good for visualizing. Sometimes, the intended consumer of the graph is just the programmer/analyst, as they confirm their findings. Other times, some graphs are meant for the traders, portfolio managers, or risk managers.

Python makes it easy to save plots. Here's a simple function to save the plot as a .jpeg file.
```python
op.multi_plotter(
    spot=100, spot_range=20, op_list=op_list, save=True, file="myOptionStrategy.jpeg"
)
```
\ 
###### 4.1.8. Conclusion

In this lesson, we used two Python packages, `optionprice` and `opstrat`, to create and visualize options and their strategies. We examined the two methods of pricing options: analytical and numerical.  We examined option strategies that use single options and multiple options.  We related the level of bullishness or bearishness to the type of option strategy using combinations of calls and puts at different strikes.  In the next module, we examine the sensitivities of options to their underlying.



##### 4.2 Option dependencies

|                     |                                                                             |
|:------------------- |:--------------------------------------------------------------------------- |
| **Reading Time**    | 40-60 minutes                                                               |
| **Prior Knowledge** | Python package opstrat, Python package optionprice, ATM, ITM, OTM, Analytic |
| **Keywords**        | Option Dependencies, Early Exercise, Stochastic Dominance                   |

*In the previous lesson, we covered the basics of option payoffs for single and multiple option strategies. In this lesson, we examine **how options depend on their various components**: stock prices, expiry times, volatilities, and interest rates.*  

```python
import matplotlib.patches as mpatches
import pandas as pd
from matplotlib import pyplot as plt
from optionprice import Option
```
###### 4.2.1 Creating objects
Recall from the previous lesson that we used the Python package optionprice.
This has a function called Option. We can use that function to create vanilla calls and puts.
```python
myCall = Option(
    european=True, kind="call", s0=100, k=100, t=30, sigma=0.20, r=0.05, dv=0
)
print(myCall)
round(myCall.getPrice(), 4)
```
| option char    | key value  |
| -------------- | ---------- |
| Type           | European   |
| Kind           | call       |
| Price initial  | 100        |
| Price strike   | 100        |
| Volatility     | 20.0%      |
| Risk free rate | 5%         |
| start date     | 2022-08-29 |
| expire date    | 2022-09-28 |
| Time span      | 30 days    |
| ---            | ---        | 
| **Output**     | **2.4934** |
While this was helpful to see payoffs, we want to use more common data structures to study the features of options. In this lesson, we'll use data frames, lists, and dictionaries. You should be familiar with all these data structures. Be sure to complete the assigned reading for this lesson. Reading the chapters in *Quantitative Economics* can refresh your memory with the creation, subsetting, and usage of data frames.

Let's get ready to save a bunch of stock prices and the corresponding option prices in a pandas data frame. We'll create a data frame with a column called Stock and a column called Option.
```python
df = pd.DataFrame(columns=["Stock", "Option"])
```

###### 4.2.2 Comparing option prices to stock prices
Now, let's define a wrapper function to the opstrat function Option. We want to price an option using different stock prices, but keeping all other variables the same.
Our `CallOptionVsStock` function will use default values for everything except the stock price.
It is not our intent to write a very general function, but just one that can help create plots that show how the option price varies with the underlying stock price.
```python
def CallOptionVsStock(S, k=100, t=30, sigma=0.20, r=0.05, dv=0):
    myCall = Option(european=True, kind="call", s0=S, k=k, t=t, sigma=sigma, r=r, dv=0)
    return myCall.getPrice()
```
This is an easy function to understand. We give it a descriptive, albeit somewhat long, function name that indicates we will be able to price options given stock prices.

Notice that we use default for the other five variables: strike, expiry, volatility, risk-free rate, and dividend yield. The function merely passes these arguments to the `opstrat` function `Option`. The function then returns the price of that option using the analytical method.

We'll define two more simple functions. First, we'll define a function, `getCallPayoff`, that determines the call's payoff, which is the non-negative value of S-K or 0.
Second, we'll define a function, `addCallPayoff`, that will add the call payoff to the price chart. Note, in `addCallPayoff`, we take advantage of the Python function map, by mapping the `getCallPayoff` function over each of the stock prices, and storing the results in a list of option prices. Just like data frames, these data structures should be familiar. Please see the required reading on lists in the textbook.
```python
def getCallPayoff(S, K=100):
    if S > K:
        return S - K
    return 0


def addCallPayoff(K, rng=21):
    stockP = range(K - 21, K + 21)
    OptionP = list(map(getCallPayoff, stockP))
    plt.plot(stockP, OptionP, linestyle="dotted")
```
Next, we create a list of the stock prices.  To create a smooth graph, we would like to have, say, about 40 different stock prices.  So we'll create a sequence of stock prices that span values centered around the strike level. Suppose the strike is 90.  We'll have stock prices at 70, 71, 72, ..., 90, 91, ..., 108, 109, and 110.  Likewise, we'll initialize a list of the option prices. Again, we make good use of the map function by mapping the `CallOptionVsStock` function over each of the stock prices and storing the results in a list of option prices.
```python
StockPrices = list(range(80, 120))
OptionPrices = list(map(CallOptionVsStock, StockPrices))
```
It's time to graph. Let's use the `matplotlib` package. Please read the chapter in *Quantitative Economics* to understand this extremely useful package for graphing.
```python
plt.plot(StockPrices, OptionPrices)
plt.title("Call Option vs. Stock Price")
plt.xlabel("Stock Price")
plt.ylabel("Call Price")
addCallPayoff(100)
```
> [!Note] Output
> ![](https://i.imgur.com/ICGlCuz.png)

Be sure to distinguish between the two curves. The blue line represents the option's price. The price applies during the option's lifetime. The orange line represents the option's payoff. The payoff applies only at the option's expiration.

Let's repeat the same process for puts. First, we'll define functions for `PutOptionsVsStock`, `getPutPayoff`, and `addPutPayoff`.

```python
def PutOptionVsStock(S, k=100, t=30, sigma=0.20, r=0.05, dv=0):
    myPut = Option(s0=S, european=True, kind="put", k=k, t=t, sigma=sigma, r=r, dv=0)
    return myPut.getPrice()


def getPutPayoff(S, K=100):
    if S < K:
        return K - S
    return 0


def addPutPayoff(K, rng=21):
    stockP = range(K - 21, K + 21)
    optionP = list(map(getPutPayoff, stockP))
    plt.plot(stockP, optionP, linestyle="dotted")
```
Now we can reuse the list of the stock prices, ranging 20% from the strike.
```python
StockPrices = list(range(80, 120))
OptionPrices = list(map(PutOptionVsStock, StockPrices))
from matplotlib import pyplot as plt

plt.plot(StockPrices, OptionPrices)
plt.title("Put Option vs. Stock Price")
plt.xlabel("Stock Price")
plt.ylabel("Put Price")
addPutPayoff(100)
```
![](https://i.imgur.com/DiM4QlN.png)

```python
myCall = Option(
    european=True, kind="call", s0=100, k=100, t=30, sigma=0.20, r=0.05, dv=0
)
print(myCall)
round(myCall.getPrice(), 4)
```
![](https://i.imgur.com/PUiMte7.png)


###### 4.2.3 Time value of Calls and puts
In each of these plots, the orange dotted line represents the option's payoff. This is the value of the option at expiration. The blue line represents the option's price.
There is a subtle point to notice regarding the relative location. When we are out of the money, the blue line exceeds the option payoff. Why?

Recall from Module 4 in Financial Markets that an option's value equals its intrinsic value plus its time value.
Out-of-the-money options do not have intrinsic value.  
All their value comes from having more time.
Generally, more time means more chances to get in the money!

However, look at the difference when in the money.
In fact, the effect will be even more pronounced if we increase the time to expiration.

```python
def CallOptionVsStock(S, k=100, t=180, sigma=0.20, r=0.05, dv=0):
    myCall = Option(european=True, kind="call", s0=S, k=k, t=t, sigma=sigma, r=r, dv=0)
    return myCall.getPrice()


OptionPrices = list(map(CallOptionVsStock, StockPrices))
plt.plot(StockPrices, OptionPrices)
plt.title("6-month Call Option vs. Stock Price")
plt.xlabel("Stock Price")
plt.ylabel("Call Price")
addCallPayoff(100)
```
![](https://i.imgur.com/puctOfX.png)

###### 4.2.4 Time value can hurt European puts
###### 4.2.5 Difference between european and American puts
###### 4.2.6 Time value of Options
###### 4.2.7 Option prices for different volatilities
###### 4.2.8 option prices for different interest rates
###### Conclusion











##### 4.3. OPTION DATA AND ATTRIBUTES

|  |  |
|:---|:---|
|**Reading Time** |  30- 40 minutes |
|**Prior Knowledge** |Calls and Puts, Option Parameters, Option Payoffs, Option Prices, Option Strategies    |
|**Keywords** |Open Interest, Put Call Parity Ratios, Bid-Ask Spread    |


---

*In the previous lesson, we studied how options depend on the underlying parameters. In this lesson, we'll import option data: real-time pricing and attributes. We'll see the types of metadata available and how they relate to each other and option prices.*

```python
import datetime

import matplotlib.patches as mpatches
import matplotlib.pyplot as plt
import pandas as pd
import yfinance as yf
```

###### 4.3.1. Handling Option Complexity
As an asset, options are N times more complicated than stocks
(where N > 1 and is left up to you to determine the effects of 
non-linearity, leverage, kurtosis, hedging, model risk, and other issues).

One of the reasons options are more complicated than stocks is the abundant array of options to choose from.

Suppose you are bullish on Netflix (symbol = NFLX).
(You may like the original series, and the wide variety of films, television series, and documentaries.)
You can decide to buy the stock.
But what if you decide to buy the option?
Well, you will soon realize there are a multitude of options.

So, the question is better phrased as, what if you decide to buy an option? Or even a set of options because some strategies involve multiple options?

Remember, unless you are a volatility trader, when you trade options you need to get three things correct:
1. Direction: based on what you choose between calls or puts
2. Size: based on what you choose among strike levels
3. Timing: based on what you choose among different expirations
Let's count how many there are of each!

###### 4.3.2. Importing Option Data

First, we'll refer to a function that helps not only to import option chain data but also to categorize and store it neatly.

The function uses the Python package `yfinance`.
It works with pandas Data Frames.
It is used for loops, basic subsetting, and even lambda functions.
Please do the required reading to ensure your knowledge of Python is complete and up-to-date.


```python
# https://medium.com/@txlian13/webscrapping-options-data-with-python-and-yfinance-e4deb0124613


def options_chain(symbol):

    tk = yf.Ticker(symbol)
    # Expiration dates
    exps = tk.options

    # Get options for each expiration
    options = pd.DataFrame()
    for e in exps:
        opt = tk.option_chain(e)
        opt = pd.DataFrame().append(opt.calls).append(opt.puts)
        opt["expirationDate"] = e
        options = options.append(opt, ignore_index=True)

    # Bizarre error in `yfinance` that gives the wrong expiration date
    # Add 1 day to get the correct expiration date
    options["expirationDate"] = pd.to_datetime(
        options["expirationDate"]
    ) + datetime.timedelta(days=1)
    options["dte"] = (
        options["expirationDate"] - datetime.datetime.today()
    ).dt.days / 365

    # Boolean column if the option is a CALL
    options["CALL"] = options["contractSymbol"].str[4:].apply(lambda x: "C" in x)

    # options[['bid', 'ask', 'strike']] = options[['bid', 'ask', 'strike']].apply(pd.to_numeric)
    options[["bid", "ask", "strike", "volume", "Implied Volatility"]] = options[
        ["bid", "ask", "strike", "volume", "Implied Volatility"]
    ].apply(pd.to_numeric)
    options["mark"] = (
        options["bid"] + options["ask"]
    ) / 2  # Calculate the midpoint of the bid-ask

    # Drop unnecessary and meaningless columns
    options = options.drop(
        columns=[
            "contractSize",
            "currency",
            "change",
            "percentChange",
            "lastTradeDate",
            "lastPrice",
        ]
    )

    return options
```

###### 4.3.3. Options Come in a Variety of Expiration Dates

Now, let's count the number of different expiration dates.

```python
from yahoo_fin import options

nflx_dates = options.get_expiration_dates("nflx")
len(nflx_dates)
```

As of the time we ran this code, we have 15 different expiration dates.
(You may have a different number.)
Let's see how varied the dates are.

```python
list(nflx_dates)
```

We notice that there are about six expiration dates that occur in 1-week intervals: 1-week options, 2-week options, 3-week options, 4-week options, 5-week options, and 6-week options. Then, they appear to be monthly, typically expiring the third Friday of the month. Then, there appear to be 1-year and perhaps even 2-year options. When you're bullish on Netflix, you will certainly want to know if you think the stock will increase within a few weeks for short-dated options or over longer periods of time for the longer-dated options.

Next, let's get all the calls.

```python
try:
    callsNflx = options.get_calls("nflx")
except:  # noQA E722
    callsNflx = pd.read_csv("nflx_calls.csv")

list(callsNflx.columns)
```

```python
callsNflx.head()
```

```python
callsNflx.dtypes
```

There's lots of information available on options. Keep in mind the function used to collect them dropped some other columns that are not shown in this list.  The data we have on options includes:
1. The Contract Name. This is similar to a CUSIP, ISIN, SEDOL, ticker, or identifier.
2. The Last Trade Date. This is the date of the most recent activity. If an option is inactive, you may encounter a date from a long time ago.
3. Strike. The strike level of the option.
4. Last Price. Trades in the market occur at a specific price. This is the most recent one.
5. Bid. Market participants willing to buy agree to do so at the bid price. This is a quote rather than a trade.
6. Ask. Market participants willing to sell agree to do so at the ask price. This is also known as the offer price.  Again, this is quote data rather than trade data.
Just to clarify: Last Price refers to data that actually traded. Bid and Ask refer to price levels offered by market makers to buy and sell, respectively.
7. Change. This gives the change in price on the day.  Positive change means prices increased on the day; negative changes mean prices decreased.
8. % Chg. This gives the percent change. This is usually more helpful than the level change because it is scaled relative to the option's price.
9. Volume. This gives the number of contracts that traded today.
10. Open Interest. This gives the number of contracts outstanding for that particular option. This is sometimes confused with volume.  
11. Implied Volatility. Of all the option's inputs, volatility is the most important. The other numeric inputs, stock price, strike level, risk-free rate, and dividend yield, are easily observed in the market. The volatility is the one number that is key to the option's price. If we are given the price of an option, we can imply what volatility was used to achieve that price. This means that we had agreement on all the other parameters. When we imply the volatility from the option's price, we compute the implied probability.

Let's start counting.

###### 4.3.4. Options Come in a Variety of Strikes

How many different strike levels are there?

```python
numStrikes = callsNflx["Strike"].count()
numStrikes
```

This great number of strikes is bewildering.  It can make the specific selection of an option's strike a daunting process.  Fortunately, if we  investigate the strikes, we see a lot of them are deep OTM or deep ITM.

```python
callsNflx["Strike"]
```

At the time of writing, NFLX is 340.  However, you can find strikes ranging from 10 to 1050. The overwhelming majority of these are OTM.

###### 4.3.5. Options Have Different Amounts of Open Interest

An easy way to filter options is to examine their open interest.
The open interest refers to the number of contracts in existence.  
Unlike stocks, the open interest of options can change moment by moment.
To issue a new option, a buyer and seller simply come to terms.  
Effectively, there is as much supply as the sellers are willing to write.
(Practically, they will want to have access to the underlying so they can properly hedge their exposures).
Many of the strikes we examined have little or no open interest.
That means, market makers are offering these securities, but there have been no contracts written yet.  Perhaps the combination of being far from the strike and the time to expiration being too soon means that there is little interest in hedging or speculating with these options.

```python
callStrikes = list(callsNflx["Strike"])
callOpenInt = list(callsNflx["Open Interest"])
```

```python
plt.plot(callStrikes, callOpenInt)
plt.xlabel("Call Strikes")
plt.ylabel("Call Open Interest")
```

```python
plt.xlim([300, 500])
plt.plot(callStrikes, callOpenInt)
plt
plt.xlabel("Strike")
plt.ylabel("Open Interest")
```

A handful of options have the vast majority of open interest.  This means that when we move far from the strike, we see much less open activity.

Options with low amounts of open interest are not liquid.  Recall from Financial Markets that we studied liquidity.  Think of each option as a vendor at an outdoor market.  Think of open interest as the number of customers who bought fruits and vegetables at this market.  
A vendor with no customers is like an option with insufficient open interest.
There are little to no option contracts written.
Therefore, the markets are illiquid.  

Unlike our outdoor market, the options market allows participants to buy and sell. For illiquid securities, there is likely going to be a large bid-ask spread. Those options will be unfavorable to trade due to the illiquidity.

So we have lots of calls. We could run through the same exercise for puts, but the results should be similar.  There would be a lot of strikes.

```python
try:
    putsNflx = options.get_puts("nflx")
except:  # noqa E722
    putsNflx = pd.read_csv("nflx_puts.csv")
```

```python
for index in putsNflx.index:
    if "-" == putsNflx["Volume"][index]:
        putsNflx.loc[index, "Volume"] = 0
numPutStrikes = putsNflx["Strike"].count()
numPutStrikes
```

```python
putStrikes = list(putsNflx["Strike"])
putOpenInt = list(putsNflx["Open Interest"])
plt.plot(putStrikes, putOpenInt)
plt.xlabel("Put Strikes")
plt.ylabel("Put Open Interest")
```

Rather than plot all of the open interest amounts, let's just focus on the options near the current stock price.

```python
plt.xlim([300, 500])
plt.plot(putStrikes, putOpenInt)
plt.xlabel("Strike")
plt.ylabel("Open Interest");
```

###### 4.3.6. Cleaning Volume

There's a problem with volume.  Contracts with no volume used '-' instead of 0.
This data cleaning is an important step.  
The following for loop will replace instances of '-' with a 0.

```python
for index in callsNflx.index:
    if "-" == callsNflx["Volume"][index]:
        callsNflx.loc[index, "Volume"] = 0
```

Now we convert the column to float.

```python
callsNflx.Volume = callsNflx.Volume.astype(float)
```

Let's do the same for puts: replace dashes and then convert to float.

```python
for index in putsNflx.index:
    if "-" == putsNflx["Volume"][index]:
        putsNflx.loc[index, "Volume"] = 0

putsNflx.Volume = putsNflx.Volume.astype(float)
```

Let's create simple lists so we can add them to a data frame later.

```python
callVolume = list(callsNflx["Volume"])
putVolume = list(putsNflx["Volume"])
```

###### 4.3.7. Diving Deeper into Open Interest

Let's dive deeper into open interest.
We can start by graphing open interest for calls and puts across different strikes.

```python
callDf = pd.DataFrame()
callDf["Strikes"] = callStrikes
callDf["CallOpenInt"] = callOpenInt
callDf["CallVolume"] = callVolume
putDf = pd.DataFrame()
putDf["Strikes"] = putStrikes
putDf["PutOpenInt"] = putOpenInt
putDf["PutVolume"] = putVolume
```

Now let's merge the two data frames for strikes near the current stock price.

```python
df = callDf.merge(putDf)
df = df[(df["Strikes"] > 300) & (df["Strikes"] < 400)]
list(df.dtypes)
```

```python
plt.xlim([300, 400])
plt.plot(list(df["Strikes"]), list(df["CallOpenInt"]))
plt.plot(list(df["Strikes"]), list(df["PutOpenInt"]))
plt.title("Open Interest vs. Strike Level")
plt.xlabel("Strike")
plt.ylabel("Open Interest")
patch1 = mpatches.Patch(color="blue", label="Call Open Interest")
patch2 = mpatches.Patch(color="orange", label="Put Open Interest")
plt.legend(handles=[patch1, patch2])
```

What is so interesting about open interest? 
Meaningful data ratios derive from these open interest numbers.
Let's define one.
Put Call Ratio of Open Interest = Put Open Interest / Call Open Interest

Read the required reading to see how useful Open Interest can be in predicting the direction of a stock.
How can we define a function for put call ratio?

```python
def PutCallRatioOpenInterest(df):
    pcroi = sum(df["PutOpenInt"]) / sum(df["CallOpenInt"])
    return round(pcroi, 4)


PutCallRatioOpenInterest(df)
```

```python
def PutCallRatioVolume(df):
    pcv = sum(df["PutVolume"]) / sum(df["CallVolume"])
    return round(pcv, 4)


PutCallRatioVolume(df)
```

###### 4.3.8. Handling Python Data Structures

```python
info = {}
for date in nflx_dates:
    info[date] = options.get_options_chain("nflx")
type(info)
```

Notice the familiar data structures.  Info is a dictionary.  It is keyed by the expiration date.

```python
exp_dates = list(info.keys())
exp_dates
```

Let's extract one key by extracting one date.

```python
z1 = info[exp_dates[0]]
type(z1)
```

```python
z1.keys()
```

We still have a dictionary. Let's get the calls.

```python
z2 = z1["calls"]
type(z2)
```

Now, we have a data frame.

```python
z2["Strike"].count()
z2.columns
```

```python
z3 = z2[(z2["Strike"] >= 330) & (z2["Strike"] <= 350)]
z3
```

Let's compute the bid-ask spread.

```python
# Compute the bid-ask spread
z4 = z2[(z2["Strike"] >= 300) & (z2["Strike"] <= 400)]
plt.plot(list(z4["Strike"]), list(z4["Ask"] - z4["Bid"]))
plt.title("Bid-Ask Spread as a Function of Strike")
plt.xlabel("Strike")
plt.ylabel("Bid-Ask Spread")
```

When we are OTM, the bid-ask spread is considerably higher.
OTM calls tend to have very low liquidity.


###### 4.3.9. Conclusion
In this lesson, we introduced Python functions to import option data. Unlike stock data, option data is messier because there are many options for a single stock: calls and puts, different strikes, and different expiration times. In the next lesson, we'll look at option strategies.




##### 4.4. **COMPARING LEVERAGED STRATEGIES**

|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** |Option payoffs, Option pricing using Python, Option strategies, P&L concepts, Leverage     |
|**Keywords** |Bull Spread    |
> [!Caution] Excel
> This module uses `nflx_calls` excel sheet. This is copied in local. 
> Same has been used earlier also.

---


*In the previous module, we showed how to get option data imported into Python. This data included not only price, but bid and ask levels, volume and open interest, and implied volatility, among other fields. In this lesson, we compare different ways to enact a bullish trade, using different combinations of stocks, options, and leverage.*

###### 4.4.1. Importing Real-Time Data

In this lesson, let's get some real-time pricing of stocks and options.

```python
import math

import opstrat as op
import pandas as pd
import pandas_datareader as pdr
from optionprice import Option
```

```python
# https://analyticsindiamag.com/top-python-libraries-to-get-historical-stock-data-with-code/
# Alpha vintage
myApiKey = "O2ZMKAVEVDVQ4RWF"

ts = pdr.av.time_series.AVTimeSeriesReader("NFLX", api_key=myApiKey)
df = ts.read()
df.index = pd.to_datetime(df.index, format="%Y-%m-%d")
# plotting the opening and closing value
df[["close"]].plot()
```

###### 4.4.2. Overview of Strategies

Suppose we have \$100,000 to invest in a bullish strategy for Netflix.

1. Buy stock using cash.
2. Buy stock on margin.
3. Buy a call option.
4. Buy a bull spread (buy call at K, sell call at K+d).

How much data do we need?
In all cases, we certainly need to know the current stock price, specifically the ask price.
For the cash stock strategies, all we need to know is the current ask price.
For the financed stock strategy, we also need to know the financing rate.
For the option strategies, we need to know the option chain.

###### 4.4.3. Stock Strategy

First, we'll begin with the stock strategy.
Let's suppose you buy NFLX at 333, and you plan to sell it at 345.

```python
nflx0 = 333
nflx1 = 345
```

```python
def BuyShares(capital, sharePrice):
    return math.floor(capital / sharePrice)
```

```python
myCapital = 100000
numShares = BuyShares(myCapital, nflx0)
numShares
```

```python
def CalculatePnL(sellPrice, buyPrice, numShares):
    return round(numShares * (sellPrice - buyPrice), 2)
```

You can buy 300 shares

```python
cashStockPnL = CalculatePnL(nflx1, nflx0, numShares)
cashStockPnL
```

You made \$3,600. Let's write a quick function to compute percent return.

```python
def CalculatePctReturn(fundsOut, fundsIn):
    return round(fundsOut / fundsIn * 100, 2)
```

```python
CalculatePctReturn(cashStockPnL, myCapital)
```

The stock increased (345-333)/333 = 3.6%
You bought the stock cash.
Your investment earned 3.6%
This is an example of no leverage.
All the other examples involve some form of leverage.
Consequently, they will have higher returns due to that leverage.

###### 4.4.4. Financed Stock Strategy

Let's write a short function to calculate functions for buying stocks with borrowed funds.

```python
def FinanceShares(capital, sharePrice, financePct=0.50):
    return BuyShares(capital / financePct, sharePrice)
```

```python
# We can finance 50% of our purchase.
numLvgShares = FinanceShares(myCapital, nflx0)
lvgPnL = CalculatePnL(nflx1, nflx0, numLvgShares)
lvgPnL
```

```python
CalculatePctReturn(lvgPnL, myCapital)
```

###### 4.4.5. Call Option Strategy

For the call option strategy, we have to select a call and an expiration date.
Clearly, there are many choices.
Suppose we think the stock will increase \$10.

It is prudent to purchase a call that is OTM (strike above the current stock, but not more than \$10; otherwise, it will not be ITM.


```python
from yahoo_fin import options

nflx_dates = options.get_expiration_dates("nflx")
print(len(nflx_dates))

try:
    callsNflx = options.get_calls("nflx")
except:  # noQA E722
    callsNflx = pd.read_csv("nflx_calls.csv")

    list(callsNflx.columns)
```

Let's choose a call option with a strike of 340.

```python
myOption = callsNflx[(340 == callsNflx["Strike"])]
opt = myOption["Last Price"]
myOption
```

```python
nflxCall1 = Option(
    european=True, kind="call", s0=333, k=340, t=4, sigma=0.573, r=0.0, dv=0
)
nflxOpt1 = round(nflxCall1.getPrice(), 4)
round(nflxOpt1 * 100, 2)
```

```python
# The option will cost 100 times this, or $503.
nflxOpt1 = 503
numCallOptions = BuyShares(myCapital, nflxOpt1)
numCallOptions
```

We can buy 198 options; that's a lot of options! Now the stock price jumps to 345. Let's revalue the option at this new price.

```python
nflxCall2 = Option(
    european=True, kind="call", s0=345, k=340, t=4, sigma=0.573, r=0.0, dv=0
)
nflxOpt2 = round(nflxCall2.getPrice(), 4)
round(nflxOpt2 * 100, 2)
```

Let's calculate the P&L.

```python
optPnL = CalculatePnL(nflxOpt2, nflxOpt1, numCallOptions)
optPnL
```

Now, calculate the return.

```python
CalculatePctReturn(optPnL, myCapital)
```

###### 4.4.6. Bull Spread Strategy

In this strategy, we buy a call option at 340 and sell one at 350.
Let's price these options.

```python
nflxCall1 = Option(
    european=True, kind="call", s0=333, k=340, t=4, sigma=0.573, r=0.0, dv=0
)
nflxOpt1 = round(nflxCall1.getPrice(), 4)
nflxCall2 = Option(
    european=True, kind="call", s0=333, k=350, t=4, sigma=0.573, r=0.0, dv=0
)
nflxOpt2 = round(nflxCall2.getPrice(), 4)
print([nflxOpt1, nflxOpt2])
nflxSpr1 = nflxOpt1 - nflxOpt2
```

Let's use the `opstrat` package to view the payoff of the bull strategy.

```python
myCall = {"op_type": "c", "strike": 340, "tr_type": "b", "op_pr": 5.0306}
myPut = {"op_type": "c", "strike": 350, "tr_type": "s", "op_pr": 3.4836}
op_list = [myCall, myPut]
op.multi_plotter(spot=333, spot_range=10, op_list=op_list)
```

For each call option we buy, we need to sell one.
The sale creates \\$233.33 per contract.
The purchase costs \\$503.06 per contract.
Therefore, the net price is \\$269.73.
The bull spread costs a little more than half the amount that the regular call option costs. This is because we are "rebated" by selling a call that is further OTM.

```python
# The option will cost 100 times this, or $269.73
nflxOptB = (nflxOpt1 - nflxOpt2) * 100
numSpreadOptions = BuyShares(myCapital, nflxOptB)
numSpreadOptions
```

```python
nflxCall3 = Option(
    european=True, kind="call", s0=345, k=340, t=4, sigma=0.573, r=0.0, dv=0
)
nflxOpt3 = round(nflxCall3.getPrice(), 4)
nflxCall4 = Option(
    european=True, kind="call", s0=345, k=350, t=4, sigma=0.573, r=0.0, dv=0
)
nflxOpt4 = round(nflxCall4.getPrice(), 4)
print([nflxOpt3, nflxOpt4])
nflxSpr2 = nflxOpt3 - nflxOpt4
```

```python
sprPnL = CalculatePnL(nflxSpr2, nflxSpr1, numCallOptions)
sprPnL
```

```python
CalculatePctReturn(sprPnL, myCapital)
```

###### 4.4.7. Leverage
| .           | .   |
| -------------- | ------ |
| stock          | 3.6%   |
| Financed stock | 7.2%   |
| Call option    | 117.4% |
| Bull spread    | 43.5%       |



Keep in mind that these options expire in four days.
If the price does not move that much in a short time, we stand to lose 100% of the option investment. This is extremely risky.
Of course, we could find options that have more time to expiration, which
would be more expensive to buy but less risky since the extra time allows more volatility to take place.

Nevertheless, the results are evident.
The most leveraged position is the call option: It has the highest return.
Options have built-in leverage because they control 100 shares of stock.

The next most leveraged position is the bull spread: It has a long call option but is hedged by selling another call option. This limits the upside but is cheaper than merely buying the call option.

The next most leveraged position is using the underlying. Borrowing money to buy assets is a different type of leverage; rather than through a multiplier, it is simply through the fact that the invested funds should earn a higher rate of return than the borrowed funds.

The unleveraged position is simply trading the underlying without any financing. Leveraged returns attract institutional money for the potential of greater returns. Looking at data, such as the put call open interest ratio, tells us how the option traders are behaving through market data.

There is much more data than just prices and returns. When you use derivatives, there are extraordinary amounts of data that indicate both sentiment and fear in the market. In future courses, we'll examine these in more detail, especially when we study implied volatility.


###### 4.4.8. Conclusion

In this lesson, we compared different ways to enact a bullish trade, using different combinations of stocks, options, and leverage. Leverage can work through borrowed funds or through a derivative controlling a multitude of underlying assets. In the next module, we expand our knowledge of Python to areas of securitization and credit.


#### M5. Credit modelling
##### 5.1. Downloading, cleaning, and transforming data 

###### 5.1.1. Re-introduction to Probability of Default (PD)

As we discussed in the Financial Markets course, the probability of default is the probability that a bond issuer will not meet its contractual obligations on schedule. Although the most common event of default is nonpayment leading to bankruptcy proceedings, the bond prospectus might identify other events of default, such as the failure to meet a different obligation or the violation of a financial covenant.

In the following example, we will determine the probability of default given corporate bond prices. The default probabilities that are reached in this exercise are called market-implied default probabilities. Historically, practitioners have focused on the one-year probability of default calculation. Over shorter horizons of one or two years, firms are exposed to the business cycle effect, while over longer horizons, the business cycle effect tends to have a lesser impact and the company’s capital structure becomes more important. This effect has made long-run risk levels less cyclical and more stable. Intuitively, default risk over a longer time period is less sensitive to the instantaneous default rates in the economy (Beygi 3). For this reason, we will focus on corporate bonds with one or two years until maturity to calculate the market-implied default probabilities.

We will verify the accuracy of the market-implied default probabilities with the Standard & Poor’s "Average One-Year Transition Rates For Global Corporates" table, which uses historical data from 1981-2019. This transition matrix shows the observed historical probabilities of a particular rating transitioning to another rating, including default, over the course of one year.

In order to calculate the market-implied default probabilities, we must first acquire the company's current bond prices. Using a short Selenium script that emulates a user's keystrokes and clicks in a browser as a means of navigating to Trade Reporting and Compliance Engine (TRACE) bond data provided by the Financial Industry Regulatory Authority (FINRA), we can access the data needed to calculate the market-implied default probabilities.

The following is an example script. In case you do not have [Selenium](https://pypi.org/project/selenium/) installed, you can visit their respective links and download them using pip in your terminal. We will also need a chromedriver (the simulated chrome browser Selenium controls). To download it using Python, you can use the [WebDriver-manager](https://pypi.org/project/webdriver-manager/) package also found in PyPi.

You will need to insert your own path to your chromedriver in the code block below.

###### 5.1.2. Selenium and WebDrivers

[As discussed by van Gulik](https://www.go-euc.com/basic-website-performance-testing/), Selenium is tool we can use to automate browser activity that would be done by a user, for example loading a web page and filling out a form on that web page. It requires a WebDriver specific to one's web browser. 

We will use SM Energy (SM) in the subsequent code; however, this analysis works with the ticker of any large publicly traded company.

We download information about the company's bonds from the database TRACE (Trade Reporting and Compliance Engine), which is maintained by FINRA (Financial Industry Regulatory Authority).

```python
# Python libraries to install

import time
from datetime import date
from datetime import datetime as dt

import numpy as np
import pandas as pd
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import Select, WebDriverWait
from webdriver_manager.chrome import ChromeDriverManager
```

```python
# Required
company_ticker = "HES"
# or Try:
# 'F'
# 'KHC'
# 'DVN'

# Optional
company_name = "Hess"
# or Try:
# 'Ford Motor'
# 'Kraft Heinz Co'
# 'Devon Energy'

# Optional Input Choices:
# ALL, Annual, Anytime, Bi-Monthly, Monthly, N/A, None, Pays At Maturity, Quarterly, Semi-Annual, Variable
coupon_frequency = "Semi-Annual"
```
```python
# Selenium script
options = Options()
options.add_argument("--headless")
options.add_argument("--no-sandbox")
options.add_argument("--disable-dev-shm-usage")
driver = webdriver.Chrome(
    service=Service(ChromeDriverManager().install()), options=options
)

# store starting time
begin = time.time()

# FINRA's TRACE Bond Center
driver.get("http://finra-markets.morningstar.com/BondCenter/Results.jsp")

# click agree
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, ".button_blue.agree"))
).click()

# click edit search
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "a.qs-ui-btn.blue"))
).click()

# input Issuer Name
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "input[id=firscreener-issuer]"))
)
inputElement = driver.find_element_by_id("firscreener-issuer")
inputElement.send_keys(company_name)

# input Symbol
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "input[id=firscreener-cusip]"))
)
inputElement = driver.find_element_by_id("firscreener-cusip")
inputElement.send_keys(company_ticker)

# click advanced search
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "a.ms-display-switcher.hide"))
).click()

# input Coupon Frequency
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "select[name=interestFrequency]"))
)
Select(
    (driver.find_elements_by_css_selector("select[name=interestFrequency]"))[0]
).select_by_visible_text(coupon_frequency)

# click show results
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "input.button_blue[type=submit]"))
).click()

# wait for results
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located(
        (By.CSS_SELECTOR, ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn")
    )
)

# create DataFrame from scrape
frames = []
for page in range(1, 11):
    bonds = []
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, (f"a.qs-pageutil-btn[value='{str(page)}']"))
        )
    )  # wait for page marker to be on expected page
    time.sleep(2)

    headers = [
        title.text
        for title in driver.find_elements_by_css_selector(
            ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn"
        )[1:]
    ]

    tablerows = driver.find_elements_by_css_selector(
        "div.rtq-grid-bd > div.rtq-grid-row"
    )
    for tablerow in tablerows:
        tablerowdata = tablerow.find_elements_by_css_selector("div.rtq-grid-cell")
        bond = [item.text for item in tablerowdata[1:]]
        bonds.append(bond)

        # Convert to DataFrame
        df = pd.DataFrame(bonds, columns=headers)

    frames.append(df)

    try:
        driver.find_element_by_css_selector("a.qs-pageutil-next").click()
    except:  # noqa E722
        break

bond_prices_df = pd.concat(frames)

# store end time
end = time.time()

# total time taken
print(f"Total runtime of the program is {end - begin} seconds")

bond_prices_df
```
###### 5.1.3. Cleaning, Transforming, and Filtering

We will now filter the corporate bond prices DataFrame to align with the purpose of this example using the code below.

```python
def bond_dataframe_filter(df):
    # Drop bonds with missing yields and missing credit ratings
    df["Yield"].replace("", np.nan, inplace=True)
    df["Moody's®"].replace({"WR": np.nan, "": np.nan}, inplace=True)
    df["S&P"].replace({"NR": np.nan, "": np.nan}, inplace=True)
    df = df.dropna(subset=["Yield"])
    df = df.dropna(subset=["Moody's®"])
    df = df.dropna(subset=["S&P"])

    # Create Maturity Years column that aligns with Semi-Annual Payments from corporate bonds
    df["Yield"] = df["Yield"].astype(float)
    df["Coupon"] = df["Coupon"].astype(float)
    df["Price"] = df["Price"].astype(float)
    now = dt.strptime(date.today().strftime("%m/%d/%Y"), "%m/%d/%Y")
    df["Maturity"] = pd.to_datetime(df["Maturity"]).dt.strftime("%m/%d/%Y")
    daystillmaturity = []
    yearstillmaturity = []
    for maturity in df["Maturity"]:
        daystillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days)
        yearstillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days / 360)
    df = df.reset_index(drop=True)
    df["Maturity"] = pd.Series(daystillmaturity)
    #         `df['Maturity Years'] = pd.Series(yearstillmaturity).round()` # Better for Annual Payments
    df["Maturity Years"] = (
        round(pd.Series(yearstillmaturity) / 0.5) * 0.5
    )  # Better for Semi-Annual Payments

    # Target bonds with short-term maturities
    df["Maturity"] = df["Maturity"].astype(float)
    years_mask = (df["Maturity Years"] > 0) & (df["Maturity Years"] <= 5)
    df = df.loc[years_mask]
    return df
```

```python
bond_df_result = bond_dataframe_filter(bond_prices_df)
bond_df_result
```

Make sure that you review the documentation for the relevant code and are familiar with how the code above works; in particular, understand the following (and their parameters), as these will all serve you well when you clean, transform, and filter your data in the future (the related documentation is also required reading): 

df.dropna() <br>
inplace <br>
df.replace() <br>
df['X'].astype() <br> 
pd.to_datetime() <br>
df['X']).dt.strftime <br>
and the code lines that involve the variable years_mask <br>

Also, be sure to understand how df.values.tolist() works.<br>


###### 5.1.4. Conclusion

In this lesson, we revisited the calculation for market-implied probability of default but in much more detail. We also downloaded price and rating information for bonds issued by a particular issuer from a well-regarded bond database, FINRA's TRACE. Once we downloaded it, we cleaned it, transformed some of the data related to bond maturity, and filtered the data so that we could focus our analysis on the bonds with shorter maturities.
In the following lesson, we will take the next step toward calculating the market-implied probability of default by estimating the expected cashflows. Then, we can estimate the risk-adjusted discount rate, which equates the bond price to those expected cash flows.



**References**

* Donnelly, Hugh. "Calculating a Company's Probability of Default with Python." AlphaWave Data. https://github.com/AlphaWaveData/Jupyter-Notebooks/blob/master/AlphaWave%20Market-Implied%20Probability%20of%20Default%20Example.ipynb.

* van Gulik, Eltjo. "Basic website performance testing with Python and Selenium." 19 Mar 2021. https://www.go-euc.com/basic-website-performance-testing/

* Beygi, Sajjad et al. “Features of a Lifetime PD Model: Evidence from Public, Private, and Rated Firms.” Moody’s Analytics, May 2018.

* The  code and related documentation used in this lesson is adapted from: <br>**Hugh Donnelly, CFA**<br>*AlphaWave Data* <br> **March 2021** under the following  MIT License:

**Note:** The above MIT license notice is copied here to comply with its requirements, but it does **not** apply to the content in these lesson notes. 





---
Copyright © 2022 WorldQuant University. This
content is licensed solely for personal use. Redistribution or
publication of this material is strictly prohibited.

##### 5.2. Risk adjusted discount rate



|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | CAPM (Capital Asset Pricing Model), Probability of Default, Recovery Rate, Variance, Standard deviation, Correlation   |
|**Keywords** |Market Risk Premium, Expected Risk Premium, Risk-free rate, DataReader |   



*In the last lesson, we went into detail about the calculation of market-implied probability of default. We also took the first steps in the multi-step process of gathering the inputs to this calculation.  We downloaded data from a bond database, cleaned the data, and transformed the "maturity date" into "time to maturity." Then, we used a mask to filter the bonds to fit our desired parameters*.  

*In this lesson, we will estimate the risk-adjusted discount rate. This is the discount rate that sets the bond's expected cash flows equal to the price of the bond.  In order to do this, we need to estimate the risk-free interest rate, the expected risk premium for the bond, the market risk premium, and the beta of the bond*.  

>[!Note] Note
>The code that was introduced in the previous lesson is below, followed by the new code and text for this lesson.
```python
# Python libraries to install
# Lesson 1
import time
from datetime import date
from datetime import datetime as dt
from datetime import timedelta

# Lesson 2 (in addition to above)
import numpy as np
import pandas as pd
import pandas_datareader as dr
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import Select, WebDriverWait
from webdriver_manager.chrome import ChromeDriverManager
```

```python
# Required
company_ticker = "HES"
# or Try:
# 'F'
# 'KHC'
# 'DVN'

# Optional
company_name = "Hess"
# or Try:
# 'Ford Motor'
# 'Kraft Heinz Co'
# 'Devon Energy'

# Optional Input Choices:
# ALL, Annual, Anytime, Bi-Monthly, Monthly, N/A, None, Pays At Maturity, Quarterly, Semi-Annual, Variable
coupon_frequency = "Semi-Annual"
```

```python
# Selenium script
options = Options()
options.add_argument("--headless")
options.add_argument("--no-sandbox")
options.add_argument("--disable-dev-shm-usage")
driver = webdriver.Chrome(
    service=Service(ChromeDriverManager().install()), options=options
)

# store starting time
begin = time.time()

# FINRA's TRACE Bond Center
driver.get("http://finra-markets.morningstar.com/BondCenter/Results.jsp")

# click agree
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, ".button_blue.agree"))
).click()

# click edit search
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "a.qs-ui-btn.blue"))
).click()

# input Issuer Name
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "input[id=firscreener-issuer]"))
)
inputElement = driver.find_element_by_id("firscreener-issuer")
inputElement.send_keys(company_name)

# input Symbol
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "input[id=firscreener-cusip]"))
)
inputElement = driver.find_element_by_id("firscreener-cusip")
inputElement.send_keys(company_ticker)

# click advanced search
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "a.ms-display-switcher.hide"))
).click()

# input Coupon Frequency
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.CSS_SELECTOR, "select[name=interestFrequency]"))
)
Select(
    (driver.find_elements_by_css_selector("select[name=interestFrequency]"))[0]
).select_by_visible_text(coupon_frequency)

# click show results
WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, "input.button_blue[type=submit]"))
).click()

# wait for results
WebDriverWait(driver, 10).until(
    EC.presence_of_element_located(
        (By.CSS_SELECTOR, ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn")
    )
)

# create DataFrame from scrape
frames = []
for page in range(1, 11):
    bonds = []
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, (f"a.qs-pageutil-btn[value='{str(page)}']"))
        )
    )  # wait for page marker to be on expected page
    time.sleep(2)

    headers = [
        title.text
        for title in driver.find_elements_by_css_selector(
            ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn"
        )[1:]
    ]

    tablerows = driver.find_elements_by_css_selector(
        "div.rtq-grid-bd > div.rtq-grid-row"
    )
    for tablerow in tablerows:
        tablerowdata = tablerow.find_elements_by_css_selector("div.rtq-grid-cell")
        bond = [item.text for item in tablerowdata[1:]]
        bonds.append(bond)

        # Convert to DataFrame
        df = pd.DataFrame(bonds, columns=headers)

    frames.append(df)

    try:
        driver.find_element_by_css_selector("a.qs-pageutil-next").click()
    except:  # noqa E722
        break

bond_prices_df = pd.concat(frames)

# store end time
end = time.time()

# total time taken
print(f"Total runtime of the program is {end - begin} seconds")

bond_prices_df
```

```python
def bond_dataframe_filter(df):
    # Drop bonds with missing yields and missing credit ratings
    df["Yield"].replace("", np.nan, inplace=True)
    df["Moody's®"].replace({"WR": np.nan, "": np.nan}, inplace=True)
    df["S&P"].replace({"NR": np.nan, "": np.nan}, inplace=True)
    df = df.dropna(subset=["Yield"])
    df = df.dropna(subset=["Moody's®"])
    df = df.dropna(subset=["S&P"])

    # Create Maturity Years column that aligns with Semi-Annual Payments from corporate bonds
    df["Yield"] = df["Yield"].astype(float)
    df["Coupon"] = df["Coupon"].astype(float)
    df["Price"] = df["Price"].astype(float)
    now = dt.strptime(date.today().strftime("%m/%d/%Y"), "%m/%d/%Y")
    df["Maturity"] = pd.to_datetime(df["Maturity"]).dt.strftime("%m/%d/%Y")
    daystillmaturity = []
    yearstillmaturity = []
    for maturity in df["Maturity"]:
        daystillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days)
        yearstillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days / 360)
    df = df.reset_index(drop=True)
    df["Maturity"] = pd.Series(daystillmaturity)
    df["Maturity Years"] = (
        round(pd.Series(yearstillmaturity) / 0.5) * 0.5
    )  # Better for Semi-Annual Payments

    # Target bonds with short-term maturities
    df["Maturity"] = df["Maturity"].astype(float)
    years_mask = (df["Maturity Years"] > 0) & (df["Maturity Years"] <= 5)
    df = df.loc[years_mask]
    return df
```
```python
bond_df_result = bond_dataframe_filter(bond_prices_df)
bond_df_result
```

###### Required reading 
The pandas development team. _pandas documentation._ Version 1.4.2. [https://pandas.pydata.org/docs/reference/](https://pandas.pydata.org/docs/reference/)
    -   **Required pages:** The documentation for the following functions: "pandas.DataFrame.dropna", "pandas.DataFrame.replace", "pandas.DataFrame.astype", "pandas.to_datetime", "pandas.Series.dt.strftime", "pandas.DataFrame.values", "pandas.Series.tolist"
    -   **Estimated reading time:** 25 minutes





|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Basic Python, Probability of default (PD)  |
|**Keywords** |df.dropna(), inplace, df.replace(), .astype(), pd.to_datetime(), df['X'].dt.strftime, masking / filtering, df.concat(), <br> .append, df.values.tolist(), datetime.strptime, datetime.datetime|   	





*In this module, we perform the several steps required to calculate the market-implied probability of default (PD), which we introduced in Module 5.*
*In this lesson, we will indicate the company (bond issuer) and determine which of the company's bonds to use after cleaning, transforming, and filtering the data.*

*In the lessons that follow in this module, we will estimate the expected cashflows and the risk-adjusted discount rate (lesson 2). Finally we estimate the market-implied probability of default (lesson 3) and compare it to the PD that Standard and Poor's (S&P) associates with the rating (lesson 4).*

###### 5.2.1. Discounting Expected Cashflows

To calculate the probability of default using current corporate bond prices, we will use bond valuation techniques. The valuation of corporate bonds is similar to that of any risky asset; it is dependent on the present value of future expected cash flows, discounted at a risk-adjusted rate (similar to Discounted Cash Flow analysis).

$$\begin{equation}
BOND\ PRICE = \frac{ECF_1}{1+d}\ +\ \frac{ECF_2}{(1+d)^2}\ +\ \frac{ECF_3}{(1+d)^3}
\end{equation}$$
*where*
$ECF = Expected\ Cash\ Flow$
$d = Discount\ Rate$

Corporate bond valuation also accounts for the probability of the bond defaulting and not paying back the principal in full.

We now need to estimate the expected cash flows and the risk-adjusted discount rate.

###### 5.2.2. Estimating Expected Cash Flows
The first step in valuing the bond is to find the expected cash flow at each period. This is done by adding the product of the default payout and the probability of default (P) with the product of the promised payment (coupon payments and repayment of principal) and the probability of not defaulting (1-P), which is also referred to as the probability of survival.

$ECF_1 = (P)*(Default\ Payout)\ +\ (1-P)*(Coupon\ Payment)$<br>
$ECF_2 = (1-P)*\{(P)\ *(Default\ Payout)\ +\ (1-P)*(Coupon\ Payment)\}$<br>
$ECF_3 = (1-P)^2*\{(P)\ *(Default\ Payout)\ +\ (1-P)*(Coupon\ Payment\ +\ Principal)\}$<br>

$P = Probability\ of\ Default$<br>
$Default\ Payout = Principal\ *\ Recovery\ Rate$<br>

If the bond defaults, the default payout is the product of recovery rate and the principal. In the following example, the principal will be at par value for the bond (e.g. $100). The recovery rate is the percentage of the loss recovered from a bond in default. The recovery rate varies by industry, the degree of seniority in the capital structure, the amount of leverage in the capital structure in total, and whether a particular security is secured or otherwise collateralized. We assume a 40% recovery rate for the corporate bonds in the following example, which is a common baseline assumption in practice.

The code in the below function shows how the expected cash flow is calculated at each period. We then use the solve function from the Python library `SymPy` to calculate the probability of default that will equate future expected cash flows with the current price of the corporate bond when discounted at the risk-adjusted rate. Running the cell below defines the function for use, but it will not run the function. We will wait to run the function until after the risk-adjusted discount rate is calculated.

###### 5.2.3. The Market Risk Premium and the Expected Risk Premium
After the expected cash flows are calculated, they are discounted back to period 0 at a risk-adjusted discount rate (d) to calculate the bond’s price. A risk-adjusted discount rate is the rate obtained by combining an expected risk premium with the risk-free rate during the calculation of the present value of a risky investment.

**Risk-adjusted Discount Rate = Risk-free Interest Rate + Expected Risk Premium**


We use the (risk-adjusted) discount rate in order to account for the liquidity, maturity, and tax considerations that cause corporate bonds to have an observed spread over the yield on a risk-free bond like the bonds issued by the government in a stable economy. (We grouped all of these factors together under the term "credit spread" in the Financial Markets course.) The minimum required return expected for a bond investor is equal to the sum of the following, which accounts for this spread between corporate bonds and risk-free bonds:
- the sum of: 
	* **Default Risk Premium** – Compensates investors for the business’ likelihood of default.
	* **Liquidity Premium** – Compensates investors for investing in less liquid securities such as bonds. Government bonds typically are more liquid than corporate bonds. Government bonds are available in greater supply than even the most liquid corporates and have demand from a wider set of institutional investors. In addition, government bonds can be used more readily as collateral in repo transactions and for centrally cleared derivatives.
	* **Maturity Premium** – Compensates investors for the risk associated with bonds that mature many years into the future, which inherently carry more risk.
	* **Taxation Premium** – Compensates investors for the taxable income that bonds generate. Interest income on U.S. corporate bonds is taxable by both the federal and state governments. Government debt, however, is exempt from taxes at the state level.
	* **Projected Inflation** – Accounts for the devaluation of currency over time.
	* **Risk-free Rate** – Refers to the rate of return an investor can expect on a riskless security (such as a T-bill).

We begin our calculation of the risk-adjusted discount rate by first turning our attention to estimating the expected risk premium.

The expected risk premium is obtained by subtracting the risk-free rate of return from the market rate of return and then multiplying the result by the beta that adjusts based on the magnitude of the investment risk involved. By carefully selecting a proxy short-term corporate bond's beta to the overall market, we can calculate an expected risk premium that will result in a risk-adjusted discount rate that incorporates liquidity, maturity, and tax considerations to produce a more accurate probability of default when using the bond valuation technique.

**_Expected Risk Premium = (Market Rate of Return - Risk-free Rate of Return) * Beta_**


To calculate the expected risk premium, we must first calculate the market rate of return. We can use the capital asset pricing model (CAPM) to determine the market rate of return.

$$r_m = r_f\ +(\beta*MRP)$$<br>
$r_m = Market\ Rate\ of\ Return$<br>
$r_f = Riskfree\ Rate$<br>
$\beta = Beta$<br>
$MRP = Market\ Risk\ Premium$<br>

CAPM is an equilibrium model that takes the risk-free rate, the stock market's beta, and the market risk premium as inputs. Let's now determine the value for each of these inputs.

Government securities are assumed to be risk-free, at least from a credit standpoint. With this assumption, the appropriate rate to use in the market rate of return calculation is the government security having approximately the same duration as the asset being valued and sufficient liquidity so that the yield does not have an embedded liquidity risk premium. Equities are assumed to have a long duration, so a long-term government bond yield is an appropriate proxy for the risk-free rate.

In this step, the yield on the 10-year U.S. Treasury note will be used as the risk-free rate.  We can scrape the current yield on the 10-year U.S. Treasury note from Yahoo Finance using the code below.

```python
# Ten-Year Risk-free Rate
timespan = 100
current_date = date.today()
past_date = current_date - timedelta(days=timespan)
ten_year_risk_free_rate_df = dr.DataReader("^TNX", "yahoo", past_date, current_date)
ten_year_risk_free_rate = (
    ten_year_risk_free_rate_df.iloc[len(ten_year_risk_free_rate_df) - 1, 5]
) / 100
ten_year_risk_free_rate
```

The market risk premium should be the expected return on the market index less the expected return (or yield) on the long-term government bond. For our purposes, we use the annual [market risk premium](http://pages.stern.nyu.edu/~adamodar/New_Home_Page/datafile/ctryprem.html) provided by Aswath Damodaran, a professor at the Stern School of Business at New York University.

```python
# Market Risk Premium
market_risk_premium = 0.0472
```

According to asset pricing theory, beta represents the type of risk, systematic risk, that cannot be diversified away. By definition, the market itself has a beta of 1. As a result, beta will be equal to 1 when calculating the market rate of return.

```python
# Market Equity Beta
stock_market_beta = 1
```

We now have all the inputs required to calculate the market rate of return.

```python
# Market Rate of Return
market_rate_of_return = ten_year_risk_free_rate + (
    stock_market_beta * market_risk_premium
)
market_rate_of_return
```

Now that we have calculated the market rate of return, we can determine the expected risk premium by subtracting the risk-free rate from the market rate of return and multiplying the result by the beta for the bond.

**_Expected Risk Premium = (Market Rate of Return - Risk-free Rate of Return) * Beta_**

In this step, we will use a one-year risk-free rate so that the expected risk premium matches the duration we want for the risk-adjusted discount rate. We accomplish this by taking the yield on the very liquid 10-year U.S. Treasury note and raising it to the power of 1/10 in order to convert the yield to a one-year equivalent.

Note that 2\*\*3 is Pythonic for $2^3$, or 2 raised to the power of 3 (= 8).
By the same token, 8**(1/3) is the cube root of 8 (=2).

```python
# One-Year Risk-free Rate
one_year_risk_free_rate = (1 + ten_year_risk_free_rate) ** (1 / 10) - 1
one_year_risk_free_rate
```

The final component needed to calculate the expected risk premium is the corporate bond's beta.  Knowing that differences in liquidity within the universe of corporate bonds are great, we use the Vanguard Short-Term Corporate Bond Index Fund ETF Shares (VCSH) as a proxy for short-term maturity bonds. The beta from this index will enable us to embed some of the liquidity and maturity risk into the risk-adjusted discount rate that will be used to calculate the probability of default for the corporate bonds we will be analyzing. This should allow for better isolation of the credit risk associated with the chosen bonds.

A bond's beta is the sensitivity of that bond's return to the return of the market index. It is a measure of undiversifiable, systematic risk. As you see below, it can be calculated in (at least) two ways.
<br>
```python
# Vanguard Short-Term Corporate Bond Index Fund ETF Shares
bond_fund_ticker = "VCSH"
```

```python
# Download data for the bond fund and the market
market_data = dr.get_data_yahoo("SPY", past_date, current_date)  # the market
fund_data = dr.get_data_yahoo("VCSH", past_date, current_date)  # the bond fund
```

Calculate the beta of the bond fund (with respect to the S&P):
```python
# Approach #1 - Covariance/Variance Method:

# Calculate the covariance between the fund and the market -- this is the numerator in the Beta calculation
fund_market_cov = fund_data["Adj Close"].cov(market_data["Adj Close"])
print("covariance between fund and market: ", fund_market_cov)

# Calculate market (S&P) variance -- this is the denominator in the Beta calculation
market_var = market_data["Adj Close"].var()
print("market variance: ", market_var)

# Calculate Beta
bond_fund_beta_cv = fund_market_cov / market_var
print("bond fund beta (using covariance/variance): ", bond_fund_beta_cv)
```

```python
# Approach #2 - Correlation Method:

# Calculate the standard deviation of the market by taking the square root of the variance, for use in the denominator
market_stdev = market_var ** 0.5
print("market standard deviation: ", market_stdev)

# Calculate bond fund standard deviation, for use in the numerator

fund_stdev = fund_data["Adj Close"].std()
print("fund standard deviation: ", fund_stdev)

# Calculate Pearson correlation between bond fund and market (S&P), for use in the numerator
fund_market_Pearson_corr = fund_data["Adj Close"].corr(
    market_data["Adj Close"], method="pearson"
)
print("Pearson correlation between fund and market: ", fund_market_Pearson_corr)

# Calculate Beta
fund_beta_corr = fund_stdev * fund_market_Pearson_corr / market_stdev
print("bond fund beta (using correlation): ", fund_beta_corr)
```


Note that `.corr()` above can be used to calculate any of the three correlation metrics we have discussed, taking the arguments ‘pearson’, ‘kendall’, or ‘spearman’ (with 'pearson' as the default).
We include the argument here to emphasize this fact.

```python
# Bond's Beta: use the result of either of the two above approaches, bond_fund_beta_cv or fund_beta_corr
bond_beta = fund_beta_corr
bond_beta
```

We now have all the components required to calculate the expected risk premium.
```python
# Expected Risk Premium
expected_risk_premium = (market_rate_of_return - one_year_risk_free_rate) * bond_beta
expected_risk_premium
```

With the expected risk premium now in hand, we revisit the (risk-adjusted) discount rate equation:

**_Discount Rate = Risk-free Rate  + Expected Risk Premium_**

The final input required for the risk-adjusted discount rate is the risk-free interest rate, which we define next.

*Estimating the Risk-Free Rate*<br>
We will again use a one-year risk-free rate so that it matches the duration we want for the risk-adjusted discount rate, which we will use to discount expected cash flows to determine the probability of default.

```python
# One-Year Risk-free Rate (same code as above)
one_year_risk_free_rate = (1 + ten_year_risk_free_rate) ** (1 / 10) - 1
one_year_risk_free_rate
```

We can now combine the risk-free interest rate and the expected risk premium to obtain the risk-adjusted discount rate.

```python
# Risk-adjusted Discount Rate
risk_adjusted_discount_rate = one_year_risk_free_rate + expected_risk_premium
risk_adjusted_discount_rate
```

###### 5.2.4. Conclusion
In this lesson, we reviewed CAPM and found the risk-adjusted discount rate, which is an input to our market-implied probability of default estimation. 

In order to find the risk-adjusted discount rate, we had to find the one-year risk-free rate and the expected risk premium.

We found the one-year risk-free rate by taking the tenth-root of the ten-year risk-free rate.

We found the expected risk premium by first finding the market risk premium and the beta.

We saw that beta can be calculated using correlation and standard deviations, or covariance and the market variance, due to the mathematical relationships between these variables.

In the next lesson, we can use this newly found data point to finally calculate the market-implied probability of default, with a function built for this purpose.


**References**

* Donnelly, Hugh. "Calculating a Company's Probability of Default with Python." AlphaWave Data. https://github.com/AlphaWaveData/Jupyter-Notebooks/blob/master/AlphaWave%20Market-Implied%20Probability%20of%20Default%20Example.ipynb.




##### 5.3. Estimating the market-implied probability of default 
###### Required Readings

Required readings for this program are open access, which means you should be able to access them at no cost. The link provided in the citation will take you directly to the reading or to a page where you can download it.

1.  Sullivan, Eric. "Numerical Methods: An Inquiry-Based Approach in Python." _GitHub_. [https://numericalmethodssullivan.github.io/ch-python.html#solving-equations-symbolically](https://numericalmethodssullivan.github.io/ch-python.html#solving-equations-symbolically)
    
    -   **Required pages:** Section A.7.5
    -   **Estimated reading time:** 15 minutes
2.  Python Software Foundation. _Python 3.10.4 Documentation._ [https://docs.python.org/3/tutorial/controlflow.html](https://docs.python.org/3/tutorial/controlflow.html).
    
    -   **Required pages:** Sections 4.7 and 4.8
    -   **Estimated reading time:** 20 minutes
3.  Sargent, Thomas J., and John Stachurski. _Python Programming for Economics and Finance_. QuantEcon. [https://python-programming.quantecon.org/python_essentials.html#id7](https://python-programming.quantecon.org/python_essentials.html#id7)
    
    -   **Required pages:** Section 5.6
    -   **Estimated reading time:** 10 minutes
4.  Sargent, Thomas J., and John Stachurski. _Python Programming for Economics and Finance_. QuantEcon. [https://python-programming.quantecon.org/matplotlib.html](https://python-programming.quantecon.org/matplotlib.html)
    
    -   **Required pages:** Entire chapter
    -   **Estimated reading time:** 30 minutes
5.  The pandas development team. _pandas documentation_. Version 1.4.2. [https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html)
    
    -   **Required pages:** All
    -   **Estimated reading time:** 10 minutes
>[!Note] NOTE
>this section requires a csv file to be copied to the .ipynb file location

###### CSV table
use [tableconvert.com](https://tableconvert.com/excel-to-markdown) to convert csv into markdown table
|   | Issuer Name                  | Symbol     | Callable | Sub-Product Type | Coupon | Maturity   | Moody's® | S&P  | Price   |
|---|------------------------------|------------|----------|------------------|--------|------------|----------|------|---------|
| 1 | HESS CORP                    | HES.GH     | Yes      | Corporate Bond   | 6.000  | 01/15/2040 | Ba1      | BBB- | 107.168 |
| 2 | HESS CORP                    | HES.GI     | Yes      | Corporate Bond   | 5.600  | 02/15/2041 | Ba1      | BBB- | 102.172 |
| 3 | HESS CORP                    | HES4136877 | Yes      | Corporate Bond   | 3.500  | 07/15/2024 | Ba1      | BBB- | 100.089 |
| 4 | HESS CORP                    | HES4405829 | Yes      | Corporate Bond   | 4.300  | 04/01/2027 | Ba1      | BBB- | 99.580  |
| 5 | HESS CORP                    | HES4405830 | Yes      | Corporate Bond   | 5.800  | 04/01/2047 | Ba1      | BBB- | 104.191 |
| 6 | HESS MIDSTREAM OPERATIONS LP | HES4567499 | Yes      | Corporate Bond   | 5.625  | 02/15/2026 |          | BB+  | 104.500 |
| 7 | HESS MIDSTREAM OPERATIONS LP | HES4927355 | Yes      | Corporate Bond   | 5.625  | 02/15/2026 |          | BB+  | 100.625 |
| 8 | HESS MIDSTREAM OPERATIONS LP | HES5233164 | Yes      | Corporate Bond   | 4.250  | 02/15/2030 | Ba2      | BB+  | 90.970  |
| 9 | HESS MIDSTREAM OPERATIONS LP | HES5392919 | Yes      | Corporate Bond   | 5.500  | 10/15/2030 | Ba2      | BB+  | 98.430  |






|  |  |
|:---|:---|
|**Reading Time** |  25 minutes |
|**Prior Knowledge** | Probability of default, Basic Python, DataFrames  |
|**Keywords** |`.apply()`, Lambda functions, `numpy.arange()`, Symbol library |   	

---

*So far in this module, we have been gathering all the inputs we need for the market-implied probability of default (PD). Now that we have calculated the risk-adjusted discount rate in the last lesson, we can solve for the PD using `SymPy`. We will also refresh our understanding of some essential Python, e.g., control-flow tools, data types, as well as the append and apply methods*. 




###### 5.3.1. SymPy: Solving the Probability of Default
Given the semi-annual coupon payment frequency for the bonds we are analyzing, we can feed the above annual risk-adjusted discount rate into the *bonds probability of default* function below and it will convert these annual rates into semi-annual rates.

Our last step before running the *bonds probability of default* function is to define the principal payment, the recovery rate, and the symbol for probability of default (P) that the solve function from the Python library `SymPy` will use to calculate the probability of default by equating future expected cash flows with the current price of the corporate bond when discounted at the risk-adjusted rate.

**Note:** The code that was introduced in the previous lessons is below, followed by the new code and text for this lesson.

```python
# Python libraries to install
# Lesson 1
import time
from datetime import date
from datetime import datetime as dt
from datetime import timedelta

# Lesson 2
import numpy as np
import pandas as pd
import pandas_datareader as dr
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import Select, WebDriverWait

# Lesson 3 (in addition to above)
from sympy import solve, symbols
from webdriver_manager.chrome import ChromeDriverManager
```

```python
# Required
company_ticker = "HES"
# or Try:
# 'F'
# 'KHC'
# 'DVN'

# Optional
company_name = "Hess"
# or Try:
# 'Ford Motor'
# 'Kraft Heinz Co'
# 'Devon Energy'

# Optional Input Choices:
# ALL, Annual, Anytime, Bi-Monthly, Monthly, N/A, None, Pays At Maturity, Quarterly, Semi-Annual, Variable
coupon_frequency = "Semi-Annual"
```


The cell below using a web-scraping library `selenium` to collect the data we need. However, there is a dataset that has been pre-loaded onto your virtual machine. If you'd like to download the latest data, change the value of `scrape_new_data` to `True`. Otherwise, you will use the pre-loaded data.

```python
scrape_new_data = False

if scrape_new_data:
    # Selenium script
    options = Options()
    options.add_argument("--headless")
    options.add_argument("--no-sandbox")
    options.add_argument("--disable-dev-shm-usage")
    driver = webdriver.Chrome(
        service=Service(ChromeDriverManager().install()), options=options
    )

    # store starting time
    begin = time.time()

    # FINRA's TRACE Bond Center
    driver.get("http://finra-markets.morningstar.com/BondCenter/Results.jsp")

    # click agree
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, ".button_blue.agree"))
    ).click()

    # click edit search
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, "a.qs-ui-btn.blue"))
    ).click()

    # input Issuer Name
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, "input[id=firscreener-issuer]")
        )
    )
    inputElement = driver.find_element_by_id("firscreener-issuer")
    inputElement.send_keys(company_name)

    # input Symbol
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.CSS_SELECTOR, "input[id=firscreener-cusip]"))
    )
    inputElement = driver.find_element_by_id("firscreener-cusip")
    inputElement.send_keys(company_ticker)

    # click advanced search
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, "a.ms-display-switcher.hide"))
    ).click()

    # input Coupon Frequency
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, "select[name=interestFrequency]")
        )
    )
    Select(
        (driver.find_elements_by_css_selector("select[name=interestFrequency]"))[0]
    ).select_by_visible_text(coupon_frequency)

    # click show results
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, "input.button_blue[type=submit]"))
    ).click()

    # wait for results
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn")
        )
    )

    # create DataFrame from scrape
    frames = []
    for page in range(1, 11):
        bonds = []
        WebDriverWait(driver, 10).until(
            EC.presence_of_element_located(
                (By.CSS_SELECTOR, (f"a.qs-pageutil-btn[value='{str(page)}']"))
            )
        )  # wait for page marker to be on expected page
        time.sleep(2)

        headers = [
            title.text
            for title in driver.find_elements_by_css_selector(
                ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn"
            )[1:]
        ]

        tablerows = driver.find_elements_by_css_selector(
            "div.rtq-grid-bd > div.rtq-grid-row"
        )
        for tablerow in tablerows:
            tablerowdata = tablerow.find_elements_by_css_selector("div.rtq-grid-cell")
            bond = [item.text for item in tablerowdata[1:]]
            bonds.append(bond)

            # Convert to DataFrame
            df = pd.DataFrame(bonds, columns=headers)

        frames.append(df)

        try:
            driver.find_element_by_css_selector("a.qs-pageutil-next").click()
        except:  # noqa E722
            break

    bond_prices_df = pd.concat(frames)

    # store end time
    end = time.time()

    # total time taken
    print(f"Total runtime of the program is {end - begin} seconds")

else:
    bond_prices_df = pd.read_csv("bond-prices.csv")

bond_prices_df
```

```python
def bond_dataframe_filter(df):
    # Drop bonds with missing yields and missing credit ratings
    df["Yield"].replace("", np.nan, inplace=True)
    df["Moody's®"].replace({"WR": np.nan, "": np.nan}, inplace=True)
    df["S&P"].replace({"NR": np.nan, "": np.nan}, inplace=True)
    df = df.dropna(subset=["Yield"])
    df = df.dropna(subset=["Moody's®"])
    df = df.dropna(subset=["S&P"])

    # Create Maturity Years column that aligns with Semi-Annual Payments from corporate bonds
    df["Yield"] = df["Yield"].astype(float)
    df["Coupon"] = df["Coupon"].astype(float)
    df["Price"] = df["Price"].astype(float)
    now = dt.strptime(date.today().strftime("%m/%d/%Y"), "%m/%d/%Y")
    df["Maturity"] = pd.to_datetime(df["Maturity"]).dt.strftime("%m/%d/%Y")
    daystillmaturity = []
    yearstillmaturity = []
    for maturity in df["Maturity"]:
        daystillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days)
        yearstillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days / 360)
    df = df.reset_index(drop=True)
    df["Maturity"] = pd.Series(daystillmaturity)
    #         `df['Maturity Years'] = pd.Series(yearstillmaturity).round()` # Better for Annual Payments
    df["Maturity Years"] = (
        round(pd.Series(yearstillmaturity) / 0.5) * 0.5
    )  # Better for Semi-Annual Payments

    # Target bonds with short-term maturities
    df["Maturity"] = df["Maturity"].astype(float)
    # `df = df.loc[df['Maturity'] >= 0]`
    years_mask = (df["Maturity Years"] > 0) & (df["Maturity Years"] <= 5)
    df = df.loc[years_mask]
    return df
```

```python
bond_df_result = bond_dataframe_filter(bond_prices_df)
bond_df_result
```

```python
# Ten-Year Risk-free Rate
timespan = 100
current_date = date.today()
past_date = current_date - timedelta(days=timespan)
ten_year_risk_free_rate_df = dr.DataReader("^TNX", "yahoo", past_date, current_date)
ten_year_risk_free_rate = (
    ten_year_risk_free_rate_df.iloc[len(ten_year_risk_free_rate_df) - 1, 5]
) / 100
ten_year_risk_free_rate
```

```python
# Market Risk Premium
market_risk_premium = 0.0472
```

```python
# Market Equity Beta
stock_market_beta = 1
```

```python
# Market Rate of Return
market_rate_of_return = ten_year_risk_free_rate + (
    stock_market_beta * market_risk_premium
)
market_rate_of_return
```

```python
# One-Year Risk-free Rate
one_year_risk_free_rate = (1 + ten_year_risk_free_rate) ** (1 / 10) - 1
one_year_risk_free_rate
```

```python
# Vanguard Short-Term Corporate Bond Index Fund ETF Shares
bond_fund_ticker = "VCSH"
```

```python
# Download data for the bond fund and the market
market_data = dr.get_data_yahoo("SPY", past_date, current_date)  # the market
fund_data = dr.get_data_yahoo("VCSH", past_date, current_date)  # the bond fund
```

```python
# Approach #1 - Covariance/Variance Method:

# Calculate the covariance between the fund and the market -- this is the numerator in the Beta calculation
fund_market_cov = fund_data["Adj Close"].cov(market_data["Adj Close"])
print("covariance between fund and market: ", fund_market_cov)

# Calculate market (S&P) variance -- this is the denominator in the Beta calculation
market_var = market_data["Adj Close"].var()
print("market variance: ", market_var)

# Calculate Beta
bond_fund_beta_cv = fund_market_cov / market_var
print("bond fund beta (using covariance/variance): ", bond_fund_beta_cv)
```

```python
# Approach #2 - Correlation Method:

# Calculate the standard deviation of the market by taking the square root of the variance, for use in the denominator
market_stdev = market_var ** 0.5
print("market standard deviation: ", market_stdev)

# Calculate bond fund standard deviation, for use in the numerator

fund_stdev = fund_data["Adj Close"].std()
print("fund standard deviation: ", fund_stdev)

# Calculate Pearson correlation between bond fund and market (S&P), for use in the numerator
fund_market_Pearson_corr = fund_data["Adj Close"].corr(
    market_data["Adj Close"], method="pearson"
)
print("Pearson correlation between fund and market: ", fund_market_Pearson_corr)

# Calculate Beta
fund_beta_corr = fund_stdev * fund_market_Pearson_corr / market_stdev
print("bond fund beta (using correlation): ", fund_beta_corr)
```

```python
# Bond's Beta: use the result of either of the two above approaches, bond_fund_beta_cv or fund_beta_corr
bond_beta = fund_beta_corr
bond_beta
```
```python
# Expected Risk Premium
expected_risk_premium = (market_rate_of_return - one_year_risk_free_rate) * bond_beta
expected_risk_premium
```
```python
# One-Year Risk-free Rate (same code as above)
one_year_risk_free_rate = (1 + ten_year_risk_free_rate) ** (1 / 10) - 1
one_year_risk_free_rate
```

```python
# Risk-adjusted Discount Rate
risk_adjusted_discount_rate = one_year_risk_free_rate + expected_risk_premium
risk_adjusted_discount_rate
```


Notice below that the numpy library method "np.append()" is different from the pandas library method "df1.append(df2)".

```python
def bonds_probability_of_default(
    coupon, maturity_years, bond_price, principal_payment, risk_adjusted_discount_rate
):

    price = bond_price
    prob_default_exp = 0

    #     `times = np.arange(1, maturity_years+1)` # For Annual Cashflows
    #     annual_coupon = coupon # For Annual Cashflows
    times = np.arange(0.5, (maturity_years - 0.5) + 1, 0.5)  # For Semi-Annual Cashflows
    semi_annual_coupon = coupon / 2  # For Semi-Annual Cashflows

    # Calculation of Expected Cash Flow
    cashflows = np.array([])
    for i in times[:-1]:
        #         cashflows = np.append(cashflows, annual_coupon) # For Annual Cashflows
        #     cashflows = np.append(cashflows, annual_coupon+principal_payment)#  For Annual Cashflows
        cashflows = np.append(
            cashflows, semi_annual_coupon
        )  # For Semi-Annual Cashflows
    cashflows = np.append(
        cashflows, semi_annual_coupon + principal_payment
    )  # For Semi-Annual Cashflows

    for i in range(len(times)):
        #         This code block is used if there is only one payment remaining
        if len(times) == 1:
            prob_default_exp += (
                cashflows[i] * (1 - P) + cashflows[i] * recovery_rate * P
            ) / np.power((1 + risk_adjusted_discount_rate), times[i])
        #         This code block is used if there are multiple payments remaining
        else:
            #             For Annual Cashflows
            #             if times[i] == 1:
            #                 prob_default_exp += ((cashflows[i]*(1-P) + principal_payment*recovery_rate*P) / \
            #                                     np.power((1 + risk_adjusted_discount_rate), times[i]))
            #             For Semi-Annual Cashflows
            if times[i] == 0.5:
                prob_default_exp += (
                    cashflows[i] * (1 - P) + principal_payment * recovery_rate * P
                ) / np.power((1 + risk_adjusted_discount_rate), times[i])
            #             Used for either Annual or Semi-Annual Cashflows
            else:
                prob_default_exp += (
                    np.power((1 - P), times[i - 1])
                    * (cashflows[i] * (1 - P) + principal_payment * recovery_rate * P)
                ) / np.power((1 + risk_adjusted_discount_rate), times[i])

    prob_default_exp = prob_default_exp - price
    implied_prob_default = solve(prob_default_exp, P)
    implied_prob_default = round(float(implied_prob_default[0]) * 100, 2)

    if implied_prob_default < 0:
        return 0.0
    else:
        return implied_prob_default
```

Understand all of the code above: how the function works, how the methods work (here and in general).  Also, see the required reading section "A.7.5 Solving Equations Symbolically" and "A.7.6. Symbolic Plotting" from the following website, [which shows you how powerful and easy to use the `SymPy` library is.](https://numericalmethodssullivan.github.io/ch-python.html#solving-equations-symbolically)

```python
# Variables defined for bonds_probability_of_default function
principal_payment = 100
recovery_rate = 0.40
P = symbols("P")
```

We are now ready to run the *bonds_probability_of_default* function to calculate the market-implied probability of default for the chosen corporate bonds.
```python
bond_df_result.head(1)
```

```python
# This calculation may take some time if there are many coupon payments
bond_df_result.head(1).apply(
    lambda row: bonds_probability_of_default(
        row["Coupon"],
        row["Maturity Years"],
        row["Price"],
        principal_payment,
        risk_adjusted_discount_rate,
    ),
    axis=1,
)

bond_df_result.head(1)
```

###### 5.3.2. Relevant and Essential Python: Control Flow, Data Types, and Apply

[Read sections 4.7 and 4.8 of this website.](https://docs.python.org/3/tutorial/controlflow.html)

[Read section 5.6 of this website.](https://python-programming.quantecon.org/python_essentials.html#id7)

[Read this website.](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html)

These resources will help you understand the dense line of code above.

###### 5.2.3. Conclusion

In this lesson, we used the inputs we found in the previous lessons to finally estimate the probability of default for the bond issuer of our choice. We had to provide an assumed recovery rate, and then use a solver (the "solve" method) embedded in the *bonds probability of default* function, to find the probability of default implied by the price of the relevant bonds.

In the next lesson, we look at the ratings for these bonds provided by the ratings agencies. We will download the transition matrices (which include the probability of default for each rating) and compare the probability of default (PD) that we calculated in this lesson to the PD associated with the ratings agencies' ratings.


* ***References**

	* "More Control Flow Tools." Python.org.  https://docs.python.org/3/tutorial/controlflow.html
	
	* Sargent, Thomas J., and John Stachurski. "Python Programming for Finance and Economics." QuantEcon.org, https://python-programming.quantecon.org/python_essentials.html#id7
	
	* "Pandas.DataFrame.apply." Pandas.pydata.org. https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html



##### 5.4. Plotting
###### Required Readings

Required readings for this program are open access, which means you should be able to access them at no cost. The link provided in the citation will take you directly to the reading or to a page where you can download it.

1.  Coleman, Chase et al. "GroupBy." QuantEcon Data Science. [https://datascience.quantecon.org/pandas/groupby.html](https://datascience.quantecon.org/pandas/groupby.html).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 20 minutes
2.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.00-Introduction-To-Matplotlib.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.00-Introduction-To-Matplotlib.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 10 minutes
3.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.01-Simple-Line-Plots.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.01-Simple-Line-Plots.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 15 minutes
4.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.02-Simple-Scatter-Plots.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.02-Simple-Scatter-Plots.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 15 minutes
5.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.06-Customizing-Legends.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.06-Customizing-Legends.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 15 minutes
6.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.08-Multiple-Subplots.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.08-Multiple-Subplots.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 15 minutes
7.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.09-Text-and-Annotation.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.09-Text-and-Annotation.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 15 minutes
8.  jakevdp. "PythonDataScienceHandbook." _GitHub_. [https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.10-Customizing-Ticks.ipynb](https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.10-Customizing-Ticks.ipynb).
    
    -   **Required pages:** All
    -   **Estimated reading time:** 15 minutes
copy the below excels and paste into tableconvert
###### CSV: transition-matrix
|    | From/to                                                                                                                                                                                          | AAA                                                                                                                                                                                              | AA+                                                                                                                                                                                              | AA                                                                                                                                                                                               | AA-                                                                                                                                                                                              | A+                                                                                                                                                                                               | A                                                                                                                                                                                                | A-                                                                                                                                                                                               | BBB+                                                                                                                                                                                             | BBB                                                                                                                                                                                              | BBB-                                                                                                                                                                                             | BB+                                                                                                                                                                                              | BB                                                                                                                                                                                               | BB-                                                                                                                                                                                              | B+                                                                                                                                                                                               | B                                                                                                                                                                                                | B-                                                                                                                                                                                               | CCC                                                                                                                                                                                              | D                                                                                                                                                                                                | NR                                                                                                                                                                                               | Unnamed: 20_level_1                                                                                                                                                                              | Unnamed: 21_level_1                                                                                                                                                                              | Unnamed: 22_level_1                                                                                                                                                                              | Unnamed: 23_level_1                                                                                                                                                                              | Unnamed: 24_level_1                                                                                                                                                                              | Unnamed: 25_level_1                                                                                                                                                                              | Unnamed: 26_level_1                                                                                                                                                                              | Unnamed: 27_level_1                                                                                                                                                                              | Unnamed: 28_level_1                                                                                                                                                                              | Unnamed: 29_level_1                                                                                                                                                                              | Unnamed: 30_level_1                                                                                                                                                                              | Unnamed: 31_level_1                                                                                                                                                                              | Unnamed: 32_level_1                                                                                                                                                                              | Unnamed: 33_level_1                                                                                                                                                                              | Unnamed: 34_level_1                                                                                                                                                                              | Unnamed: 35_level_1                                                                                                                                                                              | Unnamed: 36_level_1                                                                                                                                                                              | Unnamed: 37_level_1                                                                                                                                                                              | Unnamed: 38_level_1                                                                                                                                                                              | Unnamed: 39_level_1                                                                                                                                                                              | Unnamed: 40_level_1                                                                                                                                                                              |
|----|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | AAA                                                                                                                                                                                              | 87.03                                                                                                                                                                                            | 5.89                                                                                                                                                                                             | 2.51                                                                                                                                                                                             | 0.69                                                                                                                                                                                             | 0.16                                                                                                                                                                                             | 0.24                                                                                                                                                                                             | 0.13                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.05                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.05                                                                                                                                                                                             | 0                                                                                                                                                                                                | 3.12                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 2  |                                                                                                                                                                                                  | -7.17                                                                                                                                                                                            | -6.21                                                                                                                                                                                            | -3.19                                                                                                                                                                                            | -1.04                                                                                                                                                                                            | -0.45                                                                                                                                                                                            | -0.56                                                                                                                                                                                            | -0.34                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.25                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.17                                                                                                                                                                                            | -0.19                                                                                                                                                                                            | -0.14                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.17                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.34                                                                                                                                                                                            | 0                                                                                                                                                                                                | -2.42                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 3  | AA+                                                                                                                                                                                              | 2.31                                                                                                                                                                                             | 78.94                                                                                                                                                                                            | 10.91                                                                                                                                                                                            | 3.54                                                                                                                                                                                             | 0.71                                                                                                                                                                                             | 0.33                                                                                                                                                                                             | 0.19                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.09                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 2.88                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 4  |                                                                                                                                                                                                  | -3.78                                                                                                                                                                                            | -11.46                                                                                                                                                                                           | -7.3                                                                                                                                                                                             | -4.08                                                                                                                                                                                            | -2.32                                                                                                                                                                                            | -0.81                                                                                                                                                                                            | -0.47                                                                                                                                                                                            | -0.24                                                                                                                                                                                            | -0.66                                                                                                                                                                                            | -0.22                                                                                                                                                                                            | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -2.97                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 5  | AA                                                                                                                                                                                               | 0.42                                                                                                                                                                                             | 1.31                                                                                                                                                                                             | 80.76                                                                                                                                                                                            | 8.53                                                                                                                                                                                             | 2.72                                                                                                                                                                                             | 1.15                                                                                                                                                                                             | 0.36                                                                                                                                                                                             | 0.39                                                                                                                                                                                             | 0.13                                                                                                                                                                                             | 0.08                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.02                                                                                                                                                                                             | 0.02                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.02                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.02                                                                                                                                                                                             | 3.96                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 6  |                                                                                                                                                                                                  | -0.51                                                                                                                                                                                            | -1.58                                                                                                                                                                                            | -8.91                                                                                                                                                                                            | -6.18                                                                                                                                                                                            | -2.59                                                                                                                                                                                            | -1.22                                                                                                                                                                                            | -0.58                                                                                                                                                                                            | -0.81                                                                                                                                                                                            | -0.35                                                                                                                                                                                            | -0.24                                                                                                                                                                                            | -0.16                                                                                                                                                                                            | -0.12                                                                                                                                                                                            | -0.1                                                                                                                                                                                             | -0.12                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.09                                                                                                                                                                                            | -0.15                                                                                                                                                                                            | -0.08                                                                                                                                                                                            | -2.57                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 7  | AA-                                                                                                                                                                                              | 0.04                                                                                                                                                                                             | 0.11                                                                                                                                                                                             | 3.77                                                                                                                                                                                             | 78.8                                                                                                                                                                                             | 9.68                                                                                                                                                                                             | 2.19                                                                                                                                                                                             | 0.6                                                                                                                                                                                              | 0.25                                                                                                                                                                                             | 0.15                                                                                                                                                                                             | 0.07                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.08                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 4.18                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 8  |                                                                                                                                                                                                  | -0.13                                                                                                                                                                                            | -0.3                                                                                                                                                                                             | -4.26                                                                                                                                                                                            | -7.43                                                                                                                                                                                            | -4.82                                                                                                                                                                                            | -2.57                                                                                                                                                                                            | -0.82                                                                                                                                                                                            | -0.48                                                                                                                                                                                            | -0.43                                                                                                                                                                                            | -0.24                                                                                                                                                                                            | -0.2                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.14                                                                                                                                                                                            | -0.37                                                                                                                                                                                            | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.1                                                                                                                                                                                             | -2.02                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 9  | A+                                                                                                                                                                                               | 0                                                                                                                                                                                                | 0.06                                                                                                                                                                                             | 0.44                                                                                                                                                                                             | 4.44                                                                                                                                                                                             | 78.38                                                                                                                                                                                            | 8.73                                                                                                                                                                                             | 2.15                                                                                                                                                                                             | 0.61                                                                                                                                                                                             | 0.34                                                                                                                                                                                             | 0.09                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 0.09                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.07                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.05                                                                                                                                                                                             | 4.45                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 10 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | -0.19                                                                                                                                                                                            | -0.68                                                                                                                                                                                            | -2.5                                                                                                                                                                                             | -5.85                                                                                                                                                                                            | -3.23                                                                                                                                                                                            | -1.48                                                                                                                                                                                            | -0.65                                                                                                                                                                                            | -0.43                                                                                                                                                                                            | -0.19                                                                                                                                                                                            | -0.16                                                                                                                                                                                            | -0.25                                                                                                                                                                                            | -0.05                                                                                                                                                                                            | -0.19                                                                                                                                                                                            | -0.13                                                                                                                                                                                            | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.14                                                                                                                                                                                            | -1.84                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 11 | A                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.04                                                                                                                                                                                             | 0.22                                                                                                                                                                                             | 0.41                                                                                                                                                                                             | 5.32                                                                                                                                                                                             | 78.88                                                                                                                                                                                            | 6.74                                                                                                                                                                                             | 2.38                                                                                                                                                                                             | 0.86                                                                                                                                                                                             | 0.27                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 0.1                                                                                                                                                                                              | 0.06                                                                                                                                                                                             | 0.08                                                                                                                                                                                             | 0.02                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.01                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 4.42                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 12 |                                                                                                                                                                                                  | -0.13                                                                                                                                                                                            | -0.13                                                                                                                                                                                            | -0.5                                                                                                                                                                                             | -0.48                                                                                                                                                                                            | -2.01                                                                                                                                                                                            | -5.34                                                                                                                                                                                            | -3.03                                                                                                                                                                                            | -1.72                                                                                                                                                                                            | -0.91                                                                                                                                                                                            | -0.38                                                                                                                                                                                            | -0.19                                                                                                                                                                                            | -0.27                                                                                                                                                                                            | -0.29                                                                                                                                                                                            | -0.28                                                                                                                                                                                            | -0.09                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.05                                                                                                                                                                                            | -0.12                                                                                                                                                                                            | -2.17                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 13 | A-                                                                                                                                                                                               | 0.04                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 0.15                                                                                                                                                                                             | 0.42                                                                                                                                                                                             | 6.49                                                                                                                                                                                             | 78.12                                                                                                                                                                                            | 7.23                                                                                                                                                                                             | 1.98                                                                                                                                                                                             | 0.57                                                                                                                                                                                             | 0.13                                                                                                                                                                                             | 0.13                                                                                                                                                                                             | 0.11                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 0.02                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 4.34                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 14 |                                                                                                                                                                                                  | -0.19                                                                                                                                                                                            | -0.05                                                                                                                                                                                            | -0.15                                                                                                                                                                                            | -0.27                                                                                                                                                                                            | -0.61                                                                                                                                                                                            | -3.08                                                                                                                                                                                            | -6.14                                                                                                                                                                                            | -3.07                                                                                                                                                                                            | -1.56                                                                                                                                                                                            | -0.61                                                                                                                                                                                            | -0.32                                                                                                                                                                                            | -0.34                                                                                                                                                                                            | -0.23                                                                                                                                                                                            | -0.29                                                                                                                                                                                            | -0.07                                                                                                                                                                                            | -0.08                                                                                                                                                                                            | -0.14                                                                                                                                                                                            | -0.18                                                                                                                                                                                            | -1.8                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 15 | BBB+                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.01                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 0.2                                                                                                                                                                                              | 0.74                                                                                                                                                                                             | 7.13                                                                                                                                                                                             | 75.83                                                                                                                                                                                            | 7.98                                                                                                                                                                                             | 1.56                                                                                                                                                                                             | 0.36                                                                                                                                                                                             | 0.29                                                                                                                                                                                             | 0.13                                                                                                                                                                                             | 0.15                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 0.02                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 5.23                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 16 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | -0.05                                                                                                                                                                                            | -0.15                                                                                                                                                                                            | -0.17                                                                                                                                                                                            | -0.42                                                                                                                                                                                            | -0.96                                                                                                                                                                                            | -2.79                                                                                                                                                                                            | -6.31                                                                                                                                                                                            | -3.28                                                                                                                                                                                            | -1.42                                                                                                                                                                                            | -0.51                                                                                                                                                                                            | -0.56                                                                                                                                                                                            | -0.21                                                                                                                                                                                            | -0.4                                                                                                                                                                                             | -0.29                                                                                                                                                                                            | -0.09                                                                                                                                                                                            | -0.17                                                                                                                                                                                            | -0.26                                                                                                                                                                                            | -1.9                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 17 | BBB                                                                                                                                                                                              | 0.01                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.04                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 0.31                                                                                                                                                                                             | 1                                                                                                                                                                                                | 7.73                                                                                                                                                                                             | 76                                                                                                                                                                                               | 6.11                                                                                                                                                                                             | 1.34                                                                                                                                                                                             | 0.58                                                                                                                                                                                             | 0.27                                                                                                                                                                                             | 0.22                                                                                                                                                                                             | 0.11                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.16                                                                                                                                                                                             | 5.9                                                                                                                                                                                              |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 18 |                                                                                                                                                                                                  | -0.07                                                                                                                                                                                            | -0.07                                                                                                                                                                                            | -0.13                                                                                                                                                                                            | -0.12                                                                                                                                                                                            | -0.21                                                                                                                                                                                            | -0.67                                                                                                                                                                                            | -0.96                                                                                                                                                                                            | -3.09                                                                                                                                                                                            | -5.01                                                                                                                                                                                            | -2.3                                                                                                                                                                                             | -1.05                                                                                                                                                                                            | -0.61                                                                                                                                                                                            | -0.46                                                                                                                                                                                            | -0.44                                                                                                                                                                                            | -0.38                                                                                                                                                                                            | -0.1                                                                                                                                                                                             | -0.12                                                                                                                                                                                            | -0.27                                                                                                                                                                                            | -2.03                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 19 | BBB-                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.02                                                                                                                                                                                             | 0.04                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 0.14                                                                                                                                                                                             | 0.25                                                                                                                                                                                             | 1.17                                                                                                                                                                                             | 9.31                                                                                                                                                                                             | 72.4                                                                                                                                                                                             | 5.47                                                                                                                                                                                             | 2.08                                                                                                                                                                                             | 0.83                                                                                                                                                                                             | 0.36                                                                                                                                                                                             | 0.22                                                                                                                                                                                             | 0.16                                                                                                                                                                                             | 0.21                                                                                                                                                                                             | 0.25                                                                                                                                                                                             | 7                                                                                                                                                                                                |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 20 |                                                                                                                                                                                                  | -0.07                                                                                                                                                                                            | -0.05                                                                                                                                                                                            | -0.06                                                                                                                                                                                            | -0.19                                                                                                                                                                                            | -0.17                                                                                                                                                                                            | -0.38                                                                                                                                                                                            | -0.52                                                                                                                                                                                            | -1.13                                                                                                                                                                                            | -3.01                                                                                                                                                                                            | -5.11                                                                                                                                                                                            | -2.65                                                                                                                                                                                            | -1.46                                                                                                                                                                                            | -0.75                                                                                                                                                                                            | -0.72                                                                                                                                                                                            | -0.46                                                                                                                                                                                            | -0.43                                                                                                                                                                                            | -0.54                                                                                                                                                                                            | -0.39                                                                                                                                                                                            | -2.12                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 21 | BB+                                                                                                                                                                                              | 0.04                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.08                                                                                                                                                                                             | 0.08                                                                                                                                                                                             | 0.41                                                                                                                                                                                             | 1.59                                                                                                                                                                                             | 11.33                                                                                                                                                                                            | 65.29                                                                                                                                                                                            | 7.42                                                                                                                                                                                             | 2.61                                                                                                                                                                                             | 0.95                                                                                                                                                                                             | 0.53                                                                                                                                                                                             | 0.24                                                                                                                                                                                             | 0.36                                                                                                                                                                                             | 0.31                                                                                                                                                                                             | 8.7                                                                                                                                                                                              |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 22 |                                                                                                                                                                                                  | -0.21                                                                                                                                                                                            | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.12                                                                                                                                                                                            | -0.1                                                                                                                                                                                             | -0.37                                                                                                                                                                                            | -0.27                                                                                                                                                                                            | -0.69                                                                                                                                                                                            | -1.82                                                                                                                                                                                            | -4.19                                                                                                                                                                                            | -6.55                                                                                                                                                                                            | -3.91                                                                                                                                                                                            | -1.93                                                                                                                                                                                            | -1.55                                                                                                                                                                                            | -1.05                                                                                                                                                                                            | -0.37                                                                                                                                                                                            | -0.9                                                                                                                                                                                             | -0.6                                                                                                                                                                                             | -2.6                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 23 | BB                                                                                                                                                                                               | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.06                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.16                                                                                                                                                                                             | 0.47                                                                                                                                                                                             | 2                                                                                                                                                                                                | 9.44                                                                                                                                                                                             | 65.41                                                                                                                                                                                            | 8.46                                                                                                                                                                                             | 2.22                                                                                                                                                                                             | 1.02                                                                                                                                                                                             | 0.31                                                                                                                                                                                             | 0.52                                                                                                                                                                                             | 0.51                                                                                                                                                                                             | 9.33                                                                                                                                                                                             |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 24 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.2                                                                                                                                                                                             | -0.06                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.35                                                                                                                                                                                            | -0.21                                                                                                                                                                                            | -0.4                                                                                                                                                                                             | -0.83                                                                                                                                                                                            | -2.14                                                                                                                                                                                            | -4.03                                                                                                                                                                                            | -5.32                                                                                                                                                                                            | -3.37                                                                                                                                                                                            | -1.46                                                                                                                                                                                            | -1.26                                                                                                                                                                                            | -0.56                                                                                                                                                                                            | -0.94                                                                                                                                                                                            | -0.66                                                                                                                                                                                            | -2.97                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 25 | BB-                                                                                                                                                                                              | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.01                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.09                                                                                                                                                                                             | 0.23                                                                                                                                                                                             | 0.35                                                                                                                                                                                             | 1.69                                                                                                                                                                                             | 9.57                                                                                                                                                                                             | 63.71                                                                                                                                                                                            | 8.42                                                                                                                                                                                             | 3.04                                                                                                                                                                                             | 0.81                                                                                                                                                                                             | 0.66                                                                                                                                                                                             | 0.91                                                                                                                                                                                             | 10.42                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 26 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.09                                                                                                                                                                                            | -0.08                                                                                                                                                                                            | -0.07                                                                                                                                                                                            | -0.27                                                                                                                                                                                            | -0.24                                                                                                                                                                                            | -0.42                                                                                                                                                                                            | -0.61                                                                                                                                                                                            | -1.62                                                                                                                                                                                            | -3.93                                                                                                                                                                                            | -5.36                                                                                                                                                                                            | -3.64                                                                                                                                                                                            | -1.53                                                                                                                                                                                            | -0.77                                                                                                                                                                                            | -0.81                                                                                                                                                                                            | -1.4                                                                                                                                                                                             | -2.49                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 27 | B+                                                                                                                                                                                               | 0                                                                                                                                                                                                | 0.01                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.06                                                                                                                                                                                             | 0.04                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 0.31                                                                                                                                                                                             | 1.42                                                                                                                                                                                             | 8.17                                                                                                                                                                                             | 62.91                                                                                                                                                                                            | 9.2                                                                                                                                                                                              | 2.51                                                                                                                                                                                             | 1.71                                                                                                                                                                                             | 1.98                                                                                                                                                                                             | 11.45                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 28 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | -0.06                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.14                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.09                                                                                                                                                                                            | -0.2                                                                                                                                                                                             | -0.13                                                                                                                                                                                            | -0.16                                                                                                                                                                                            | -0.21                                                                                                                                                                                            | -0.35                                                                                                                                                                                            | -1.1                                                                                                                                                                                             | -3.33                                                                                                                                                                                            | -5.6                                                                                                                                                                                             | -3.6                                                                                                                                                                                             | -1.24                                                                                                                                                                                            | -1.57                                                                                                                                                                                            | -2.01                                                                                                                                                                                            | -2.64                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 29 | B                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.01                                                                                                                                                                                             | 0.01                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0.04                                                                                                                                                                                             | 0.02                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.11                                                                                                                                                                                             | 0.23                                                                                                                                                                                             | 1.09                                                                                                                                                                                             | 7.38                                                                                                                                                                                             | 62                                                                                                                                                                                               | 9.32                                                                                                                                                                                             | 3.85                                                                                                                                                                                             | 3.2                                                                                                                                                                                              | 12.63                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 30 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.08                                                                                                                                                                                            | -0.06                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.19                                                                                                                                                                                            | -0.35                                                                                                                                                                                            | -0.07                                                                                                                                                                                            | -0.28                                                                                                                                                                                            | -0.1                                                                                                                                                                                             | -0.28                                                                                                                                                                                            | -0.53                                                                                                                                                                                            | -1.18                                                                                                                                                                                            | -3.16                                                                                                                                                                                            | -6.74                                                                                                                                                                                            | -3.65                                                                                                                                                                                            | -3.04                                                                                                                                                                                            | -4.04                                                                                                                                                                                            | -2.56                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 31 | B-                                                                                                                                                                                               | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.02                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.06                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.1                                                                                                                                                                                              | 0.08                                                                                                                                                                                             | 0.13                                                                                                                                                                                             | 0.46                                                                                                                                                                                             | 2.18                                                                                                                                                                                             | 10.06                                                                                                                                                                                            | 54.63                                                                                                                                                                                            | 11.7                                                                                                                                                                                             | 6.49                                                                                                                                                                                             | 14.02                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 32 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.29                                                                                                                                                                                            | -0.28                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.31                                                                                                                                                                                            | -0.17                                                                                                                                                                                            | -0.42                                                                                                                                                                                            | -0.43                                                                                                                                                                                            | -0.81                                                                                                                                                                                            | -0.85                                                                                                                                                                                            | -2.21                                                                                                                                                                                            | -4.89                                                                                                                                                                                            | -6.85                                                                                                                                                                                            | -3.76                                                                                                                                                                                            | -5.99                                                                                                                                                                                            | -3.82                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 33 | CCC/C                                                                                                                                                                                            | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0.03                                                                                                                                                                                             | 0                                                                                                                                                                                                | 0.08                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.08                                                                                                                                                                                             | 0.05                                                                                                                                                                                             | 0.03                                                                                                                                                                                             | 0.16                                                                                                                                                                                             | 0.4                                                                                                                                                                                              | 0.98                                                                                                                                                                                             | 2.57                                                                                                                                                                                             | 9.41                                                                                                                                                                                             | 43.64                                                                                                                                                                                            | 27.08                                                                                                                                                                                            | 15.45                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 34 |                                                                                                                                                                                                  | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | 0                                                                                                                                                                                                | -0.22                                                                                                                                                                                            | 0                                                                                                                                                                                                | -0.36                                                                                                                                                                                            | -0.45                                                                                                                                                                                            | -0.31                                                                                                                                                                                            | -0.36                                                                                                                                                                                            | -0.22                                                                                                                                                                                            | -0.49                                                                                                                                                                                            | -0.73                                                                                                                                                                                            | -1.48                                                                                                                                                                                            | -2.88                                                                                                                                                                                            | -5.41                                                                                                                                                                                            | -8.42                                                                                                                                                                                            | -10.5                                                                                                                                                                                            | -5.09                                                                                                                                                                                            |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |                                                                                                                                                                                                  |
| 35 | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. | NR--Not rated. Note: Numbers in parentheses are weighted standard deviations, weighted by the issuer base. Sources: S&P Global Ratings Research and S&P Global Market Intelligence's CreditPro®. |




###### CSV: bond-prices
|   | Issuer Name                  | Symbol     | Callable | Sub-Product Type | Coupon | Maturity   | Moody's® | S&P  | Price   |
|---|------------------------------|------------|----------|------------------|--------|------------|----------|------|---------|
| 1 | HESS CORP                    | HES.GH     | Yes      | Corporate Bond   | 6.000  | 01/15/2040 | Baa3     | BBB- | 103.276 |
| 2 | HESS CORP                    | HES.GI     | Yes      | Corporate Bond   | 5.600  | 02/15/2041 | Baa3     | BBB- | 98.664  |
| 3 | HESS CORP                    | HES4136877 | Yes      | Corporate Bond   | 3.500  | 07/15/2024 | Baa3     | BBB- | 98.772  |
| 4 | HESS CORP                    | HES4405829 | Yes      | Corporate Bond   | 4.300  | 04/01/2027 | Baa3     | BBB- | 99.512  |
| 5 | HESS CORP                    | HES4405830 | Yes      | Corporate Bond   | 5.800  | 04/01/2047 | Baa3     | BBB- | 101.269 |
| 6 | HESS MIDSTREAM OPERATIONS LP | HES5392919 | Yes      | Corporate Bond   | 5.500  | 10/15/2030 | Ba2      | BB+  | 89.594  |
| 7 | HESS MIDSTREAM OPERATIONS LP | HES4567499 | Yes      | Corporate Bond   | 5.625  | 02/15/2026 | WR       | BB+  | 104.500 |
| 8 | HESS MIDSTREAM OPERATIONS LP | HES4927355 | Yes      | Corporate Bond   | 5.625  | 02/15/2026 |          | BB+  | 95.520  |
| 9 | HESS MIDSTREAM OPERATIONS LP | HES5233164 | Yes      | Corporate Bond   | 4.250  | 02/15/2030 | Ba2      | BB+  | 84.818  |



|  |  |
|:---|:---|
|**Reading Time** |  30 minutes |
|**Prior Knowledge** | Ratings  |
|**Keywords** |Transition matrix, Loss Given Default (LGD), Matplotlib library |   	

---


*In this lesson, we compare the probabilities of default (PDs) that we estimated in the last lesson to ratings-implied PDs. We can do this because we will download the ratings agency transition matrix, which includes PD. We will also note that the PD increases with maturity by graphing, which means we will practice our graphing skills*.

**Note:** The code that was introduced in the previous lesson is below, followed by the new code and text for this lesson.

```python
# Python libraries to install
# Lesson 1
import time
from datetime import date
from datetime import datetime as dt
from datetime import timedelta

# Lesson 4
import matplotlib.pyplot as plt

# Lesson 2
import numpy as np
import pandas as pd
import pandas_datareader as dr
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import Select, WebDriverWait

# Lesson 3
from sympy import solve, symbols
from webdriver_manager.chrome import ChromeDriverManager
```

```python
# Required
company_ticker = "HES"
# or Try:
# 'F'
# 'KHC'
# 'DVN'

# Optional
company_name = "Hess"
# or Try:
# 'Ford Motor'
# 'Kraft Heinz Co'
# 'Devon Energy'

# Optional Input Choices:
# ALL, Annual, Anytime, Bi-Monthly, Monthly, N/A, None, Pays At Maturity, Quarterly, Semi-Annual, Variable
coupon_frequency = "Semi-Annual"
```

```python
scrape_new_data = False

if scrape_new_data:
    # Selenium script
    options = Options()
    options.add_argument("--headless")
    options.add_argument("--no-sandbox")
    options.add_argument("--disable-dev-shm-usage")
    driver = webdriver.Chrome(
        service=Service(ChromeDriverManager().install()), options=options
    )

    # store starting time
    begin = time.time()

    # FINRA's TRACE Bond Center
    driver.get("http://finra-markets.morningstar.com/BondCenter/Results.jsp")

    # click agree
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, ".button_blue.agree"))
    ).click()

    # click edit search
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, "a.qs-ui-btn.blue"))
    ).click()

    # input Issuer Name
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, "input[id=firscreener-issuer]")
        )
    )
    inputElement = driver.find_element_by_id("firscreener-issuer")
    inputElement.send_keys(company_name)

    # input Symbol
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.CSS_SELECTOR, "input[id=firscreener-cusip]"))
    )
    inputElement = driver.find_element_by_id("firscreener-cusip")
    inputElement.send_keys(company_ticker)

    # click advanced search
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, "a.ms-display-switcher.hide"))
    ).click()

    # input Coupon Frequency
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, "select[name=interestFrequency]")
        )
    )
    Select(
        (driver.find_elements_by_css_selector("select[name=interestFrequency]"))[0]
    ).select_by_visible_text(coupon_frequency)

    # click show results
    WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CSS_SELECTOR, "input.button_blue[type=submit]"))
    ).click()

    # wait for results
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located(
            (By.CSS_SELECTOR, ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn")
        )
    )

    # create DataFrame from scrape
    frames = []
    for page in range(1, 11):
        bonds = []
        WebDriverWait(driver, 10).until(
            EC.presence_of_element_located(
                (By.CSS_SELECTOR, (f"a.qs-pageutil-btn[value='{str(page)}']"))
            )
        )  # wait for page marker to be on expected page
        time.sleep(2)

        headers = [
            title.text
            for title in driver.find_elements_by_css_selector(
                ".rtq-grid-row.rtq-grid-rzrow .rtq-grid-cell-ctn"
            )[1:]
        ]

        tablerows = driver.find_elements_by_css_selector(
            "div.rtq-grid-bd > div.rtq-grid-row"
        )
        for tablerow in tablerows:
            tablerowdata = tablerow.find_elements_by_css_selector("div.rtq-grid-cell")
            bond = [item.text for item in tablerowdata[1:]]
            bonds.append(bond)

            # Convert to DataFrame
            df = pd.DataFrame(bonds, columns=headers)

        frames.append(df)

        try:
            driver.find_element_by_css_selector("a.qs-pageutil-next").click()
        except:  # noqa E722
            break

    bond_prices_df = pd.concat(frames)

    # store end time
    end = time.time()

    # total time taken
    print(f"Total runtime of the program is {end - begin} seconds")

else:
    bond_prices_df = pd.read_csv("bond-prices.csv")

bond_prices_df
```

```python
def bond_dataframe_filter(df):
    # Drop bonds with missing yields and missing credit ratings
    df["Yield"].replace("", np.nan, inplace=True)
    df["Moody's®"].replace({"WR": np.nan, "": np.nan}, inplace=True)
    df["S&P"].replace({"NR": np.nan, "": np.nan}, inplace=True)
    df = df.dropna(subset=["Yield"])
    df = df.dropna(subset=["Moody's®"])
    df = df.dropna(subset=["S&P"])

    # Create Maturity Years column that aligns with Semi-Annual Payments from corporate bonds
    df["Yield"] = df["Yield"].astype(float)
    df["Coupon"] = df["Coupon"].astype(float)
    df["Price"] = df["Price"].astype(float)
    now = dt.strptime(date.today().strftime("%m/%d/%Y"), "%m/%d/%Y")
    df["Maturity"] = pd.to_datetime(df["Maturity"]).dt.strftime("%m/%d/%Y")
    daystillmaturity = []
    yearstillmaturity = []
    for maturity in df["Maturity"]:
        daystillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days)
        yearstillmaturity.append((dt.strptime(maturity, "%m/%d/%Y") - now).days / 360)
    df = df.reset_index(drop=True)
    df["Maturity"] = pd.Series(daystillmaturity)
    #         `df['Maturity Years'] = pd.Series(yearstillmaturity).round()` # Better for Annual Payments
    df["Maturity Years"] = (
        round(pd.Series(yearstillmaturity) / 0.5) * 0.5
    )  # Better for Semi-Annual Payments

    # Target bonds with short-term maturities
    df["Maturity"] = df["Maturity"].astype(float)
    # `df = df.loc[df['Maturity'] >= 0]`
    years_mask = (df["Maturity Years"] > 0) & (df["Maturity Years"] <= 5)
    df = df.loc[years_mask]
    return df
```

```python
bond_df_result = bond_dataframe_filter(bond_prices_df)
bond_df_result
```

```python
# Ten-Year Risk-free Rate
timespan = 100
current_date = date.today()
past_date = current_date - timedelta(days=timespan)
ten_year_risk_free_rate_df = dr.DataReader("^TNX", "yahoo", past_date, current_date)
ten_year_risk_free_rate = (
    ten_year_risk_free_rate_df.iloc[len(ten_year_risk_free_rate_df) - 1, 5]
) / 100
ten_year_risk_free_rate
```

```python
# Market Risk Premium
market_risk_premium = 0.0472
```

```python
# Market Equity Beta
stock_market_beta = 1
```

```python
# Market Rate of Return
market_rate_of_return = ten_year_risk_free_rate + (
    stock_market_beta * market_risk_premium
)
market_rate_of_return
```

```python
# One-Year Risk-free Rate
one_year_risk_free_rate = (1 + ten_year_risk_free_rate) ** (1 / 10) - 1
one_year_risk_free_rate
```

```python
# Vanguard Short-Term Corporate Bond Index Fund ETF Shares
bond_fund_ticker = "VCSH"
```

```python
# Download data for the bond fund and the market
market_data = dr.get_data_yahoo("SPY", past_date, current_date)  # the market
fund_data = dr.get_data_yahoo("VCSH", past_date, current_date)  # the bond fund
```

```python
# Approach #1 - Covariance/Variance Method:

# Calculate the covariance between the fund and the market -- this is the numerator in the Beta calculation
fund_market_cov = fund_data["Adj Close"].cov(market_data["Adj Close"])
print("covariance between fund and market: ", fund_market_cov)

# Calculate market (S&P) variance -- this is the denominator in the Beta calculation
market_var = market_data["Adj Close"].var()
print("market variance: ", market_var)

# Calculate Beta
bond_fund_beta_cv = fund_market_cov / market_var
print("bond fund beta (using covariance/variance): ", bond_fund_beta_cv)
```

```python
# Approach #2 - Correlation Method:

# Calculate the standard deviation of the market by taking the square root of the variance, for use in the denominator
market_stdev = market_var ** 0.5
print("market standard deviation: ", market_stdev)

# Calculate bond fund standard deviation, for use in the numerator

fund_stdev = fund_data["Adj Close"].std()
print("fund standard deviation: ", fund_stdev)

# Calculate Pearson correlation between bond fund and market (S&P), for use in the numerator
fund_market_Pearson_corr = fund_data["Adj Close"].corr(
    market_data["Adj Close"], method="pearson"
)
print("Pearson correlation between fund and market: ", fund_market_Pearson_corr)

# Calculate Beta
fund_beta_corr = fund_stdev * fund_market_Pearson_corr / market_stdev
print("bond fund beta (using correlation): ", fund_beta_corr)
```

```python
# Bond's Beta: use the result of either of the two above approaches, bond_fund_beta_cv or fund_beta_corr
bond_beta = fund_beta_corr
bond_beta
```

```python
# Expected Risk Premium
expected_risk_premium = (market_rate_of_return - one_year_risk_free_rate) * bond_beta
expected_risk_premium
```

```python
# One-Year Risk-free Rate (same code as above)
one_year_risk_free_rate = (1 + ten_year_risk_free_rate) ** (1 / 10) - 1
one_year_risk_free_rate
```

```python
# Risk-adjusted Discount Rate
risk_adjusted_discount_rate = one_year_risk_free_rate + expected_risk_premium
risk_adjusted_discount_rate
```

```python
def bonds_probability_of_default(
    coupon, maturity_years, bond_price, principal_payment, risk_adjusted_discount_rate
):

    price = bond_price
    prob_default_exp = 0

    #     `times = np.arange(1, maturity_years+1)` # For Annual Cashflows
    #     annual_coupon = coupon # For Annual Cashflows
    times = np.arange(0.5, (maturity_years - 0.5) + 1, 0.5)  # For Semi-Annual Cashflows
    semi_annual_coupon = coupon / 2  # For Semi-Annual Cashflows

    # Calculation of Expected Cash Flow
    cashflows = np.array([])
    for i in times[:-1]:
        #         cashflows = np.append(cashflows, annual_coupon) # For Annual Cashflows
        #     cashflows = np.append(cashflows, annual_coupon+principal_payment)#  For Annual Cashflows
        cashflows = np.append(
            cashflows, semi_annual_coupon
        )  # For Semi-Annual Cashflows
    cashflows = np.append(
        cashflows, semi_annual_coupon + principal_payment
    )  # For Semi-Annual Cashflows

    for i in range(len(times)):
        #         This code block is used if there is only one payment remaining
        if len(times) == 1:
            prob_default_exp += (
                cashflows[i] * (1 - P) + cashflows[i] * recovery_rate * P
            ) / np.power((1 + risk_adjusted_discount_rate), times[i])
        #         This code block is used if there are multiple payments remaining
        else:
            #             For Annual Cashflows
            #             if times[i] == 1:
            #                 prob_default_exp += ((cashflows[i]*(1-P) + principal_payment*recovery_rate*P) / \
            #                                     np.power((1 + risk_adjusted_discount_rate), times[i]))
            #             For Semi-Annual Cashflows
            if times[i] == 0.5:
                prob_default_exp += (
                    cashflows[i] * (1 - P) + principal_payment * recovery_rate * P
                ) / np.power((1 + risk_adjusted_discount_rate), times[i])
            #             Used for either Annual or Semi-Annual Cashflows
            else:
                prob_default_exp += (
                    np.power((1 - P), times[i - 1])
                    * (cashflows[i] * (1 - P) + principal_payment * recovery_rate * P)
                ) / np.power((1 + risk_adjusted_discount_rate), times[i])

    prob_default_exp = prob_default_exp - price
    implied_prob_default = solve(prob_default_exp, P)
    implied_prob_default = round(float(implied_prob_default[0]) * 100, 2)

    if implied_prob_default < 0:
        return 0.0
    else:
        return implied_prob_default
```

```python
# Variables defined for bonds_probability_of_default function
principal_payment = 100
recovery_rate = 0.40
P = symbols("P")
```

```python
# This calculation may take some time if there are many coupon payments
bond_df_result["Probability of Default %"] = bond_df_result.head(1).apply(
    lambda row: bonds_probability_of_default(
        row["Coupon"],
        row["Maturity Years"],
        row["Price"],
        principal_payment,
        risk_adjusted_discount_rate,
    ),
    axis=1,
)

bond_df_result.head(1)
```


###### 5.4.1. Credit Ratings
As you recall from the Financial Markets course, credit ratings are used for bonds issued by corporations and government entities as well as for asset-backed securities (ABS) and mortgage-backed securities (MBS). The three major global credit rating agencies are Moody’s Investors Service, Standard & Poor’s, and Fitch Ratings. Each provides credit quality ratings for issuers as well as specific issues. These are ordinal ratings focusing on the probability of default.

The credit rating agencies consider the expected loss given default (LGD) by means of **notching**, which is an adjustment to the issuer rating to reflect the priority of claim for specific debt issues of that issuer and to reflect any subordination. The issuer rating is typically for senior unsecured debt. The rating on subordinated debt is then adjusted, or “notched,” by lowering it one or two levels—for instance, from A+ down to A or further down to A–. This inclusion of loss given default in addition to the probability of default explains why they are called “credit ratings” and not just “default ratings.”

The rating agencies report transition matrices based on their historical data. A transition matrix shows the probability that a rating changes (or stays the same) in one year's time. (The probability that the rating changes to default is the probability of default.)

We can verify the accuracy of the market-implied default probabilities with these rating agencies' transition matrices. Using the code below, we can obtain the Standard & Poor’s Average One-Year Transition Rates For Global Corporates using historical data from 1981-2019 to verify the market-implied default probabilities calculated earlier.

###### 5.4.2. Plotting

To get ready for the graphing below, please make sure you do all the required readings for this lesson and lesson 3.

```python
def prob_default_term_structure(df):

    fig, (ax1, ax2) = plt.subplots(1, 2, clear=True)
    fig.subplots_adjust(wspace=0.5)
    Mgroups = df.groupby("Moody's®")
    ax1.clear()
    ax1.margins(0.5)
    ax1.set_xlabel("Days Until Maturity")
    ax1.set_ylabel("Probability of Default %")
    ax1.set_title("Moody's® Ratings")
    for name, group in Mgroups:
        ax1.plot(
            group["Maturity"],
            group["Probability of Default %"],
            marker="o",
            linestyle="",
            ms=12,
            label=name,
        )
    ax1.legend(numpoints=1, loc="upper left")

    SPgroups = df.groupby("S&P")
    ax2.clear()
    ax2.margins(0.5)
    ax2.set_xlabel("Days Until Maturity")
    ax2.set_ylabel("Probability of Default %")
    ax2.set_title("S&P Ratings")

    for name, group in SPgroups:
        ax2.plot(
            group["Maturity"],
            group["Probability of Default %"],
            marker="o",
            linestyle="",
            ms=12,
            label=name,
        )
    ax2.legend(numpoints=1, loc="upper left")
    plt
```

```python
prob_default_term_structure(bond_df_result)
```


###### 5.4.3. Downloading the Transition Matrix

```python
tgt_website = r"https://www.spglobal.com/ratings/en/research/articles/200429-default-transition-and-recovery-2019-annual-global-corporate-default-and-rating-transition-study-11444862"
```
```python
def get_transition_matrix(tgt_website):

    df_list = pd.read_html(tgt_website)
    matrix_result_df = df_list[22]

    return matrix_result_df


scrape_new_data = False
if scrape_new_data:
    transition_matrix_df = get_transition_matrix(tgt_website)
else:
    transition_matrix_df = pd.read_csv("transition-matrix.csv")
```

```
sp_clean_result_df = pd.DataFrame(transition_matrix_df.iloc[:34, :19].dropna(axis=0))
sp_clean_result_df
```

The above is the Standard & Poor’s 2019 transition matrix. It shows the probabilities of a particular rating transitioning to another over the course of the following year. An A-rated issuer has a 78.88% probability of remaining at that level, a 0.03% probability of moving up to AAA; a 0.22% probability of moving up to AA; an 0.86% probability of moving down to BBB; 0.10% down to BB; 0.02% to B, 0.01% to CCC, CC, or C; and 0.05% to D, where it is in default.

Using the Selenium script mentioned earlier to retrieve the Standard & Poor’s credit ratings, we can use the corporate bond's credit rating to determine the probability of a particular rating transitioning to D (default) during the next year according to the Standard & Poor’s 2019 transition matrix.

```python
# Will scrape the default probability for each rating

sp_rating_list = [
    "AAA",
    "AA+",
    "AA",
    "AA-",
    "A+",
    "A",
    "A-",
    "BBB+",
    "BBB",
    "BBB-",
    "BB+",
    "BB",
    "BB-",
    "B+",
    "B",
    "B-",
]

ccc_list = ["CCC+", "CCC", "CCC-", "CC+", "CC", "CC-", "C+", "C", "C-"]

sp_rating = None

for i in sp_rating_list:
    if bond_df_result["S&P"].iloc[0] == i:
        sp_rating = bond_df_result["S&P"].iloc[0]

if sp_rating is None:
    for i in ccc_list:
        if bond_df_result["S&P"].iloc[0] == i:
            sp_rating = "CCC/C"

sp_transition_dp = 0

for i in range(33):
    if transition_matrix_df.loc[i][0] == sp_rating:
        sp_transition_dp += float(sp_clean_result_df.loc[i][18])

sp_transition_dp
```


It appears that the market-implied probability of default we calculated for the nearest maturity corporate bond is close to the probability of default as determined from the historical data in the Standard & Poor’s 2019 transition matrix.
```python
# Compare the nearest maturity Market-implied probability of default with
# the historical probability of default in the Standard & Poor’s 2019 transition matrix
print(
    "Market-implied probability of default = %s"
    % (bond_df_result["Probability of Default %"].iloc[0])
    + "%"
)
print("Standard & Poor’s probability of default = %s" % (sp_transition_dp) + "%")
```

###### 5.4.4. Conclusion

In the example above, the bond valuation techniques using a risk-adjusted discount rate do a reasonably good job of estimating the market-implied default probabilities. We calculated the expected cash flow at each period by adding the product of the default payout and the probability of default (P) with the product of the promised payment (coupon payments and repayment of principal) and the probability of not defaulting (1-P). One reason for any differences between historical and market-implied default probabilities is that historical default probabilities do not include the default risk premium associated with uncertainty over the timing of possible default loss.

The model used here is very sensitive to the discount and recovery rates selected. For simplicity, we assume a flat government bond yield curve, but it could be upward or downward sloping. A more sophisticated and realistic model of the discount rates would require that they be calculated sequentially by a process known as “bootstrapping.” We also assume in this example that the recovery rate is 40%, but another possibility is to change the assumed recovery rate to either 30% or 60% of exposure. Another simplifying assumption is that recovery is instantaneous. In practice, lengthy time delays can occur between the event of default and eventual recovery of cash. Notice that we assume that the recovery rate applies to interest as well as principal.

Also, we assume that default occurs only on coupon payment dates and that default will not occur on date 0, the current date. Although we assumed the annual default probability is the same each year, this does not need to be the case.

Even with the assumptions made in this analysis, the market-implied probability of default model built here does a fairly good job at identifying risk of corporate defaults and may suffice for simply rank ordering firms by credit worthiness.

**References**

* Vanderplas, Jake. “04.00-Introduction-To-Matplotlib.ipynb.” *GitHub*, https://github.com/jakevdp/PythonDataScienceHandbook/blob/master/notebooks/04.00-Introduction-To-Matplotlib.ipynb
* Sargent, Thomas, and John Stachurski. "10. Matplotlib." *Python Programming for Economics and Finance*. https://python-programming.quantecon.org/matplotlib.html.
* Coleman, Chase, et al. "GroupBy." *QuantEcon DataScience.* https://datascience.quantecon.org/pandas/groupby.html


### Notes
[[GWP3-Financial data]]
###### 4. Options in python
required readings: functions in python , [python essentials](https://python-programming.quantecon.org/python_essentials.html#iterating): basic, skippable
##### takeaways from a fellow student
###### What are Options Payoffs?

**Overview**

The optionality characteristic of options results in a non-linear payoff for options. In simple words, it means that the losses for the buyer of an option are limited, however the profits are potentially unlimited. For a writer (seller), the payoff is exactly the opposite. His profits are limited to the option premium, however his losses are potentially unlimited. These nonlinear payoffs are fascinating as they lend themselves to be used to generate various payoffs by using combinations of options and the underlying. We look here at the six basic options payoffs (pay close attention to these pay-offs, since all the strategies in the book are derived out of these basic payoffs).

-   **Payoff profile of buyer of asset: Long asset**

In this basic position, an investor buys the [underlying asset](https://upstox.com/learning-center/futures-and-options/what-is-an-underlying-asset/), ABC Ltd. shares for instance, for Rs. 2220, and sells it at a future date at an unknown price, St. Once it is purchased, the investor is said to be "long" the asset.

-   **Payoff profile of seller of asset: Short asset**

In this basic position, an investor shorts the underlying asset, ABC Ltd. shares for instance, for Rs. 2220, and buys it back at a future date at an unknown price, St. Once it is sold, the investor is said to be "short" the asset.

-   **Payoff profile for buyer of call options: Long call**

A call option gives the buyer the right to buy the underlying asset at the [strike price](https://upstox.com/learning-center/futures-and-options/strike-price/) specified in the option. The profit/loss that the buyer makes on the option depends on the [spot price](https://upstox.com/learning-center/futures-and-options/what-is-spot-price/) of the underlying. If upon expiration, the spot price exceeds the strike price, he makes a profit. Higher the spot price, more is the profit he makes. If the spot price of the underlying is less than the strike price, he lets his option expire un-exercised. His loss in this case is the premium he paid for buying the option.

-   **Payoff profile for writer (seller) of call options: Short call**

A call option gives the buyer the right to buy the underlying asset at the strike price specified in the option. For selling the option, the writer of the option charges a premium. The profit/loss that the buyer makes on the option depends on the spot price of the underlying. Whatever is the buyer's profit is the seller's loss. If upon expiration, the spot price exceeds the strike price, the buyer will exercise the option on the writer. Hence as the spot price increases the writer of the option starts making losses. Higher the spot price, more is the loss he makes. If upon expiration the spot price of the underlying is less than the strike price, the buyer lets his option expire un-exercised and the writer gets to keep the premium.

-   **Payoff profile for buyer of put options: Long put**

A put option gives the buyer the right to sell the underlying asset at the strike price specified in the option. The profit/loss that the buyer makes on the option depends on the spot price of the underlying. If upon expiration, the spot price is below the strike price, he makes a profit. Lower the spot price, more is the profit he makes. If the spot price of the underlying is higher than the strike price, he lets his option expire un-exercised. His loss in this case is the premium he paid for buying the option.

-   **Payoff profile for writer (seller) of put options: Short put**

A put option gives the buyer the right to sell the underlying asset at the strike price specified in the option. For selling the option, the writer of the option charges a premium. The profit/loss that the buyer makes on the option depends on the spot price of the underlying. Whatever is the buyer's profit is the seller's loss. If upon expiration, the spot price happens to be below the strike price, the buyer will exercise the option on the writer. If upon expiration the spot price of the underlying is more than the strike price, the buyer lets his option un-exercised and the writer gets to keep the premium.