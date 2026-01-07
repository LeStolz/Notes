2025-11-23 14:31

#Computer-Vision 

> Blurring can occur during image acquisition (defocusing), scanning or scaling. This is noticeable along edges. Image sharpening reduce blurring by enhancing luminance transition by amplifying high frequency. 2 main approaches: Laplacian or Unsharp masking.

# [[Image Laplacian Filters]]
Using Laplacian filters to detect edge and distinguish edge sides (sign). Edge contrast enhancement is achieved by subtracting from the image a fraction of its Laplacian:
$$\phi_{S}(L)=L-\beta \Delta L$$
Or its equivalent kernel:
$$K^S=\mathbb{I}d-\beta\Delta$$
![[Edge Enhancement using Laplacian.png|400]]
## Some standard sharpening kernels ($\beta=1$)
### 4-connected
$$\begin{bmatrix}
0 & -1 & 0 \\
-1 & 5 & -1 \\
0 & -1 & 0
\end{bmatrix}$$
### 8-connected
$$\begin{bmatrix}
-1 & -1 & -1 \\
-1 & 9 & -1 \\
-1 & -1 & -1
\end{bmatrix}$$
$$\begin{bmatrix}
1 & -2 & 1 \\
-2 & 5 & -2 \\
1 & -2 & 1
\end{bmatrix}$$
Robust sharpening kernels are built from [[Image Laplacian Filters|LoG/DoG]] kernels.
# Unsharp masking
Build a detail mask by subtracting the smoothed image from the original. Edge enhancement is achieved by adding a fraction of the detail mask to the image:
$$\phi_{S}(L)=L+\beta(L-K \ast L)$$
Equivalent to kernel:
$$K^S=(1+\beta)\mathbb{I}d-\beta K$$
This is called highboost filtering if $\beta>1$.
# Comparison
- Unsharp masking uses smoothing and does not need differentiation => More robust to noise. The smoothing kernel bandwidth provides additional scale hyperparameter => better performance control.
- Laplacian performs similarly to unsharp.