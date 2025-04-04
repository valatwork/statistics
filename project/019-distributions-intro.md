# Distributions

## Introduction

In statistics, usually distributions are *probability* distributions.

A distribution is a function that provides the probabilities of occurrence of different possible outcomes in an experiment.

## Random variable

### Definition

Variable whose value is determined by a process that has uncertainty.

A random variable has no data values until an experimental trial is performed or a survey question is asked and answered.

Random variables are either discrete, in which the possible numerical values are a set of integers (or coded values, in the case of categorical data), or continuous, in which any value is possible within a specific range.

#### Notation

- Scalar: plain type, e.g. $h$ for height
- Italics: once a random variable is defined, it is written in italics, e.g. $\it{h}$

### Discrete and continuous variables

#### Discrete

- Countable number of states (finite or infinite)
- Could be a category (e.g. "head", "tails")
- Could be an integer (e.g. number of children)


#### Continuous

- Real value (float)
- Measured (e.g. height, speed, temperature)

## Standard error

The standard error of a statistic (usually an estimate of a parameter) is the standard deviation of its sampling distribution or an estimate of that standard deviation.

It allows, for instance, to tell whether two distributions vary significantly from each other and whether it's likely that those distributions represent two different phenomena.

### Formulas

#### Exact value

Sample of $n$ observations taken from a population with a standard deviation $\sigma$. The mean value calculated from the sample, $\bar{x}$, will have an associated *standard error of the mean*, $\sigma_x$:

$$ \sigma_x = \frac{\sigma}{\sqrt{n}} $$

Practically this tells us that when trying to estimate the value of a population mean, due to the factor  $\frac{1}{\sqrt {n}}$, reducing the error on the estimate by a factor of two requires acquiring four times as many observations in the sample; reducing it by a factor of ten requires a hundred times as many observations.

#### Estimate

The standard deviation $\sigma$ of the population being sampled is seldom known. Therefore, the standard error of the mean is usually estimated by replacing $\sigma$ with the sample standard deviation $\sigma_x$ instead:

$$\sigma_{\bar{x}}\ \approx {\frac {\sigma _{x}}{\sqrt {n}}}$$

As this is only an estimator for the true "standard error", it is common to see other notations here such as:

$$\widehat{\sigma_{\bar{x}}} := \frac{\sigma_{x}}{\sqrt{n}}\  \ or \ \ s_{\bar{x}}:=\frac{s}{\sqrt{n}}$$

A common source of confusion occurs when failing to distinguish clearly between:

- The standard deviation of the population $\sigma$,
- The standard deviation of the sample $\sigma_{x}$,
- The standard deviation of the mean itself $\sigma_{\bar{x}}$ (which is the standard error),
- The estimator of the standard deviation of the mean $\widehat{\sigma_{\bar{x}}}$ (which is the most often calculated quantity, and is also often colloquially called the standard error).



### Standard Error in Python

To calculate the standard error of x, we can use the `sem()` function from the `scipy.stats` module.

`scipy.statis.sem(x)` defaults to `ddof=1`, which can be ignored with the larger data sets.

### Cumulative distribution function (CDF)

The probability that a random variable is less than or equal to a certain value.

$$ F_X(x) = P(X \leq x) $$
