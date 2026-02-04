# Clustering

## Clustering

Clustering is an unsupervised machine learning algorithm that organizes and classifies different objects, data points, or observations into groups or clusters based on similarities or patterns. We can use clustering for the end process like data grouping, but we can also use it in the initial explorations to understand underlying trends, patterns, or outliers. We can also use it to split dataset into multiple data or reduce its dimensionality during preprocessing.

## Types of Clustering

### Centroid-based clustering

Centroid-based clustering is a type of clustering method that partitions data into similar groups based on the distance between their centroids. Each cluster's centroids is either the mean or median of all the data points in the cluster.

Most commonly used techniques is the k-means clustering algorithm. K-means used a distance measure, Euclidean or Manhattan, to calculate the distance between each data points to a cluster centroid.

Another centroid based approach is K-medoids. Medoids are representative objects of a dataset or a cluster within a dataset whose sum of distances to other objects in the cluster is minimal. Instead of having an arbitrary centroid to be the center of the graph, the algorithm creates clusters using individual data points as the medoid or center of the cluster.

### Hierarchical Clustering

Hierarchical clustering groups data points together based on the proximity and connectivity of their attributes. Instead of specifying the number of clusters like K-means, hierarchical clustering creates a graph network of the clusters at each hierarchical level. Two approaches are agglomerative, which is a bottom-up approach, and divisive, which is a top-down approach.

### Distribution-based clustering

Distribution-based clustering groups together data points based on their probability distribution. Distribution-based approach doesn't use distance metric. Instead, it looks for a well-defined distribution which appears across each dimension. One commonly used model is Gaussian Mixture Model (GMM)

### Density-based Clustering

Density-based Clustering works by detecting areas where points are concentrated and where they are separated by areas that are empty or sparse. Unlike other approaches, density clustering can detect clusters of an arbitrary shape. This can be helpful when clusters aren't defined around a specific location. It can also distinguish part of cluster or data points that should be labelled as noise. This method is especially useful when working with datasets with noise or outliers or if we don't have prior knowledge about the number of clusters in the data.

DBSCAN is a clustering algorithm that uses this approach. It used density-based spatial clustering approach to create clusters with a density passed in by the user which centres around a spatial centroid. DBSCAN looks at two main parameters:

- eps, the radius around a point to look for neighbors
- min_samples, the minimum number of points required to form a dense region (cluster)

DBSCAN will define three types of data points:

- **Core Points:** a point that has at least min_samples points (including self) within its eps radius.
- **Border Points:** a data point that has fewer than min_samples in its eps radius but it is close to a core point.
- **Outlier:** a point that is not a core point and is not within the eps of any core point

# Reference

[IBM](https://www.ibm.com/think/topics/clustering)