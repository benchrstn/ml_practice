# Principal Component Analysis (PCA)

## What is PCA

PCA reduces the number of dimension in large datasets to principal component that retain most of the original information. It does this by transforming potentially correlated variables into a smaller set of variables, called principal components. PCA is one of unsupervised learning method as it can reduce dimensions without having to consider class labels or categories.

PCA is commonly used for data preprocessing for machine learning algorithm. It can extract the most informative features from large datasets wile preserving the most relevant information from the original dataset. This reduces model complexity as the addition of each new feature or dimension negatively impacts model performance, often referred to as the "curse of dimensionality".

## How PCA works

PCA summarizes the information content of large datasets into a smaller set of uncorrelated variables known as principal components. These principal components are linear combinations of the original variables that have the maximum variance to other combinations. These components capture as much information from the original dataset as possible.

### First principal component

The first principal component (PC1) is the direction in space along which the data points have the highest or most variance. It is the line that best represents the shape of the projected points. The larger variability captured in the first component, the larger the information retained from the original dataset.

### Second principal component

PC2 accounts for the next highest variance in the dataset and must be uncorrelated with PC1. PC2 must be orthogonal or perpendicular to PC1.

### Subsequent components

If there are any subsequent components, they would also retain the same properties. They retain the next highest variance, and they would not be correlated with other components.

## Interpreting PCA Results

A PCA plot is a scatter plot created using the first two principal components as axes. The first component (PC1) is the x-axis, and the second component (PC2) is the y-axis. The scatter plot shows the relationships between observations (data points) and the new variables (the principal components).

The direction and length of the plot arrows indicate the loadings of the variables, which is how each variable contributes to the principal components. If a variable has a high loading for a particular component, it is strongly correlated with that component. It can highlight which variables have a significant impact on data variations.

The number of principal components that remain after applying PCA can help you interpret the data output. The first principal component explains the most data variance, and each later component accounts for less variance. Thus, the number of components can indicate the amount information retained from the original dataset. Fewer components might not capture much data variation while more components may be harder to interpret. We can decide the optimal number of components using scree plot or cumulative explained variance.

## When to Use PCA

There are many other dimensionality reduction techniques other than PCA, such as Uniform Manifold Approximation and Projection (UMAP) and t-distributed stochastic neighbour (t-SNE). Some factors to consider when deciding to use PCA

- **Linearity:** PCA is a linear technique, so it is better suited to datasets with linear relationships between features. Non-linear techniques like t-SNE or UMAP
- **Computation:** PCA uses matrix operations for computation to efficiently manage large datasets. Other techniques might not be suitable for large datasets.
- **Information preservation:** PCA preserves the maximum amount of variance in the data while t-SNE focus on preserving structure of the data. Therefore, PCA is better suited for identifying the most important data variables while other techniques more suitable for visualizing the data
- **Feature extraction:** PCA is a feature extraction technique. It produces new variables that are linear combinations of the original variables.

# Reference

[IBM](https://www.ibm.com/think/topics/principal-component-analysis)