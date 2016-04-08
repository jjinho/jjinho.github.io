---
layout: post
title: 3.1.1 Simple Linear Regression and Estimating the Coefficients
subtitle: ISLR Chapter 3 Outline
---

## 3.1 - Simple Linear Regression

<br/>

#### Estimation of Y

$$Y \approx \beta_0 + \beta_1 x$$

<br/>

#### Prediction of Y:

$$\hat{y} = \hat{\beta}_0 + \hat{\beta}_1 x$$

<br/>

---

### 3.1.1 - Estimating the Coefficients

#### Residuals 

$$e_i = y_i - \hat{y_i}$$

<br/>

#### Residual Sum of Squares

$$RSS = e_1^2 + e_2^2 + ... + e_n^2$$

$$RSS = \sum_{i=1}^n (y_i - \hat{\beta_0} - \hat{\beta_1} x_i)^2$$

<br/>

#### Least Squares Coefficient Estimates that minimize the RSS

$$\hat{\beta_1} = \frac { \sum_{i=1}^n{(x_i - \bar{x}) (y_i - \bar{y})} }
                        { \sum_{i=1}^n{(x_i - \bar{x})^2} }$$

$$\hat{\beta_0} = \bar{y} - \hat{\beta_1} \bar{x}$$

<br/>

#### Deriving the Least Squares Coefficient Estimates

Partial derivatives of RSS with respect to $$\hat{\beta_0}$$

$$
\begin{align}
\frac{\partial{RSS}}{\partial{\hat{\beta_0}}} 
  &=  \frac{\partial}{\partial{\hat{\beta_0}}} \Big[
      \sum_{i=1}^n (y_i - \hat{\beta_0} - \hat{\beta_1} x_i)^2 \Big]  \\
  &=  \sum_{i=1}^n \Big[ \frac{\partial}{\partial{\hat{\beta_0}}}
      (y_i - \hat{\beta_0} - \hat{\beta_1} x_i)^2 \Big] \\
  &=  \sum_{i=1}^n \Big[ -2 (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big] \\
  &=  -2 \sum_{i=1}^n \Big[ (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big]
\end{align}
$$

Partial derivatives of RSS with respect to $$\hat{\beta_1}$$

$$
\begin{align}
\frac{\partial{RSS}}{\partial{\hat{\beta_1}}} 
  &= \frac{\partial}{\partial{\hat{\beta_1}}} \Big[
      \sum_{i=1}^n (y_i - \hat{\beta_0} - \hat{\beta_1} x_i)^2 \Big]  \\
  &=  \sum_{i=1}^n \Big[ \frac{\partial}{\partial{\hat{\beta_1}}}
      (y_i - \hat{\beta_0} - \hat{\beta_1} x_i)^2 \Big] \\
  &=  \sum_{i=1}^n \Big[ -2 x_i (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big] \\
  &=  -2 \sum_{i=1}^n \Big[ x_i (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big]
\end{align}
$$

Find the minimal RSS by setting the partial derivatives of RSS with respect to $$\hat{\beta_0}$$ to 0

$$
\begin{align}
  0 &= \frac{\partial{RSS}}{\partial{\hat{\beta_0}}}  \\
  0 &= -2 \sum_{i=1}^n \Big[ (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big]  \\
  0 &= \sum_{i=1}^n \Big[ (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big]  \\
  0 &= \sum_{i=1}^n y_i - \sum_{i=1}^n \hat{\beta_0} - \sum_{i=1}^n \hat{\beta_1} x_i \\
  \sum_{i=1}^n \hat{\beta_0} &= \sum_{i=1}^n y_i - \sum_{i=1}^n \hat{\beta_1} x_i \\
  n \hat{\beta_0}            &= \sum_{i=1}^n y_i - \sum_{i=1}^n \hat{\beta_1} x_i \\
  \hat{\beta_0}   &= \frac{1}{n} \sum_{i=1}^n y_i - \frac{1}{n} \sum_{i=1}^n \hat{\beta_1} x_i \\
  \hat{\beta_0}   &= \underbrace{\frac{1}{n} \sum_{i=1}^n y_i}_\text{mean of y}
                     - \hat{\beta_1} \underbrace{(\frac{1}{n} \sum_{i=1}^n x_i)}_\text{mean of x} \\
  \hat{\beta_0}   &= \bar{y} - \hat{\beta_1} \bar{x}
\end{align}
$$

Find the minimal RSS by setting the partial derivatives of RSS with respect to $$\hat{\beta_1}$$ to 0

$$
\begin{align}
  0 &= \frac{\partial{RSS}}{\partial{\hat{\beta_1}}}  \\
  0 &=  -2 \sum_{i=1}^n \Big[ x_i (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big] \\
  0 &= \sum_{i=1}^n \Big[ x_i (y_i - \hat{\beta_0} - \hat{\beta_1} x_i) \Big] \\
  0 &= \sum_{i=1}^n \Big[ x_i y_i - \hat{\beta_0} x_i - \hat{\beta_1} x_i^2) \Big] \\
  0 &= \sum_{i=1}^n x_i y_i - \hat{\beta_0} \sum_{i=1}^n x_i - \hat{\beta_1} \sum_{i=1}^n x_i^2 \\
  0 &= \sum_{i=1}^n x_i y_i - (\bar{y} - \hat{\beta_1} \bar{x}) \sum_{i=1}^n x_i - 
       \hat{\beta_1} \sum_{i=1}^n x_i^2 \\
  0 &= \sum_{i=1}^n x_i y_i - \bar{y} \sum_{i=1}^n x_i + \hat{\beta_1} \bar{x} \sum_{i=1}^n x_i -
       \hat{\beta_1} \sum_{i=1}^n x_i^2 \\
  \hat{\beta_1} \Big( \sum_{i=1}^n x_i^2 - \bar{x} \sum_{i=1}^n x_i \Big)
    &= \sum_{i=1}^n x_i y_i - \bar{y} \sum_{i=1}^n x_i \\
  \hat{\beta_1}
    &= \frac{\sum_{i=1}^n x_i y_i - \bar{y} \sum_{i=1}^n x_i}
            {\sum_{i=1}^n x_i^2 - \bar{x} \sum_{i=1}^n x_i} \\
  \hat{\beta_1}
    &= \frac{\sum_{i=1}^n x_i y_i - \frac{1}{n} \sum_{i=1}^n y_i \sum_{i=1}^n x_i}
            {\sum_{i=1}^n x_i^2 - \frac{1}{n} \sum_{i=1}^n x_i \sum_{i=1}^n x_i} \\
  \hat{\beta_1}
    &= \frac{\sum_{i=1}^n x_i y_i - \frac{1}{n} \sum_{i=1}^n y_i \sum_{i=1}^n x_i}
            {\sum_{i=1}^n x_i^2 - \frac{1}{n} (\sum_{i=1}^n x_i)^2} \\
  \hat{\beta_1}
    &= \frac{\sum_{i=1}^n x_i y_i - \frac{1}{n} \sum_{i=1}^n y_i \sum_{i=1}^n x_i}
            {\sum_{i=1}^n x_i^2 - \frac{1}{n} (\sum_{i=1}^n x_i)^2} \cdot
       \frac{n}{n}  \\
  \hat{\beta_1}
    &= \frac{n \sum_{i=1}^n x_i y_i - \sum_{i=1}^n y_i \sum_{i=1}^n x_i}
            {n \sum_{i=1}^n x_i^2 - (\sum_{i=1}^n x_i)^2} \\
  \hat{\beta_1}
    &= \frac{n \sum_{i=1}^n x_i y_i - \sum_{i=1}^n y_i \sum_{i=1}^n x_i}
            {n \sum_{i=1}^n x_i^2 - (\sum_{i=1}^n x_i)^2} \cdot
       \frac{ \frac{1}{n^2} }{ \frac{1}{n^2} }  \\
  \hat{\beta_1}
    &= \frac{ \frac{1}{n} \sum_{i=1}^n x_i y_i - \frac{1}{n} \sum_{i=1}^n y_i \frac{1}{n} \sum_{i=1}^n x_i}
            { \frac{1}{n} \sum_{i=1}^n x_i^2 - (\frac{1}{n} \sum_{i=1}^n x_i)^2} \\
  \hat{\beta_1}
    &= \frac{ \frac{1}{n} \sum_{i=1}^n x_i y_i - \bar{x} \bar{y} }
            { \frac{1}{n} \sum_{i=1}^n x_i^2 - (\bar{x})^2}
\end{align}
$$

We show that the numerator is equivalent to $$\frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})$$

$$
\begin{align}
\frac{1}{n} \sum_{i=1}^n x_i y_i - \bar{x} \bar{y}
  &= \frac{1}{n} \sum_{i=1}^n x_i y_i - \frac{n}{n} \bar{x} \bar{y} \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i y_i - n \bar{x}\bar{y} \Big) \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i y_i - n \bar{x}\bar{y} - n \bar{x}\bar{y} + n \bar{x}\bar{y} \Big) \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i y_i - \bar{x}(n \bar{y}) - \bar{y}(n \bar{x}) + n \bar{x}\bar{y} \Big) \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i y_i - \bar{x} \sum_{i=1}^n y_i - \bar{y} \sum_{i=1}^n x_i + \sum_{i=1}^n \bar{x}\bar{y} \Big) \\  
  &= \frac{1}{n} \sum_{i=1}^n \Big(x_i y_i - \bar{x} y_i - \bar{y} x_i + \bar{x}\bar{y} \Big) \\  
  &= \underbrace{\frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}_{Cov(X, Y)}
