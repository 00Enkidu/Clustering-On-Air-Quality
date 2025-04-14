# Clustering Assignment

### Way to run the code:
Run the code cells by cells, the first cell is for data preprocessing (Turning Air Quality tag from text to number) and normalization by StandarScaler().

## Task 1: Compute Purity

### **Objective**
Implemented a function `compute_purity(y_true, y_pred)` to evaluate the alignment of clustering results with ground truth labels. Purity is the sum of the majority class examples across clusters, divided by the total number of data points.

### **Key Results**
- Tested with an example:
  - \(y\_pred = [2, 2, 1, 2, 2, 2, 0, 0, 0, 1, 2, 1, 1, 1, 1, 1]\)
  - \(y\_true = [0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2]\)
- Resulting purity: **75%**

---

## Task 2: Compute SSE

### **Objective**
Implemented a function `compute_sse(x, y_pred)` to calculate the Sum of Squared Error (SSE), measuring clustering compactness. It sums the squared distances between points and their respective cluster centers.

### **Key Results**
- Tested with the Iris dataset (\(k=3\)):
  - **Custom SSE**: \(78.9451\)
  - **KMeans SSE (scaled)**: \(78.9451\)
- Exact match between custom SSE and scikit-learn KMeans inertia.

---

## Task 3: K-Means Clustering with \(k=4\)

### **Objective**
Run K-Means clustering with \(k=4\), compute cluster distribution percentages, calculate overall purity, and determine cluster-wise purities.

### **Key Results**
| Cluster | Percentage (%) | Purity (%) |
|---------|----------------|------------|
| 0       | \(18.18\)      | \(59.19\)  |
| 1       | \(41.38\)      | \(96.52\)  |
| 2       | \(7.32\)       | \(46.45\)  |
| 3       | \(33.12\)      | \(82.13\)  |

- **Overall Purity**: \(81.30\%\)
- **Cluster with Highest Purity**: Cluster \(1\) (\(96.52\%\))

---

## Task 4: K-Means with Multiple \(k\) Values

### **Objective**
Run K-Means clustering for \(k = [2, 3, 4, 10, 20, 30]\), calculate average purity and SSE over 10 runs for each \(k\), and analyze the trends.

### **Key Results**
| \(k\)  | Purity  | SSE            |
|--------|---------|----------------|
| 2      | \(0.59634\) | \(27447.015716\) |
| 3      | \(0.76350\) | \(22364.604964\) |
| 4      | \(0.80280\) | \(19687.694874\) |
| 10     | \(0.87814\) | \(14844.681977\) |
| 20     | \(0.89036\) | \(12003.423479\) |
| 30     | \(0.89830\) | \(10741.957436\) |

- **Best \(k\) for Purity**: \(k=30\) (\(89.83\%\))
- **Best \(k\) for SSE**: \(k=30\) (\(10741.957436\))


---

## Task 5: DBSCAN Clustering

### **Objective**
Run DBSCAN with \(eps = [0.8, 0.9, 1.0, 1.1, 1.2]\), calculate purity, SSE, and silhouette coefficient, and evaluate clustering performance.

### **Key Results**
| \(eps\) | Clusters | Anomalies | Purity  | SSE      | Silhouette Coefficient |
|---------|----------|-----------|---------|----------|-------------------------|
| 0.8     | 12       | 2656      | \(0.7901\) | \(6850.021544\) | \(-0.009287\)           |
| 0.9     | 11       | 2071      | \(0.6664\) | \(10580.821406\) | \(0.007289\)            |
| 1.0     | 8        | 1532      | \(0.5712\) | \(15668.087223\) | \(0.100165\)            |
| 1.1     | 10       | 1136      | \(0.5210\) | \(19746.073374\) | \(0.097361\)            |
| 1.2     | 4        | 854       | \(0.4824\) | \(23556.197082\) | \(0.227144\)            |

- **Best Purity**: \(eps=0.8\)
- **Best SSE**: \(eps=0.8\)
- **Best Silhouette Coefficient**: \(eps=1.2\)

---

## Task 6: Agglomerative Clustering

### **Objective**
Run Agglomerative Clustering with \(distance\_threshold = [25, 75, 125]\), calculate purity and SSE, and use the dendrogram to determine the optimal threshold for detecting 5 clusters.

### **Key Results**
| Distance Threshold | Purity  | SSE            | Clusters |
|--------------------|---------|----------------|----------|
| 25                 | \(0.8818\) | \(15675.166567\) | 11       |
| 75                 | \(0.8450\) | \(20364.869108\) | 4        |
| 125                | \(0.6940\) | \(28813.695008\) | 2        |

- **Threshold for 5 Clusters**: \(46\) (based on dendrogram analysis).
- **Best Purity and SSE**: Achieved at \(distance\_threshold=25\).
