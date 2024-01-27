#convex-optimization #concepts

# Properties of conjugates of convex functions

- **Fenchel's inequality:** By definition of the conjugate, $f(x) + f^{*}(x) \geq x^{T} y$
- **Conjugate of the conjugate:** The conjugate of the conjugate of a function is the original function, provided $f$ is convex and closed (i.e., $\textbf{epi } f$ is a closed set, see [[Epigraph]]). For example, for $\mathbb{R}^n$, $f^{**} = f$.
- **Differentiable functions:** If $f$ is differentiable, then $f^{*}$ is called the *Legendre transform* of $f$.
	- Suppose $f$ is convex and differentiable, and let $\textbf{dom }f = \mathbb{R}^n$. Any maximizer $x^{*}$ of $y^{T}x - f(x)$ satisfies $y = \nabla f(x^{*})$. Therefore, if $y = \nabla f(x^{*})$, then

	$$
		f^{*}(y) = x^{*T}\nabla f(x^{*}) - f(x^{*})
	$$
	
	Expressed another way, let $z \in \mathbb{R}^n$ be arbitrary and let $y = \nabla f(z)$. Then
	
	$$
		f^{*}(y) = z^{T}\nabla f(z) - f(z)
	$$

	This allows us to compute the conjugate of $f$ at a point $y$, if $f(z)$ and $\nabla f(z)$ are known for some $z$.
- **Scaling and composition with affine transform:** For $a > 0, b \in \mathbb{R}$, the conjugate of $g(x) = af(x) + b$ is $g^{*}(y) = af^{*}(y/a)+ b$. If $A \in \mathbb{R}^{n\times n}$ is nonsingular and $b \in \mathbb{R}^n$, the conjugate of $g(x) = f(Ax+b)$ is $g^{*}(y) = f^{*}(A^{-1}y + b) - b^{T}A^{-T} y$ and $\textbf{dom } g = A^{T}\textbf{dom }f$.
- **Sum of independent functions:** If $f(u, v) = f_{1}(u) + f_{2}(v)$, where $f_1$ and $f_2$ are convex, then $f^{*}(w, z) = f_{1}^{*}(w)+ f_{2}^{*}(z)$.