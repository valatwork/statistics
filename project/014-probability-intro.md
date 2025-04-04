# Probability

Probability theory serves as one of the building blocks for inferential statistics.  It's a branch of mathematics that tells you how often different kinds of events will happen.

In a long run, probability of an event can be viewed as a *proportion* of times this event happens, or its *relative frequency*. In forecasting, it is common to speak about the probability as a *likelihood*. In gambling and lottery, probability is equivalent to *odds*.

### Terminology

Note: unless otherwise specified, the definitions apply to probability theory.

#### Experiment
- A process that generates well-defined *outcomes*.

When discussing probability, many statisticians use the word *experiment* broadly to include surveys, so you can use the shorter definition “an outcome of an experiment”.

#### Sample space ($\Omega$)

- A collection of all elementary results, or outcomes of an experiment.

####  Outcome
- An outcome is a possible result of an *experiment*.

Each possible outcome of a particular experiment is unique, and different outcomes are mutually exclusive (only one outcome will occur on each trial of the experiment). All the possible outcomes of an experiment form the elements of a sample space ($\omega \in \Omega$).

#### Sigma-algebra ($\sigma$$-$$algebra$)
- A collection of events whose probabilities we can consider in our problem. It provides a way to define which subsets are measurable or observable within a particular event.

#### Event

- Any set of outcomes is an event. Thus, events are subsets of the sample space.

A single outcome may be an element of many different events, and different events in an experiment are usually not equally likely, since they may include very different groups of outcomes.

**Empty event** ($\emptyset$) : Empty events are always considered impossible.

**Elementary event**:  an event consisting of only a single outcome / an outcome that satisfies a single criterion

*(Synonym: atomic event)*

**Joint event**: an event consisting of two or more outcomes / an outcome that satisfies two or more criteria

*(Synonym: compound event)*

**Collectively exhaustive events**: a set of events that includes all possible outcomes of an experiment. When you have a set of collectively exhaustive events, one of them must occur.

**Dependent and independent events**: events that are affected by the occurrence of other events. Roughly speaking, we say that two events A and B are *dependent* if knowing something about whether A happens gives us information about whether B happens (and vice versa). Otherwise, they are *independent*.

#### Random variable
- A variable whose numerical values represent the events of an experiment

*(Synonym: random quantity, aleatory variable, stochastic variable)*

You use the phrase random variable to refer to a variable that has no data values until an experimental trial is performed or a survey question is asked and answered.

Random variables are either discrete, in which the possible numerical values are a set of integers (or coded values, in the case of categorical data), or continuous, in which any value is possible within a specific range.

#### Probability
- A number that represents the chance that a particular event will occur for a random variable.

Probability determines the likelihood that a random variable will be assigned a specific value. Probability considers things that might occur in the future, and its forward-looking nature provides a bridge to inferential statistics.

Probabilities can be developed for an elementary event of a random variable or any group of joint events.

Probabilities are formally stated as decimal numbers in the range of 0 to 1.

- A probability of 0 indicates an event that never occurs. (Such an event is known as a *null event*)
- A probability of 1 indicates a *certain event* — an event that must occur.

