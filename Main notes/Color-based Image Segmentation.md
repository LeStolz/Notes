2025-10-11 13:06

#Computer-Vision

Segmentation using only *colors* (assume gray scale for simplicity, multichannel, multi-view, sequences,... are the same):
$$L(x)\in\{0\dots2^b-1\}\ |\ x\in \Omega$$
Where $L$ = gray level; $x$ = pixel coordinate; $\Omega$ = grid of all pixels.

A segmentation scheme is [[Histogram-based Image Segmentation]].
# Operators
## Thresholding
Basic operator for retaining pixels in a luminance range.
### Upper
$$T^{\lambda}(L)(x)=\begin{cases}
L(x), & \text{if } L(x) \ge \lambda, \\
0, & \text{otherwise}
\end{cases}$$
### Lower
$$T_{\lambda}(L)(x)=\text{Similar}$$
## Binarization
Similar to thresholding but gives *sets* instead of pixels.
$$B^{\lambda}(L)(x)=\begin{cases}
1, & \text{if } L(x) \ge \lambda, \\
0, & \text{otherwise}
\end{cases}$$
## Level sets
$$L_{\lambda}=\{x\in \Omega\ |\ L(x)\leq\lambda\}$$
The collection of level sets: $L_{\lambda}\ |\ \lambda\in\Lambda$ defines the *image topographic map* which gives an algebraic image decomposition:
$$L = \bigcup_{\lambda\in\Lambda} L_{\lambda}$$
=> region-based geometric processing => mathematical morphology
## Level line
$$\underline{L_{\lambda}}=\{x\in \Omega\ |\ L(x)=\lambda\}$$
If $\Omega\subset R^n$, level line represents:
- Constant luminance regions (plateau), non-generic (easily perturbed by noise)
- Non-intersecting closed (except along $\partial \Omega$) codimension-1 surfaces
if $\Omega\subset Z^n$, no connectivity => sub-pixel image interpolation

Level lines give a geometric image decomposition:
- Description of local image geometry
- Contour-based geometric image processing
# Basic intensity-based segmentation
Finding $\lambda_{1}<\mu_{1},\lambda_{2}<\mu_{2},\dots$ to partition the luminance space $\Lambda$ into non-overlapping intervals $[\lambda_{i},\mu_{i}]$ which define region $R_{i}$:
$$
R_{i}=\{x\in \Omega\ |\ B^{\lambda_{i}}T_{\mu_{i}}(L)(x)=1\}
$$
$$
R_{0}=\Omega-\bigcup_{1\leq i\leq N}R_{i}
$$
However, accurately segmenting natural images based on color is rarely possible:
- Noisy, textured, sensor & scene properties induce variability in appearance.
- Low contrast, shadows, transparency, non-uniform lighting, reflections,...
=> [[Image Noise|Preprocessing]].
# Performance & Limitation
- Used for simple images (cartoon).
- Used for coarse segmentation (pre-segmentation) => Good for real-time (object tracking in live video sequences).
- Using spatial(temporal) context info is usually necessary to disambiguate local intensity information => Better accuracy, robustness.