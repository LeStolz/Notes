2025-10-29 10:54

#Computer-Vision 

> Since image sensors have continuous transfer functions, fast local variation/discontinuity of properties of the image are assumed to be *various types of* edges.

Edges convey various information about 3D scene structure:
- Properties: surface normal, texture, reflectance.
- Ordering: depth.
- Lighting (shadow, lighting variations) => scene illumination.
- Boundaries between image regions (depth) => segmentation.
- Singular lines within image regions (shape, texture, reflection) => recognition.
However, can't really detect Illusory edges because no variation of luminance, thus, use image-extrinsic priors => perceptual grouping techniques.
# Edge Types
By Photometric characterization, Image regions have 2 types of luminance profiles.
### Low-texture (Smooth luminance)
Low frequency, continuous, deterministic [[Digital Media Contents & Data representation|luminance model]] $L$: Region boundary is a fast local variation/discontinuity => *shape edge*.
### Hi-texture
Hi frequency, fast local variation,
Deterministic model => confusion with shape's edge.
Statistical model (random variable) is spatially homogeneous: Region boundary is local variation/discontinuity of statistics => *texture edge*.
# Shape Edge Detection Pipeline
1. Preprocessing ([[Image Smoothing Filters|denoising]], enhancement,...).
2. [[Image Edge Detection Using Low-Order Derivatives]], [[Image Edge Detection Using the Laplacian]], or [[Image Edge Detection Using Canny-Deriche]] (edge map estimation, detection (thresholding)).
3. [[Gradient based Image Edge Detection Postprocessing|Postprocessing]] (artifacts removal, thinning, linking).

Preprocessing can be built into Edge detection => Robust edge detectors.
Contrast threshold => *Critical* => Tradeoff between saliency (robustness) and level of detail (sensitivity). Set based on noise, texture, lighting,...