# Cryptocurrencies
## Overview

Bitcoin, due to its popularity, has caught a price jump making it unaffordable for many new investors. The good news, however, is that there are many more cryptocurrencies available at more affordable prices.  A prominent investment bank called Accountability Accounting, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. I have gotten the opportunity to pitch an investment in Cryptocurrency to Accountability Accounting. They have asked me to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

Data set of cryptocurrencies is available as a CSV file to be analyzed in any way I want. However, the data is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what I am looking for, I will use unsupervised machine learning to discover trends that will convince the firm to invest in these new cryptocurrencies. To group the cryptocurrencies, I will use a clustering algorithm then use data visualizations to share my findings with the board of Accountability Accounting.

## Results
To begin with, I preprocessed the data. I first of all read it to a Pandas DataFrame. This original dataframe had 1,252 rows and 6 columns. I kept all the cryptocurrencies that are being traded and have a working algorithm which reduced the rows to 1,144. I then dropped the 'IsTrading' column and removed rows that had at least one null value. The data frame now had 685 rows and 5 columns. The DataFrame was filtered so it only had rows where coins are mined and this reduced the rows to 532.
From this dataframe I created a new dataframe called names_df that held only the cryptocurrency names, and used the crypto_df DataFrame index as the index for this new DataFrame. Afterwards I removed the CoinName column from the crypto DataFrame since it was not going to be used on the clustering algorithm. The final dataframe obtained is shown below:

![image1](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/image1.png)

Using the get_dummies() method, I created variables for the two text features, 'Algorithm' and 'ProofType', and stored the resulting data in a new DataFrame named X. This dataframe had 532 rows and 98 columns. Then using the StandardScaler fit_transform() function, I standardized the features from the X DataFrame which completed the preprocessing step of my data.

Continuing with my tasks, I reduced the data dimensions using the Principal Component Analysis (PCA) algorithm. I reduced the dimensions of the X DataFrame to three principal components and placed these dimensions in a new DataFrame. This DataFrame named pcs_df included the following columns: PC 1, PC 2, and PC 3, and used the index of the crypto_df DataFrame as the index. The code used to obtain this datafrae is shown below:

``` python 
# Using PCA to reduce dimension to three principal components.
pca = PCA(n_components=3)
crypto_pca = pca.fit_transform(X_scaled)
# Create a DataFrame with the three principal components.
pcs_df = pd.DataFrame(data = crypto_pca, columns = ["PC 1", "PC 2", "PC 3"], index = crypto_df.index)
```

The pcs_df is also as shown:

![image2](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/image2.png)

It was then time to cluster the Cryptocurrencies using K-means algorithm. Using the pcs_df DataFrame, I created an elbow curve with hvPlot to find the best value for K.

![image3](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/Elbow_curve.png)



From the plot, the best value for K is 4. I then run the K-means algorithm to predict the K clusters for the cryptocurrencies’ data. Then I created a new data frame called clustered_df by concatenating the crypto data frame and pcs_df data frame on the same columns. The index used for this new data frame was same as the crypto_df data frame index. I added the CoinName column that holds the names of the cryptocurrencies, that was created earlier, to the clustered_df. I added another new column called 'Class' to the clustered_df that holds the predictions (model.labels_). The clustered dataframe is as shown:

![image4](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/clustered_df.png)


My final task on this project was to make visualizations of the cryptocurrencies results. I created a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three principal components PC 1, PC 2 and PC 3 from the clustered_df data frame. I added the 'CoinName' and 'Algorithm' columns to the hover_name and hover_data parameters, respectively, so each data point showed the CoinName and Algorithm on hover.

![image6](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/3d%20plot.png)


I also created a table with all the 532 currently tradable cryptocurrencies using the hvplot.table() function.

![image0](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/table.png)

Finally, I used the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of 0 and 1. Then I created a new DataFrame that contained the scaled data created and uses the clustered_df DataFrame index as its index. I then added the CoinName and Class columns from the clustered_df data frame to this new data frame. The data farame looks like this: 

![image7](https://github.com/GerlechJen/Credit_Risk_Analysis/blob/main/Images/table2.png)

Finally, using the above dataframe I create an hvplot scatter plot with "TotalCoinsMined" on the x axis,, "TotalCoinSupply" on the y axis and by="Class". I made the plot show the CoinName when a data point is hovered over.

![image8](https://github.com/GerlechJen/Cryptocurrencies/blob/main/Images/scatter%20plot.png)





## Summary

To summarize, the crypocurrencies were grouped into 3. 




----

**Completed by:** Jennifer Anno-Kusi

**Email:** jannokusi@gmail.com 
