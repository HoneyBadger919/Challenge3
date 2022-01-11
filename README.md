# Challenge3 - Arbitrage Analysis Report

In this report there are some clarification regarding the Jupyter Notebook created from the challenge. Since many inputs and decision are on the analyst's choice (especially in the last part), reference here for explanations.

Throughout the Jupyter Notebook there are some clarification as well. Check out for "STUDENT'S NOTES" in the markdown sections.

---

## Technologies

Programming Language: **JupyterLab** loaded from the distribution [Anaconda 4.10.3](https://anaconda.org/anaconda/conda/files?version=4.10.3)

Operative system: Windows 10 (it may be working on MAC OS and Linux too but the software was not designed on these)

Libraries:
* [pandas 1.3.4](https://github.com/pandas-dev/pandas) - For DataFrame manipulation and plotting (already included in the Anaconda distribution)

---

## Analyze the Data

After computing the statistics for the whole period under consideration through the [describe()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html) function, by looking at the mean, we can see that on average Bitstamp's price is $10 higher than the one on Coinbase. 
Of course to get insights regarding the exploitation of arbitrage opportunities we must look at the data more closely.

By plotting the data in their entire period we can see that there is a huge spread at the end of January 2018, where Bitstamp prices are consistently higher than Coinbase prices. By plotting the month of January only we can see this even more closely.
By plotting the month of March instead, we can see that the spread is decreased, hence the price actions are more overlapped.

We go on plotting the price action of the 28th of January and this provides a clear picture of the spread that happened in that day. To get numeric metrics we compute the spread between the highest price and the lowest one, and by looking at the statistics we see that on average the spread during the day is $247.6, so enough to exploit arbitraging.

We plot other two daily dates: Februray 15th 2018 and March 31st 2018. In these two we can see from the plot instantly, and more carefully from the statistics, that the spread is very low.

## Calculate the Arbitrage Profits

For each of the three dates we compute the spread and then buy using a boolean vector we focus just on the minutes where the spread is positive. For the first and potential profitable date the price on Bitstamp is always higher and Coinbase's.
We go on computing the spread return, by dividing the profitable moments with the price of the exchange we're buying on, hence the least priced one.

To get a closer view of the potential profits in practice we take into account 1% of costs to carry out the trading strategy in each moment of the series, and so we consider the only moments when the spread return is higher than 1%.
No profitable trades were found with this condition in the middle and late date chosen from the dataset.

We then multiply the profitable trades (those returns higher than 1%) by the cost of the purchased Bitcoin, hence the price on the exchange we are buying. We can than plot this multiple trades to see how they are distributed.

By cumulating the profit of each trade along with time we can also plot the cumulative return which at the end of the day, by follow this theretical setup, leads us with a gross profit of $ 341,771.87.


