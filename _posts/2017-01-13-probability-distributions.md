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


## Probability Distributions

### Expectation

#### Discrete Distributions

$$ \mathbb{E}[f] = \sum_x p(x) f(x) $$

#### Continuous Distributions

$$ \mathbb{E}[f] = \int p(x) f(x) dx $$


### Variance

#### Variance of a function

$$ var[f] = \mathbb{E}[f(x)^2] - \mathbb{E}[f(x)]^2 $$

#### Variance of a random variable

$$ var[x] = \mathbb{E}[x] - \mathbb{E}[x]^2 $$


### Covariance

#### Covariance of two random variables

$$ cov[x,y] = \mathbb{E}_{x,y}[xy] - \mathbb{E}[x]\mathbb{E}[y] $$

#### Covariance of two vectors of random variables

$$ cov[\mathbf{x},\mathbf{y}] = \mathbb{E}_{\mathbf{x},\mathbf{y}}[\mathbf{x}\mathbf{y}^T] - \mathbb{E}[\mathbf{x}]\mathbb{E}[\mathbf{y}^T] $$


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