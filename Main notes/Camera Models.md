2025-10-25 16:58

#Computer-Vision 

> From [[Camera Model Parameters]], we know that $\tilde{p}=T_{c}^e T_{o}^c \tilde{P}$, now we calculate it.

# Perspective Camera Model
## Internal model $T_{c}^e$
$T_{c}^e=T_{th}T_{p}$ where:
- $T_{p}$ perspectively projects $\tilde P$ (gives $\tilde P'$) onto the image plane (expressed in $R_{c}$).
- $T_{th}$ transforms $R_{c}$ into $R_{e}$ (rotation + scale + translation).

Using similar triangles, we have:
- $\frac{X}{Z}=\frac{X'}{F}\implies X'=\frac{fX}{Z}$
- $\frac{Y}{Z}=\frac{Y'}{F}\implies Y'=\frac{fY}{Z}$
- $Z'=f$
We can represent this in matrix form:
$$
\tilde P'=
\begin{bmatrix}
sX' \\
sY' \\
sZ' \\
s
\end{bmatrix}=
\underbrace{\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & \frac{1}{f} & 0
\end{bmatrix}}_{T_{p}}
\dot{}
\begin{bmatrix}
X \\
Y \\
Z \\
1
\end{bmatrix}
$$

By convention, transforming $R_{c}$ to $R_{e}$ needs a rotation of $\pi$ around the $Y$ (in $R_{c}$) axis (done by using the following $T_{th}$ matrix).
Thus, the full *internal model* is:
$$
\begin{align}
\tilde p=T_{th}T_{p}\tilde P=
\begin{bmatrix}
u \\
v \\
s \\
\end{bmatrix}
= &
\underbrace{\begin{bmatrix}
k_{u} & 0 & 0 & u_{0} \\
0 & k_{v} & 0 & v_{0} \\
0 & 0 & 0 & 1
\end{bmatrix}}_{\text{Scaling \& Translating}}
\underbrace{
\begin{bmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
}_{\text{Rotating by } \pi \text{ around Y}}
T_{p}\tilde P \\
= &
\begin{bmatrix}
-k_{u} & 0 & 0 & u_{0} \\
0 & k_{v} & 0 & v_{0} \\
0 & 0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & \frac{1}{f} & 0
\end{bmatrix}
\tilde{P} \\
= &
\begin{bmatrix}
-k_{u} & 0 & \frac{u_{0}}{f} & 0 \\
0 & k_{v} & \frac{v_{0}}{f} & 0 \\
0 & 0 & \frac{1}{f} & 0
\end{bmatrix}
\tilde{P} \\
= &
\begin{bmatrix}
\alpha_{u} & 0 & u_{0} & 0 \\
0 & \alpha_{v} & v_{0} & 0 \\
0 & 0 & 1 & 0 \\
\end{bmatrix}
\tilde{P}
\end{align}
$$
Where $\alpha_{u}=-k_{u}f$ and $\alpha_{v}=k_{v}f$.
*Thus*,
$$u=\frac{\alpha_{u}X}{Z}+u_{0}$$
$$v=\frac{\alpha_{v}Y}{Z}+v_{0}$$
If camera is bad, there could be shearing where the angle between the axes is $\theta$:
$$
T_{c}^e=
\begin{bmatrix}
\alpha_{u} & \gamma & u_{0} & 0 \\
0 & \alpha_{v} & v_{0} & 0 \\
0 & 0 & 1 & 0
\end{bmatrix}
$$
Where $\alpha_{u}=-k_{u}f$ and $\alpha_{v}=k_{v}\sin \theta f$ and $\gamma=-k_{u}\cos \theta$.
## External model $T_{o}^c$
The external model (or camera pose) represents rotation and translation from $R_{o}$ to $R_{c}$:
$$
T_{o}^c=
\begin{bmatrix}
r_{11} & r_{12} & r_{13} & t_{x} \\
r_{21} & r_{22} & r_{23} & t_{y} \\
r_{31} & r_{32} & r_{33} & t_{z} \\ 
0 & 0 & 0 & 1
\end{bmatrix}=
\begin{bmatrix}
r_{1} & t_{x} \\
r_{2} & t_{y} \\
r_{3} & t_{z} \\ 
O_{1\times3} & 1 \\
\end{bmatrix}
$$
## Full model
$$
M=M_{int}M_{ext}=T_{c}^eT_{o}^c
$$
# [[Affine Camera Models]]