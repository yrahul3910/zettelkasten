---
title: Lipschitz continuity
date: 2023-04-29
id: 20230429232710
author: Rahul Yedida
---

#lipschitz-constant #theoretical-ml

# Lipschitz continuity

**Lipschitz continuity.** _A real-valued function $f$ is $L-$Lipschitz continuous iff $\forall x, y \in \text{dom}(f)$ the following holds:_

$$
|f(x) - f(y)| \leq L \lVert x - y \rVert
$$

_for some non-negative constant $L$._

The notes show that it is pretty easy to prove a first-order condition for Lipschitz continuity:

**Lemma 1.** _A differentiable function $f$ is $L-$Lipschitz continuous iff the norm of its gradient is bounded by $L$._

The proof for the forward case follows from the definition of the derivative for $\mathbb{R}$ and can be generalized to $\mathbb{R}^d$. For the reverse case uses the mean-value theorem and the Cauchy-Schwarz inequality. See [Lecture notes](ift-6085-lecture-2-notes.pdf).