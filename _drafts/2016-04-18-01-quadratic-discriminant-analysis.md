---
layout: post
title: 4.4.4 Quadratic Discriminant Analysis
subtitle: ISLR Chapter 4 Outline
---

### 4.4.4 Quadratic Discriminant Analysis

In LDA we assume that each of the $$K$$ classes is drawn from a multivariate
Gaussian distribution and that the classes share a common covariance matrix
$$\Sigma$$. In otherwords, each class will appear similar to one another in
shape. However although **Quadratic Discriminant Analysis (QDA)** still assumes
that the classes are drawn from a multivariate Gaussian distribution, it now
assumes that each class has its own covariance matrix $$\Sigma_k$$.

In other words, the observation of the *kth* class is of the form 
$$X \sim N(\mu_k, \Sigma_k)$$.

<br/>

#### Discriminant Function ($$\delta_k(x)$$)

$$
\begin{align}
\delta_k(x) &= -\frac{1}{2} (x - \mu_k)^T \Sigma_k^{-1} (x - \mu_k)
               -\frac{1}{2} log |\Sigma| + 
               log(\pi_k) \\
            &= -\frac{1}{2} x^T \Sigma_k^{-1} x + x^T \Sigma_k^{-1} \mu_k
               -\frac{1}{2} \mu_k^T \Sigma_k^{-1} \mu_k
               -\frac{1}{2} log |\Sigma| + 
               log(\pi_k) \\
\end{align}
$$

Note that this discriminant function is quadratic in appearance.

<br/>

#### LDA vs QDA

LDA has higher bias while QDA has higher variance. Situations when LDA will
perform better than QDA:

* Fewer training observations available, therefore it is better to reduce the
  variance
* High number of predictors $$p$$ make it computationally prohibitive to 
  calculate the covariance matrix of each class

Situations when QDA will perform better than LDA:

* Large training set such that the variance of the classifier is not as much a
  concern
* The assumption that each class shares a common covariance matrix $$\Sigma$$ is
  badly off