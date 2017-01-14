---
layout: post
title: Probability Distributions
subtitle: The Basics
---

## Rules of Probability

### Sum Rule

$$ P(X) = \sum_{Y} P(X,Y) $$


### Product Rule

$$ P(X,Y) = P(X | Y) P(X) $$


### Independence

$$ P(X,Y) = P(X) P(Y) $$

<br/>

## Definitions for Bayes Theorem

### Posterior Probability

$$ P(Y | X) $$


### Likelihood

$$ P(X | Y) $$


### Prior Probability

$$ P(Y) $$


### Bayes Theorem

$$ P(Y | X) = \frac{ P(X | Y) P(Y) }{ P(X) } $$


### Derivation of Bayes Theorem

$$
\begin{align}
  P(Y,X) &= P(X,Y) \\
  P(Y | X) P(X) &= P(X | Y) P(Y) \\
  P(Y | X) &= \frac{ P(X | Y) P(Y) }{ P(X) } 
\end{align}
$$
