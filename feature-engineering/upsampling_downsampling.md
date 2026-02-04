# Upsampling

## Upsampling

Upsampling increases the number of data samples in a dataset. It aims to correct imbalanced data and thereby improve model performance.

Upsampling, also known as oversampling, is a data processing techniques that addresses class imbalance in a dataset by adding data. Upsampling adds data by using original samples from minority classes until all classes are equal in size. Python scikit-learn contains built-in function for implementing upsampling techniques.

## Why Upsampling?

Upsampling is an effective way to address imbalance within a dataset. It populates the dataset with points generated using the characteristic of original dataset's minority class. This balance the dataset by increasing the number of samples from the minority class until the dataset contains an equal ratio of data across classes.

We can use performance metrics, such as ROC curves or precision-recall curves, to gauge how well an upsampling technique corrects for class imbalance.

## Advantages and Disadvantages

### Advantages

- **No information loss:** unlike downsampling, it does not remove data points, avoiding information loss
- **Increase data at low costs:** a way to increase dataset size in cases where data can only be acquired through observation

### Disadvantages

- **Overfitting:** because it creates new data based on existing class, the classifier can be overfitted to the data. Upsampling assumes the existing data captures reality, if that is not the case, the classifier may not be able to generalize
- **Data noise:** upsampling can instead increase the amount of noise in the data

## Upsampling Techniques

### Random Oversampling

Random oversampling is the process of duplicating random data points in the minority class. Though they are similar in nature, random oversampling is different from bootstrapping. Despite its simplicity, random oversampling only duplicate data points which can potentially lead to overfitting.

### SMOTE

Synthetic Minority Oversampling Technique (SMOTE) is an upsampling technique that synthesizes new data points from the existing points in the minority class. It consists of this process:

- Find the K nearest neighbours for all minority class data points (K is usually 5)
- Pick one of the data point's nearest neighbours
- Pick a random point on the line segment connecting these two points to generate a new output sample, also known as interpolation
- Repeat step 2-3 using different neighbours until the amount of upsampling required is reached

SMOTE counters the problem of overfitting in random oversampling by adding unseen data to the dataset rather than just duplicating data. On the other hand, SMOTE's artificial data points also adds extra noise to the dataset, potentially making the classifier more unstable.

### Borderline SMOTE

Borderline SMOTE create harder data points. Harder data points are data points close to the decision boundary, therefore harder to classify. These harder data points are more useful for model to learn.

Borderline SMOTE identifies the minority class points that are close to many majority class points and puts them into a DANGER set. DANGER points are the hard data points to learn, and they are harder to classify to points that are surrounded by minority class points. This selection process excludes points whose nearest neighbours are only majority class points and are counted as noise. From there, SMOTE algorithm will continue using this DANGER set.

The algorithm increases the data points that are harder to classify because data points that is further from majority class are already easy to classify, there is no need to add more data to it. The DANGER set on the other hand, are usually neglected because they are a few and close to majority class. Therefore, by adding more data points to these area, it reduces the potential classification error around the boundaries where classes overlap.

### ADASYN

Adaptive Synthetic Sampling Approach (ADASYN) is similar to borderline SMOTE in that it generates more difficult data for the model to learn but also aims to preserve the distribution of minority class data. It first creates a weighted distribution of al the minority points based on the number of majority class examples in its neighbourhood. From there, it uses minority class points closer to the majority class more often in generating new data.

The process are as follows:

- Create a KNN model on the entire dataset
- Each minority class points is given a hardness factor (r), which is ratio of the number of majority class points over the total number of neighbours in KNN
- Like SMOTE, the synthetically generated points are linear interpolation between minority data, but the number of points generated scales with a point's hardness factor.

### Data Transformation / Augmentations

Data augmentation creates new data by creating variations of the actual data. Data augmentation applies across a variety of machine learning fields.

The most basic form of data augmentation deals with transforming the raw inputs of the dataset. For example, in computer vision, image augmentations (cropping, blurring, mirroring) can be used to create more images for the model to classify. Similarly, in NLP tasks, it replaces words with their synonyms or create a semantically equivalent sentence

# Downsampling

## Downsampling

Downsampling, also known as undersampling, decreases the number of data samples in a dataset. Like upsampling, it aims to correct imbalanced data to improve model performance. Downsampling is a common data processing technique that addresses imbalances in a dataset by removing data from the majority class, so it matches the size of the minority class.

