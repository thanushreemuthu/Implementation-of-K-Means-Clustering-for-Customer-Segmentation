Developed by: Thanushree M

RegisterNumber:  212224240169


# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm


1. **Load Data**: Read the dataset using Pandas and explore it with `.head()` and `.info()` to understand the structure.

2. **Find Optimal Clusters (Elbow Method)**: Use the Elbow method by fitting KMeans for `k` values from 1 to 10 and plot the Within-Cluster Sum of Squares (WCSS) to find the optimal number of clusters.

3. **Train KMeans Model**: Initialize and fit the KMeans model using the chosen number of clusters (e.g., 5) on the selected features (Annual Income and Spending Score).

4. **Predict Clusters**: Use the trained model to predict cluster labels and add them as a new column to the dataset.

5. **Segment Data**: Split the data into separate DataFrames based on predicted cluster labels for visualization.

6. **Visualize Clusters**: Plot the clusters using different colors to visualize how customers are grouped based on income and spending score.


## Program:
Program to implement the K Means Clustering for Customer Segmentation.

```


        import pandas as p
        import matplotlib.pyplot as py
        data=p.read_csv("/content/Mall_Customers.csv")
        data.head()
        data.info()
        
        
        from sklearn.cluster import KMeans
        wcss=[]
        for i in range(1,11):
          kmeans=KMeans(n_clusters=i,init="k-means++")
          kmeans.fit(data.iloc[:,3:])
          wcss.append(kmeans.inertia_)
        
        
        py.plot(range(1,11),wcss)
        py.xlabel("No.of cluster")
        py.ylabel("wcss")
        py.title("Elbow method")
        py.show()
        
        
        km=KMeans(n_clusters=5)
        km.fit(data.iloc[:,3:])
        y_pred=km.predict(data.iloc[:,3:])
        y_pred
        
        
        data["clusters"]=y_pred
        df0=data[data["clusters"]==0]
        df1=data[data["clusters"]==1]
        df2=data[data["clusters"]==2]
        df3=data[data["clusters"]==3]
        df4=data[data["clusters"]==4]
        
        
        py.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],color="gold")
        py.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],color="pink")
        py.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],color="green")
        py.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],color="blue")
        py.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],color="red")
```

## Output:

![image](https://github.com/user-attachments/assets/3fd07536-a6ec-40cf-8516-0ba68fd6469e)
![image](https://github.com/user-attachments/assets/188aaa65-4792-4cf9-bc22-cf8b182718ab)
![image](https://github.com/user-attachments/assets/a77c0a68-d682-430d-9a88-5ccbbabeb72b)
![image](https://github.com/user-attachments/assets/46d89198-becd-4157-919d-744c04c9fcf4)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.

Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
