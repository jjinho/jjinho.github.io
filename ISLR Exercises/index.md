---
layout: page
title: ISLR
subtitle: Exercises
---

## Chapter 3

#### Conceptual

1. Describe the null hypotheses to which the p-values given in Table 3.4 
correspond. Explain what conclusions you can draw based on these p-values. Your 
explanation should be phrased in terms of sales, TV, radio, and newspaper, 
rather than in terms of the coefficients of the linear model.

    *Null Hypothesis for TV: TV advertisements have no relationship to sales*
    
    *The p-value of <0.0001 means that we reject the null hypothesis because 
    there is <0.01% probability of the null hypothesis being true, therefore TV
    advertisements are related to sales.*
    
    *Null Hypothesis for Radio: Radio advertisements have no relationship to sales*

    *The p-value of <0.0001 means that we reject the null hypothesis because
    there is a <0.01% probability of the null hypothesis being true, therefore
    radio advertisements are related to sales.*

    *Null Hypothesis for Newspaper: Newspaper advertisements have no relationship to sales*

    *The p-value of 0.8599 means that we accept the null hypothesis , therefore
    newspaper advertisements are not likely to be related to sales.*
    

2. Carefully explain the differences between the KNN classifier and KNN
regression methods.
    
    *The KNN classifier is a qualitative method that for a given point in space
    looks at the k-closest neighbors and whichever class has the majority, will
    classify that point as belonging to the majority. The KNN regression method
    is a quantitative method that for a given predictor $$x_i$$ looks at the 
    k-closest neighbors and takes the average value to generate $$\hat{y_i}$$.*

3. Suppose we have a data set with five predictors, $$X_1$$ = GPA, $$X_2$$ = IQ,
$$X_3$$ = Gender (1 for Female and 0 for Male), $$X_4$$ = Interaction between
GPA and IQ, and $$X_5$$ = Interaction between GPA and Gender. The
response is starting salary after graduation (in thousands of dollars).
Suppose we use least squares to fit the model, and get $$\hat{\beta_0}$$ = 50, 
$$\hat{\beta_1}$$ = 20, $$\hat{\beta_2}$$ = 0.07, $$\hat{\beta_3}$$ = 35, 
$$\hat{\beta_4}$$ = 0.01, $$\hat{\beta_5}$$ = −10.

    1. Which answer is correct, and why?
    
        1. For a fixed value of IQ and GPA, males earn more on average than females.
    
        2. For a fixed value of IQ and GPA, females earn more on average than males.
        
        3. For a fixed value of IQ and GPA, males earn more on average than females 
           provided that the GPA is high enough.
        
            *True provided that the GPA of the female is >3.5*
        
        4. For a fixed value of IQ and GPA, females earn more on average than males 
           provided that the GPA is high enough.
    
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
        
    2. Predict the salary of a female with IQ of 110 and a GPA of 4.0.
    
        $$
        \begin{align}
        Salary_F &= 50 + 20 X_1 + 0.07 X_2 + 35 + 0.01 (X_1 X_2) - 10 X_1   \\
            &= 50 + 20 (4.0) + 0.07 (110) + 35 + 0.01 (110 \cdot 4.0) - 10 (4.0)    \\
            &= 137.1 (k)
        \end{align}
        $$
    
    3. True or false: Since the coefficient for the GPA/IQ interaction
       term is very small, there is very little evidence of an interaction
       effect. Justify your answer.
       
        *This statement is false. The coefficient alone does not tell us whether
        we can accept the null hypothesis. We need the standard error of the
        coefficient to give us the t-statistic and therefore the p-value which
        will let us decide whether or not to accept the null hypothesis.*

4. I collect a set of data (n = 100 observations) containing a single
predictor and a quantitative response. I then fit a linear regression
model to the data, as well as a separate cubic regression, i.e. $$Y =
\beta_0 + \beta_1 X + \beta_2 X^2 + \beta_3 X^3 + \epsilon$$.

    1. Suppose that the true relationship between $$X$$ and $$Y$$ is linear,
    i.e. $$Y = \beta_0 + \beta_1 X + \epsilon$$. Consider the training residual 
    sum of squares (RSS) for the linear regression, and also the training
    RSS for the cubic regression. Would we expect one to be lower
    than the other, would we expect them to be the same, or is there
    not enough information to tell? Justify your answer.
   
    *Since the cubic regression will fit the training data better, we would
    expect the RSS to be lower compared to the linear regression model.*
    
    2. Answer (1) using test rather than training RSS.
    
    *However since the cubic regression overfits the training data, once fitted
    onto test data, we would expect the RSS to be higher compared to the linear
    regression model.*
    
    3. Suppose that the true relationship between $$X$$ and $$Y$$ is not linear,
    but we don’t know how far it is from linear. Consider the training
    RSS for the linear regression, and also the training RSS for the
    cubic regression. Would we expect one to be lower than the
    other, would we expect them to be the same, or is there not
    enough information to tell? Justify your answer.
    
    *We would still expect the cubic model to fit the training data better and
    therefore to have a lower RSS.*
    
    4. Answer (3) using test rather than training RSS.
    
    *We do not have enough information to answer the question since we do not
    know "how far it is from linear." The linear regression model may do better
    to a "more linear" model while the cubic regression model may do better with
    a more non-linear model.*

5. Consider the fitted values that result from performing linear regression
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

6. Using (3.4), argue that in the case of simple linear regression, the
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

7. It is claimed in the text that in the case of simple linear regression
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