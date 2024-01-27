---
title: The Hessian
date: 2023-04-29
id: 20230429234036
author: Rahul Yedida
---
#theoretical-ml #hessian

# The Hessian

The Hessian is the multivariate generalization of the second derivative. Specifically, it is a symmetric[^1] square matrix of the second-order partial derivatives of a function. The Hessian provides curvature bounds on a function. A multivariate quadratic function has the form $\frac{1}{2}x^T H x$ where $H$ is the Hessian. The eigenvalues of the Hessian determine its curvature along its eigenvectors. Consider the eigendecomposition[^2]

$$
H = Q\Lambda Q^T
$$

where $\Lambda$ is an identity matrix with the ones replaced by $\lambda_i$. If we change the basis to $Q$, we can focus on the directions described by $Q = [q_1, q_2, \ldots, q_n]$. Then along the direction $q_i$, the curvature is $\lambda_i$.

[^1]: This is provided by the Schwarz Theorem.
[^2]: This follows from the spectral theorem, and guarantees that $Q$ is orthogonal, i.e., $Q^{-1} = Q^T$.