2025-11-09 10:31

#Computer-Vision 

# Analytically
Solving $p_{j}=Hp_{i}$ (from [[Homography]]) analytically, we have:
$$
\left\{
\begin{align}
(h_{31}x_{i}+h_{32}y_{i}+h_{33})x_{j}=h_{11}x_{i}+h_{12}y_{i}+h_{13} \\
(h_{31}x_{i}+h_{32}y_{i}+h_{33})y_{j}=h_{21}x_{i}+h_{22}y_{i}+h_{23}
\end{align}
\right.
$$
Assume $h_{33}=1$, put everything into matrix form $Ax=b$:
$$
\begin{bmatrix}
x_{i} & y_{i} & 1 & 0 & 0 & 0 & -x_{i}x_{j} & -y_{i}x_{j} \\
0 & 0 & 0 & x_{i} & y_{i} & 1 & -x_{i}x_{j} & -y_{i}x_{j}
\end{bmatrix}
\begin{bmatrix}
h_{11} \\
h_{12} \\
h_{13} \\
h_{21} \\
h_{22} \\
h_{23} \\
h_{31} \\
h_{32}
\end{bmatrix}
=\begin{bmatrix}
x_{j} \\
y_{j}
\end{bmatrix}
$$
By using pseudo-inverse, we can find it.
# Direct Linear Transformation
Because $Hp_{1}=p_{2}$, we know $\alpha p_{1} \times p_{2}=0$, assume $h_{1},h_{2},h_{3}$ are lines in $H$, we have:
$$
\begin{align}
Hp_{1}&=\begin{bmatrix}
h_{1}p_{1} \\
h_{2}p_{1} \\
h_{3}p_{1}
\end{bmatrix} \\
\implies p_{2}\times p_{1}&= \begin{bmatrix}
y_{2}h_{3}p_{1}-h_{2}p_{1} \\
h_{1}p_{1}-x_{2}h_{3}p_{1} \\
x_{2}h_{2}p_{1}-y_{2}h_{1}p_{1}
\end{bmatrix} \\
&=\begin{bmatrix}
0 & -p_{1}^T & y_{2}p_{1}^T \\
p_{1}^T & 0 & -x_{2}p_{1}^T \\
-y_{2}p_{1}^T & x_{2}p_{1}^T & 0
\end{bmatrix} \begin{bmatrix}
h_{1}^T \\
h_{2}^T \\
h_{3}^T
\end{bmatrix}=0
\end{align}
$$