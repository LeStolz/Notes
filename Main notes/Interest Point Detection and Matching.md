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
- Performance measured by [[Confusion Matrix and ROC|few failures]] and computation complexity.

*Edges* cannot be used because not distinctive (not invariant to spatial transforms): Matching ambiguity along edge tangent:
![[Edges are not spatial transform-invariant.png]]

[[Image Corner Detection|Corners]] fit these descriptions but are not invariant to scaling => [[Scale Invariant Feature Transform (SIFT) Detector and Descriptor]].
# Description
After extracting interest points, find, normalize, and transform interest patch around each key points into invariant local coordinates, then compute the patch local descriptor (similarity metric to match).

Can store neighbor intensities or gradients (patches) => Not rotation-invariant.

Matching between 2 interest points is by finding its nearest neighbor in description space. However, using only descriptor is bad due to too much individual invariance, deformation, local appearance is ambiguous => Use local spatial relation verification to verify after match:
- Semi-local constraints: neighbors of a point have to match and angles correspond.
- Global constraints: all matches must be consistent with a global [[3D Transformation Matrices]] using [[Image Processing|Calibration]] or [[RANSAC]].