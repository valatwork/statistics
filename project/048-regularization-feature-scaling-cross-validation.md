## Introduction: Bias-Variance Tradeoff

Increasing the complexity of a model in search for better performance leads to a Bias-Variance Tradeoff.

- Bias is the error due to wrong assumptions. A high bias model is most likely to underfit the training data.

- Variance is the amount that the estimate of the target function will change if different training data were used. A model with many degrees of freedom (such as a high-degree polynomial) is likely to have high variance and underfit the data.

In short: a model with high bias will *underfit* the data, while a model with high variance will *overfit* the data.

The goal is to find the sweet spot where the model is complex enough to capture the underlying patterns in the data, but not so complex that it starts capturing noise.

- Overfitting: the model will perform well on the training set but poorly on the test set.
- Underfitting: the model has high bias, it will perform poorly on both the training set and the test set.

## Regularization

Constraining a model to make it simpler and reduce the risk of overfitting is called regularization.

The amount of regularization applied is controlled by what is called a hyperparameter.

A hyperparameter is a parameter of a learning algorithm and not of the model, as such it is not affected by the learning algorithm itself; it must be set prior to training and remains constant during training.

If you set the regularization hyperparameter to a very large value, you will get an almost flat model (a slope close to zero); the learning algorithm will almost certainly not overfit the training data, but it will be less likely to find a good solution.

Regularization seeks to solve the overfitting problem by:

- Minimizing the model complexity
- Penalizing the loss function
- Adding more bias to reduce variance

There are three types of regularization.

#### **L1 regularization** (Lasso regression)

Adds a penalty equal to the absolute value of the magnitude of the coefficients.
- it limits the size of the coefficients
- it can yield sparse models where some coefficients can become zero zero

The absolute value of a number is the number without its sign. For example, the absolute value of -3 is 3. The *magnitude* is the length of a vector in a vector space.

Where:
- $\lambda$ is the hyperparameter
- $w$ are the coefficients (weight) of the model
- $n$ is the number of features

$$Loss = MSE + \lambda \sum_{i=1}^{n} |w_i|$$

#### **L2 regularization** (Ridge regression)

Adds a penalty equal to the square of the magnitude of the coefficients.

- All coefficients are shrunk by the same factor (none are eliminated)
- Does not necessarily eliminate coefficients

$$Loss = MSE + \lambda \sum_{i=1}^{n} w_i^2$$

#### **Elastic Net**

Elastic Net is a combination of L1 and L2 regularization. It adds both penalties to the loss function.

- It works well when there are multiple features correlated with each other
- It can be used to select important features
- It can be used to handle multicollinearity

$$\text{Loss} = \text{MSE} + \lambda \left( \alpha \sum_{i=1}^n |w_i| + \frac{1 - \alpha}{2} \sum_{i=1}^n w_i^2 \right)$$

## Feature Scaling

With few exceptions, machine learning algorithms don’t perform well when the input numerical attributes have very different scales.

Without any scaling, most models will be biased towards the features with the larger values; with gradient descent, features with larger values will have a larger impact on the model and the algorithm will take longer to converge.

Features with uniform ranges are easier to compare, especially when the data has different units of measurement.

There are two main methods for scaling features: normalization and standardization. These can be applied with scikit-learn.

The feature scaling steps are:

- Perform the train test split
- Fit to the training feature data
- Transform the training feature data
- Transform the test feature data

And what about the target variable? In general, it is not necessary nor advised: normalizing the output distribution is altering the output of the model, and it may predict a distribution that does not mirror the real-world target. It will also negatively impact stochastic gradient descent. There's a good explanation in this [Stats Stack Exchange answer](https://stats.stackexchange.com/a/111995).

#### Things to keep in mind and advantages

**Things to keep in mind:**

- Unseen data (new data) must be scaled using the same parameters as the existing data
- It's easier to compare coefficients with one another, but
- It's harder to relate back to the original, unscaled feature

**Advantages:**

- Can lead to a great increase in performance
- Necessary for some models
- Virtually no real downsides to scaling features

#### Normalization (AKA min-max normalization)

Also known as min-max scaling or min-max normalization, rescaling is the simplest method and consists in rescaling the range of features to scale the range in [0, 1]

$$X' = \frac{X - X_{min}}{X_{max} - X_{min}}$$

Rescaling can be applied to an arbitrary range [a, b] using the following formula, where $a$ and $b$ are the minimum and maximum values of the desired range:

$$X' = a + \frac{(X - X_{min})(b - a)}{X_{max} - X_{min}}$$

The values of the feature will be between 0 and 1.

#### Standardization (AKA Z-score normalization)

Rescales the data to have a mean ($\mu$) of 0 and a standard deviation ($\sigma$) of 1 (unit variance), as a result the data will be normally distributed.

$$X' = \frac{X - \mu}{\sigma}$$

#### Mean normalization

$$X' = \frac{X - \bar{X}}{X_{max} - X_{min}}$$

#### Robust scaling

Also known as *standardization using median and interquartile range (IQR)*, is designed to be robust to outliers. It scales features using the median and IQR as reference points instead of the mean and standard deviation.

Where $Q_1(X)$ and $Q_3(X)$ are the first and third quartiles of the data, respectively:

$$x' = \frac{X - Q_2(X)}{Q_3(X) - Q_1(X)}$$

#### Feature scaling in scikit-learn

The methods are:

- `StandardScaler`: standardization
- `MinMaxScaler`: normalization
- `RobustScaler`: robust scaling

- the `.fit()` method is used to calculate the necessary statistics for scaling
- the `.transform()` method is used to apply the scaling
- the `.fit_transform()` method is a shortcut that combines the two steps
- the `.inverse_transform()` method can be used to reverse the scaling

One important thing to keep in mind is that only the training data should be used to fit the scaler.

Using the entire dataset can lead to data leakage: some information from the test set leaks into the training process upon the `transform()` conversion, and the test set should stay completely unseen by the model.


## Cross-Validation introduction

We perform a train-test split to fairly evaluate the model's performance on unseen data. This split means we are not able to tune the hyperparameters to the entire dataset.

Cross-validation is a technique that allows us to tune the hyperparameters and evaluate the model on the entire dataset.

The most common cross-validation technique is k-fold cross-validation: the training set is split into $k$ smaller sets (*folds*), then every fold is used and validated against the remaining folds. The process is repeated k times, each time with a different fold as the validation set.

A very common choice for $k$ is 10, as each test set would be 10% of the dataset, but it could be any number: the largest value for $k$ is the number of observations (columns) in the dataset. The higher the $k$, the more computationally expensive the process becomes.

Scikit-Learn’s cross-validation features expect a utility function (greater is better) rather than a cost function (lower is better), so the scoring function is actually the opposite of the RMSE. It’s a negative value, so you need to switch the sign of the output to get the RMSE scores.

To make sure we understand how the model behaves with unseen data for hyperparameter tuning, we can use a *hold out* set: it's a subset of data that the model will never see and never get adjusted to. The final data will not be tuned and will instead be used to evaluate the model's performance.
