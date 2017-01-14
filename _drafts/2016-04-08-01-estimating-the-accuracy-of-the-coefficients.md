---
layout: post
title: 3.1.2 Estimating the Accuracy of the Coefficients
subtitle: ISLR Chapter 3 Outline
---
### 3.1.2 - Estimating the Accuracy of the Coefficients

#### Relationship between Standard Deviation and Variance

$$Var(X) = \sigma^2$$

<br/>

#### Derivation of the relationship between Standard Deviation and Variance

$$E[X] = \mu$$

$$E[\mu] = \mu$$

$$
\begin{align}
\sigma &= \sqrt{ E[(X - \mu)^2] } \\
  &= \sqrt{ E[X^2] + E[-2 \mu X] + E[\mu^2] }  \\
  &= \sqrt{ E[X^2] - 2\mu E[X] + \mu^2 } \\
  &= \sqrt{ E[X^2] - 2\mu^2 + \mu^2 }  \\
  &= \sqrt{ E[X^2] - \mu^2 } \\
  &= \sqrt{ E[X^2] - E[X]^2 }  \\
  &= \sqrt{Var(X)}
\end{align}
$$

<br/>

#### Standard Error

$$SE(\hat{\mu}) = \frac{\sigma}{\sqrt{n}}$$

<br/>

#### Relationship between Standard Error and Variance

$$SE(\hat{\mu})^2 = \frac{Var(\hat{\mu})}{n} = \frac{\sigma^2}{n}$$

<br/>

#### Derivation of the relationship between Standard Error and Variance

$$
\begin{align}
SE(\hat{\mu}) & = \frac{\sigma}{\sqrt{n}} \\
  & = \sqrt{\frac{Var(\hat{\mu})}{n}}
\end{align}
$$

<br/>

#### Standard Error associated with $$\hat{\beta_0}$$ and $$\hat{\beta_1}$$

$$SE(\hat{\beta_0}^2) = \sigma^2 \Big[ \frac {1}{n} +
                        \frac {\bar{x}^2}{\sum_{i=1}^n(x_i - \bar{x})^2} \Big]$$
                        
$$SE(\hat{\beta_1}^2) = \frac {\sigma^2}{\sum_{i=1}^n(x_i - \bar{x})^2}$$

<br/>

#### Derivation of the Standard Error associated with $$\hat{\beta_1}$$

Some initial assumptions:

$$
\begin{align}
\sum_{i=1}^n (x_i - \bar{x}) \bar{y}
  &= \bar{y} \sum_{i=1}^n (x_i - \bar{x}) \\
  &= \bar{y} \Big( \sum_{i=1}^n x_i - \sum_{i=1}^n \bar{x} \Big)  \\
  &= \bar{y} \Big( \sum_{i=1}^n x_i - n \bar{x} \Big)  \\
  &= \bar{y} \Big( \sum_{i=1}^n x_i - n \frac{1}{n} \sum_{i=1}^n x_i \Big) \\
  &= \bar{y} \Big( \sum_{i=1}^n x_i - \sum_{i=1}^n x_i \Big) \\
  &= \bar{y} (0)  \\
  &= 0
\end{align}
$$

Another assumption:

$$
\begin{align}
\sum_{i=1}^n (x_i - \bar{x}) (y_i - \bar{y})
  &= \sum_{i=1}^n (x_i - \bar{x}) y_i - \sum_{i=1}^n (x_i - \bar{x}) \bar{y}  \\
  &= \sum_{i=1}^n (x_i - \bar{x}) y_i \\
  &= \sum_{i=1}^n (x_i - \bar{x}) (\beta_0 + \beta_1 x_i + \epsilon_i)
\end{align}
$$

Therefore:

