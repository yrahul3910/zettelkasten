#convex-optimization #concepts

# Quasiconvex functions

A function $f: \mathbb{R}^{n}\to \mathbb{R}$ is said to be *quasiconvex* (or *unimodal*) if its domain and all its sublevel sets (see [[Sublevel sets]]) are convex.

For a function on $\mathbb{R}$, quasiconvexity requires that each sublevel set be an interval, possibly infinite.

Convex functions have convex sublevel sets, and are therefore also quasiconvex.

## Examples

- $\log x$ on $\mathbb{R}_{++}$ is quasiconvex. It is also quasiconcave, and is therefore *quasilinear*.
- $\lceil x \rceil$ is also both quasiconvex and quasiconcave.
- The function $f: \mathbb{R}_{+}^{2}\to \mathbb{R}_{+}$ given by $f(x_{1}, x_{2}) = x_{1}x_{2}$ is quasiconcave, since the superlevel sets given by $\{ x \in \mathbb{R}_{+}^{2} | x_{1}x_{2} \geq \alpha \}$ are convex for all $\alpha$ (see proof below). However, this function is neither convex nor concave, since its Hessian $\nabla^{2}f = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$ is indefinite.
	- *Proof:* Suppose $x_A = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$ and $x_B = \begin{bmatrix} x_3 \\ x_4 \end{bmatrix}$ in $\textbf{dom } f$. Then $x_1 x_2 \geq \alpha$ and $x_3 x_4 \geq \alpha$. We have, $\theta x_A + (1-\theta) x_B = \begin{bmatrix} \theta x_{1}+ (1-\theta)x_{3}\\ \theta x_{2}+ (1-\theta)x_{4} \end{bmatrix}$ and we need to show this is also in domain of f. The product of its two elements is $\theta^{2}x_{1}x_{2}+ \theta(1-\theta) x_{1}x_{4}+ \theta(1-\theta)x_{2}x_{3}+ (1-\theta)^{2}x_{3}x_4$. Trivially, $x_1x_{2} \geq \alpha$ and $x_{3}x_{4}\geq \alpha$.
	
	- Now, we have $x_{1} \geq \alpha/x_{2}$ and $x_{4}\geq \alpha/x_3$. Then $x_1x_{4}+ x_2x_{3}\geq \frac{\alpha^{2}}{x_2x_{3}} + x_2x_{3}\geq 2\alpha$, where the last step follows from the AM-GM inequality.

## Basic properties

Quasiconvexity is a generalization of convexity. Moreover, there is also a version of Jensen's inequality for quasiconvex functions. Specifically, a function is said to be quasiconvex iff its domain is convex and for any $x, y \in \textbf{dom } f$ and $\theta \in [0, 1]$, we have

$$
f(\theta x + (1-\theta)y) \leq \max \{f(x), f(y) \}
$$

Intuitively, this says that the value of the function on a segment does not exceed the value at either of its endpoints.

## Conditions for quasiconvexity

### First-order condition

Suppose $f: \mathbb{R}^n \to \mathbb{R}$ is differentiable. Then $f$ is quasiconvex iff $\textbf{dom } f$ is convex and $\forall x, y \in \textbf{dom } f$,

$$
	f(y) \leq f(x) \Rightarrow \nabla f(x)^T (y-x) \leq 0
$$

There is an important difference from the condition for convexity: if $f$ is convex and $\nabla f(x) = 0$, then $x$ is a global minimizer of $f$. However, this is not true for quasiconvex functions: it is possible that $\nabla f(x) = 0$ but $x$ is not a global minimizer of $f$.

### Second-order conditions

Suppose $f$ is twice-differentiable. If $f$ is quasiconvex, then for all $x \in \textbf{dom } f$, and for all $y \in \mathbb{R}^n$, we have

$$
	y^T \nabla f(x) = 0 \Rightarrow y^T \nabla^2 f(x) y \geq 0
$$

For a quasiconvex function on $\mathbb{R}$, this reduces to the simpler condition:

$$
	f^\prime(x) = 0 \Rightarrow f^{\prime\prime}(x) \geq 0
$$

As a partial converse, if $f$ satisfies the above condition but with a strict inequality, then $f$ is quasiconvex.

## Operations that preserve quasiconvexity

### Non-negative weighted maximum

A function of the form $f = \max\{w_1 f_1, \ldots w_n f_n\}$ with $w_i \geq 0$ and $f_i$ quasiconvex, is also quasiconvex.

### Composition

If $g: \mathbb{R}^n \to \mathbb{R}$ is quasiconvex and $h: \mathbb{R} \to \mathbb{R}$ is nondecreasing, then the function $f = h \circ g$ is quasiconvex. The composition of a quasiconvex function with an affine function or linear-fractional function also yields a quasiconvex function. Specifically, if $f$ is quasiconvex, then $f(Ax + b)$ is quasiconvex, and $f((Ax + b) / (Cx + d))$ is quasiconvex on the set

$$
	x: c^T x + d > 0, (Ax + b) / (Cx + d) \in \textbf{dom } f
$$

### Minimization

If $f(x, y)$ is jointly quasiconvex in $x$ and $y$, and $C$ is a convex set, then the function $\inf\limits_{y \in C} f(x, y)$ is also quasiconvex.