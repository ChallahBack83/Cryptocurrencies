# Cryptocurrencies

## Overview

The goal of this project is to provide an analysis of cryptocurrencies for our client, Accountability Accounting, so they may carefully consider investing opportunities in a growing market.  Since we do not know what results we are looking for, we are using unsupervised learning to create clusters and group the hundreds of tradable cryptocurrencies into a classification system. In order to do this, we first must process and clean the data, reduce the dimensions and principal components, and visualize the new clusters in scatter charts as well as a sortable table.  To complete this process I will use Python, specifically StandardScaler, PCA, K-Means, MinMaxScaler, and Hvplot to visualize the results.

## Process

To begin the analysis, I started with cleaning and reducing the data. First, I reduced the cryptocurrencies to only ones that are currently trading, dropped any rows containing null values, and filtered out any where the Total Coins Mined was 0. After, preserving Coin Names in a new dataframe, I removed that column as well as the IsTrading Column to limit what data we will put into our model. Then, I converted the two rows with string data to numerical variables using get_dummies and scaled the new dataframe using StandardScaler.

## Results

After processing the data, reducing it to a manageable set for analysis, we are able to visualize the clusters based on the principal components createde using PCA.  See the 3d scatter plot below:

![3d_scatter](https://github.com/ChallahBack83/Cryptocurrencies/blob/main/Images/3d_scatter.png)

Through our elbow curve chart, we discovered that the best value for k (our number of clusters) should be 4, and we see 4 distinct clusters on the scatter plot.  However, we can note that one "cluster" is just a single point outlier, while another contains only a few data points.  The majority of our data points are clustered into two sets.

Using hvplot.table, I created a sortable table containing the Coin Name, Algorithm, ProofType, Total Coin Supply, Total Coins Mined, and the Class assignment generated through K-Means and plotted in the above 3d_scatter plot. Sorting the table by class, we can look for patterns in the different cryptocurrencies.  Here, we have the two smaller categories filtered to the top of the table:

![hvplot_table](https://github.com/ChallahBack83/Cryptocurrencies/blob/main/Images/hvplot_table.png)

Our stand alone point is BitTorrent, which also has the most Total Coins Mined at just under 1 trillion coins, approximately a value of $52,469,401.82 USD based on today's exchange rate( $0.000053 as of 4.18.2023). We can assume this is the main reason it is in its own cluster since the second highest amount (from ByteCoin) only has 184 billion coins.  ProofType also seems to accurately assist in defining the clusters with Class 1 mostly being PoW (Proof of Work) versus class 0 being PoS or DPos (Proof of Stake or Delegated Proof of Stake). Class 3 contains outlying prooftypes. Prooftypes are a way to validate transactions and award tokens 

## Summary

This is a solid start to generating an algorithm to group potential cryptocurrency investments, but it will require further analysis to understand the best investments. As a beginning, I would recommend looking further into the Class 1 coins.  As PoW cryptocurrencies, they are the most common and longest used forms of proof. According to our scatter plot, generated from our new dataframe combining class with Total Coins Mined and Total Coins Supply scaled using MinMaxScaler, Class 1 coins have both the largest supply and the most mined, excluding our Class 2 outlier, BitTorrent.

![coin_scatter](https://github.com/ChallahBack83/Cryptocurrencies/blob/main/Images/coins_scatter.png)

However, PoS, is generally considered more secure and is apparently growing in use in the community. Our Class 2 point even uses DPoS, or Delegate Proof of Stake, which means these coins may be stronger long term investments.

