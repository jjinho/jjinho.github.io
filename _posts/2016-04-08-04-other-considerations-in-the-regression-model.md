---
layout: post
title: 3.3 Other Considerations in the Regression Model
subtitle: ISLR Chapter 3 Outline
---
## 3.3 - Other Considerations in the Regression Model

### 3.3.1 - Qualitative Predictors

**Dummy variables** can be used as a way of including qualitative predictors 
into the regression model.

### 3.3.2 - Extensions of the Linear Model

### 3.3.3 - Potential Problems

#### Non-linearity of the data

**Residual Plots** are good for identifying *non-linearity* .In Simple Linear 
Regression we plot $$e_i = y_i - \hat{y_i}$$ against $$x_i$$ .In Multiple Linear 
Regression we plot $$e_i = y_i - \hat{y_i}$$ against $$\hat{y_i}$$. Ideally 
there should be no discernable pattern, however if there is a discernable 
pattern this may suggest non-linearity in the data. This can be dealt with by 
performing a non-linear transformation of the predictors (e.g. $$log(X)$$, 
$$\sqrt{X}$$, $$X^2$$, etc.).

<br/>

#### Correlation of Error Terms

Assumption of the linear regression model is that error terms ($$\epsilon_1,
\epsilon_2, ..., \epsilon_n$$) are uncorrelated. However correlation of the 
error terms means that the estimated Standard Error will underestimate the true
Standard Error, resulting in narrower Confidence/Prediction Intervals and lower
p-values.

Correlation of Error Terms is usually a problem with data belonging to a times
series. Observations at adjacent time points are more likely to have correlating
errors. If this is the case then when performing a residual plot we may see
**tracking** in the residuals

<br/>

#### Non-constant Variance of the Error Terms

Non-constant variance of the errors is called **heteroscedasticity**, which 
appears as a funnel shape in the residual plot. When this occurs a strategy is
to transform the response $$Y$$ using a concave function (e.g. $$log(Y)$$ or 
$$\sqrt{Y}$$).

<br/>

#### Outliers

Point for which $$y_i$$ is far from the predicted value of the model. To 
determine "how big" a residual needs to be before we consider it to be an 
outlier we plot the **Studentized Residuals** which is performed by dividing
each $$e_i$$ by its estimated Standard Error. If a *Studentized Residual* has an
absolute value >3, then we can consider it to be an outlier. Outliers can either
be due to problems with data collection or indicate a problem with the model.

<br/>

#### High Leverage Points

Observations with **high leverage** have an unusual value of $$x_i$$. 
Observations with a high leverage can have a disproportionate impact on the
estimated regression line. This can be clearly seen in Simple Linear Regression
by plotting the response to the observations, but this may not be so clear in
Multiple Linear Regression. 

#### Simple Linear Regression Leverage Statistic

$$h_i = \frac{1}{n} + \frac{ (x_i - \bar{x})^2 ) }{ \sum_{i=1}^n (x_i - \bar{x}) }$$

The value of $$h_i$$ ranges from $$1/n$$ to $$n$$ and the average leverage is 
$$(p+1)/n$$. A way to think of $$h_i$$ is that it is a measure of the distance 
from the mean of $$X$$.

<br/>

#### Multiple Linear Regression Leverage Statistic

$$h_i = H_{ii} = (X (X^T X)^{-1} X^T)_{ii}$$

In Multiple Linear Regression, $$h_i$$ measures the distance from the centroid
of $$X$$.

<br/>

#### Collinearity

**Collinearity** is where two or more predictor variables are closely related to 
one another. Collinearity reduces the accuracy of the estimates of the 
regression coefficients and therefore causes the Standard Error to increase,
which also causes a decrease in the t-statistic, therefore we may fail to reject
the null hypothesis and fail to find a non-zero coefficient.

Collinearity can be detected by a correlation matrix, with a high value telling
us that there is a highly correlated pair. However in the case of 
*multicollinearity* we cannot use correlation matrices. Instead we use the 
**Variance Inflation Factor (VIF)**.

#### Variance Inflation Factor

$$VIF(\hat{\beta_j}) = \frac{1}{ 1 - R_{X_j | X_{-j}}^2 }$$

where $$R_{X_j | X_{-j}}^2$$ is the regression of $$X_j$$ unto all other 
predictors. Note that as $$R_{X_j | X_{-j}}^2$$ becomes closer to 1, the VIF
grows larger. A VIF >5-10 indicates that there may be a problematic amount of
collinearity present.

<br/>