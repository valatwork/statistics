## Information Theory
Information theory is a field of applied mathematics.

It quantifies the uncertainty in a signal, for instance a distribution of data points.
### Self-information
Likelier events has less information than rares ones. E.g., the sun rising tomorrow has no information value

$$I(x) = -\log P(x)$$

The self-information of an event x is the logarithm of the probability of that event.

- if the event is certain, the probability is 1, and the self-information is 0 ($P(x) = 1 \Rightarrow I(x) = -\log 1 = 0$)
- less likely events have higher self-information values
- independent events have additive self-information values, e.g., one head flip has $I(x) = -\log 0.5 = 1$, two head flips have $I(x)$, two head flips have $2I(x)$
import numpy as np
import matplotlib.pyplot as plt
def self_info(prob):
    return -1*np.log(prob)
self_info(1)
self_info(0.01)
self_info(0.5)
self_info(0.5) + self_info(0.5)
Depending on the base of the logarithm, the unit of self-information varies.

- **nats**
    - Natural logarithm (base e)
    - Typically used in machine learning
- **bits** (AKA **shannons**)
    - base-2 logarithm
    - Typically used in computer science
self_info(0.1)
The self-information of $P(x) = 0.1$ is 2.3 nats or 3.3 bits.

## Bayesian vs Frequentist Statistics

### Bayesian Statistics
- Can incorporate prior knowledge into the model
- "There's a 70% chance of rain today" is a Bayesian statement

Drawbacks:
- Computationally expensive
- Based on beliefs, which can be subjective

### Frequentist Statistics
- "On 100 days with the same conditions as today, it would rain on 70 of them" is a frequentist statement
- Arbitrary significance threshold (p-value)
- Because of the arbitrary threshold, frequentist statistics aren't completely objective
- Computationally efficient

## Application of statistics to Machine Learning

- Examine the distribution of the data (including outputs, perspective inputs)
    - Deepen the understanding of the data
    - Identify irregularities (outliers)
    - Reshape inputs towards a standard normal distribution
- Examine relationships between data
    - Guides model selection
- Compare model performance
- Ensure that the model isn't biased against a particular group
- Bayesian statistics can be used where:
    - Sample sizes tend not to be very large
    - Typically, have evidence for priors (initial parameter values)

## Preprocessing Data for a Model (statistics and ML)

- Most popular statistical models are parametric, meaning that they make assumptions about the distribution of the data. For example, linear regression assumes that the data is normally distributed.
    - Box-Cox transformation adjusts towards normal

- Standard normal is ideal for most models:
    - Subtract the mean (adjusts $\mu$ to 0)
    - Divide by the standard deviation (adjusts $\sigma$ to 1)
    - In neural network architecture, a batch normalization layer can be used to normalize the data

- Binary variables are encoded as 0 or 1
