---
layout: page
title: ISLR
subtitle: Exercises
---

## Chapter 3

#### Conceptual

1) Describe the null hypotheses to which the p-values given in Table 3.4 
correspond. Explain what conclusions you can draw based on these p-values. Your 
explanation should be phrased in terms of sales, TV, radio, and newspaper, 
rather than in terms of the coefficients of the linear model.

*Null Hypothesis for TV: TV advertisements have no relationship to sales*
    
*The p-value of <0.0001 means that we reject the null hypothesis because there 
is <0.01% probability of the null hypothesis being true, therefore TV
advertisements are related to sales.*
    
*Null Hypothesis for Radio: Radio advertisements have no relationship to sales*

*The p-value of <0.0001 means that we reject the null hypothesis because there 
is a <0.01% probability of the null hypothesis being true, therefore radio 
advertisements are related to sales.*

*Null Hypothesis for Newspaper: Newspaper advertisements have no relationship to sales*

*The p-value of 0.8599 means that we accept the null hypothesis, therefore
newspaper advertisements are not likely to be related to sales.*
    
<br/>

2) Carefully explain the differences between the KNN classifier and KNN
regression methods.
    
*The KNN classifier is a qualitative method that for a given point in space
looks at the k-closest neighbors and whichever class has the majority, will
classify that point as belonging to the majority. The KNN regression method is a
quantitative method that for a given predictor $$x_i$$ looks at the k-closest 
neighbors and takes the average value to generate $$\hat{y_i}$$.*

<br/>

3) Suppose we have a data set with five predictors, $$X_1$$ = GPA, $$X_2$$ = IQ,
$$X_3$$ = Gender (1 for Female and 0 for Male), $$X_4$$ = Interaction between
GPA and IQ, and $$X_5$$ = Interaction between GPA and Gender. The
response is starting salary after graduation (in thousands of dollars).
Suppose we use least squares to fit the model, and get $$\hat{\beta_0}$$ = 50, 
$$\hat{\beta_1}$$ = 20, $$\hat{\beta_2}$$ = 0.07, $$\hat{\beta_3}$$ = 35, 
$$\hat{\beta_4}$$ = 0.01, $$\hat{\beta_5}$$ = −10.

A. Which answer is correct, and why?

i. For a fixed value of IQ and GPA, males earn more on average than females.

ii. For a fixed value of IQ and GPA, females earn more on average than males.
    
iii. For a fixed value of IQ and GPA, males earn more on average than females 
provided that the GPA is high enough.
    
iv. For a fixed value of IQ and GPA, females earn more on average than males 
provided that the GPA is high enough.

*Choice iii is true provided that the GPA of the female is >3.5*
    
The multiple regression equation is:

$$Salary = \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \beta_3 X_3 + 
           \beta_4 (X_1 X_2) + \beta_5 (X_1 X_3)$$

Since $$X_3 = 0$$ for males:

$$
\begin{align}
Salary_M &= \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \beta_4 (X_1 X_2) \\
    &= 50 + 20 X_1 + 0.07 X_2 + 0.01 (X_1 X_2)
\end{align}
$$

Since $$X_3 = 1$$ for females:

$$
\begin{align}
Salary_F &= \beta_0 + \beta_1 X_1 + \beta_2 X_2 + \beta_3 + 
             \beta_4 (X_1 X_2) + \beta_5 X_1  \\
    &= 50 + 20 X_1 + 0.07 X_2 + 35 + 0.01 (X_1 X_2) - 10 X_1
\end{align}
$$

B. Predict the salary of a female with IQ of 110 and a GPA of 4.0.

$$
\begin{align}
Salary_F &= 50 + 20 X_1 + 0.07 X_2 + 35 + 0.01 (X_1 X_2) - 10 X_1   \\
    &= 50 + 20 (4.0) + 0.07 (110) + 35 + 0.01 (110 \cdot 4.0) - 10 (4.0)    \\
    &= 137.1 (k)
\end{align}
$$

C. True or false: Since the coefficient for the GPA/IQ interaction term is very 
small, there is very little evidence of an interaction effect. Justify your 
answer.
   
*This statement is false. The coefficient alone does not tell us whether we can 
accept the null hypothesis. We need the standard error of the coefficient to 
give us the t-statistic and therefore the p-value which will let us decide 
whether or not to accept the null hypothesis.*

