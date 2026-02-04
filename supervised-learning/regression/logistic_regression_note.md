# Logistic Regression

## Logistic regression

We explored how to construct a model to make continuous numerical predictions. But when we want to build a model that help answers yes or no questions, such as "is this email a spam?" or "will it rain today?", we use logistic regression. This model is designed to predict the probability of a given outcome.

Many problems require a probability estimate as output. Logistic regression has an output of probability, which means it takes an input like email, for a spam-prediction model, and gives value like 0.932, that implies a 93.2% probability that the email is a spam. In later model, we will learn to convert this into a binary category such as True or False and Yes or No.

## Sigmoid Function

Logistic regression model ensures its output represents a probability and always outputting a value between 0 and 1. It used a standard logistic function, also known as the sigmoid function, has the formula:

![Sigmoid function](sig_fc.png)

Where:

- f(x) is the output of the sigmoid function
- e is Euler's number: a mathematical constant
- x is the input to the sigmoid function

A sigmoid function has a graph like shown here

![Sigmoid function](sig_graph.png)

As the input increases, the output approaches but never reaches 1. Similarly, as the input decreases, the output approaches but never reaches 0.

## Transforming linear output using the sigmoid function

The following equation represents the linear component of a logistic regression model:

![Linear function](linear_log.png)

Where:

- z is the output of the linear equation, also called the log odds
- b is the bias
- w values are the model's learned weights
- x values are the feature values for a particular example

To obtain the logistic regression prediction, the z value is then passed to the sigmoid function, resulting in a value (probability) between 0 and 1:

![Sigmoid function](sig_fc2.png)

This figure shows how linear output is transformed to logistic regression output.

![Linear to log function](linear_log2.png)

## Loss & Regularization

### Log Loss

In the linear regression model, we used squared loss (L2) as the loss function. Squared loss works well for a linear model where the rate of change of the output values is constant. However, the rate of change of a logistic regression is not constant, because we used a sigmoid function that resulted in an s-shaped curve rather than linear. When the z value is closer to 0, small increases in z results in much larger changes to y than when z is a large positive or negative number.

The following table shows the output for input values from 5 to 10. If we used squared loss to calculate errors for the sigmoid function, as the output get closed to 0 and 1, we would need more memory to preserve the precision needed to track these values.

![Log loss](log_loss.png)

That's why we used Log Loss instead. The Log Loss equation returns the logarithm of the magnitude of the change, rather than just the distance from data to prediction. It is calculated as follows:

![Log loss](log_loss2.png)

Where:

- N is the number of labelled examples in the dataset
- t is the index of an example in the dataset
- yi is the label for the i-th example. Since this is logistic regression, this is either 0 or 1
- yi' is the model's prediction

### Regularization

Regularization is a mechanism to penalize model complexity during training and is very important to logistic regression. Without regularization, the nature of logistic regression would keep driving the loss towards in cases where the model has a large number of features. Logistic regression uses the same regularization as linear regression, which are:

- L2 regularization (Ridge): reduce the weights but keeps all of it
- L1 regularization (Lasso): can shrink some weights exactly to 0
- Combination of both L1 & L2 (Elastic Net): uses a mix ratio to balance the two effects

Another type of regularization for logistic regression is early stopping. A model like logistic regression can go forever to fit the data better and better. To prevent the model to overfit the training data, we can limit how far the model's parameters can be optimized with early stopping.

# Reference

[Google ML Course](https://developers.google.com/machine-learning/crash-course/logistic-regression)
