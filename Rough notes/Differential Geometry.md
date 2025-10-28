2025-10-28 08:26

#Calculus

> To describe and measure the local geometry of objects using calculus.

![[Geometry of a Curve]]

At a point $\textbf{x}$ at time $u$ along a parameterized curve $C$, we can find its unit tangent $\textbf{t}$ and unit normal $\textbf{n}$. $[\textbf{t},\textbf{n}]$ defines a local coordinate system *Frenet*. We represent $C$ as:
$$C=\left\{\textbf{x}(u)\ |\ u\in \Lambda\subseteq R\right\}$$
Where each $u$ corresponds to a unique point $\textbf{x}=[x(u),y(u)]^T\in C$.
Thus, the geometry of the curve is described by the derivative of $\textbf{x}$ with respect to $u$:
- $\textbf{x}_{u}$ is tangent to $C$.
- $|\textbf{x}_{u}|=\sqrt{ x_{u}^2+y_{u}^2 }$ is the velocity near $\textbf{x}$, also denoted $v$. Thus, $\textbf{x}_{u}=v\textbf{t}$. By definition, $v\neq 0$ so that all points are unique (the points always move).
Out of all parameterization, a special one is denoted $s$ which normalizes the velocity:
$$|\textbf{x}_{s}|=1$$
In which case, $\textbf{x}_{s}=t$ and $\textbf{x}_{u}=v\textbf{x}_{s}$. More importantly, since its norm is 1, $s$ measures the *arc length*. We can see this by taking the differential of both sides of $\textbf{x}_{u}=v\textbf{x}_{s}$:
$$ds=vdu\quad \text{or more cooly}\quad s=vt$$