4) I collect a set of data (n = 100 observations) containing a single
predictor and a quantitative response. I then fit a linear regression
model to the data, as well as a separate cubic regression, i.e. $$Y =
\beta_0 + \beta_1 X + \beta_2 X^2 + \beta_3 X^3 + \epsilon$$.

A. Suppose that the true relationship between $$X$$ and $$Y$$ is linear, i.e. 
$$Y = \beta_0 + \beta_1 X + \epsilon$$. Consider the training residual sum of 
squares (RSS) for the linear regression, and also the training RSS for the cubic
regression. Would we expect one to be lower than the other, would we expect them
to be the same, or is there not enough information to tell? Justify your answer.

*Since the cubic regression will fit the training data better, we would
expect the RSS to be lower compared to the linear regression model.*

B. Answer (A) using test rather than training RSS.

*However since the cubic regression overfits the training data, once fitted
onto test data, we would expect the RSS to be higher compared to the linear
regression model.*

C. Suppose that the true relationship between $$X$$ and $$Y$$ is not linear, but
we don’t know how far it is from linear. Consider the training RSS for the 
linear regression, and also the training RSS for the cubic regression. Would we
expect one to be lower than the other, would we expect them to be the same, or 
is there not enough information to tell? Justify your answer.

*We would still expect the cubic model to fit the training data better and
therefore to have a lower RSS.*

D. Answer (C) using test rather than training RSS.

*We do not have enough information to answer the question since we do not
know "how far it is from linear." The linear regression model may do better
to a "more linear" model while the cubic regression model may do better with
a more non-linear model.*

<br/>

5) Consider the fitted values that result from performing linear regression
without an intercept. In this setting, the *i*th fitted value takes
the form

$$\hat{y_i} = x_i \hat{\beta_i}$$

where

$$\hat{\beta} = \Big( \sum_{i=1}^n x_i y_i \Big) / \Big( \sum_{i=1}^n x_{k}^2 \Big)$$

Show that we can write

$$\hat{y_i} = \sum_{j=1}^n a_{j} y_{j}$$

What is $$a_{j}$$?

*Note: We interpret this result by saying that the fitted values from
linear regression are linear combinations of the response values.*

$$
\begin{align}
\hat{y_i} &= x_i \hat{\beta}    \\
    &= x_i \Big( \frac{ \sum_{j=1}^n x_j y_j }
                      { \sum_{k=1}^n x_k^2 } \Big)  \\
    &= \frac{ \sum_{j=1}^n x_i x_j y_j }{ \sum_{k=1}^n x_k^2 }  \\
    &= y_i \Big( \frac{ \sum_{j=1}^n x_j x_i }
                      { \sum_{k=1}^n x_k^2 } \Big)  \\
    &= y_i \sum_{j=1}^n \Big( \frac{ x_j x_i }
                                   { \sum_{k=1}^n x_k^2 } \Big)
\end{align}
$$

Therefore $$a_j = \frac{ x_j x_i }{ \sum_{k=1}^n x_k^2 }$$

<br/>

6) Using (3.4), argue that in the case of simple linear regression, the
least squares line always passes through the point ($$\bar{x}$$, $$\bar{y}$$).

$$\hat{Y} = \hat{\beta_0} + \hat{\beta_1} X$$

If we assume that this line passes through $$(\bar{x}, \bar{y})$$, then let
us set $$\hat{Y} = \bar{y}$$ and $$X = \bar{x}$$.

$$
\begin{align}
\bar{y} &= \hat{\beta_0} + \hat{\beta_1} \bar{x}    \\
    &= (\bar{y} - \hat{\beta_1} \bar{x}) + \hat{\beta_1} \bar{x}    \\
    &= \bar{y}
\end{align}
$$

Therefore we show that in simple linear regression the least squares line 
always passes through $$(\bar{x}, \bar{y})$$

<br/>

7) It is claimed in the text that in the case of simple linear regression
of $$Y$$ onto $$X$$, the $$R^2$$ statistic (3.17) is equal to the square of the
correlation between $$X$$ and $$Y$$ (3.18). Prove that this is the case. For
simplicity, you may assume that $$\bar{x} = \bar{y} = 0$$.

$$Y = \hat{Y} + \epsilon$$

$$
\begin{align}
TSS &= \sum_{i=1}^n (y_i - \bar{y})^2   \\
    &= \sum_{i=1}^n (y_i)^2
