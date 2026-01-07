2025-11-01 11:31

#Computer-Vision 

Linear filter of an image:
$$
\phi_{K}(L)=\underbrace{K}_{\text{Kernel}} \ast L
$$
Continuous case:
$$
\phi_{K}(L)(\textbf{x}_{0})=\int_{\Omega} K(\textbf{x}_{0}-\textbf{x})L(\textbf{x})d\textbf{x}
$$
Discrete case, $\mathcal{N}$ is the usually square neighborhood of $\textbf{x}_{ij}$ ([[Convolution|Convolutional matrix]]):
$$
\phi_{K}(L)_{ij}=\sum_{(lm)\in\mathcal{N}} K_{i-l,j-m}L_{lm}
$$
The convolution theorem:
$$
\begin{align}
\phi_{K}(L)&=K \ast L \\
\xRightarrow{\text{Fourier Transform}}\widehat{\phi_{K}(L)}&= \hat{K} \cdot \hat{L}
\end{align}
$$
Such spectral implementation (calculation in frequency space) results in:
- $O(|\mathcal{N}|)$ spatial integration translates into $O(1)$.
- Truncation error-free (since the operation is global and not local, we do everything at once).
- Direct/Inverse image Fourier Transform is computed quickly using [[Fast Fourier Transform]] $O(N\log N)$.
- Separable into smaller independent convolutions along each dimension => faster.
## Smoothing kernel admissible conditions
- Positive: $K(\textbf{x})>0$, $K_{ij}>0$.
- Symmetric: $K(\textbf{x})=K(-\textbf{x})$, $K_{i,j}=K_{-i,-j}$.
- Unimodal (decreasing from center): $\partial_{x_{i}}K(\textbf{x})<0$, $K_{ij}>K_{i+l,j+m}$.
- Unit mass: $\int K(\textbf{x})d\textbf{x}=1$, $\sum K_{ij}=1$.
- Equi-distributed: $\sum K_{2i,2j}=\sum K_{2i+1,2j+1}$. Useful for down-sampling by 2.
## Mean Filter
$$
\phi_{K}(L)(\textbf{x})=\frac{1}{|\mathcal N|}\begin{bmatrix}
1 & \dots & 1 \\
\vdots & \ddots & \vdots \\
1 & \dots & 1 \\
\end{bmatrix} \ast L(\textbf{x})=\frac{1}{|\mathcal N|}\sum_{\textbf{y} \in \mathcal N}L(\textbf{y})
$$
Strongly smoothing, isotropic (same properties in all directions):
- Non-edge preserving.
- Loss of contrast, sharpness.
- Delocalization.
These artifacts increase with kernel extension.
## [[PDF|Gaussian]] Filter
### Continuous
$$
\text{G(\textbf{x})} = \frac{1}{\sigma \sqrt{ 2\pi }}\exp\left( -\frac{1}{2}\left( \frac{|\textbf{x}|}{\sigma} \right)^2 \right)
$$
Same properties as Mean Filter but separable (can be implemented as tensor product of 1D kernels along grid axes ($x$, $y$,... axes)).
### Discrete
#### Real-coefficients
Sample the Gaussian over a $[-M,M]$ window (usually $M=C\sigma+1$ with $C\in [3,6]$) into a kernel => Significant error for large windows.

Instead of sampling, we could define the kernel as the solution of the discrete heat equation. Scale-Space theory:
- Consistency across all scales.
- Smooth nicely when increase $\sigma$.

Recursive Filters: Infinite Impulse Response (IRR) filters to approximate $G(\textbf{x})$ with given orders => Canny Filtering.
#### Integer-coefficients
![[Integer Gaussian Filter Kernel.png]]
## Median Filter
Denote $L^{\mathcal{N},k}(\textbf{x})$ the $k^{th}$ smallest pixel value in $\mathcal{N}$ of $\textbf{x}$, we have the rank filter of rank $k$:
$$\phi_{\mathcal{N},k}(L)(\textbf{x})=L^{\mathcal{N},k}(\textbf{x})$$
- $k=1$: Minimum => Erosion.
- $k=|\mathcal{N}|$: Maximum => Dilation.
- $k=\left\lfloor  \frac{|\mathcal{N}|}{2} +1 \right\rfloor$: Median => Median filter.

Pros:
- Optimal for moderate [[Image Noise|impulse (salt-and-pepper) noise]] (# noisy pixel < 20%).
- Edge preservation, contrast enhancement.
Cons:
- Fine details are smoothed.
- Computational bottleneck = sorting $O(|\mathcal{N}|\log|\mathcal{N}|)$.
## Adaptive Median Filter
Only filter impulse noise pixels => Detail preservation + filtering bias reduction.
```C++
for (r = 1; <= rmax; r++) { // Grow neighbor until noise is detectable 
	// If most neighbors differ from noise
	if (min(L(Neighbor(r))) < med(L(Neighbor(r))) < max(L(Neighbor(r)))) {
		// 
		if (min(L(Neighbor(r))) < L(x) < max(L(Neighbor(r)))) {
			return L(x);
		} else {
			return med(L(Neighbor(r)));
		}
	} 
}
return L(x) // No noise found
```
Improved:
- Denoising for impulse noise > 20%.
- Edge contrast.
- Fine detail preservation.