---
title: $\alpha-$sublevel sets
date: 2023-05-01
id: 20230502003042
author: Rahul Yedida
---
#convex-optimization

# $\alpha-$sublevel Sets

The $\alpha-$sublevel set of a function $f$ is given by

$$
C_\alpha = \{x \in \text{dom} f | f(x) \leq \alpha \}
$$

Sublevel sets of a convex function are always convex (for proof, see [@boydConvexOptimization2004] Page 75), but the converse is not true (for example, $f(x) = -e^x$ is not convex, but all its sublevel sets are). 