2025-11-01 12:26

#Computer-Vision 

> Extension of [[Image Edge Detection Using Low-Order Derivatives]].

- Directional derivative along vector $\textbf{d}$ is $\partial_{\textbf{d}}=\textbf{d}\cdot \nabla$.
- Phase $\textbf{n}= \frac{\nabla L}{|\nabla L|}$ = orientation => Level line normal.
- Amplitude $\partial_{\textbf{n}}L = |\nabla L|$ = contrast => Level line density along normal.

An point $\textbf{x}$ is an edge point if it has a direction $\textbf{d}$ that is a local maximum of contrast change along it:
$$\partial_{\textbf{d}}|\nabla L|=0$$
By consequence, $\textbf{d}$ is the edge's local normal and $\partial_\textbf{d}L$ is its directional contrast.

Thus, 2 approaches to find an edge point:
- Finite Difference Filters: Find local maximum of $|\nabla L|$, estimate local edge as level line => $\textbf{d}\approx\textbf{n}$.
- Template matching: Generate edge candidate orientations ($\textbf{d}$), test for $\partial_{\textbf{d}}|\nabla L|=0$ for candidates.
# Discrete mapping
Contrast map: $L_{\mathbf{x}}$ = Vertical + Diagonal edges, $L_{\mathbf{y}}$ = Horizontal + Diagonal edges, $\nabla L$ = Both.

Gradient magnitude (norms):
- $L2$: $\sqrt{ L_{\mathbf{x}}^2 + L_{\mathbf{y}}^2 }$ => $R^2$.
- $L1$: $|L_{\mathbf{x}}+L_{\mathbf{y}}|$ => 4-connectivity.
- $L_{\infty}$: $\max(L_{\mathbf{x}},L_{\mathbf{y}})$ => 8-connectivity.
- Hybrid: $\max(L_{\mathbf{x}},L_{\mathbf{y}})+\frac{1}{4}\min(L_{\mathbf{x}},L_{\mathbf{y}})$.
Isotropy (Same in all direction):
![[Norm Isotropy.png|200]]
# [[Image Edge Detection Using Finite Difference Filters|Finite Difference Filters]]
# Template matching
Generate edge candidate orientations ($\textbf{d}$), test for $\partial_{\textbf{d}}|\nabla L|=0$ or $\partial_{\textbf{d}}L \approx D_{i}L = \max$ using discrete templates ([[Image Edge Detection Using Finite Difference Filters|Finite Difference Filters]]) $D_{i}$ for candidates.
Computation cost increase with kernel size and direction resolution => Standard size: $3 \times 3$, $45^{o}$.
Some kernels to do this: Robinson:
$$
D_{0^o}=\frac{1}{4}
\begin{bmatrix}
-1 & 0 & 1 \\
-2 & 0 & 2 \\
-1 & 0 & 1
\end{bmatrix}
$$
Kirsch:
$$
D_{0^o}=\frac{1}{15}
\begin{bmatrix}
-3 & -3 & 5 \\
-3 & 0 & 5 \\
-3 & -3 & 5
\end{bmatrix}
$$
Prewitt comparss:
$$
D_{0^o}=\frac{1}{15}
\begin{bmatrix}
-1 & 1 & 1 \\
-1 & -2 & 1 \\
-1 & 1 & 1
\end{bmatrix}
$$
And many others with larger kernels, higher angular resolutions.
