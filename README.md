# Clustering based anonymizer

### Clustering Based K Anonymity

Only recommend if there are more catogorical columns, than numerical column. if there are more numerical column, then modrian algorithm is recommended.

It is recommended to use 5 <= k <= 20 to minimize the data loss, if your data set is small better to use a small k value

he spark.sql.dataframe you get after anonymizing will always contain a extra column count which indicates the number of similar rows. Return type of all the non categorical columns will be string

In Clustering base Anonymizer you can choose how the how to initialize the cluster centroids.

1. 'fcbg' = This method return cluster centroids weight on the probability of row's column values appear in dataframe. Default Value.
2. 'rsc' = This method will choose centroids weight according to the column that has most number of unique values.
3. 'random = Return cluster centroids in randomly.

just enter the `center_type= 'fcbg'`to use fcbg, default is **fcbg**

You can also decide the clustering method.

1. default is special method
2. kmodes method

if you want to use default dont enter anything to attribute `mode=`, else if you want to use the kmodes method `mode= 'kmode'` if you have a huge data amount default is recommended.

you can also decide the return mode. If this value equal to `return_mode=''equal` ; K anonymization will done with equal member clusters. Default value is 'Not_Equal' Not equal is often run fast, but could be data lossy. equal is vice versa.

### Clustering based L-Diversity

This method is recommended only for k anonymized dataframe. Input anonymized dataframe will group into similar k clusters and clusters that have not L number of distinct sensitive attributes will be suspressed. Recommended small number of l to minimum the data loss. Default value is l = 2.

### Clustering based T closeness

This method is recommended only for k anonymized dataframe. Input anonymized dataframe will group into similar k clusters and clusters that not have sensitive attribute distribution according to t value will be suspressed. t should be in between 0 and 1. Larger value of t to minimum the data loss. Default value is t = 0.2.