2025-10-23 20:47

#Computer-Vision 

![[Inversed vs Non-inversed Camera Model|600]]
![[Camera Model.png]]
Camera's intrinsic parameters:
- $k_{u}$ and $k_{v}$ are focal length in pixel (pixel/m) along the $u$ and $v$ axes.
- $(u_{o},v_{o})$ is pixel coordinates of $O'$.
Mathematical parameters:
- $R_{e}\text{: Screen coordinate space}$
- $R_{c}\text{: Camera coordinate space}$
- $R_{o}\text{: World coordinate space}$
- $T_{c}^e\text{: Internal model (Camera2Screen)}$
- $T_{o}^c\text{: External model (World2Camera)}$
- [[Homogenous Coordinates]]:
	- $\tilde{p}=(u,v,1)\text{: Image point}$
	- $\tilde{P}=(X,Y,Z,1)\text{: Object point}$
Thus the image point is:
$$
\tilde{p}=T_{c}^e T_{o}^c \tilde{P}
$$
Where $T_{c}^e=T_{th}T_{p}$ where:
- $T_{p}$ perspectively projects $\tilde P$ (gives $\tilde P'$) onto the image plane (expressed in $R_{c}$).
- $T_{th}$ transforms $R_{c}$ into $R_{e}$ (rotation + scale + translation).
## $T_{p}$
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
## $T_{th}$
By convention, $R_{c}$ to $R_{e}$ needs a rotation of $\pi$ around the $Y$ (in $R_{c}$) axis.
Thus, to transform $R_{c}$ to $R_{e}$, we have:
$$
\begin{align}
\tilde p=T_{hr}\tilde P'+t=
\begin{bmatrix}
u \\
v \\
s \\
\end{bmatrix}
= &
\underbrace{\begin{bmatrix}
k_{u} & 0 & 0 & 0 \\
0 & k_{v} & 0 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}}_{\text{Scaling}}
\underbrace{
\begin{bmatrix}
-1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
}_{\text{Rotation } \pi \text{ around Y}}
\tilde P'+
\begin{bmatrix}
u_{0} \\
v_{0}
\end{bmatrix} \\
= &
\begin{bmatrix}
-k_{u} & 0 & 0 & u_{0} \\
0 & k_{v} & 0 & v_{0} \\
0 & 0 & 0 & 1
\end{bmatrix}\tilde{P'}
\end{align}
$$
## Internal model $T_{c}^e$
$$
\begin{align}
\tilde{p}=T_{hr}T_{p}\tilde{P}=&
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

If camera is bad, there could be sheering where the angle between the axes is $\theta$:
$$
M_{int}=
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
\end{bmatrix}
$$
## Full model
$$
M=M_{int}M_{ext}
$$