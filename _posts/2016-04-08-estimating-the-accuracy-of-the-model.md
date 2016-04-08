---
layout: post
title: 3.1.3 Estimating the Accuracy of the Model
subtitle: ISLR Chapter 3 Outline
---
### 3.1.3 - Estimating the Accuracy of the Model

<br/>

#### Residual Standard Error (RSE)

$$RSE = \sigma \approx \sqrt{ \frac{1}{n - 2} RSS }$$

where RSS is:

$$RSS = \sum_{i=1}^n (y_i - \hat{y_i})^2$$

The RSE is the estimate of the Standard Deviation of $$\epsilon$$. The RSE is 
considered to be a measure of the *lack of fit* of a model. If the values of
$$\hat{y}$$ are very close to $$y$$ then the RSE will be small and we can say
that the model fits the data well.

The RSE is in terms of units $$Y$$. The $$R^2$$ statistic is an alternative form
of measuring the *fit* of a model that is in terms of a proportion.

<br/>

#### Total Sum of Squares (TSS)

$$TSS = \sum_{i=1}^n (y_i - \bar{y})^2$$

The Total Sum of Squares measures the *total variance* in the response $$Y$$. 
Recall that $$Var(y) = \frac{1}{n} \sum_{i=1}^n (y_i - \bar{y})^2$$. Therefore
the TSS tells us the variability inherent in the response $$Y$$ before we have
performed regression. 

<br/>

#### $$R^2$$ statistic

$$R^2 = \frac{ TSS - RSS }{ TSS } = 1 - \frac{ RSS }{ TSS }$$

TSS - RSS tells us the amount of variability that is removed by performing the 
regression. Since the value of RSS depends on $$X$$ ($$\hat{y}$$ having been 
derived from $$X$$), $$R^2$$ tells us the proportion of variability in $$Y$$ 
that can be explained using $$X$$. A value approaching 1 tells us that the
regression can explain all variability in $$Y$$ while a value approaching 0 
tells us that the regression explains none of the variability in $$Y$$ (either
because the model is wrong or the inherent error $$\sigma^2$$ is high or both).

<br/>

#### Correlation

$$r = \hat{Cor}(X,Y) = \frac{ \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y}) }
                            { \sqrt{\sum_{i=1}^n (x_i - \bar{x})^2} 
                              \sqrt{\sum_{i=1}^n (y_i - \bar{y})^2} }$$

The correlation also measures the linear relationship between $$X$$ and $$Y$$.
In simple cases, $$r^2 = R^2$$. However this does not extend to the case of
multiple linear regression, which is why we use $$R^2$$.