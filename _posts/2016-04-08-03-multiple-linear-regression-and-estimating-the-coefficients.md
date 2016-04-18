---
layout: post
title: 3.2 Multiple Linear Regression and Estimating the Coefficients
subtitle: ISLR Chapter 3 Outline
---
## 3.2 - Multiple Linear Regression

#### Multiple Linear Regression Model

$$Y = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + ... + \beta_p X_p + \epsilon$$

We interpret $$\beta_i$$, as the average effect on $$Y$$ for one unit change in 
$$X_i$$ holding all other predictors fixed.

<br/>

### 3.2.1 - Estimating the Regression Coefficients

#### Prediction of $$Y$$

$$\hat{y} = \hat{\beta_0} + \hat{\beta_1} x_1 + \hat{\beta_2} x_2 + ... + \hat{\beta_p} x_p$$

<br/>

#### Residual Sum of Squares

$$
\begin{align}
RSS &= \sum_{i=1}^n (y_i - \hat{y_i})^2 \\
  &= \sum_{i=1}^n (y_i - \hat{\beta_0} + \hat{\beta_1} x_{i1} + 
                                         \hat{\beta_2} x_{i2} + ... + 
                                         \hat{\beta_p} x_{ip})^2
\end{align}
$$

<br>

---

### 3.2.2 - Some Important Questions

#### One: Is there a relationship between the Response and the Predictors?

**Null Hypothesis ($$H_0$$)**: All the regression coefficients are zero

$$H_0: \beta_1 = \beta_2 = ... = \beta_p = 0$$

**Alternative Hypothesis ($$H_a$$)**: At least one regression coefficient is non-zero

<br/>

#### F-statistic

$$\frac{ (TSS - RSS) / p }
       { RSS / (n-p-1) }$$

When the linear model assumptions hold true then we have:

$$RSS / (n-p-i) = \sigma^2$$

However if $$H_0$$ is true then:

$$(TSS - RSS) / p = \sigma^2$$

and we would expect the F-statistic to be 1.

However if $$H_a$$ is true then:

$$(TSS - RSS) / p > \sigma^2$$

and we would expect the F-statistic to be >1. A large F-statistic correlates to
a low p-value.

However even if we have a F-statistic close to 1, if *n* is large, this might 
allow us to reject $$H_0$$.

We can also test whether a subset $$q$$ of the regression coefficients are zero,
which corresponds to the null hypothesis that:

$$H_0: \beta_{p-q+1} = \beta_{p-q+2} = ... = \beta_p = 0$$

in which you can see that we test whether all the other coefficients except the
last $$q$$ are equal to 0.

In this case the F-statistic would be:

$$F = \frac{ (RSS_0 - RSS) / q }{ RSS / (n - p - 1) }$$

where $$RSS_0$$ is the residual sum of squares for the model corresponding to 
$$H_0$$.

The t-statistic is equivalent to the F-statistic where we have omitted a single
variable from the model ($$t^2 = F$$)

#### Why Use the F-Statistic?

If we have a model with a large number of predictors (e.g. $$p$$ = 100), and if
the null hypothesis ($$H_0: \beta_1 = \beta_2 = ... = \beta_100 = 0$$) is true,
then 5% of p-values associated with the coefficients will be <0.05 by chance.
Therefore if we use the individual t-statistics and p-values we will
erroneously conclude that there is a relationship between the variables and the
response. However the F-statistic adjusts for the number of predictors and so
independent of the number of predictors, if $$H_0$$ is true, there is only 5%
chance that the F-statistic will have a p-value <0.05 by chance, regardless of
the number of predictors.

<br/>

#### Two: Deciding on Important Variables

**Forward Selection**: start with the null model and add the variable that
results in the lowest RSS and continue until a stopping rule has been satisfied

**Backward Selection**: start with all the variables in the model and remove the
variable with the largest p-value and continue until a stopping rule is reached

**Mixed Selection**: start with null model and add variables with the lowest RSS
as in Forward Selection, however if the p-value of a variable rises above a
certain threshold then it is removed, and this process is continued until all
variables in the model have a sufficiently low p-value and all the variables
outside the model have a high p-value if added

<br/>

#### Three: Model Fit

#### $$R^2$$ Statistic in the Multiple Linear Regression Model

$$R^2 = Cor(Y, \hat{Y})^2$$

<br/>

#### RSE in the Multiple Linear Regression Model

$$RSE = \sqrt{ \frac{1}{n-p-1} RSS }$$

Note that in the Simple Linear Regression, $$RSE = \sqrt{ \frac{1}{n-2} RSS }$$
because $$p = 1$$

<br/>

#### Four: Predictions

#### True Population Regression Plane

$$f(X) = \beta_0 + \beta_1 X_1 + ... + \beta_p X_p$$ 

<br/>

#### Least Squares Plane

$$\hat{Y} = \hat{\beta_0} + \hat{\beta_1} X_1 + ... + \hat{\beta_p} X_p$$

<br/>

Inaccuracy in the coefficient estimates is related to the *reducible error* and
we can calculate the **Confidence Interval** to determine how close $$\hat{Y}$$
will be to $$f(X)$$

To answer the question of how much will $$\hat{Y}$$ vary from $$Y$$, we use the 
**Prediction Intervals** which also incorporate the *irreducible error*. 
Therefore although the Prediction Interval will be centered at the same mean as
the Confidence Interval, it will be wider since it also takes into account the
irreducible error.