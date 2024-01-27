---
title: Subgradients
date: 2023-04-29
id: 20230430003359
author: Rahul Yedida
---
#theoretical-ml #convex-optimization

# Subgradients

A subgradient is a vector that generalizes the concept of a derivative to functions that are not necessarily differentiable. Specifically, given a function $f$ defined on a convex set, a subgradient $g$ of $f$ at a point $x_0$ is a vector that satisfies the following inequality:

$$
f(x) >= f(x_0) + g^T (x-x_0)
$$
