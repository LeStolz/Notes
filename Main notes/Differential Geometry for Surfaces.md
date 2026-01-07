2025-10-28 22:22

#Calculus 

> A 3D extension of [[Differential Geometry for Curves]].

We define $S={\textbf{x}(u_{1},u_{2})\ |\ (u_{1},u_{2})\in \Lambda}$ is the surface to analyze. Defined same as in [[Differential Geometry for Curves]]. $\mathcal{T}_{\textbf{x}}$ is the local tangent plane with trivial director vectors $\textbf{x}_{u_{1}}$ and $\textbf{x}_{u_{2}}$, and unit normal vector $\textbf{n}$. There are infinite [[Differential Geometry for Curves|Frenet]] frames.

The velocity $v$ is $\sqrt{ \textbf{x}_{u}.\textbf{x}_{u} }$.

The $|d\textbf{x}|$ can be derived from:
$$
\begin{align}
d\textbf{x}&=\textbf{x}_{u_{1}}du_{1}+\textbf{x}_{u_{2}}du_{2} \\
\iff d\textbf{x}.d\textbf{x}&=(\textbf{x}_{u_{1}}du_{1}+\textbf{x}_{u_{2}}du_{2}).(\textbf{x}_{u_{1}}du_{1}+\textbf{x}_{u_{2}}du_{2}) \\
\iff |d\textbf{x}|^2&=((x_{u_{1}},y_{u_{1}})du_{1}+(x_{u_{2}},y_{u_{2}})du_{2}).((x_{u_{1}},y_{u_{1}})+(x_{u_{2}},y_{u_{2}})du_{2}) \\
&=((du_{1}x_{u_{1}},du_{1}y_{u_{1}})+(du_{2}x_{u_{2}},du_{2}y_{u_{2}})).((du_{1}x_{u_{1}},du_{1}y_{u_{1}})+(du_{2}x_{u_{2}},du_{2}y_{u_{2}})) \\
&=(du_{1}x_{u_{1}}+du_{2}x_{u_{2}},du_{1}y_{u_{1}}+du_{2}y_{u_{2}}).(du_{1}x_{u_{1}}+du_{2}x_{u_{2}},du_{1}y_{u_{1}}+du_{2}y_{u_{2}}) \\
&=(du_{1}x_{u_{1}}+du_{2}x_{u_{2}})^2+(du_{1}y_{u_{1}}+du_{2}y_{u_{2}})^2 \\
&=du_{1}^2x_{u_{1}}^2 + 2du_{1}x_{u_{1}}du_{2}x_{u_{2}} + du_{2}^2x_{u_{2}}^2 + du_{1}^2y_{u_{1}}^2 + 2du_{1}y_{u_{1}}du_{2}y_{u_{2}} + du_{2}^2y_{u_{2}}^2 \\
&=du_{1}^2(\textbf{x}_{u_{1}}.\textbf{x}_{u_{1}}) + du_{2}^2(\textbf{x}_{u_{2}}.\textbf{x}_{u_{2}}) + 2du_{1}du_{2}(\textbf{x}_{u_{1}}.\textbf{x}_{u_{2}}) \\
&=
\begin{bmatrix}
du_{1} & du_{2}
\end{bmatrix}
\underbrace{\begin{bmatrix}
\textbf{x}_{u_{1}}.\textbf{x}_{u_{1}} & \textbf{x}_{u_{1}}.\textbf{x}_{u_{2}} \\
\textbf{x}_{u_{1}}.\textbf{x}_{u_{2}} & \textbf{x}_{u_{2}}.\textbf{x}_{u_{2}}
\end{bmatrix}}_{M}
\begin{bmatrix}
du_{1} \\
du_{2}
\end{bmatrix}
\end{align}
$$
The parameterization is admissible (all points are unique, points always move) iff $\det(M)\neq 0$. Note that $\det(M) = | \textbf{x}_{u_{1}} \times \textbf{x}_{u_{2}} |^2$, thus:
$$g=\sqrt{ \det(M) }$$
represents the elementary area change (metric). The parameterization $(s_{1},s_{2})$ such that $M=\mathcal{I}d$ and normalizes $g$ is called the *normal Euclidean parameterization*.

The unit normal vector $\textbf{n}$ is represented as:
$$\textbf{n}=\frac{1}{g}\textbf{x}_{u_{1}} \times \textbf{x}_{u_{2}}$$

Similar to the [[Differential Geometry for Curves|curve]] case, the curvature $\kappa$ is:
$$\kappa=\frac{1}{v^2}\textbf{x}_{uu}.\textbf{n}$$