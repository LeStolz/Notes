2025-10-23 20:47

#Computer-Vision 

![[Inversed vs Non-inversed Camera Model|600]]
![[Camera Model.png]]
Camera's intrinsic parameters:
- $k_{u}$ and $k_{v}$ are focal length in pixel (pixel/m) along the $u$ and $v$ axes.
- $(u_{o},v_{o})$ is pixel coordinates of $O'$.

Mathematical parameters:
- $R_{e}$: Screen coordinate space
- $R_{c}$: Camera coordinate space
- $R_{o}$: World coordinate space
- $T_{c}^e$: [[Camera Models|Internal model]] (Camera2Screen)
- $T_{o}^c$: [[Camera Models|External model]] (World2Camera)
- $\tilde{p}=(u,v,1)$: [[Homogenous Coordinates|Image point]]
- $\tilde{P}=(X,Y,Z,1)$: [[Camera Models|Object point]]

Thus the image point is:
$$
\tilde{p}=T_{c}^e T_{o}^c \tilde{P}
$$