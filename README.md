# Ex.8 Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages
2. Insert the dataset to perform the k - means clustering
3. perform k - means clustering on the dataset
4. Then print the centroids and labels
5. Plot graph and display the clusters

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Don Bosco Blaise A
RegisterNumber: 212221040045
*/

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = [] # Within-Cluster Sum of Square
# It is the sum of squared distance between each point & the centroid in a cluster
for i in range(1, 11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1, 11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
<img src="https://github.com/DonBoscoBlaiseA/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/140850829/8d7af815-e4f3-4464-923c-c76d1bbe92f6.png" width="560">  

![image](https://github.com/DonBoscoBlaiseA/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/140850829/bacd5af8-bcd1-4507-aa94-fc78d808722c)  

<img src="https://github.com/DonBoscoBlaiseA/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/140850829/6f14b9ca-d634-492b-8de4-c0b0c8a31d6a.png" width="588">  

![image](https://github.com/DonBoscoBlaiseA/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/140850829/545931ba-177d-4ccc-958b-ec52c3f381f5)  

![image](https://github.com/DonBoscoBlaiseA/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/140850829/19ec1932-9abc-443a-ae2b-aaca0c43bf3e)  

<img src="https://github.com/DonBoscoBlaiseA/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/140850829/98fabdae-dac0-4fb1-afa6-04dbe997aeb1.png" width="588">  

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
