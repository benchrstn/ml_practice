# Feature Selection

## Feature Selection

Feature Selection is the process of selecting the most relevant features of a dataset to use when building and training a machine learning model. By reducing the feature or dimension of a dataset into a selected subset, feature selection improves model performance while lowering its computational demands.

### Benefits

Feature selection process streamlines a model by identifying the most important, impactful, and nonredundant features in the dataset. Reducing the number of features enhances model efficiency and boost performance. The benefits of feature selection include:

- **Better model performance:** irrelevant features weaken model performance. Choosing the right set of features makes it more accurate.
- **Reduced overfitting:** overfitting happens when a model cannot generalize past its training data. Removing redundant features decreases the chance of overfitting
- **Shorter training times:** by focusing on a smaller subset of features, algorithms take less time to train
- **Lower compute cost:** a smaller dataset can be solved with simpler predictive models which require lower computational cost
- **Greater interpretability:** as a model grow more complex due to many features, it becomes more difficult to interpret the result. Simpler model with fewer features are easier to explain

## Supervised Feature Selection Methods

Supervised feature selection uses the target variable to determine the most important features. Because the data features are already identified, the task is about identifying which input variables most directly affect the target variable. Correlation is the primary criterion when assessing the most important features.

Supervise methods include:

- Filter methods
- Wrapper methods
- Embedded methods

Hybrid methods that combine these methods are also possible.

### Filter Methods

Filter methods are a group of feature selection techniques that are solely concerned with the data itself and do not directly consider model performance optimization. Features are assessed independently against the target variable to determine which has the highest correlation.

Often used, filter methods are fast and efficient. Various statistical test are used to score each input variable for correlation. Some common filter methods are:

- **Information gain:** measures how important the presence or absence of a feature is in determining the target variable by the degree of entropy reduction
- **Mutual information:** assesses the dependence between variables by measuring the information obtained about one through the other
- **Chi-square test:** assesses the relationship between categorical variable with the target variable. Used for classification problems
- **Fisher's score:** uses derivatives to calculate the relative importance of each feature for classifying data. A higher score indicates greater influence
- **Pearson's correlation coefficient:** quantifies the relationship between two continuous variables
- **Analysis of Variance (ANOVA):** determines whether a numerical feature affect the value of the target variable. Used for classification problems.

### Wrapper Methods

Wrapper methods train the machine learning algorithm with various subsets of features, adding or removing features, and testing the results at each iteration. The goal of all the wrapper methods is to find the feature set that leads to optimal model performance.

Wrapper methods that test all possible feature combinations are known as greedy algorithms. The calculations are computationally intensive and time consuming, so it is best for smaller datasets. Wrapper methods include:

- **Forward selection:** starts with an empty feature set and gradually adds new features until the optimal set is found
- **Backward selection:** trains a model with all the original features and iteratively removes the least important feature
- **Exhaustive feature selection:** tests every possible combination of features to find the overall best one by optimizing a specified performance metric.
- **Recursive feature elimination (RFE):** a type of backward selection that begins with an initial feature space and eliminates or adds features after each iteration based on their relative importance
- **Recursive feature elimination with cross validation:** a RFE variation that uses cross validation, which tests a model on unseen data, to select best performing feature set

### Embedded methods

Embedded methods fold feature selection into the model training process. As the model undergoes training, it uses various mechanisms to detect underperforming features and discard those from future iterations.

Embedded methods revolve around regularization, which penalizes features based on a preset coefficient thresholds. The result is that models perform slightly less well during training but become more generalizable by reducing overfitting. Embedded methods include:

- **Lasso regression (L1):** adds a penalty to the loss function for high-value correlated coefficients, moving them toward 0. Coefficients with a value of 0 are removed. Effective lasso use is about balancing the penalty to remove irrelevant features while keeping the important ones
- **Random forest importance:** build hundreds of decision trees, each with a random selection of data points and features. Each tree is then assessed of how well it divides data points and the better the results, the more important the feature in that tree considered to be
- **Gradient boosting:** adds predictors in sequence to an ensemble with each iteration correcting the errors of the previous one.

## Unsupervised Feature Selection Methods

Unsupervised feature selection tailor input variables without using the target variables. One of the method is principal component analysis (PCA). It reduces the dimensionality of large datasets by transforming potentially correlated variables into smaller set of variables. Other include independent component analysis (ICA), which separates multivariate data into individual components that are statistically independent.

Another one is autoencoders, which is a type of neural network that learns to compress and the reconstruct data.

## Choosing A Feature Selection Method

The type of feature selection used depends on the nature of the input and output variables, also whether it is a classification or regression task.

- **Numerical input, numerical output:** This indicates a regression problem that uses linear models. For this, correlation coefficients such as Pearson's correlation coefficients are an ideal method
- **Numerical input, categorical output:** This is a classification task that uses numerical input, usually using logistic regression models. ANOVA method can be used
- **Categorical input, numerical output:** this can also be solved with correlation method that support categorical variables
- **Categorical input, categorical output:** common classification problems. Chi squared method is preferred

Other things to consider include the size of dataset and feature space, feature complexity, and model type. Filter methods can quickly eliminate a large portion of features but struggle with complex feature interactions. In these cases, wrapper and embedded methods might be more suitable


# Reference

[IBM](https://www.ibm.com/think/topics/feature-selection)