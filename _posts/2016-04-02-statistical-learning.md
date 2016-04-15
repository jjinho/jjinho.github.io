---
layout: post
title: 2 Statistical Learning
subtitle: ISLR Chapter 2 Outline
---
## Section 2

### Derivation of Reducible and Irreducible Error

$$
\begin{align}
E(Y - \hat{Y})^2 & = E[f(X) + \epsilon - \hat{f}(X)]^2  \\
  & = E[(f(x) + \epsilon - \hat{f}(X)^2)(f(x) + \epsilon - \hat{f}(X)^2)]  \\
  & = E[f(x)^2 + 2\epsilon \cdot f(x) - 2f(x) \cdot \hat{f}(x) + \hat{f}(x)^2 - 
        2\epsilon \cdot \hat{f}(x) + \epsilon^2]  \\
  & = E[(f(x) - \hat{f}(x))^2 + \epsilon^2 + 2\epsilon (f(x) - \hat{f}(x))] \\
  & = E[(f(x) - \hat{f}(x))^2] + E[\epsilon^2] + E[2\epsilon (f(x) - \hat{f}(x))] \\
  & = ((f(x) - \hat{f}(x))^2) + E[\epsilon^2] + E[2\epsilon (f(x) - \hat{f}(x))] \\
  & = ((f(x) - \hat{f}(x))^2) + E[\epsilon^2] \\
  & = \underbrace{[f(X) - \hat{f}(X)]^2}_\text{Reducible Error} + 
      \underbrace{Var(\epsilon)}_\text{Irreducible Error}
\end{align}
$$

<br/>

### Derivation of $$Var(\epsilon)$$

$$
\begin{align}
Var(\epsilon) & = E[(\epsilon - \bar{\epsilon})^2]  \\
  & = E[(\epsilon - \bar{\epsilon}) (\epsilon - \bar{\epsilon})]  \\
  & = E[(\epsilon^2 - 2 \cdot \epsilon \cdot \bar{\epsilon} + \bar{\epsilon}^2]  \\
  & = E[\epsilon^2]
\end{align}
$$
