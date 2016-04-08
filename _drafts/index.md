---
layout: page
title: Introduction to Statistical Learning with Application in R
subtitle: My personal notes
---

## Section 2

### Why Estimate $$f$$?

$$\hat{Y} = \hat{f}(X)$$

$$
\begin{align}
E(Y - \hat{Y})^2 & = E[f(X) + \epsilon - \hat{f}(X)]^2  \\
  & = E[(f(x) + \epsilon - \hat{f}(X)^2)(f(x) + \epsilon - \hat{f}(X)^2)]  \\
  & = [f(X) - \hat{f}(X)]^2 + Var(\epsilon)
\end{align}
$$

### Measuring the Quality of Fit

$$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{f}(x_i))^2$$

**Variance** refers to the amount by which $$\hat{f}$$ would change if we 
estimated it using a different training data set.

**Bias** refers to the error that is introduced by approximating a real-life
problem, which may be extremely complicated, by a much simpler model.

When we increase the *flexibility* of a class of methods, the **bias** tends to
initially decrease faster than the **variance** increases.

### The Classification Setting

$$Error \space rate = \frac{1}{n} \sum_{i=1}^{n} I (y_i \ne \hat{y_i})$$

### Bayes Classifier

$$Bayes \space error \space rate = 1 - E \Big[ \max_{j} Pr ( Y = j  | X) \Big]$$

## Section 3

### Estimating the Coefficients

Assume that there is a simple linear relationship between the dependent ($$Y$$)
variable and $$X$$. This can be described as:

$$Y \approx \beta_0 + \beta_1 \cdot x_1 + ... + \beta_p \cdot x_p$$

We use training data to estimate the coefficients, where training data is 
presented as:

$$(x_1, y_1), (x_2, y_2), ..., (x_n, y_n)$$

where there are $$n$$ observation pairs where each $$x$$ has $$p$$ parameters.

We then find the estimates for the coefficients:

$$\hat{Y} = \hat{\beta_0} + \hat{\beta_1} \cdot x_1 + ... + \hat{\beta_p} \cdot x_p$$

We can then obtain the estimate for $$Y$$ on the *ith* value of $$X$$:

$$\hat{y_i} = \hat{\beta_0} + \hat{\beta_1} \cdot x_{i,1} + ... + \hat{\beta_p} \cdot x_{i,n}$$

We define the *residuals* ($$e$$) as the difference between the *ith* observed response
and the *ith* predicted value of the model

$$e_i = y_i - \hat{y_i}$$

We then define the *Residual Sum of Squares (RSS)* as:

$$RSS = {e_1}^2 + {e_2}^2 + ... + {e_n}^2$$

$$RSS = \sum_{i=1}^{n} (y_i - \hat{y_i})^2$$

$$RSS = \sum_{i=1}^{n} (y_i - \hat{\beta_0} + \hat{\beta_1} \cdot x_{i,1} + 
                              \hat{\beta_2} \cdot x_{i,2} + ... + 
                              \hat{\beta_p} \cdot x_{i,p} )^2$$ 

The **least squares** approach to choosing the values for $$\beta$$ minimizes
the RSS

<br/>

### Assessing the Accuracy of the Coefficient Estimates

The true relationship between $$X$$ and $$Y$$ is given by:

$$Y = f(X) + \epsilon$$

where $$\epsilon$$ is a mean-zero random error term. This model defines the 
*population regression line* which is the best possible linear approximation of
the true relationship between $$Y$$ and $$X$$.

We assume that for $$Y$$ there is a population mean $$\mu$$ and similarly we 
define a sample mean $$\hat{\mu}$$. $$\hat{\mu}$$ obtained from a single sample 
might either overestimate or underestimate $$\mu$$, however the average of 
$$\hat{\mu}$$ over many data samples will be very close to $$\mu$$.

The question that we are interested in finding an answer for is: how far from 
$$\mu$$ will a *single* estimate of $$\hat{\mu}$$ be. The answer is to calculate
the **Standard Error** of $$\hat{\mu}$$:

$$SE(\hat{\mu})^2 = \frac { {\sigma}^2 }{ n } = Var(\hat{\mu})$$

Where $$\sigma$$ is the Standard Deviation of $$Y$$ and $${\sigma}^2$$ is the 
$$Var(\epsilon)$$. The Standard Error tells us the average amount that
$$\hat{\mu}$$ differs from the actual value of $$\mu$$.

Normally $$\sigma$$ is unknown, but this value can be estimated. This estimate
is called the *Residual Standard Error (RSE)*

$$RSE = \sqrt{RSS / (n - 2)}$$

Since $$RSE \approx \sigma$$, we can approximate the Standard Error as:

$$SE = \frac{ \sigma }{ \sqrt{n} } \approx \frac{ RSE }{ \sqrt{n} }$$

We can calculate the 95% confidence interval using the Standard Error

$$x \pm 2 \cdot SE(x)$$

Estimate of $$\sigma$$ is known as the *Residual Standard Error*

A variable is said to have no relationship with the dependent variable when the
coefficient ($$\beta$$) equals 0

Alternatively, a variable is said to have a relationship with the dependent
variable when the coefficient ($$\beta$$) does not equal 0

The *t-statistic* measures the number of Standard Deviations that the
coefficient is away from 0

$$t = \frac{ \beta - 0 }{ SE(\beta) }$$

*t-statistic* values are obtained from the *t-distribution*

The *p-value* is derived from comparing the *t-statistic* to the 
*t-distribution* of the sample for a given *degree of freedoms* ($$n$$ - 2)

### Assessing the Accuracy of the Model

The RSE is an estimate of the Standard Deviation of $$\epsilon$$, which is the
average amount that the response will deviate from the true regression line.

$$RSE = \sqrt{ \frac{1}{n - 2} RSS } = \sqrt{ \frac{1}{n - 2} \sum_{i = 1}^{n} (y_i - \hat{y_i})^2}$$

Another way to think of the RSE is that it is the "lack of fit" of the model.
The RSE is a measure of the "fit" of the model, however it is given in the units
of $$Y$$, therefore what it means may be unclear at times. An alternative 
measure is the $$R^2$$ statistic, which gives the "lack of fit" in terms of a
proportion, and it takes its values between 0 and 1 and never has any units. To
measure the $$R^2$$ statistic we need the *Total Sum of Squares (TSS)* and the
*Residual Sum of Squares (RSS)*, where

$$TSS = \sum (y_i - \bar{y_i})^2, RSS = \sum (y_i - \hat{y_i})^2$$

where $$\bar{y} \equiv \frac{1}{n} \sum_{i=1}^{n} y_i$$, which is the mean of 
$$y$$ and $$\bar{x} \equiv  \frac{1}{n} \sum_{i=1}^{n} x_i$$, which is the mean
of $$x$$, then

$$R^2 = \frac{ TSS - RSS }{ TSS } = 1 - \frac{ RSS }{ TSS }$$

The $$R^2$$ statistic therefore measures the proportion of variability in $$Y$$
that can be explained using $$X$$. Another way of thinking of it is that as
RSS approaches TSS (because $$\hat{y}$$ approaches $$\bar{y}$$), the value of
$$R^2$$ will approach 1.