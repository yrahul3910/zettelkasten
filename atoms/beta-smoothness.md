---
title: $\beta-$smoothness
date: 2023-04-19
id: 20230419232933
author: Rahul Yedida
---
#math #concepts

# $\beta-$smoothness

A continuously differentiable function $f$ is said to be $\beta-$smooth if its gradient is $\beta-$Lipschitz, or

$$
\beta \leq \frac{\lVert \nabla f(y) - \nabla f(x) \rVert}{\lVert y - x \rVert}
$$

The $\beta-$smoothness imposes a bound on the curvature of the loss function [(see lecture notes)](smoothness-def.pdf). Generally speaking, smoother loss surfaces are easier to optimize over.