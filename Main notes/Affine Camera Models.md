2025-10-25 13:09

#Computer-Vision 

> [[Camera Models]] is general but complex (10 DOF), thus we approximate it: If the depth variances of the points is small compared to their average depth to the camera, we can approximate that they all have the same depth.

![[Affine Camera Models.png]]

In calibration problems, camera's intrinsic parameters are assumed known, so we assume: $\alpha_{u}=\alpha_{v}=1$ and $u_{0}=v_{0}=0$.
[[Camera Models|Recall that]] the image point $(su,sv,s)$ of object point $(X,Y,Z,1)$ is:
$$
\begin{align}
\begin{bmatrix}
su \\
sv \\
s
\end{bmatrix}
=&
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
\end{bmatrix}
\begin{bmatrix}
r_{1} & t_{x} \\
r_{2} & t_{y} \\
r_{3} & t_{z} \\ 
O_{1\times3} & 1 \\
\end{bmatrix}
\begin{bmatrix}
X \\
Y \\
Z \\
1
\end{bmatrix} \\
=&
\begin{bmatrix}
r_{1} & t_{x} \\
r_{2} & t_{y} \\
r_{3} & t_{z} \\
\end{bmatrix}
\begin{bmatrix}
X \\
Y \\
Z \\
1
\end{bmatrix} \\
\begin{bmatrix}
su \\
sv \\
s
\end{bmatrix}
=&
\begin{bmatrix}
r_{1}\tilde{P}^t+t_{x} \\
r_{2}\tilde{P}^t+t_{y} \\
r_{3}\tilde{P}^t+t_{z} \\
\end{bmatrix} \\
\iff
\begin{bmatrix}
u \\
v \\
1
\end{bmatrix}
=&
\begin{bmatrix}
\frac{{r_{1}\tilde{P}^t+t_{x}}}{r_{3}\tilde{P}^t+t_{z}} \\
\frac{{r_{2}\tilde{P}^t+t_{y}}}{r_{3}\tilde{P}^t+t_{z}} \\
1 \\
\end{bmatrix} \\
\end{align}
$$
Dividing the fractions by $t_{z}$ gives:
$$
\left\{
\begin{aligned}
u= \frac{{r_{1}\tilde{P}^t+t_{x}}}{t_{z}} \frac{1}{\xi+1}\\
v= \frac{{r_{2}\tilde{P}^t+t_{y}}}{t_{z}} \frac{1}{\xi+1}\\
\end{aligned}
\right.
$$
Where $\xi={r_{3}\tilde{P}^t/t_{z}}$
As object depth $t_{z} \to \infty, \xi\to 0$:
$$
\left\{
\begin{aligned}
u= \frac{{r_{1}\tilde{P}^t+t_{x}}}{t_{z}}\\
v= \frac{{r_{2}\tilde{P}^t+t_{y}}}{t_{z}}\\
\end{aligned}
\right.
$$
Only *5 DOF* are left. This is the equation for *weak perspective*.
# Weak perspective
Intuitively, we can understand it as:
1. Project all points onto a plane parallel to the image plane and goes through the object's origin. Thus, good when depth is large.
2. Use normal perspective projection on those points.
# Para-perspective
We could approximate this more accurately by approximating $\frac{1}{\xi+1}$ when $\xi$ is near $0$ but not exactly $0$ like weak perspective using the 1st order Taylor expansion:
$$
\frac{1}{\xi+1}\approx 1-\xi
$$
We get:
$$
\left\{
\begin{aligned}
u= \frac{{(r_{1}-t_{x}r_{3}/t_{z})\tilde{P}^t+t_{x}}}{t_{z}}\\
v= \frac{{(r_{2}-t_{y}r_{3}/t_{z})\tilde{P}^t+t_{y}}}{t_{z}}\\
\end{aligned}
\right.
$$
Still *6 DOF* but transformation is affine (no variable projection).

Intuitively:
1. Project all points onto a plane parallel to the image plane and go through the object's coordinate system. *But* projection is parallel to the line going from the camera's origin ($O_{c}$) to the object's origin $(O_{m})$ (Thus, more aligned with where the points will be). Thus good for when dimensions of object is small.
2. Use normal perspective projection on those points.