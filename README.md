# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Step 1. Start the program

Step 2. Import the necessary python libraries

Step 3. Read the dataset of Mall_Customers csv file

Step 4. From sklearn libraary select the cluster and import KMeans Clustering

Step 5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method

Step 6. Plot the graph x and y as Number of Clusters and wcss respectively

Step 7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)

Step 8. Stop the program
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: T Thrishendra
RegisterNumber:  212223230227
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = [] #Within-Cluster Sum of Square.
#It is the sum of squared distance between each point & the centroid in a cluster

for i in range(1,11):
    kmeans = KMeans(n_clusters = i, init = "k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])
KMeans(n_clusters = 5)

y_pred = km.predict(data.iloc[:, 3:])
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
![image](https://github.com/user-attachments/assets/4b804b24-0d3e-4aa6-a0f2-63bcba0d45f4)

![image](https://github.com/user-attachments/assets/551a9afa-dc7c-44d5-8437-5f183131db6b)

![image](https://github.com/user-attachments/assets/2b580923-ebe2-4e27-a1b7-091f5fec6ac7)

![image](https://github.com/user-attachments/assets/ae5fea05-d3d8-4a56-9649-a2193c73cda3)

![image](https://github.com/user-attachments/assets/31597191-e161-41d3-b048-2be653921d8a)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
