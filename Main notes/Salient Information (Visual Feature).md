2025-10-09 22:16

#Computer-Vision

Salient Information is *important feature*.

Nature: 
- Color: Lab is useful for working with lightness and color separately.
	- (L) Luminance (Lightness): For structure and contrast.
	- (ab) 2 Chrominance components. a: green $\leftrightarrow$ red axis; b: blue $\leftrightarrow$ yellow axis.
- Depth: RGB-D or multi-view images.
- Shape: Smooth image component (noise, texture removed):
	- Global geometry:
		- Topology: How parts of object are connected, inside, outside, # holes?
		- Symmetry, size,
		- Subspace: Groups shapes into categories or templates for comparison or recognition.
	- Local geometry:
		- Orientation (direction), curvature, convexity at specific point.
- Texture: non-smooth component
	- Structural properties: regularity (periodicity, orientation); homogeneity (no sudden change in color between pixels); granularity (micro/macro texture).
	- Descriptive properties:
		- Procedural if has textels (smallest repeating part of texture): deterministic, stochastic
		- Non-procedural
	- Motion: global (topology, connectivity, direction, subspace: motion of class) or local (gradient $\nabla$ field).
Localization: region or contour-based.