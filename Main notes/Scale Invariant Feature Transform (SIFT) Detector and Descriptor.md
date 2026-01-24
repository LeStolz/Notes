2026-01-01 15:15

#Computer-Vision  #Image-Recognition 

> [[Interest Point Detection and Matching]] that is isometry, scale, rotation, POV, and lighting-invariant.

[[Image Corner Detection|Corners]] are not scale-invariant so we need to find their scales so we can normalize it.
# Scale space
Represent the scale $\sigma$ of the image by blurring it (more blur = more zoomed out = smaller), giving the scale space of the image $L(\mathbf{x},\sigma)$, we use exponential scale sampling $\sigma_{n}=\xi^n\sigma_{0}$ to ensure uniform information variant between each levels.

For each corner, the scale where its response is the highest is its scale.

But since to [[Image Corner Detection|detect corners, we need the Laplacian]], so we build the scale space using the [[Image Laplacian Filters|LoG]] but scale normalized not to make the response too small. This can be approximated by the DoG filter:
$$
D(\mathbf{x},\sigma)=(G_{\xi \sigma}-G_{\sigma})\ast L(\mathbf{x})
$$
Optimize computation by applying Gaussian filters at increasing scales, compute the DoG, then downscaling by a factor to get the next scale.
# Detector
1. Construct scale space using [[Image Laplacian Filters|DoG filters]] at different $\sigma$ values.
2. Detect points of interest by finding local extrema in image and scale space.
3. Calculate orientation around each point ($L^\sigma$ is the smoothed image and $\sigma$ is the scale of the point processing): $$\theta(x,y)=\arctan\left( \frac{L_{y}^\sigma(x,y)}{L_{x}^\sigma(x,y)} \right)$$
4. Filter points (remove low contrast points and edge points because [[Interest Point Detection and Matching|edges are not good interest points]]).

# Descriptor
5. Describe the points using local region:
	1. Divide a 16x16 window around a point into 4x4 cells of pixels.
	2. Find edge orientation histogram of each cell.
	3. > Dimension: 16 cells x 8 orientation = 128.
	4. Combine all values of all histogram into a single vector then we normalize it.
# Matching
Select dominante orientation (normalized (not to be affected by lighting) gradient) and normalize. Normalize size of features as well.

To match 2 SIFT vectors, we use nearest neighbor and the similarity between 2 images A and B is:
$$\text{Similarity(A,B)}=\frac{2\times\text{\#Common SIFT Vectors}}{\#\text{SIFT Vectors in A}+\#\text{SIFT Vectors in B}}$$
# Usage in [[Image Corner Detection|other detectors]]
Use LoG with Harris-Förstner => Increased repeatability but less points => less robust.
Use LoG with Hessian.