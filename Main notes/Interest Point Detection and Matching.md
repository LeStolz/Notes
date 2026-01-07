2025-11-23 23:18

#Computer-Vision 

> Find and match interest point to use in [[Image Matching]] problems.
# Detection
Feature of interest should be distinctive, stable and efficient to detect / match:
- Structural properties:
	- Good localization,
	- Generic, 
	- Sparse (compact, computational efficiency),
	- Numerous (robust),
	- Uniformly distributed (occlusions, clutter, cropping).
- Invariance properties (repeatability, i.e. Still good when something changes):
	- Contrast (Luminance) transforms (sensor calibration, lighting).
	- Spatial (isometric, scaling, affine) transforms (sensor geometric calibration, viewpoint).
- Robustness properties (repeatability + accuracy):
	- Sampling & quantization (digital image acquisition, coding scheme).
	- Noise (sensor model).
- Performance measured by [[Confusion Matrix|few failures]] and computation complexity.

*Edges* cannot be used because not distinctive (not invariant to spatial transforms): Matching ambiguity along edge tangent:
![[Edges are not spatial transform-invariant.png]]

[[Image Corner Detection|Corners]] fit these descriptions but are not invariant to scaling => [[Scale Invariant Feature Transform (SIFT) Detector]].
# Description
After extracting interest points, find, normalize, and transform interest patch around each key points into invariant local coordinates, then compute the patch local descriptor (similarity metric to match).