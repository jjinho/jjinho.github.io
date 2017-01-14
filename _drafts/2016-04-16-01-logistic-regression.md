---
layout: post
title: 4.3 Logistic Regression
subtitle: ISLR Chapter 4 Outline
---
## 4.3 Logistic Regression

### 4.3.1 The Logistic Model

#### The Logistic Function

$$p(X) = \frac{ e^{\beta_0 + \beta_1 X} }{ 1 + e^{\beta_0 + \beta_1 X} }$$

<br/>

#### Odds

$$\frac{ p(X) }{ 1 - p(X) } = e^{\beta_0 + \beta_1 X}$$

Increasing $$X$$ by one unit multiplies the Odds by $$e^\beta_1$$.

<br/>

#### Derivation of the Odds

$$
\begin{align}
p(X) &= \frac{ e^{\beta_0 + \beta_1 X} }{ 1 + e^{\beta_0 + \beta_1 X} } \\
p(X) (1 + e^{\beta_0 + \beta_1 X}) &= e^{\beta_0 + \beta_1 X}   \\
p(X) + p(X) e^{\beta_0 + \beta_1 X} &= e^{\beta_0 + \beta_1 X}  \\
p(X) &= e^{\beta_0 + \beta_1 X} - p(X) e^{\beta_0 + \beta_1 X}  \\
p(X) &= e^{\beta_0 + \beta_1 X} (1 - p(X))  \\
\frac{ p(X) }{ 1 - p(X) } &= e^{\beta_0 + \beta_1 X}
\end{align}
$$

<br/>

#### The Logit

$$
\begin{align}
log \Big( \frac{ p(X) }{ 1 - p(X) } \Big) &= log \Big( 
                                                 e^{\beta_0 + \beta_1 X}
                                                 \Big)  \\
log \Big( \frac{ p(X) }{ 1 - p(X) } \Big) &= \beta_0 + \beta_1 X
\end{align}
$$

Increasing $$X$$ by one unit changes the log-odds (logit) by $$\beta_1$$.

<br/>

### 4.3.2 Estimating the Regression Coefficient

#### Likelihood Function

$$\ell(\beta_0, \beta_1) = \prod_{i:y_i = 1} p(x_i) 
                           \prod_{i^\prime:y_{i^\prime}} (1 - p(x_{i^\prime}))$$

$$\beta_0$$ and $$\beta_1$$ are chosen to maximize the likelihood function.

<br/>

#### z-statistic

$$z-statistic = \frac{ \hat{\beta_1} }{ SE(\hat{\beta_1}) }$$

The z-statistic plays a similar role to the t-statistic that we saw in linear
regression. A large value is evidence for us to reject the null hypothesis.

<br/>

#### Hypothesis Testing

$$H_0: \beta_1 = 0$$

The null hypothesis implies that

$$p(X) = \frac{ e^{\beta_0} }{ 1 + e^{\beta_0} }$$

<br/>

### 4.3.3 Making Predictions

#### Predicted Value

$$\hat{p}(X) = \frac{ e^{\hat{\beta_0} + \hat{\beta_1} X} }
                    { 1 + e^{\hat{\beta_0} + \hat{\beta_1} X} }$$

<br/>

### 4.3.4 Multiple Logistic Regression

#### The Logistic Function
$$p(X) = \frac{ e^{\beta_0 + \beta_1 X_1 + ... + \beta_p X_p} }
              { 1 + e^{\beta_0 + \beta_1 X_1 + ... + \beta_p X_p} }$$

<br/>

#### Logit

$$log \Big( \frac{ p(X) }{ 1 - p(X) } \Big) = \beta_0 + \beta_1 X_1 + ... + 
                                              \beta_p + X_p$$

<br/>

### 4.3.5 Logistic Regression for >2 Response Classes

This is usually not done, however it can be performed using statistical
packages such as *R*. **Discriminant Analysis** is often used instead for
multiple-class classification.