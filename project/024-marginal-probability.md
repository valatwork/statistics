# Marginal Probability Distribution

A marginal distribution gets its name because it appears in the margins of a probability distribution table.

### Random discrete variables

For every possible state of $x$ in the set of the random variable $\mathrm{x}$, the probability that $\mathrm{x}$ is going to be equal to $x$, is the sum the probabilities of $\mathrm{x,y}$ across all states of $y$.

In short: he marginal probability of $\mathrm{x}$ at a particular value $x$ is found by summing over all possible values of $\mathrm{y}$

$$\forall x \in {\mathrm{x}}, P({\mathrm{x}}=x) = \sum_{y} P({\mathrm{x}}=x, {\mathrm{y}}=y)$$

**Why is it called a marginal distribution?**

The term "marginal" comes from the idea of summing the probabilities in the margins of a table.

If you sum each row to find the totals (the distribution for $\mathrm{x}$ only) or sum each column to find the totals (the distribution for Y only), you often write these sums in the “margins” of the table. Hence, the resulting probability distributions are called “marginal distributions.”

#### Example

| $x \downarrow y \to$ | $y_1$ | $y_2$ | $y_3$ | $y_4$ | Row sum | Margin      |
|----------------------|-------|-------|-------|-------|---------|-------------|
| $x_1$                | 2     | 5     | 25    | 3     | 35      | 35/76 = 46  |
| $x_2$                | 7     | 6     | 9     | 14    | 36      | 36/76 = 47  |
| $x_3$                | 4     | 1     | 0     | 0     | 5       | 5/76 = 0.07 |
| **Column sum**       | 13    | 12    | 34    | 17    | **76**  |             |

### Random continuous variables

To find how likely a continuous random variable is to fall within a particular range, you integrate the joint probability density function over that range.

$$p(x) = \int p(x, y)dy$$

Integrate all possible values of $y$ to find the probability density function for $x$.
