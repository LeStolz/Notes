2025-11-23 09:22

#Computer-Vision 

> Used for [[Image Edge Detection Using the Laplacian]].

Since this is a 2nd order derivative, we calculate it by composing 1st order [[Image Edge Detection Using Finite Difference Filters]].
# 1D
$$
D_{xx}L_{ij}=D_{x}^+(D_{x}^-L_{ij})=\frac{1}{\delta_{x}^2} (L(i+\delta_{x},j) -2L(i,j) +L(i-\delta_{x},j))
$$
with usual choice $\delta_{x}=\delta_{y}=1$ which produces kernel:
$$\begin{bmatrix}
1 & -2 & 1
\end{bmatrix}$$
# 2D
## 4-connected
$$\begin{bmatrix}
0 & 1 & 0 \\
1 & -4 & 1 \\
0 & 1 & 0
\end{bmatrix}$$
Unique, seperable.
## 8-connected
$$
\begin{bmatrix}
1 & 1 & 1 \\
1 & -8 & 1 \\
1 & 1 & 1
\end{bmatrix}
$$
$$
\begin{bmatrix}
-1 & 2 & -1 \\
2 & -4 & 2 \\
-1 & 2 & -1
\end{bmatrix}
$$
$$
\begin{bmatrix}
1 & 2 & 1 \\
2 & -12 & 2 \\
1 & 2 & 1
\end{bmatrix}
$$
And many other kernels.
## Standard
Small size kernels are noise-sensitive, thus we use from (7x7) to (10x10):
$$\begin{bmatrix}
1 & \dots & 1 & \dots & 1 \\
\vdots & \ddots & \vdots & \ddots & \vdots \\
1 & \dots & -48 & \dots & 1 \\
\vdots & \ddots & \vdots & \ddots & \vdots \\
1 & \dots & 1 & \dots & 1 \\
\end{bmatrix}$$
# Robust filter (Regularized Laplacian Filter)
To improve robustness, we could perform low-pass filtering before differentiation:
$$
\begin{align}
& L^\sigma = K_{\sigma} \ast L \\
\implies & \Delta L^\sigma = K_{\sigma} \ast \Delta L \\
\text{or } & \Delta L^\sigma = \Delta K_{\sigma} \ast L
\end{align}
$$
The second option is better because the Laplacian operator is smoothed, not the noisy image => $\Delta_{\sigma}=\Delta K_{\sigma}\ast$ which defines a band-pass filter is the regularized Laplacian operator.
In the spatial domain, we need large discrete kernels by sampling $K_{\sigma}$, this is good if $\sigma$ is small.
In the spectral domain, [[Fast Fourier Transform]] + Precomputed Laplacian of kernel spectrum:
$$
\Delta L^\sigma=TF^{-1}(TF(\Delta K_{\sigma}) \cdot TF(L))
$$
Has quasilinear complexity and is truncation error-free.
## Laplacian of Gaussian (LoG) Filter
Choose $K_{\sigma}$ as Gaussian Kernel $G_{\sigma}$, $\sigma$ is set based on noise/texture. For small $\sigma$, we can just sample $\Delta G_{\sigma}$ => must consider boundary conditions (paddings):
- Strongly smoothing.
- Well-posed differentiation: arbitrary-order derivatives are estimated robustly.
- Separable (computationally efficient).
- Well-localized in space (don't spread far) and frequency (don't spread far in spectral space => spread far in spatial space). Gaussian is a perfect balance: $TF(G_{\sigma})=G_{\frac{1}{\sigma}}$
  => Good trade-off between accuracy vs smoothing.
- Delocalization increases with increasing $\sigma$, thus it acts as the scale at which we see the image (high $\sigma$ = low level of detail = zoom out) => Hierarchizing image structure in term of level of detail.
## Difference of Laplacian (DoG) Filter
Given $\sigma_{1}>\sigma_{2}$ and $\frac{\sigma_{1}}{\sigma_{2}} \approx 1.6$, $D_{\sigma_{1},\sigma_{2}}$ is a linear filter which approximates LoG:
$$D_{\sigma_{1},\sigma_{2}} = G_{\sigma_{1}}-G_{\sigma_{2}}$$
For a given accuracy, the DoG kernel bandwidth is slightly larger than the LoG kernel bandwidth. This filter has biological consistency as retinal cell assemblies of mammals behave as DoG filter banks.
