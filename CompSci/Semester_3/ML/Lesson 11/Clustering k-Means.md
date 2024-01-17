# Clustering: k-Means

Clustering is a method of unsupervised learning that is used to group data points into distinct subgroups or clusters. A popular algorithm for clustering is k-Means, known for its simplicity and efficiency.

## k-Means Algorithm

The k-Means algorithm partitions a dataset into k distinct, non-overlapping subsets (clusters). It assigns each data point to the cluster whose centroid (the mean of the points in the cluster) is nearest. The goal is to minimize the within-cluster variances (squared Euclidean distances), although the algorithm does not guarantee to find the global optimum.

## Steps in k-Means Algorithm

1. **Initialization**: Randomly select `k` centroids, the initial cluster centers.
2. **Assignment**: Assign each data point to the nearest centroid, creating `k` clusters.
3. **Update**: Recalculate the centroids as the mean of all points in each cluster.
4. **Repeat**: Repeat the assignment and update steps until the centroids no longer change significantly, indicating that the clusters are stable.

## Mathematical Formulation

The objective of k-Means is to minimize the within-cluster sum of squares (WCSS):

$$ \text{WCSS} = \sum_{i=1}^{k} \sum_{x \in C_i} ||x - \mu_i||^2 $$

where \( \mu_i \) is the mean of points in \( C_i \).

## Choosing the Number of Clusters (k)

One of the challenges in k-Means is choosing the right number of clusters. A common method is the Elbow Method, where the WCSS is plotted against the number of clusters, and the “elbow point” of the curve indicates an appropriate number of clusters.

## Advantages and Disadvantages

- **Advantages**:
  - Simple and easy to implement.
  - Efficient in terms of computational cost.
  - Works well with large datasets.

- **Disadvantages**:
  - The need to specify the number of clusters beforehand.
  - Sensitive to the initial choice of centroids.
  - Not suitable for clusters with complex shapes or varying sizes.
  - Sensitive to outliers.

## Applications of k-Means

- **Market Segmentation**: Grouping customers based on purchasing behavior.
- **Document Clustering**: Organizing articles or documents into different groups.
- **Image Segmentation**: Dividing an image into different parts based on pixel characteristics.

## Conclusion

k-Means is a widely used clustering algorithm due to its simplicity and efficiency. However, its effectiveness can be limited by its assumptions and the quality of the initial centroid selection. It is best used when the structure of the clusters is relatively simple and well-separated.
