---
layout: page
title: CSE
subtitle: "Exercises from 18.085: Computational Science and Engineering by Professor Gilbert Strang"
---

# Problem Set 1

$$
T_4^{-1} = 
\begin{bmatrix}
4 & 3 & 2 & 1 \\
3 & 3 & 2 & 1 \\
2 & 2 & 2 & 1 \\
1 & 1 & 1 & 1 \\
\end{bmatrix}
$$

1. For every $$n$$, $$S_n = U_n^{-1}$$ is upper triangular with ones on and 
above the diagonal. For every $$n=4$$ check that $$SS^T$$ produces the matrix 
$$T_4^{-1}$$ predicted in Problem 1. Why is $$SS^T$$ certain to be a symmetric
matrix?

<br/>

# Problem Set 2

1. For a fixed-free line of 3 springs and masses (spring constants $$c_1$$, 
$$c_2$$, $$c_3$$) write down $$A$$ and $$C$$ and $$K = A^T CA$$.

2. In this “statically determinate” problem with square matrices $$m = n$$ you 
can do this: Invert $$K$$ by inverting its 3 factors $$A^T, C, A$$.
    
    Show that this $$K^{−1}$$ has all positive entries/all displacements are 
    downward.

3. For one free-free spring sitting between 2 masses, show that the stiffness 
matrix is

    $$
    “element \space matrix \space K” =
    \begin{bmatrix}
    c & −c  \\
    −c & c   \\
    \end{bmatrix}
    $$

    when $$m = 1$$.
    
    Now assemble the three element matrices for Problem 1 into the 3 by 3 matrix 
    $$K$$ for Problem 1.
    
    The first element matrix will only be 1 by 1 because spring 1 is fixed at 
    the top.

4. Suppose spring 2 gets weak and $$c_2$$ goes to zero. What is the limiting 
$$K$$ when $$c_2 \approx 0$$? What are the properties of this limiting $$K$$? With 
$$c_2 = 0$$ and $$c_1 = 1$$ and $$c_3 = 3$$, find the eigenvalues of $$K$$. 
(OK to use `eig(K)` if you want.)

5. Let’s introduce random spring constants and run a number of simulations. 
Choose $$c_1$$ and $$c_2$$ and $$c_3$$ each as `2 + rand(1)` in 100 simulations.

    Then try $$c_1$$, $$c_2$$, $$c_3$$ as `2 + rand(1)/10` 100 times. Find the 
    averages of the matrices $$K^{−1}$$.
    
    Compare with $$c_1 = c_2 = c_3 = 2$$. Any interesting conclusions?
.
