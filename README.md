# BLENDED LEARNING
# Implementation of Customer Segmentation Using K-Means Clustering

## AIM:
To implement customer segmentation using K-Means clustering on the Mall Customers dataset to group customers based on purchasing habits.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
 
1.Import the required Python libraries and load the Mall Customers dataset.

2.Select the features Age, Annual Income, and Spending Score for clustering.

3.Normalize the selected features using StandardScaler to standardize the data.

4.Apply K-Means clustering for different cluster values and compute the WCSS.

5.Plot the Elbow Method graph to determine the optimal number of customer clusters

## Program:
```
/*
Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.
Developed by: ROSHAN V
RegisterNumber:  212225240124

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score

data=pd.read_csv('CustomerData.csv')

print(data.head())
print(data.columns)

features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

wcss=[]
for i in range(1,11):
    kmeans = KMeans(n_clusters=i,random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)
    
plt.figure(figsize=(8,4))
plt.plot(range(1,11),wcss,marker='o',linestyle='-')
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method for Optimal Number of Clusters")
plt.show()


kmeans = KMeans(n_clusters=5, random_state=42)
kmeans.fit(X_scaled)

data['Cluster'] = kmeans.labels_

sil_score = silhouette_score(X_scaled, kmeans.labels_)
print(f'Silhouette Score: {sil_score}')

plt.figure(figsize=(10, 6))
sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster', palette='viridis')
plt.title('Customer Segmentation based on Annual Income and Spending Score')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend(title='Cluster')
plt.show()



*/
```

## Output:
<img width="668" height="157" alt="image" src="https://github.com/user-attachments/assets/ba6cb066-f2bf-4310-be95-e21d8e30dcb9" />
<img width="835" height="393" alt="image" src="https://github.com/user-attachments/assets/40f3fe3b-a70f-41e3-a51d-8f6f8871cca8" />
<img width="963" height="581" alt="image" src="https://github.com/user-attachments/assets/c2f19dc5-b2fa-4e6d-8b69-6082af3fde02" />



## Result:
Thus, customer segmentation was successfully implemented using K-Means clustering, grouping customers into distinct segments based on their annual income and spending score. 
