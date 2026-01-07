2025-11-22 09:51

#Computer-Vision 

> A method of [[Image Edge Detection Using Gradients]].

For estimating an arbitrary order-derivative using neighboring points and [[Convolution]] against kernels. => Kernel size = tradeoff between accuracy (small) vs robustness (large) based on app-noise ratio and app constraints. Usually use FPGA/GPU for real-time apps.

FD estimates are derived from [[Taylor Expansions]].
## 1st-order FD
### Centered
Expression:
$$D_{\mathbf{x}}L_{ij}\approx L_{\mathbf{x}}(\mathbf{x}_{ij})\approx \frac{1}{2\delta_{\mathbf{x}}}(L(i+\delta_{\mathbf{x}},j)-L(i-\delta_{\mathbf{x}},j))$$
Kernel:
$$
\begin{bmatrix}
-1 & 0 & 1
\end{bmatrix}
$$
### Left-sided
Expression:
$$D_{\mathbf{x}}^-L_{ij}\approx L^-_{\mathbf{x}}(\mathbf{x}_{ij})\approx \frac{1}{2\delta_{\mathbf{x}}}(L(i,j)-L(i-\delta_{\mathbf{x}},j))$$
Kernel:
$$
\begin{bmatrix}
-1 & 1
\end{bmatrix}
$$
### Right-sided
Similar.
### Robert Filter
![[Robert Filter]]
- Small kernel => noise/texture-sensitive.
- Tailored to diagonal edges => directional bias.
- Subpixel edge point location => Interpolation.
## Robust Filter
Gradient filters in 1 direction $\partial$ with noise filter $S$ in orthogonal direction, represented as tensor product:
$$
D_{\mathbf{x}}=\partial^T_{\mathbf{x}}S_{\mathbf{y}}=S^T_{\mathbf{y}}\partial_{\mathbf{x}}
$$
$$
D_{\mathbf{y}}=\partial^T_{\mathbf{y}}S_{\mathbf{x}}=S^T_{\mathbf{x}}\partial_{\mathbf{y}}
$$
### Prewitt Filter
1st order centered FD + mean filtering:
$$
D_{\mathbf{x}}=\frac{1}{3} \begin{bmatrix}
-1 & 0 & 1 \\
-1 & 0 & 1 \\
-1 & 0 & 1
\end{bmatrix}\quad\quad D_{\mathbf{y}} \text{ same}
$$
### Sobel Filter
1st order centered FD + binomial (gaussian) kernel (smoother):
$$
D_{\mathbf{x}}=\frac{1}{4}\begin{bmatrix}
-1 & 0 & 1 \\
-2 & 0 & 2 \\
-1 & 0 & 1
\end{bmatrix}\quad\quad D_{\mathbf{y}} \text{ same}
$$
Diagonal bias.
### Frei-chen Filter
Directional kernels $D_{i\times 45^{o}}$ can be derived from $D_{0^{o}}$ by circular permutation.
Reweighting Sobel filter by setting the Euclidean metric over the image grid enhances isotropy but higher cost. Frei-chen proved that any 3x3 patch can be decomposed into smooth (1D) + edge (4D) + line (4D), and their filters are a basis of the 4D edge subspace:
![[Frei-chen Filter.png]]

The companion edge map is defined as the fraction of the patch belonging to the edge subspace using the Frobenius norm ($||A||_{F}^2=\sum a_{ij}^2$):
$$
\frac{\left( \sum_{i=1}^3 (D_{i \times 45^\text{o}} \ast L)^2 \right)^{1/2}}{||1_{\mathcal{Neighborhood}} \cdot L||_{F}}
$$
Standard threshold value is 95%.
![[FD Gradient Filters.png]]