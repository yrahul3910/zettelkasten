#convex-optimization

# Convexity-preserving operations

This adds on to [[Convex sets and convex functions]]. The following operations preserve convexity.

* Nonnegative weighted sums
* Composition with an affine mapping, i.e., $f(Ax + b)$
* Pointwise maximum and supremum, i.e., $f(x) = \max\{ f_{1(x),}f_2(x)\}$
	* Note: The above two are pretty important: a lot of other inequalities can be derived by showing they are a pointwise supremum of a family of affine functions.
* Composition: $f = h \circ g$ where $h: \mathbb{R}^{k}\to \mathbb{R}$ and $g: \mathbb{R}^{n}\to \mathbb{R}^k$
	* Scalar composition: $k = 1$ (for an example of a proof, see [@boydConvexOptimization2004], page 85).
		* $f$ is convex if $h$ is convex (so $h^{\prime\prime} \geq 0$), $\tilde{h}$ is nondecreasing (so $f^{\prime}\geq 0$), and $g$ is convex ($g^{\prime\prime} \geq 0$).
		* $f$ is convex is $h$ is convex, $\tilde{h}$ is nonincreasing and $g$ is concave.
		* $f$ is concave is $h$ is concave, $\tilde{h}$ is nondecreasing, and $g$ is concave.
		* $f$ is concave is $h$ is concave, $\tilde{h}$ is nonincreasing, and $g$ is convex.
	* Vector composition: $k \geq 1$: it turns out the rules are similar:
		* $f$ is convex if $h$ is convex, $h$ is nondecreasing in each argument, and $g$ is convex.
		* $f$ is convex if $h$ is convex, $h$ is nonincreasing in each argument, and $g$ is concave.
		* $f$ is concave if $h$ is concave, $h$ is nondecreasing in each argument, and $g$ is concave.
* Perspective of a function: $g(x, t) = tf(x/t)$
* Conjugate of a function: $f^{*}(y) = \sup\limits_{x \in \textbf{dom} f} \left( y^{T}x - f(x)\right)$
	* See also: [[Properties of conjugates of convex functions]]