## Statistical Distributions

### Checking for normality

```py
import scipy.stats as st
stat, p = st.shapiro(dataset['column'])
print('Shapiro-Wilk Test Statistics=%.4f, p=%.4f' % (stat, p))
alpha = 0.05
if p > alpha:
    print('Sample looks Gaussian (fail to reject H0)')
else:
    print('Sample does not look Gaussian (reject H0)')
```

### Generating distributions

**Normal distribution**

```py
import numpy as np
rng = np.random.default_rng()
x = rng.normal(size=10000)
```

**Uniform distribution**

```py
import numpy as np
rng = np.random.default_rng()
u = rng.uniform(size=10000)
```

### Permutations *with* repetition

```py
from math import factorial
from collections import Counter

def perms_with_rep(s):
    s = str(s)  # Convert the input to a string
    n = len(s)
    counts = Counter(s).values() # count the number of times each element appears in the string
    result = factorial(n) # calculate the factorial of the length of the string
    for count in counts:
        result //= factorial(count)
    return result

# Example usage
s = 'mathematics'
perms = perms_with_rep(s)
# perms = 4989600
```

### Permutations *without* repetition

##### math
`math.perm(n,k)`

*Parameters*
- `n` : int
- `k` : int
*Returns*: int

Returns the number of ways to choose k items from n items without repetition and with order.
Evaluates to `n! / (n-k)!` when `k <= n` and evaluates to zero when `k > n`.
If k is not specified or is `None`, then k defaults to n and the function returns $n!$.


##### SciPy
`scipy.special.perm(N, k, exact=False)`

*Parameters*
- `N` : int, ndarray
- `k` : int, ndarray
- `exact` : bool, optional (if exact is False, then floating point precision is used)
*Returns*: int, ndarray



### Standard Error

##### SciPy

`scipy.stats.sem(x)`

*Parameters*

- `x` : must contain at least two observations
- `ddof` : int, optional (default=0)

Compute standard error of the mean.

Calculate the standard error of the mean (or standard error of measurement) of the values in the input array.



## Machine Learning

### Model Evaluation

```py
def model_error_evaluation():

    from sklearn import metrics

    #sse = np.sum((y_test - predictions)**2)
    mae = metrics.mean_absolute_error(y_test, predictions)
    mse = metrics.mean_squared_error(y_test, predictions)
    rmse = np.sqrt(metrics.mean_squared_error(y_test, predictions))

    #print('SSE', round(sse, 3))
    print('MAE', round(mae, 3))
    print('MSE', round(mse, 3))
    print('RMSE', round(rmse, 3))

model_error_evaluation()

```

### DBSCAN hyperparameters tuning

#### Noise metrics

```py
def noise_sum_func(model,data):

    labels = model.fit_predict(data)
    return 100 * np.sum(labels == -1) / len(labels)
```

```py
def noise_percent_func(model,data):
    labels = model.fit_predict(data)
    return 100 * np.sum(labels == -1) / len(labels)
```

#### Epsilon range

```py
def noise_metrics(model, data):
    labels = model.fit_predict(data)
    noise_sum = (labels == -1).sum()
    noise_percent = 100 * noise_sum / len(labels)
    return noise_sum, noise_percent

def dbscan_eps_range(data, eps_range):
    noise_percent_list = []
    noise_sum_list = []

    for eps in eps_range:
        dbscan = DBSCAN(eps=eps)
        noise_sum, noise_percent = noise_metrics(dbscan, data)
        noise_percent_list.append(noise_percent)
        noise_sum_list.append(noise_sum)

    return noise_sum_list, noise_percent_list
```

#### MinPts range

```py
def dbscan_minpts_range(data, minpts_range):
    noise_minpts_perc_list = []
    noise_minpts_sum_list = []

    for n in minpts_range:
        dbscan = DBSCAN(min_samples=n)
        noise_sum, noise_percent = noise_metrics(dbscan, data)
        noise_minpts_perc_list.append(noise_percent)
        noise_minpts_sum_list.append(noise_sum)

    return noise_minpts_sum_list, noise_minpts_perc_list
```
