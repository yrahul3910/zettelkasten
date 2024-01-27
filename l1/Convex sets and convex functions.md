---
title: Convex functions
date: 2023-04-29
id: 20230429233105
author: Rahul Yedida
---
#convex-optimization #theoretical-ml

# Convex functions

Let's start by defining what a _convex combination_ is. A convex combination is a constrained version of a linear combination, with the condition that the coefficients are non-negative and sum to 1. It now becomes easier to define a convex set:

**Definition.** _A set $\mathcal{X}$ is convex if the convex combination of any two points in $\mathcal{X}$ is also in $\mathcal{X}$. Formally,_

$$
\forall x, y \in \mathcal{X}, \forall \theta \in [0, 1], z = \theta x + (1-\theta)y \in \mathcal{X}
$$

Intuitively, if you imagine a set by a shape, then for a convex set, the line between any two points in that set does not cross the boundary of that set.

With the above definitions, we can define a _convex function_.

**Definition.** _A function $f$ is said to be convex iff its domain is a convex set and $\forall x, y \in \text{dom}(f), \forall \theta\in [0, 1]$,_

$$
f(\theta x + (1-\theta)y) \leq \theta f(x) + (1-\theta) f(y)
$$

Succinctly, this says that the function's value on a convex combination does not exceed the convex combination of those values. This can be considered the zeroth-order condition. A function is said to be _strictly convex_ if strict inequality holds. For affine functions (whose form is $Ax + b$), the above is an equality, and so affine functions are both convex and concave by definition.

The above inequality is called _Jensen's inequality_.

For convenience, we can also extend the above definition to outside $\text{dom} f$ so that it is defined as infinity outside, called the _extended-value extension_, and denoted by $\tilde{f}$. This allows us to not specify $\forall x, y \in \text{dom} f$. Note that in [@boydConvexOptimization2004], these two notations are used interchangeably when there is no confusion.

We can define some related concepts:
* [[Sublevel sets]]
* [[Epigraph]]

**Lemma** (First-order condition for convexity). _A differentiable function $f$ is convex iff $\text{dom}(f)$ is convex and $\forall x, y \in \text{dom}(f), \forall \theta\in [0, 1]$,_

$$
f(y) \geq f(x) + \nabla f(x)^T (y-x)
$$

For the forward case, we use the fact that $\text{dom}(f)$ is convex. The definition of a convex set yields the result.

Intuitively, the above says that the tangent at any point on a convex function lies below the graph. Alternatively, since the RHS is the first-order Taylor expansion of $f$ near $x$, the equation says that the first-order Taylor expansion of $f$ near $x$ is a global underestimator of $f$. Moreover, given $f(x)$ and $\nabla f(x)$ (local information), one can find an under-approximation to $f(y)$ (i.e., global information). Note also that when $\nabla f(x) = 0$, then $x$ is a global minimum.

Now, we discuss the first and second-order conditions for convexity. First, we need to talk about _positive-semidefiniteness_.

**Definition.** _A matrix $M \in \mathbb{R}^{d\times d}$ is said to be positive-semidefinite if_

$$
\forall x \in \mathbb{R}^d, x^T Mx \geq 0
$$

_This is denoted by $M \succeq 0$._

**Theorem.** _A symmetric matrix $M \in \mathbb{R}^{d \times d}$ is positive semi-definite iff all its eigenvalues are non-negative._

This theorem is rather easy to prove. For the forward case, start with the definition of semi-definiteness above, and then use the definition of eigenvalues. For the backward case, use the eigendecomposition of $M$, and convert it to the summation form.

Finally, we have the second-order condition for convexity.

**Theorem.** _A twice-differentiable function $f$ is convex iff $\text{dom}(f)$ is convex and the Hessian is positive semi-definite, i.e.,_

$$
\nabla^2 f \succeq 0
$$

For the forward case, we use the first-order condition for convexity with $y = x +h$, with which you can show that $f^{\prime\prime} \geq 0$. For the reverse case, use a second-order Taylor expansion. The proof then generalizes this to $\mathbb{R}^{d\times d}$. See [Lecture notes](ift-6085-lecture-2-notes.pdf) for proofs.