$$
\begin{align}
Var(\hat{\beta_1}) 
  &=  Var \Big( \frac{ \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y}) }
                     { \sum_{i=1}^n (x_i - \bar{x})^2 } \Big) \\
  &=  \Big( \frac{1}{\sum_{i=1}^n (x_i - \bar{x})^2} \Big)^2
      Var \Big( \sum_{i=1}^n (x_i - \bar{x}) (y_i - \bar{y}) \Big) \\
  &=  \Big( \frac{1}{\sum_{i=1}^n (x_i - \bar{x})^2} \Big)^2
      Var \Big( \sum_{i=1}^n (x_i - \bar{x}) (\beta_0 + \beta_1 x_i + \epsilon_i) \Big) \\
  &=  \frac{( \sum_{i=1}^n (x_i - \bar{x}) )^2}{(\sum_{i=1}^n (x_i - \bar{x})^2)^2}
      Var (\beta_0 + \beta_1 x_i + \epsilon_i) \\
  &=  \frac{ \sum_{i=1}^n (x_i - \bar{x})^2 }{(\sum_{i=1}^n (x_i - \bar{x})^2)^2}
      Var (\beta_0 + \beta_1 x_i + \epsilon_i) \\
  &=  \frac{ \sum_{i=1}^n (x_i - \bar{x})^2 }{(\sum_{i=1}^n (x_i - \bar{x})^2)^2}
      Var (\epsilon_i) \\
  &=  \frac{ \sum_{i=1}^n (x_i - \bar{x})^2 }{(\sum_{i=1}^n (x_i - \bar{x})^2)^2}
      \sigma^2 \\
  &=  \frac{ 1 }{ \sum_{i=1}^n (x_i - \bar{x})^2 }
      \sigma^2 \\
  &=  \frac{ \sigma^2 }{ \sum_{i=1}^n (x_i - \bar{x})^2 }
\end{align}
$$

<br/>

#### Derivation of the Standard Error associated with $$\hat{\beta_0}$$

Some initial assumptions:

$$
\begin{align}
Var(\bar{y}) &= Var \Big( \frac{1}{n} \sum_{i=1}^n y_i \Big)  \\
  &= \frac{1}{n^2} Var \Big( \sum_{i=1}^n y_i \Big)  \\
  &= \frac{1}{n^2} Var \Big( \sum_{i=1}^n (\beta_0 + \beta_1 x_i + \epsilon_i) \Big) \\
  &= \frac{1}{n^2} Var \Big( \sum_{i=1}^n \beta_0 + \sum_{i=1}^n \beta_1 x_i + \sum_{i=1}^n \epsilon_i \Big) \\
  &= \frac{1}{n^2} Var \Big( \sum_{i=1}^n \epsilon_i \Big) \\
  &= \frac{1}{n^2} \sum_{i=1}^n Var ( \epsilon_i ) \\
  &= \frac{1}{n^2} n Var ( \epsilon_i ) \\
  &= \frac{1}{n} Var ( \epsilon_i ) \\
  &= \frac{1}{n} \sigma^2 \\
  &= \frac{\sigma^2}{n} \\
\end{align}
$$

Therefore:

$$
\begin{align}
Var(\hat{\beta_0}) &= Var(\bar{y} - \hat{\beta_1} \bar{x})  \\
  &= Var(\bar{y}) + Var(\hat{\beta_1} \bar{x})  \\
  &= \frac{\sigma^2}{n} + Var(\hat{\beta_1} \bar{x})  \\
  &= \frac{\sigma^2}{n} + \bar{x}^2 Var(\hat{\beta_1})  \\
  &= \frac{\sigma^2}{n} + \frac{ \sigma^2 \bar{x}^2 }{ \sum_{i=1}^n (x_i - \bar{x})^2 } \\
  &= \sigma^2 \Big( \frac{1}{n} + \frac{\bar{x}^2}{ \sum_{i=1}^n (x_i - \bar{x})^2 } \Big)\\
\end{align}
$$

<br/>

#### 95% Confidence Interval

$$\hat{\beta_0} \pm 2 \cdot SE(\hat{\beta_0})$$

$$\hat{\beta_1} \pm 2 \cdot SE(\hat{\beta_1})$$

<br/>

#### Hypothesis Testing

**Null Hypothesis ($$H_0$$)**: There is no relationship between $$X$$ and $$Y$$

$$H_0: \beta_1 = 0$$

**Alternative Hypothesis ($$H_a$$)**: There is a relationship between $$X$$ and $$Y$$

$$H_a: \beta_1 \ne 0$$

<br/>

#### t-statistic

$$t = \frac{\hat{\beta_1}}{SE(\hat{\beta_1})}$$

The *p-value* is the measure of the probability of observing any value $$\ge$$
to the absolute value of the t-statistic