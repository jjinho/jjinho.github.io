---
layout: post
title: 4.4 Linear Discriminant Analysis
subtitle: ISLR Chapter 4 Outline
---

## 4.4 Linear Discriminant Analysis

We seperately model the distribution of the predictors $$X$$ given $$Y$$ 
($$Pr(X | Y)$$) then use *Baye's Theorem* to obtain estimates for 
$$Pr(Y = k|X = x)$$.

Cases when an alternative to Logistic Regression are better:

* Well-separated classes: parameter estimates in Logistic Regression are
  unstable.
* $$n$$ is small and the distribution of $$X$$ is approximately normal for each
  of the classes.
* \>2 response classes

<br/>

#### Prior Probability

The **prior probability** ($$\pi_k$$) is the probability that an observation
comes from the *kth* class of a qualitative reponse variable $$Y$$, where $$Y$$
has $$K$$ classes ($$K \ge 2$$).

Estimating $$\pi_k$$ is easy as we can take the fraction of $$x$$ that belong to
class $$K$$.

<br/>

#### Density Function of $$X$$

$$f_k(X) \equiv Pr(X = x|Y = k)$$

<br/>

#### Baye's Theorem

$$Pr(Y = k|X = x) = \frac{ \pi_k f_k(x) }{ \sum_{l=1}^K \pi_l f_l(x) }$$

<br/>

#### Posterior Probability

$$p_k(X) = Pr(Y = k|X)$$

$$p_k(x)$$ is the **posterior probability** that an observation $$X = x$$
belongs to the *kth* class. In other words, it is the probability that the
observation belongs to the *kth* class given the value of the predictor. The 
**Baye's Classifier** classifies an observation to the class for which 
$$p_k(x)$$ is the largest, and has the lowest possible error rate for any given
classifier.

Therefore to find $$p_k(x)$$ we need to find a way to estimate $$f_k(X)$$.

<br/>

### 4.4.2 Linear Discriminant Analysis for p = 1 (One Predictor)

#### $$f_k(x)$$ in 1 Dimension

We assume that $$f_k(x)$$ is normal (*Gaussian*)

$$f_k(x) = \frac{1}{\sqrt{2 \pi} \sigma_k} 
           exp \Big( - \frac{1}{2 \sigma_k^2} (x - \mu_k)^2 \Big)$$

<br/>

#### Approximation of the Prior Probability

$$
p_k(x) = \frac{ \pi_k \frac{1}{\sqrt{2\pi}\sigma} 
                exp \Big(-\frac{1}{2\sigma^2}(x - \mu_k)^2 \Big) }
              { \sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi}\sigma}
                exp \Big(-\frac{1}{2\sigma^2} (x - \mu_k)^2 \Big) }  
$$

<br/>

#### Discriminant Function ($$\delta_k(x)$$)

$$\delta_k(x) = x \cdot \frac{\mu_k}{\sigma^2} -
                \frac{\mu_k^2}{2 \sigma^2} + 
                log(\pi_k)$$

<br/>

#### Derivation of $$\delta_k(x)$$

$$\delta_k(x)$$ is proportional to the $$log(p_k(x))$$. In the following
derivation we remove terms that do not depend on $$k$$.

$$
\begin{align}
p_k(x) &\propto \pi_k \frac{1}{\sqrt{2\pi}\sigma} 
                exp \Big(-\frac{1}{2\sigma^2}(x - \mu_k)^2 \Big)\\
log(p_k(x) 
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

#### Example Where $$K = 2$$ and $$\pi_1 = \pi_2$$

We will assign the observation $$x$$ to class 1 if $$\delta_1(x) > \delta_2(x)$$

$$
\begin{align}
\delta_1(x) &> \delta_2(x)  \\
x \cdot \frac{\mu_1}{\sigma^2} - \frac{\mu_1^2}{2\sigma^2}
    &> x \cdot \frac{\mu_2}{\sigma^2} - \frac{\mu_2^2}{2\sigma^2}   \\
x \cdot \Big( \frac{\mu_1 - \mu_2}{\sigma^2} \Big)
    &> \frac{\mu_1^2 + \mu_2^2}{2\sigma^2}  \\
2x \cdot (\mu_1 - \mu_2) &> \mu_1^2 + \mu_2^2
\end{align}
$$

<br/>

#### Example of the Bayes Decision Boundary Where $$K=2$$ and $$\pi_1 = \pi_2$$

$$
\begin{align}
\delta_1(x) &= \delta_2(x)  \\
x \cdot \frac{\mu_1}{\sigma^2} - \frac{\mu_1^2}{2\sigma^2}
    &= x \cdot \frac{\mu_2}{\sigma^2} - \frac{\mu_2^2}{2\sigma^2}   \\
x \cdot \Big( \frac{\mu_1 - \mu_2}{\sigma^2} \Big)
    &= \frac{\mu_1^2 + \mu_2^2}{2\sigma^2}  \\
x &= \frac{\mu_1^2 + \mu_2^2}{2(\mu_1 - \mu_2)} \\
x &= \frac{\mu_1^2 -2\mu_1\mu_2 + \mu_2^2 + 2\mu_1\mu_2 - 2\mu_2^2}
          {2(\mu_1 - \mu_2)} \\
x &= \frac{(\mu_1 - \mu_2)^2 + 2\mu_2 (\mu_1 - \mu_2)}
          {2(\mu_1 - \mu_2)} \\
x &= \frac{(\mu_1 - \mu_2)(\mu_1 - \mu_2 + 2\mu_2)}
          {2(\mu_1 - \mu_2)} \\
x &= \frac{\mu_1 + \mu_2}{2}
\end{align}
$$

<br/>

#### Linear Discriminant Analysis (LDA)

We approximate the Bayes classifier by plugging in estimates for $$\pi_k$$,
$$\mu_k$$, and $$\sigma^2$$.

$$\hat{\mu}_k = \frac{1}{n_k} \sum_{i:y_i=k} x_i$$

$$\hat{\sigma}^2 = \frac{1}{n-k} \sum_{k=1}^K 
                                 \sum_{i:y_i=k} (x_i - \hat{\mu_k})^2$$

$$\hat{\pi}_k = n_k / n$$

$$\hat{\delta}_k = x \cdot \frac{\hat{\mu}_k}{\hat{\sigma}^2} -
                   \frac{\hat{\mu}_k^2}{2\hat{\sigma}^2} + log(\hat{\pi}_k)$$
                   
Note that the "linear" comes from the fact that the discriminant function 
$$\hat{\delta}_k(x)$$ is linear to $$x$$.

<br/>
