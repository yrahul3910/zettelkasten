---
title: DL Theory, L2 - Basics of convex analysis and gradient descent
date: 2023-04-29
id: 20230429222317
author: Rahul Yedida
---
 #theoretical-ml #convex-optimization #lipschitz-constant

# Basics of convex analysis and gradient descent

## Background

* [[Convex sets and convex functions]]
* [[Convexity-preserving operations]]

## Introduction

For the full notes, see [Lecture notes](./files/ift-6085-lecture-2-notes.pdf).

In general, the most general unconstrained optimization problem for a real-valued function $f: \mathcal{X} \to \mathbb{R}$ is given by

$$
\inf\limits_{x \in \mathcal{X}} f(x)
$$

Generally speaking, this problem is NP-Hard (cf. [@bubeckConvexOptimizationAlgorithms2015] Section 6.6). However, we study convex functions because the convexity assumption allows us to prove convergence guarantees and efficient optimization algorithms.

## Concepts

We need to discuss two concepts here:
* [[Lipschitz continuity]]
* [[Convex sets and convex functions]]

## Gradient descent

Gradient descent is an iterative optimization algorithm that uses the update rule:

$$
x_{k+1} = x_k - \eta \nabla f(x_k)
$$

where $\eta$ is the learning rate. If $f$ is convex and $\eta$ decays at an appropriate rate, then it is guaranteed that as $T \to \infty$, $x_T \to x^*$.

The following theorem has a rather involved proof:

**Theorem.** _Let $f$ be convex and $L-$Lipschitz continuous. If we take $T$ steps of gradient descent with step size_

$$
\eta = \frac{\lVert x_1 - x^* \rVert_2}{L\sqrt{T}}
$$

_then the following holds:_

$$
f\left(\frac{1}{T} \sum\limits_{k=1}^T x_k \right) - f(x^*) \leq \frac{L\lVert x_1 - x^* \rVert}{\sqrt{T}}
$$

Although the algorithm, theorem, and proof rely on the it, differentiability is not necessary. Any of the subgradients (see [[Subgradients]]) can be used in place of the gradient. The convergence rate here is $\mathcal{O}(1/\sqrt{T})$, which is pretty slow. However, stronger assumptions on $f$ can guarantee faster convergence.