\end{align}
$$

We show that the denominator is equivalent to $$\frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2$$

$$
\begin{align}
\frac{1}{n} \sum_{i=1}^n x_i^2 - (\bar{x})^2
  &= \frac{1}{n} \sum_{i=1}^n x_i^2 - \frac{n}{n} (\bar{x})^2 \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i^2 - n \bar{x}^2 \Big) \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i^2 - 2n \bar{x}^2 + n \bar{x}^2 \Big) \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i^2 - 2 \bar{x} (n \bar{x}) + n \bar{x}^2 \Big) \\
  &= \frac{1}{n} \Big( \sum_{i=1}^n x_i^2 - 2 \bar{x} \sum_{i=1}^n x_i + \sum_{i=1}^n \bar{x}^2 \Big) \\
  &= \frac{1}{n} \sum_{i=1}^n \Big( x_i^2 - 2 \bar{x} x_i + \bar{x}^2 \Big) \\
  &= \underbrace{\frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2}_{Var(X)}
\end{align}
$$

Therefore the minimizer for $$\beta_1$$ is

$$
\begin{align}
  \hat{\beta_1}
    &= \frac{ \frac{1}{n} \sum_{i=1}^n x_i y_i - \bar{x} \bar{y} }
            { \frac{1}{n} \sum_{i=1}^n x_i^2 - (\bar{x})^2} \\
    &= \frac{ \overbrace{  \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y}) }^{Covariance} }
            { \underbrace{ \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2 }_{Variance} }  \\
    &= \frac{ \sum_{i=1}^n (x_i - \bar{x}) (y_i - \bar{y}) }
            { \sum_{i=1}^n (x_i - \bar{x})^2 }
\end{align}
$$