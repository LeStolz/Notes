2025-10-25 12:55

#3D-Graphics #Linear-Algebra 

> To express a point expressed in the A coordinate system in the B coordinate system, we just need to left-multiply it with the matrix that transforms A to B (how to move B to A in B's system).

# Translation
$$
\begin{bmatrix}
1 & 0 & 0 & d_{x} \\
0 & 1 & 0 & d_{y} \\
0 & 0 & 1 & d_{z} \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
# Scaling
$$\begin{bmatrix}
s_{x} & 0 & 0 & 0 \\
0 & s_{y} & 0 & 0 \\
0 & 0 & s_{z} & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$
# Rotation
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos(\theta_{x}) & -\sin(\theta_{x}) & 0 \\
0 & \sin(\theta_{x}) & \cos(\theta_{x}) & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
$$
\begin{bmatrix}
\cos(\theta_{y}) & 0 & \sin(\theta_{y}) & 0 \\
0 & 1 & 0 & 0 \\
-\sin(\theta_{y}) & 0 & \cos(\theta_{y}) & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
$$
\begin{bmatrix}
\cos(\theta_{z}) & -\sin(\theta_{z}) & 0 & 0 \\
\sin(\theta_{z}) & \cos(\theta_{z}) & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
# Sheering
$$
\begin{bmatrix}
1 & 0 & sh_{x} & 0 \\
0 & 1 & sh_{y} & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
# Perspective Projection
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & \frac{1}{d} & 0
\end{bmatrix}
$$
# Orthographic Projection
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$