## Why Downsampling

Downsampling is an effective way to address imbalances. It identifies majority class points to remove based on specified criteria. These criteria can change with the chosen downsampling technique. This balances the dataset by effectively decreasing the number of samples for an overrepresented majority class until the dataset contains an equal ratio of points across class.

Like upsampling, we can use ROC and recall-precision curves to gauge how well downsampling corrects for class imbalance.

## Advantages and Disadvantages

### Advantages

- **Faster training:** downsampling reduce datasets making training less intensive
- **Less prone to overfitting:** downsampling only deletes data, it is not prone to overfitting

### Disadvantages

- **Loss of information:** deleting points from the majority class can cause important information loss. Can be an issue especially if the classification of the majority class needs to be accurate
- **Introduce bias:** the remaining majority class points can be biased set of the original data

## Downsampling Techniques

### Random Downsampling

Random downsampling is a deletion technique where random points in the majority class are chosen without replacement and deleted from the dataset until it is equal to minority class size. This is the simplest way to balance dataset, but it can cause important patterns or distributions in the majority class to disappear.

### Near Miss Downsampling

Near miss downsampling randomly eliminating certain majority class examples. Conceptually, it operates on the principle that data should be kept in places where the majority and minority classes are very close, as these places give key information in distinguishing the two classes. These points known as hard to learn data points. Near miss operates in two steps:

- Calculate the pairwise distance between all majority-minority class instances
- Based on the calculated distances, remove instances of the majority class that are further away from minority points.

There are three variations of Near Miss algorithm that provide a way of selecting majority class instances to be removed.

#### Version 1

This version keeps the majority class instances with the smallest average distance to their k nearest minority class instances. The resulting data can potentially be unevenly distributed, with some majority class points being close to many minority class points and others being close to very few, causing both low precision and recall.

#### Version 2

This version keeps the majority class instances with the smallest average distance to their k furthest minority class instances. This version creates a more even distribution of the majority class. This tries to select majority class points that provide good coverage of the minority class space.

#### Version 3

For each minority samples, keep the k nearest majority neighbours. This ensures every minority sample has some majority samples nearby for the classifier to learn local boundaries.

### Condensed Nearest Neighbour Rule Downsampling

Condensed Nearest Neighbours (also CNN) seeks to find a subset of a dataset that can be used for training without loss in model performance. This is achieved by identifying a subset of the data that can be used to train a model that correctly predicts the entire dataset.

CNN downsampling has the following steps:

- Create a new dataset (S) that contains all instances of the minority class and a single randomly samples instance of the majority class
- Use S to classify the remaining majority samples
- Find the majority samples that are misclassified by S
- Add those misclassified majority samples to S
- Keep Iterating until no more majority samples are misclassified

Like Near Miss, this process essentially removes all majority class instances that is far away from the decision boundary, which are points that are easy to classify. It also ensures that every data in the original dataset can be correctly predicted using just the data within S. One thing to know, CNN often keeps outliers or noise since they will almost always get misclassified, which might hurt the model.

### Tomek Link

Tomek Link downsampling reduce noise in the data by removing points near the decision boundary and increase class separation. Unlike other methods that kept samples that are close, they remove these points instead. It identifies "tomek links" a pair of samples from different classes that are each other's neighbours. For all tomek links, the majority class sample is removed. These pairs are right at the boundary or very close to each other, removing the majority class reduce the sample while also increasing class separation.

### Edited Nearest Neighbours

Edited Nearest Neighbours (ENN) downsampling is similar to tomek link, where the goal is to remove examples near the decision boundary and increase class separation. This method removes data points that differ in class from a majority of its neighbours. This means that it removes majority class data points that most of its neighbours are minority class, and vice versa. These points are most likely noise, mislabelled, or outliers.

The number of neighbours can be freely defined but ENN is usually done with 3 nearest neighbours.

## When Should We Balance?

### Balance

- We care about minority class performance
- The imbalance is moderate (not extreme)
- The algorithm or model struggles with imbalance
- Cost of missing minority samples is high

### Don't balance

- The distribution reflects reality and it matters
- It is an anomaly detection problem
- We have tons of data even in minority class
- False positives are more costly than false negatives


# Reference

[IBM](https://www.ibm.com/think/topics/upsampling)
[IBM](https://www.ibm.com/think/topics/downsampling)
