# Hypothesis Testing

Our primary use of statistical modeling is to answer questions of interest from data. Hypothesis testing provides a formal framework for answering questions of interest with measures of uncertainty.

Hypothesis testing consists of two contradictory hypotheses or statements, a decision based on the data, and a conclusion.

## Types of Hypothesis

A hypothesis about the value of a population parameter is an assertion about its value. As in the introductory example we will be concerned with testing the truth of two competing hypotheses, only one of which can be true.

**Null Hypothesis** ($H_0$): the statement about the population parameter that is assumed to be true unless there is convincing evidence to the contrary. It is a statement of no difference between the variables - they are not related.

The null hypothesis typically represents the status quo, or what has historically been true.

**Alternative Hypothesis** ($H_1$ or $H_a$): a statement about the population parameter that is contradictory to the null hypothesis, and is accepted as true only if there is convincing evidence in favor of it. This is usually what a researcher is trying to prove.

The end result of a hypotheses testing procedure is a choice of one of the following two possible conclusions:

1. Reject $H0$ if the sample information favors the alternative hypothesis, or
2. Do not reject $H0$ if the sample information is insufficient to reject the null hypothesis.

| $H_0$  | $H_1$                    |
|--------|--------------------------|
| $=$    | $\ \ \neq$ or $>$ or $<$ |
| $\leq$ | $>$                      |
| $\geq$ | $<$                      |

- If $\alpha \leq p$-value, do not reject $H_0$.
- If $\alpha > p$-value, reject $H_0$.

### Statistical test of a hypothesis

The objective is to decide whether the hypothesis is supported by data from a sample (or an experiment).

- The hypothesis can be either true or false.
- We consider the hypothesis true, unless data indicate that it is false.

The practical approach is as follows:
1. Assume that the hypothesis is true.
2. Calculate the probability of outcomes at least as “rare” as the observed
outcome.
3. If this probability is small (typically less than 5 %), reject the hypothesis.
Otherwise, accept it.
