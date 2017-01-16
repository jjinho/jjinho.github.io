---
layout: post
title: Probability Distributions
subtitle: Notes from Chapter 2 of PRML
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


### Likelihood Function

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

<br>

## Probability Distributions

### Expectation

#### Discrete Distributions

$$ \mathbb{E}[f] = \sum_x p(x) f(x) $$

#### Continuous Distributions

$$ \mathbb{E}[f] = \int p(x) f(x) dx $$

<br>

### Variance

#### Variance of a function

$$ var[f] = \mathbb{E}[f(x)^2] - \mathbb{E}[f(x)]^2 $$

#### Variance of a random variable

$$ var[x] = \mathbb{E}[x] - \mathbb{E}[x]^2 $$

<br>

### Covariance

#### Covariance of two random variables

$$ cov[x,y] = \mathbb{E}_{x,y}[xy] - \mathbb{E}[x]\mathbb{E}[y] $$

#### Covariance of two vectors of random variables

$$ cov[\mathbf{x},\mathbf{y}] = \mathbb{E}_{\mathbf{x},\mathbf{y}}[\mathbf{x}\mathbf{y}^T] - \mathbb{E}[\mathbf{x}]\mathbb{E}[\mathbf{y}^T] $$

<br>

### Gaussian Distribution

$$ \mathcal{N} (x|\mu, \sigma^2) = \frac{1}{(2 \pi \sigma^2)^{1/2}} exp \Bigg\{ - \frac{1}{2 \sigma^2} (x - \mu)^2 \Bigg\} $$

#### Expectation of the first order moment

$$ \mathbb{E}[x] = \int_{-\infty}^{\infty} \mathcal{N} (x | \mu, \sigma^2) x dx = \mu $$  

#### Expectation of the second order moment

$$ \mathbb{E}[x^2] = \int_{-\infty}^{\infty} \mathcal{N} (x | \mu, \sigma^2) x^2 dx = \mu^2 + \sigma^2 $$  

#### Variance of the Gaussian Distribution

$$
\begin{align}
var[x] &= \mathbb{E}[x^2] - \mathbb{E}[x]^2 \\
       &= \mu^2 + \sigma^2 - (\mu)^2 \\
       &= \sigma^2
\end{align}
$$

#### Gaussian Distribution of D-dimensional vector x of continuous variables

$$ \mathcal{N}(\mathbf{x}| \mathbf{\mu}, \mathbf{\Sigma}) = 
\frac{1}{(2 \pi)^{D/2}} \frac{1}{|\mathbf{\Sigma}|^{1/2}}
exp \Bigg\{-\frac{1}{2} (\mathbf{x} - \mathbf{\mu})^T \mathbf{\Sigma}^{-1} (\mathbf{x} - \mathbf{\mu}) \Bigg\} $$

where $\mathbf{\mu}$ is a D-dimensional vector called the mean, $\mathbf{\Sigma}$ is a DxD matrix called the covariance,
and $|\mathbf{\Sigma}|$ denotes the determinant of $\mathbf{\Sigma}$.

<br>

### Estimating Parameters of a Gaussian Distribution from Samples

Data points that are drawn independently from the same distribution are said to 
be *independent and identically distributed* (i.i.d).

Remember that the joint probability of two independent events is the product of
the marginal probabilities for each separate events.

Therefore given a data set $\mathbf{x} = (x_1, ..., x_N)^T$, representing $N$
observations of a scalar variable $x$, we can write the probability of the data
set given $\mu$ and $\sigma^2$ as:

$$ p(\mathbf{x}|\mu, \sigma^2) = \prod_{n=1}^{N} \mathcal{N} (x_n | \mu, \sigma^2) $$

Going back to Bayes Theorem, the above expression is equivalent to the *Likelihood Function*.
Note that according to the Bayesian perspective, this is saying that we are going
to *maximize the data given the parameters of the function*, rather than the more
natural way of thinking of it, which would be to *maximize the parameters of the*
*function given the data* (note that this is the Frequentist perspective).

Our goal is to *maximize the Likelihood Function*. The easiest way to do this is
to maximize the log of the Likelihood Function, which is possible because the 
logarithm is a **monotonically** increasing function of its argument.

$$ \ln p(\mathbf{x}|\mu, \sigma^2) = - \frac{1}{2 \sigma^2} \sum_{n=1}^{N}(x_n - \mu)^2 - \frac{N}{2} \ln \sigma^2 - \frac{N}{2} \ln(2\pi) $$

Maximizing with respect to $\mu$ means that we will find find where the derivative
equals zero and so we get:

$$ \mu_{ML} = \frac{1}{N} \sum_{n=1}^{N} x_n $$

This is the *sample mean* (mean of the observed values in $\mathbf{x}$).

Doing the same process to maximize $\sigma^2$, we get:

$$ \sigma^2_{ML} = \frac{1}{N} \sum_{n=1}^{N} (x_n - \mu_{ML})^2 $$

This is the *sample variance* (variance of the observed values in $\mathbf{x}$).

From this we can show that:

$$
\begin{align}
\mathbb{E}[\mu_{ML}] &= \mu \\
\mathbb{E}[\sigma^2_{ML}] &= \Bigg( \frac{N-1}{N} \Bigg) \sigma^2 
\end{align}
$$

This suggests that the variance obtained from maximizing the Likelihood Function
underestimates the true variance, and therefore introduces *bias*. This also
suggests that as we increase the number of samples, the bias decreases.