\end{align}
$$

$$
\begin{align}
RSS &= \sum_{i=1}^n (y_i - \hat{y_i})^2    \\
    &= \sum_{i=1}^n (\epsilon_i)^2
\end{align}
$$

$$
\begin{align}
ESS &= \sum_{i=1}^n (\hat{y_i} - \bar{y})^2 \\
    &= \sum_{i=1}^n (\hat{y_i})^2
\end{align}
$$

$$
\begin{align}
R^2 &= 1 - \frac{RSS}{TSS}  \\
    &= \frac{TSS - RSS}{TSS}    \\
    &= \frac{ESS}{TSS}
\end{align}
$$

$$Cor(Y, \hat{Y}) = \frac{ Cov(Y, \hat{Y}) }{ \sqrt{Var(Y) Var(\hat{Y})} }$$

$$
\begin{align}
R^2 &= Cor(Y, \hat{Y})^2    \\
    &= \frac{ Cov(Y, \hat{Y})^2 }
            { \Big( \sqrt{Var(Y) Var(\hat{Y})} \Big)^2 }  \\
    &= \frac{ Cov(Y, \hat{Y})^2 }
            { Var(Y) Var(\hat{Y}) } \\
    &= \frac{ Cov(\hat{Y} + \epsilon, \hat{Y})^2 }
            { Var(Y) Var(\hat{Y}) } \\
    &= \frac{ Cov(\hat{Y} + \epsilon, \hat{Y})Cov(\hat{Y} + \epsilon, \hat{Y}) }
            { Var(Y) Var(\hat{Y}) } \\
    &= \frac{ \Big( Cov(\hat{Y}, \hat{Y}) + Cov(\hat{Y}, \epsilon) \Big)
              \Big( Cov(\hat{Y}, \hat{Y}) + Cov(\hat{Y}, \epsilon) \Big) }
            { Var(Y) Var(\hat{Y}) } \\
    &= \frac{ Cov(\hat{Y}, \hat{Y}) Cov(\hat{Y}, \hat{Y}) }
            { Var(Y) Var(\hat{Y}) } \\
    &= \frac{ Var(\hat{Y}) Var(\hat{Y}) }
            { Var(Y) Var(\hat{Y}) } \\
    &= \frac{ Var(\hat{Y}) }{ Var(Y) } \\
    &= \frac{ \frac{1}{n} \sum_{i=1}^n (\hat{y_i} - \bar{y})^2 }
            { \frac{1}{n} \sum_{i=1}^n (y_i - \bar{y})^2 }  \\
    &= \frac{ \sum_{i=1}^n (\hat{y_i} - \bar{y})^2 }
            { \sum_{i=1}^n (y_i - \bar{y})^2 }  \\
    &= \frac{ ESS }{ TSS }  \\
    &= R^2
\end{align}
$$

<br/>

## Chapter 4

### Conceptual

1) Using a little bit of algebra, prove that (4.2) is equivalent to (4.3). In
other words, the logistic function representation and logit representation for 
the logistic regression model are equivalent.

$$
\begin{align}
p(X) &= \frac{e^{\beta_0 + \beta_1 X}}{1 + e^{\beta_0 + \beta_1 X}} \\
p(X) (1 + e^{\beta_0 + \beta_1 X}) &= e^{\beta_0 + \beta_1 X}   \\
p(X) + p(X) (e^{\beta_0 + \beta_1 X}) &= e^{\beta_0 + \beta_1 X}    \\
p(X) &= e^{\beta_0 + \beta_1 X} - p(X) (e^{\beta_0 + \beta_1 X})    \\
p(X) &= e^{\beta_0 + \beta_1 X} (1 - p(X))  \\
\frac{p(X)}{1 - p(X)} &= e^{\beta_0 + \beta_1 X}
\end{align}
$$


2) It was stated in the text that classifying an observation to the class for 
which (4.12) is largest is equivalent to classifying an observation to the class
for which (4.13) is largest. Prove that this is the case. In other words, under 
the assumption that the observations in the $$k$$th class are drawn from a 
$$N(\mu k, \sigma_k^2)$$  distribution, the Bayes’ classifier assigns an 
observation to the class for which the discriminant function is maximized.

Equation 4.12 states

