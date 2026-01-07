2025-10-29 15:14

#Computer-Vision 

# [[Image Linear Smoothing Filters]]

# Image Non-Linear Smoothing Filters
## PDE-based Filters
Iterative filters generating increasingly smoothed images defined as solutions of nonlinear diffusion PDEs anisotropic diffusion | geometric heat equations.
## Morphological Filters
Algebraic filters with monotonicity (preserve brightness order) + idempotence (filter twice = filter once) properties derived by combining morphological erosion and dilation opening | closing | alternating sequential filters.
## Patch-based Filters
Weighted mean filters with weights depending on the similarity between patches around current and any other pixels non-local (NL) means (if find patches similar, the pixel is probably similar as well).

Non-Linear can do distinct intra-/inter-region smoothing => Less bias, better discontinuity preservation, potential contrast enhancement, sharper details.