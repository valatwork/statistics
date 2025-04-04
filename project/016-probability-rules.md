## Probability Axioms

## Simple probability

The probability of an event $A$ is equal to the number of outcomes of the event divided by the total number of outcomes in the sample space $\Omega$.

$$P(A) = \frac{number \ of \ outcomes \ of \ A}{number \ of \ outcomes \ in \ \Omega}$$

This formula is valid only when all outcomes are equally likely.

### Axioms for Events

Given a sample space  $\Omega$, the class of subsets of $\Omega$  that constitute the set of events satisfies the following axioms:

1. $\Omega$  is an event.
2. For every sequence of events $A_1,A_2,…$, the union  $\bigcup_{n=1}^{\infty} A_n$  is an event.
3. For every event $A$, the complement  $\bar{A}$  is an event.

#### Corollaries

- The empty set  $\emptyset$  is an event (since $\emptyset = \bar{\Omega}$).
- Every finite union of events is an event. $A_1...\bigcup A_n$ as $\bigcup_{n=1}^{\infty} A_n$ where $A_i = \emptyset$ for $i > n$.
- Every finite or countable intersection of events is an event:

$$\overline{\bigcap_{i \in I} A_{i}} = \bigcup_{i \in I} \overline{A_{i}}$$

$$\overline{\bigcup_{i \in I} A_{i}} = \bigcap_{i \in I} \overline{A_{i}}$$

#### Sigma-algebra ($\sigma$$-$$algebra$)

A collection of events is a **sigma-algebra** on a sample space $\Omega$ if:
1. it includes the sample space,
$$\Omega \in \sigma-algebra$$
2. every event in $\sigma$$-$$algebra$ is contained along with its complement,
$$E \in \sigma-algebra \Rightarrow \bar{A} \in \sigma-algebra$$
3. every finite or countable collection of events in $\sigma$$-$$algebra$ is contained along with its union
$$A_1, A_2, A_3, ... \in \sigma-algebra \quad \Rightarrow \quad \bigcup_{i=1}^{\infty} A_i \in \sigma-algebra$$

**Trivial sigma-algebra**: a sigma-algebra that contains only the sample space and the empty set.
$$\sigma-algebra = \{\Omega, \emptyset\}$$
**Power set**: the collection of all the events of a sample space.
$$\sigma-algebra = 2^{\Omega}$$

It is crucial to notice that **only mutually exclusive events** (those with empty intersections) satisfy the sigma-additivity. If events intersect, their probabilities cannot be simply added.

## (Some) Rules of Probability

A set of rules governs the calculation of the probabilities of elementary and joint events.

#### Rule 1
- The probability of an event must be between 0 and 1.

$$0 \leq P(A) \leq 1$$

The smallest possible probability value is 0. You cannot have a negative probability. The largest possible probability value is 1. You cannot have a probability greater than 1.

#### Rule 2
-  The event that $A$ does not occur is called *$A$ complement*, or simply *not $A$*, and is given the symbol $\bar{A}$. If $P(A)$ represents the probability of event $A$ occurring, then $1 – P(A)$ represents the probability of event $A$ not occurring.

$$P(\bar{A}) = 1 - P(A)$$


#### Rule 3 (addition rule)
- If two events $A$ and $B$ are *mutually exclusive*, the probability of *both* events $A$ and $B$ occurring is 0. This means that the two events cannot occur at the same time.

$$P(A \cap B) = 0$$


This addition rule can be extended for mutually exclusive events to situations in which more than two events exist.

#### Rule 4 (addition rule)
-  If two events $A$ and $B$ are *not mutually exclusive*, the probability of either event $A$ or event $B$ occurring is the sum of their separate probabilities minus the probability of their simultaneous occurrence (the joint probability).

$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

#### Rule 5 (addition rule for mutually exclusive events)
- If two events A and B are *mutually exclusive*, the probability of *either* event A *or* event B occurring is the sum of their separate probabilities.

$$P(A \cup B) = P(A) + P(B)$$

#### Rule 6
- If events in a set are *mutually exclusive and collectively exhaustive* (cannot occur simultaneously and cover all possible outcomes) , the sum of their probabilities must add up to 1.

$$P(A) + P(\bar{A}) = 1$$

#### Rule 7 (general multiplication rule)
- If two events A and B are *dependent* (events are events that are affected by the occurrence of other events), the probability of both events $A$ and $B$ occurring is the product of the probability of event $A$ multiplied by the probability of event $B$ occurring, given that event $A$ has occurred.

$$P(A \cap B) = P(A) \cdot P(B | A)$$

#### Rule 8 (multiplication rule for *independent* events)
- If two events A and B are *independent*, the probability of *both* events $A$ and $B$ occurring is equal to the product of their individual probabilities. Two events are independent if *the occurrence of one event in no way affects the probability of the second event*.

$$P(A \cap B) = P(A) \cdot P(B)$$

#### Rule 9 (conditional probability)

- If two events are *dependent*, the probability of $A$ given $B$ is the probability that $A$ will occur given that $B$ has already occurred. *A conditional reduce the sample space*. We calculate the probability of $A$ from the reduced sample space $B$

$$P(A|B) = \frac{P(A\cap B)}{{P(B)}}$$

Now, taking this into consideration, a very clear definition of independence:

- Events $A$ and $B$ are independent if and only if the occurrence of $B$ does not affect the probability of $A$.

$$P(A|B) = P(A)$$

According to this definition, *conditional* probability equals *unconditional* probability in case of independent events.

$$P(A \cap B) = P(A) \cdot P(B)$$

#### Bayes' Theorem
Where $A$ and $B$ are events, and $P(A) \neq 0$:
- $P(B|A)$ is a conditional probability: the probability of event $B$ occurring given that $A$ is true
- $P(A|B)$ is also a conditional probability: the probability of event $A$ occurring given that $B$ is true
- $P(A)$ and $P(B)$ are the probabilities of observing $A$ and $B$ without any given conditions.

$$
P(B|A) = {\frac{P(B) \cdot P(A|B)}{P(A)} \ , \ if \ P(A) \neq 0}
$$
