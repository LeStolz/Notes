2025-11-22 16:10

#Computer-Vision 

# Luminance Laplacian
$$\Delta L = \text{Trace}(D^2L)=L_{xx}+L_{yy}$$
This operator is isotropic, contrast-free but is sensitive to noise. Its zero-crossing contains:
- Local directional maxima of $|\nabla L|$ (shape edges).
- Local minima of $|\nabla L|$.
- Constant luminance regions (non-generic in natural (noisy) images).

Since $\Delta$ is continuous, its ZC consist of closed (except along image boundaries) curves/surfaces (i.e. geometric sets instead of point sets). Salient edge points are then filtered using a local contrast criterion:
- $|\nabla L(x)|\geq \lambda$, or
- $\text{Var}_{\mathcal{N}(x)}L\geq \lambda$.

The $\Delta$ can be approximated using [[Image Laplacian Filters]].

This method of edge detection does not need linking or thinning in the [[Gradient based Image Edge Detection Postprocessing]] since edges are level lines (continuous).

ZC detection uses sign change (better than checking = 0 since you need to account for errors):
- 8-connected neighborhood is used => Jordan curve theorem holds.
- ZC location is computed at subpixel scale via interpolation.