$$
p_k(x) = \frac{ \pi_k \frac{1}{\sqrt{2\pi}\sigma} 
                exp \Big(-\frac{1}{2\sigma^2}(x - \mu_k)^2 \Big) }
              { \sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi}\sigma}
                exp \Big(-\frac{1}{2\sigma^2} (x - \mu_k)^2 \Big) }  
$$

Equation 4.13 states

$$\delta_k(x) = x \cdot \frac{\mu_k}{\sigma^2} -
                \frac{\mu_k^2}{2 \sigma^2} + 
                log(\pi_k)
$$
                
Since we are trying to classify an observation to the $$k$$th class we can say

$$
\begin{align}
p_k(x) &\propto \pi_k \frac{1}{\sqrt{2\pi}\sigma} 
                exp \Big(-\frac{1}{2\sigma^2}(x - \mu_k)^2 \Big)\\
log(p_k(x)) 
    &\propto log(\pi_k) - log(\sqrt{2\pi}\sigma) - 
             \frac{1}{2 \sigma^2} (x - \mu_k)^2  \\
    &\propto log(\pi_k) - log(\sqrt{2\pi}\sigma) - 
             \frac{1}{2 \sigma^2} (x^2 - 2x\mu_k + \mu_k^2)  \\
    &\propto log(\pi_k) - log(\sqrt{2\pi}\sigma) - \frac{x^2}{2 \sigma^2} + 
             \frac{2x\mu_k}{2 \sigma^2} + \frac{\mu_k^2}{2 \sigma^2} \\
    &\propto log(\pi_k) + \frac{2x\mu_k}{2 \sigma^2} + 
             \frac{\mu_k^2}{2 \sigma^2} \\
    &\propto log(\pi_k) + x \cdot \frac{\mu_k}{\sigma^2} + 
             \frac{\mu_k^2}{2 \sigma^2} \\
\end{align}
$$

<br/>

3) This problem relates to the QDA model, in which the observations within each
class are drawn from a normal distribution with a class specific mean vector and
a class specific covariance matrix. We consider the simple case where $$p = 1$$;
i.e. there is only one feature.

Suppose that we have $$K$$ classes, and that if an observation belongs to the 
$$k$$th class then $$X$$ comes from a one-dimensional normal distribution,
$$X \sim N(\mu k, \sigma_k^2)$$. Recall that the density function for the
one-dimensional normal distribution is given in (4.11). Prove that in this case,
the Bayes’ classifier is not linear. Argue that it is in fact quadratic.


Equation 4.11 states

$$f(x) = \frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}} 
         exp \Big( -\frac{1}{2}(x-\mu)^T \Sigma^{-1}(x - \mu) \Big)$$

Bayes' Theorem states

$$
Pr(Y = k | X = x) = \frac{\pi_k f_k(x)}{\sum_{l=1}^K \pi_l f_l(x)}
$$


We will assume that the covariance matrix is distinct for each class $$K$$.
Since we are trying to classify an observation to the $$k$$th class we can say

$$
\begin{align}
p_k(x) &\propto \pi_k f_k(x) \\
log(p_k(x)) 
    &\propto log(\pi_k) + log(f_k(x)) \\
    &\propto log(\pi_k) + 
             log \Big[
                      \frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}} 
                      exp \Big( -\frac{1}{2}(x-\mu)^T \Sigma^{-1}(x - \mu) \Big)
                  \Big]
\end{align}
$$

<br/>

<br/>

4) When the number of features p is large, there tends to be a deterioration in 
the performance of KNN and other local approaches that perform prediction using 
only observations that are near the test observation for which a prediction must
be made. This phenomenon is known as the *curse of dimensionality*, and it ties 
into the fact that non-parametric approaches often perform poorly when p is 
large. We will now investigate this curse.

A. Suppose that we have a set of observations, each with measurements on 
$$p = 1$$ feature, $$X$$. We assume that $$X$$ is uniformly (evenly) distributed
on $$[0, 1]$$. Associated with each observation is a response value. Suppose 
that we wish to predict a test observation’s response using only observations 
that are within 10% of the range of $$X$$ closest to that test observation. For 
instance, in order to predict the response for a test observation with 
$$X = 0.6$$, we will use observations in the range $$[0.55, 0.65]$$. On average, 
what fraction of the available observations will we use to make the prediction?

