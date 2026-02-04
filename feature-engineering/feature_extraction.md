# Feature Extraction

## Feature Extraction

Feature Extraction is a technique that reduces the dimensionality or complexity of data to improve model performance. During extraction process, unstructured data is converted into a more structured and usable format to enhance the data quality and model interpretability. Common tasks that rely on efficient feature extraction include image processing, natural language processing (NLP), and signal processing.

## How Feature Extraction Work

First, the model takes in input data, then the feature extractor transforms the data into a numerical representation that can be used to compute the dimensionality reduction methods for feature extraction. These representations are stored in feature factors for the model to perform algorithms for data reduction.

After extraction, it is sometimes necessary to standardize the data using feature normalization, especially when using algorithms that are sensitive to magnitude, such as k-means clustering. Most modern models perform automatic feature extraction, but it is still useful to understand the diverse way of handling it. Common feature extraction methods:

- **Principal Component Analysis (PCA)**
- **Linear Discriminant Analysis (LDA):** Commonly used in supervise learning to separate multiple classes and features to solve classification problems
- **T-distributed Stochastic Neighbour Embedding (t-SNE):** this technique is commonly used for feature visualization in deep learning. This is especially useful when the task is to visualize high dimensional data in 2D or 3D
- **Term Frequency**\-**Inverse document Frequency (TF-IDF)**: this method evaluates the importance of words based on how frequently they appear. Commonly used in NLP

## Use Cases

### Image processing and computer vision

The feature extraction process identifies and extracts the key characteristics from images and video. Raw image data (pixel) is transformed into features that the machine can apply algorithms to extract and classify a new set of features

### Natural Language Processing (NLP)

Feature extraction converts raw text data into a format structure that the machine learning model can process. This is useful for tasks such as classification, sentiment analysis, or named entity recognition (NER).

### Signal Processing

This technique is used to analyse and extract meaningful information from raw signal data (audio, images, or time-series data) to facilitate tasks such as classification, detection or prediction.

# Reference

![IBM](https://www.ibm.com/think/topics/feature-extraction)