2025-10-28 08:26

#Calculus

![[Geometry of a Curve]]

# Definition
At a point $\textbf{x}$ at time $u$ along a parameterized curve $C$, we can find its unit tangent $\textbf{t}$ and unit normal $\textbf{n}$. $[\textbf{t},\textbf{n}]$ defines a local coordinate system called *Frenet*. We represent $C$ as:
$$C=\left\{\textbf{x}(u)\ |\ u\in \Lambda\subseteq R\right\}$$
Where each $u$ corresponds to a unique point $\textbf{x}=[x(u),y(u)]^T\in C$, where:
- $\textbf{x}_{u}$ is tangent to $C$.
- $|\textbf{x}_{u}|=\sqrt{ x_{u}^2+y_{u}^2 }$ is the velocity (metric) near $\textbf{x}$, also denoted $v$. Thus, $\textbf{x}_{u}=v\textbf{t}$. By definition, $v\neq 0$ so that all points are unique (the points always move).
## Parameterization
Out of all *parameterization, a special one* is denoted $s$ which normalizes the velocity:
$$|\textbf{x}_{s}|=1$$
In which case, $\textbf{x}_{s}=t$ and $\textbf{x}_{u}=v\textbf{x}_{s}$. More importantly, since its norm is 1, $s$ measures the *arc length*. We can see this by taking the differential of both sides of $\textbf{x}_{u}=v\textbf{x}_{s}$:
$$ds=vdu\quad \text{or more cooly}\quad s=vt$$
## Curvature
Define $\theta$ as the angle between $\textbf{t}$ and $\hat{i}$, to determine *the curvature* of a curve, we use:
$$\frac{d\theta}{ds}=\frac{d\theta}{du} \frac{1}{v}=\kappa\quad\quad\frac{1}{\kappa} \text{ is called the radius of curvature}$$
Thus, we also have:
$$
\begin{align}
\frac{d\textbf{t}}{ds}&=\frac{d\textbf{t}}{d\theta}\frac{d\theta}{ds} \\
&=\frac{d(\cos \theta,\sin \theta)}{d\theta}\kappa \\
&=(-\sin \theta,\cos \theta)\kappa \\
&=\kappa\textbf{n}
\end{align}
$$
Also easily derived:
$$
\frac{d\textbf{n}}{ds}=-\kappa \textbf{t}
$$
Derive $\textbf{x}_{u}=v\textbf{t}$ with respect to $u$, we get:
$$
\begin{align}
\textbf{x}_{uu}&=v_{u}\textbf{t} + v\frac{d\textbf{t}}{du} \\
&=v_{u}\textbf{t} + v\frac{d\textbf{t}}{ds}\frac{ds}{du} \\
&=v_{u}\textbf{t} + v\kappa \textbf{n}v \\
\iff \textbf{n}.\textbf{x}_{uu}&= \textbf{n}.v_{u}\textbf{t} + v\kappa \textbf{n}.\textbf{n}v \\
\iff \textbf{n}.\textbf{x}_{uu}&= v\kappa v \\
\iff \kappa&= \frac{\textbf{n}.\textbf{x}_{uu}}{v^2} \\
\iff \kappa&= \frac{-y_{u}.x_{uu}+x_{u}y_{uu}}{v^3}
\end{align}
$$
## Arc length and area
$$\text{Length}(C)=\int_{\Lambda}ds==\int_{\Lambda}vdu$$
If the curve is closed and the domain it delimits is $D$:
$$\text{Area}(C)=\int \int_{D}dxdy$$