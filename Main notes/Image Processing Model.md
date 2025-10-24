2025-10-09 22:20

#Computer-Vision

# Image model
## Local topology
### Signal (1D)
Uses local window
![[Local window.png|200]]
### Images (2D or beyond)
Uses neighborhood systems
![[Local neighbors.png]]
- Obviously can have higher order with more complex topology but affects processing => most use local processing + neighborhood operators.
- A pixel's neighborhood determines its *spatial context* for processing. Its extension (i.e. size) defines the *processing scale*.
- Neighboring pixels are implicitly assumed to be *spatially correlated* and processed as a *statistically homogeneous* sample.
- => To avoid bias, we should define neighborhood (square, circle,...) to be consistent with spatial correlation properties of image data.
## Function
Deterministic: Images as functions using calculus or differential geometry.
$L$ = mapping or topographic surface over $\Omega$

=> $\Omega\subset R\ or\ \Omega\subset Z$
## Set
Algebraic: Images as unions of level sets (topographic maps) using mathematical morphology.
$$L = \bigcup_{l=0}^{2^b - 1} \{ x \in \Omega \mid L(x) \le l \}$$
=> $\Omega\subset Z$ because $L(x)$ is usually defined on integers, if not then it's a function.
## Random variables
Stochastic: Images as random variables using probability and statistics.
$L_{ij}=Lightness\ at\ (i,j)\ of\ RV\ L(x)$ with $x\in\Omega$, defined by its PDF.

=> $\Omega\subset Z$
# Analysis domain
The many transformation/representation of the domain in which we analyze the image.
X = texture | curvature | motion.

| Domain         | Tool                                              | Properties                                                                                     | Purpose                                                            |
| -------------- | ------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Color          | [[Color-based Image Segmentation\|Histogram]]     | [[Salient Information (Visual Feature)\|Salient]] => mode (peak) i.e. dominant color or region | Analyze intensity or color                                         |
| Spatiotemporal | Gradient                                          | Low-X region => smooth<br>Hi-X region, edge, noise => non-smooth                               | Analyze texture or motion                                          |
| Spectral       | Fourier                                           | Low-X => Low Hz => smooth<br>Hi-X => Edge/noise                                                | Use frequency to filter noise or detect patterns, texture analysis |
| Space scale    | Wavelet                                           | Salient => stable across scale<br>Detail/noise => transient across scale                       | Analyze structures at multiple scales, denoising                   |
| Parametric     | Hough space: Geometric feature => Parameter space | Salient => mode i.e. geometric configuration                                                   | Shape detection                                                    |
