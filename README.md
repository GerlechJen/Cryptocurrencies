# Cryptocurrencies
## Overview

Bitcoin, due to its popularity, has caught a price jump making it unaffordable for many new investors. The good news, however, is that there are many more cryptocurrencies available at more affordable prices.  A prominent investment bank called Accountability Accounting, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. I have gotten the opportunity to pitch an investment in Cryptocurrency to Accountability Accounting. They have asked me to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

Data set of cryptocurrencies is available as a CSV file to be analyzed in any way I want. However, the data is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what I am looking for, I will use unsupervised machine learning to discover trends that will convince the firm to invest in these new cryptocurrencies. To group the cryptocurrencies, I will use a clustering algorithm then use data visualizations to share my findings with the board of Accountability Accounting.

## Results
To begin with, I preprocessed the data. I read it to a Pandas DataFrame. The original dataframe had 1252 rows and 6 columns. I kept all the cryptocurrencies that are being traded and have a working algorithm which reduced the rows to 1144. I then dropped teh IsTrading column and removed rows that have at least one null value. The data frame now had 685 rows and 5 columns. The DataFrame was filtered so it only had rows where coins are mined and this reduced the rows to 532.
rom this dataframe I created a new dataframe that held only the cryptocurrency names, and used the crypto_df DataFrame index as the index for this new DataFrame. Afterwards I removed the CoinName column from the crypto DataFrame since it was not going to be used on the clustering algorithm.
I further reduced the Data dimensions Using PCA
Then I clustered the Cryptocurrencies Using K-means
Finally I made Visualizing Cryptocurrencies Results





## Summary
