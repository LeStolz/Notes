2025-11-09 08:31

#Computer-Vision 

> A homography $H$ is a linear transformation between 2 projective planes.

Thus, can be expressed as the projection (Thus we use [[Homogenous Coordinates]]) of all points $p_{i}$ in plane $\pi_{i}$ onto points $p_{j}$ in plane $\pi_{j}$ using a transformation matrix:
$$
p_{j}=H_{3\times3}p_{i}
$$
Properties:
- Because $kp_{j}=p_{j}$ (property of [[Homogenous Coordinates]]), $H \equiv kH$, thus, we can lose a DOF => Only 8; choose $H_{3,3}\neq0$.
- $H$ must be invertible (because one plane to another, not to a line or point).
- If we have $H_{01}:\pi_{0}\to \pi_{1}$ and $H_{12}:\pi_{1}\to \pi_{2}$, we can find $H_{02}=H_{01}H_{12}$.

![[Homography.png]]
Assume: 
- A point $P$ in $R^3$ in plane $\pi$ with bases $\vec{s}$ and $\vec{t}$, 
- 2 camera poses $C_{1}$, $C_{2}$, 
- $P$ expressed in these bases are $P_{1}$ and $P_2$,
- Its points on the 2 image planes are $p_1$, $p_{2}$,
- $H_{12}$ transforms from image plane 1 to 2,
- $P\in \text{plane } \pi:(a,b,c,d)^T=(\vec{\mathbf{n}}^T,d)^T \text{ expressed in } C_{1}$.
- Thus, $\vec{\mathbf{n}}^T \cdot P_{1}+d=0 \iff -\frac{1}{d}\vec{\mathbf{n}}^T \cdot P_{1}=1$.
- The transformation from $P_{1}$ to $P_{2}$ is done by some rotation $R$ and translation $T$.
$$
\begin{align}
P_{2}&=R \cdot P_{1}+T \\
\iff P_{2}&=R \cdot P_{1}+T \cdot -\frac{1}{d}\vec{\mathbf{n}}^T \cdot P_{1} \\
\iff P_{2}&=\underbrace{{(R -\frac{1}{d}\vec{\mathbf{n}}^T \cdot T)}}_{H_{12}} \cdot P_{1} \\
\iff \alpha_{2} p_{2}&=H_{12} \cdot \alpha_{1}p_{1} \\
\iff p_{2}&=H_{12} \cdot \alpha p_{1}
\end{align}
$$
Thus, $H_{12}$ represent the *transformation of projections* according to the change to the camera pose. There are 4 possible solutions to the equation. Every pair of corresponding points gives 2 equations => 4 pairs needed for 8 equations.
# [[Finding the Homography Matrix]]

# Homography and Cameras
Point $P$ expressed as $(s,t)$ in plane $\pi$ in scene to base $R_{o}$:
$$
\begin{bmatrix}
x \\
y \\
z \\
1
\end{bmatrix}=\underbrace{\begin{bmatrix}
a_{x} & b_{x} & x_{0} \\
a_{y} & b_{y} & y_{0} \\
a_{z} & b_{z} & z_{0} \\
0 & 0 & 1
\end{bmatrix}}_{T} \begin{bmatrix}
s \\
t \\
1
\end{bmatrix}
$$
From $R_{o}$ to $R_{e}$, we use the [[Camera Models|global camera model]]:
$$
\tilde{P}=\underbrace{MT}_{H} \cdot P
$$
Thus $H$ is from world plane to screen plane.

Assume 2 cameras *at the same location*, we have:
$$
\begin{align}
\begin{bmatrix}
wx_{2} \\
wy_{2} \\
w
\end{bmatrix}&=H_{2} \begin{bmatrix}
s \\
t \\
1
\end{bmatrix} \\
&=H_{2}H_{1}^{-1}\begin{bmatrix}
wx_{1} \\
wy_{1} \\
w
\end{bmatrix}
\end{align}
$$
We also have, from [[Finding the Homography Matrix]]:
$$
\begin{align} \\
H_{2}^{-1}
\begin{bmatrix}
wx_{2} \\
wy_{2} \\
w
\end{bmatrix}&=H_{1}^{-1}
\begin{bmatrix}
wx_{1} \\
wy_{1} \\
w
\end{bmatrix} \\
\iff (KR_{2})^{-1}
\begin{bmatrix}
wx_{2} \\
wy_{2} \\
w
\end{bmatrix}&=(KR_{1})^{-1}
\begin{bmatrix}
wx_{1} \\
wy_{1} \\
w
\end{bmatrix} \\
\iff
\begin{bmatrix}
wx_{2} \\
wy_{2} \\
w
\end{bmatrix}&=(KR_{2})(KR_{1})^{-1}
\begin{bmatrix}
wx_{1} \\
wy_{1} \\
w
\end{bmatrix} \\
&=KR_{2}R_{1}^{-1}K^{-1}
\begin{bmatrix}
wx_{1} \\
wy_{1} \\
w
\end{bmatrix}
\end{align}
$$