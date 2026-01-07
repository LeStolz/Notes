2026-01-07 19:29

#Computer-Vision 

> At edge points, comparing its patch to its neighbors shows dissimilarity in all directions unlike untextured region or edges.

Thus, we need a similarity metric (more similar, closer to 0) based on [[Autocorrelation]] with shift $\mathbf{u}$ and finding its maximum:
$$
E(\mathbf{x,u}) = \int_{\mathbf{y} = \text{ pixels in } \mathbf{x} \text{'s patch}} K_{\rho}(\mathbf{x}-\mathbf{y})(L(\mathbf{y}+\mathbf{u})-L(\mathbf{y}))^2d\mathbf{y}
$$

A different approach:
Using the [[Taylor Expansions]] on L, we get:
$$
E(\mathbf{x,u}) \approx \mathbf{u}^T\underbrace{(K_{\rho} \ast (\nabla L(\nabla L)^T))}_{\text{Structure Tensor}}\mathbf{u}
$$
Instead of $L$, we use apply the [[Image Smoothing Filters|Gaussian]] filter on it for robustness $L_{\sigma}$, we expand it to:
$$
J(\mathbf{x},\rho,\sigma) = K_{\rho} \ast \begin{pmatrix}
L_{\mathbf{x}}^2 & L_{\mathbf{x}}L_{\mathbf{y}} \\
L_{\mathbf{x}}L_{\mathbf{y}} & L_{\mathbf{y}}^2
\end{pmatrix}
$$
The matrix is described by its eigenvectors $\mathbf{d}_{max}=\frac{\nabla L}{|\nabla L|}$ (dominant direction), $\mathbf{d}_{min}=\frac{\nabla^{\perp} L}{|\nabla L|}$ (anti-dominant direction) and eigenvalues $\lambda_{max}=|\nabla L|$, $\lambda_{min}=0$ (directional contrasts) (when $\rho=0$).

As corner is where 2 edges intersection, there is high variant in many directions => $\lambda_{max}$ and $\lambda_{min}$ large.
# Size-variant detectors
Isometry-invariance (because eigenvalues).
Insensitive to affine intensity transforms (because we find maxima).
*But not invariant to scaling*.
## KLT detector
Closer to human's sight, often used for image motion tracking.

For each point $\mathbf{x}\in \Omega$, if its kernel ($D\times D$)'s $\lambda_{min}>t_{\lambda_{min}}$, put it in a list $L$, sort it in decreasing order $L_{sort}$ and scan from top to bottom, for each point $\mathbf{x}$, discard all points after $\mathbf{x}$ in $L_{sort}$ in the $D\times D$ neighborhood of it.

$t_{\lambda_{min}}$ is sensitivity of detector, estimated from histogram of $\lambda_{min}$. $D$ is usually $\in[2,10]$.
## Harris-Förstner detector
Good repeatability under varying rotation and lighting, usually for [[3D Reconstruction]] and image retrieval.

Uses $r=\frac{\lambda_{min}}{\lambda_{max}}$ but avoids computing $\lambda$ explicitly using $\det(J)=\lambda_{min}\lambda_{max}$, $\text{trace}(J)=\lambda_{min}+\lambda_{max}$ which gives the corner metric (large at corners):
$$
R(\mathbf{x})=\det(J)-\alpha\text{trace}^2(J)
$$
For each point $\mathbf{x}\in \Omega$, if $R(\mathbf{x})>t_{R}$, and it's a local maxima, put it in $L$. Filter weak corners in the $\rho$-neighborhood of strong corners similar to KLT.

$\alpha$ is sensitivity.
## Hessian detector
Same principal as above but uses the hessian matrix:
$$
H(\mathbf{x})=\begin{pmatrix}
L^\sigma_{\mathbf{xx}} & L^\sigma_{\mathbf{xy}} \\
L^\sigma_{\mathbf{xy}} & L^\sigma_{\mathbf{xx}}
\end{pmatrix}
$$
Since more similarity means smoother ($\det(H_{\mathbf{x}})$ low) => opposite is corner.
=> Also detect textures => Denser, lower localization accuracy because of higher order derivatives.

Algorithm is same as Harris but with $H(\mathbf{x})>t_{\det}$.
# [[Scale Invariant Feature Transform (SIFT) Detector]]