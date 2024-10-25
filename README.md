# CryptoClustering</br>
</br>
This project uses K-Means Clustering to analyse and predict CryptoCurrencies. The purpose of this is to determine the best method of clustering CryptoCurrencies in order to determine how each currency price change is affected over 24 hours and 7 days. The data is provided in a CVS and does not represent real life data. </br>
</br>
### Dependencies</br>
Pandas</br>
hvplot</br>
scikit learn</br>
</br>
## Code Overview</br>
</br>
###Prepare the Data</br>
1. Data is first scaled using scikit learn StandardScaler. This normalizes the data for easier ananlysis.</br>
2. The scaled data is placed into a pandas dataframe. The index of the new dataframe is created using the "coin_id" column from the original data.</br>
</br>
###Find the Best Value for k Using the Original Scaled DataFrame</br>
1. The next step is to find the n\best value for k. A for loop is created to loop through the data and append to an empty inertia list.</br>
2. After appending, the inertia list is used to plot an elbow curve. The last sharpest point of the curve is determined to be the best k value. For this data, the best k value is 4. The data is now ready for clustering.</br>
</br>
###Cluster Cryptocurrencies with K-means Using the Original Scaled DataFrame</br>
1. In order to find the best clustering, the data is tested using kMeans and PCA.</br>
2. kMeans model is fit to the scaled data prepped in the "Prepare the Data" section using .fit module from scikit learn library.</br>
3. Predictions are made and, using a copy of the dataframe, a predictions column is added to the dataframe.</br>
4. A scatter plot is made using the new predictions column to cluster the data.</br>
</br>
###Optimize Clusters with Principal Component Analysis.</br>
1. The second clustering is created with PCA.</br>
2. Much like the kMeans code, the PCA code uses pca from the scikit learn library. This data is then similarly fit to the scaled data.</br>
3. pca.explained_variance_ratio_ is used to determine the variance of the data.</br>
4. The PCA data is also added to a dataframe, with "coin_id" again set as the index.</br>
</br>
###Find the Best Value for k Using the Scaled PCA DataFrame</br>
1. The PCA dataframe recieves the same for loop to determine the inertia.</br>
2. The data is plotted in an elbow curve to determine the best k value for PCA. For this data, the best k value is again 4.</br>
</br>
###Cluster Cryptocurrencies with K-means Using the Scaled PCA DataFrame</br>
1. Steps 1-4 from "Cluster Cryptocurrencies with K-means Using the Original Scaled DataFrame" are repeated using the PCA data.</br>
</br>
###Visualize and Compare the Results</br>
1. The two elbow graphs are compared.</br>
2. The two scatter plots are compared.</br>
3. Looking at the data, despite having similar elbow curves, the PCA data is more tightly clustered. PCA data in this instance would more benefit LLM than kMeans. </br>
