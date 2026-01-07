2025-11-01 12:56

#Computer-Vision 

> Discontinuity in derivatives = Edge. Thus, spatial variations are described by image derivatives (of order $m$) $D^mL$:

$$
D^mL=\left(L_{x_{1}^{i_{1}}\dots x_{n}^{i_{n}}}\right)_{i_{1}+\dots+i_{n}=m}
$$
![[Standard Edge Models]]
Object shape/shadow is detected using: 
- $D^0$ (step edge): Dis. in luminance (impractical for discrete signals),
- $D^1$ (roof edge): Local maximum, edge map = $|\nabla L|$
- $D^2$ (slope, roof edge): Zero-crossing, edge map = $\Delta L=Trace(D^2L)$
Occlusion solid, transparent is detected using:
- $D^3$ (T-junction): Dis. in curvature.
- $D^4$ (X-junction): Dis. in change in curvature.

*The connection "dis. = Edge" holds for all visual contents (color, vector image, scalar image, video, 3D objects (manifold derivatives)*.
## What geometry to derive?
Image structure is encoded in its topographic map:
$$L = \bigcup_{\lambda \in \Lambda}\underbrace{\{\textbf{x} \in \Omega\ |\ L(\textbf{x}) \leq \lambda\}}_{\text{Level Set}}$$
Image geometry is encoded in its level lines:
$$\underline{L}_{\lambda} = \underbrace{\{\textbf{x} \in \Omega\ |\ L(\textbf{x}) = \lambda\}}_{\text{Level Line}}$$
> [[Differential Geometry]] is used to characterize their local geometries:

Assume a parameterized representation of level lines
$$\underline{L}_{\lambda} = \{\textbf{x}(u) \in \Omega, u \in \Gamma\ |\ L(\textbf{x}(u)) = \lambda\}$$
Its orientation at $\textbf{x}$ is given by its Frenet frame $[\textbf{t},\textbf{n}]$ (\[tangent, normal\]):
$$
\begin{align}
L(\textbf{x}(u))&=\lambda \\
\iff L_{u}&=0 \\
\iff \frac{dL}{dx} \frac{dx}{du}+\frac{dL}{dy} \frac{dy}{du} &= 0 \\
\iff \nabla L \cdot \textbf{x}_{u}&=0 \\
\implies \textbf{n}&=\frac{\nabla L}{|\nabla L|} \\
\implies \textbf{t}&=\frac{\nabla^\perp L}{|\nabla L|}
\end{align}
$$
The curvature is thus the rate of change of the orientation for *unit speed tangent motion*:
$$\kappa=\nabla \cdot n$$
[[Gray Level Image as Surface|Gray level images can also be viewed as a surface]] in $R^3$.
## But images are noisy
For example, additive noise:
$$
\begin{align}
L=&L_{0}+n \\
\implies D^pL=&D^pL_{0}+D^pn \\
\xRightarrow{\text{Fourier Transform}} (i\omega)^p\hat{L}=&(i\omega)^p\hat{L_{0}}+(i\omega)^p\hat{n}
\end{align}
$$
But $(i\omega)^p$ increase polynomially with each differential order => Degrade hi-frequencies of $D^pL$ => Differentiation is sensitive to noise, thus:

> Must always use [[Image Smoothing Filters]] before or together and keep differentiation order low. Based on Signal-Noise Ratio (SNR), a trade-off between smoothing (robustness) and discontinuity preservation (accuracy) must be set.

# [[Image Edge Detection Using Gradients]]