B. Now suppose that we have a set of observations, each with measurements on 
$$p = 2$$ features, $$X1$$ and $$X_2$$. We assume that $$(X_1,X_2)$$ are 
uniformly distributed on $$[0, 1] × [0, 1]$$. We wish to predict a test 
observation’s response using only observations that are within 10% of the range 
of $$X_1$$ and within 10% of the range of $$X_2$$ closest to that test 
observation. For instance, in order to predict the response for a test 
observation with $$X_1 = 0.6$$ and $$X_2 = 0.35$$, we will use observations in 
the range $$[0.55, 0.65]$$ for $$X_1$$ and in the range $$[0.3, 0.4]$$ for 
$$X_2$$. On average, what fraction of the available observations will we use to 
make the prediction?

C. Now suppose that we have a set of observations on $$p = 100$$ features. Again
the observations are uniformly distributed on each feature, and again each 
feature ranges in value from 0 to 1. We wish to predict a test observation’s 
response using observations within the 10% of each feature’s range that is 
closest to that test observation. What fraction of the available observations 
will we use to make the prediction?

D. Using your answers to parts (A)–(C), argue that a drawback of KNN when $$p$$ 
is large is that there are very few training observations “near” any given test
observation.

E. Now suppose that we wish to make a prediction for a test observation by 
creating a $$p$$-dimensional hypercube centered around the test observation that
contains, on average, 10% of the training observations. For $$p = 1, 2,$$ and 
$$100$$, what is the length of each side of the hypercube? Comment on your 
answer.

*Note: A hypercube is a generalization of a cube to an arbitrary number of 
dimensions. When $$p = 1$$, a hypercube is simply a line segment, when $$p = 2$$
it is a square, and when $$p = 100$$ it is a 100-dimensional cube.*


<br/>

5) We now examine the differences between LDA and QDA.

A. If the Bayes decision boundary is linear, do we expect LDA or QDA to perform
better on the training set? On the test set? 

B. If the Bayes decision boundary is non-linear, do we expect LDA or QDA to 
perform better on the training set? On the test set?

C. In general, as the sample size n increases, do we expect the test prediction
accuracy of QDA relative to LDA to improve, decline, or be unchanged? Why?

D. True or False: Even if the Bayes decision boundary for a given problem is 
linear, we will probably achieve a superior test error rate using QDA rather 
than LDA because QDA is flexible enough to model a linear decision boundary. 
Justify your answer.

<br/>

6) Suppose we collect data for a group of students in a statistics class with 
variables $$X_1$$ =hours studied, $$X_2$$ =undergrad GPA, and $$Y$$ = receive an
A. We fit a logistic regression and produce estimated coefficient, 
$$\hat{\beta_0} = -6$$, $$\hat{\beta_1} = 0.05$$, $$\hat{\beta_2} = 1$$.

A. Estimate the probability that a student who studies for 40h and has an 
undergrad GPA of 3.5 gets an A in the class.

B. How many hours would the student in part (A) need to study to have a 50% 
chance of getting an A in the class?

<br/>

7) Suppose that we wish to predict whether a given stock will issue a dividend 
this year (“Yes” or “No”) based on $$X$$, last year’s percent profit. We examine
a large number of companies and discover that the mean value of $$X$$ for 
companies that issued a dividend was $$\bar{X} = 10$$, while the mean for those 
that didn’t was $$\bar{X} = 0$$. In addition, the variance of $$X$$ for these 
two sets of companies was $$\hat{\sigma}^2 = 36$$. Finally, 80% of companies 
issued dividends. Assuming that $$X$$ follows a normal distribution, predict the
probability that a company will issue a dividend this year given that its 
percentage profit was $$X = 4$$ last year.

*Hint: Recall that the density function for a normal random variable is
$$f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-(x - \mu)^2 / 2 \sigma^2}$$. You
will need to use Bayes' Theorem.*

<br/>

8) Suppose that we take a data set, divide it into equally-sized training and 
test sets, and then try out two different classification procedures. First we 
use logistic regression and get an error rate of 20% on the training data and 
30% on the test data. Next we use 1-nearest neighbors (i.e. $$K = 1$$) and get 
an average error rate (averaged over both test and training data sets) of 18%. 
Based on these results, which method should we prefer to use for classification 
of new observations? Why?

<br/>

9) This problem has to do with odds.

A. On average, what fraction of people with an odds of 0.37 of defaulting on 
their credit card payment will in fact default?

B. Suppose that an individual has a 16% chance of defaulting on her credit card
payment. What are the odds that she will default?