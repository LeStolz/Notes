2025-10-05 20:39

#Computer-Vision

# Data representation
Data can be natural or synthetic.
- Visual data:
	- Image: Still or Sequence
	- 3D Graphics
- Audio
- Text
- Sampled (measured at some points), Quantized (mapped measurements to a finite set of values) over a discrete (spatial/temporal) grid:
	- Structured: 
		- Regular: Often from sensors
		- Irregular: When processing
		- ![[Structured Grid Data.png]]
	- Unstructured (Graph): 3D sensor and processing
- Array (discrete index, value bounded in interval).
# Still images
- Single channel => Intensity, luminance, or gray level:
	- 2D pixel representation: $(i,j,L_{ij})\ |\ L_{ij}\in\{0\dots2^b-1\}$
	- 3D (slices of 2D, from medical/geographical imaging): $(i,j,k,L_{ijk})$
- Multi channel 
	- => color (RGB, HSI,...): 2D: $(i,j,L_{ij})\ |\ L_{ij}\in\{0\dots2^b-1\}^3$
	- => hyperspectral: More color (wavelength) than RGB for remote sensing, astronomy
- Multi view => stereoscopic (2 camera eyes), used in photogrammetry, AR, motion capture,...: $(i,j,L_{ij}^{num\_view})\ |\ L_{ij}\in\{0\dots2^b-1\}^3$
# Sequence images
- Single channel => single channel still images + $time$.
- Multi channel => multi channel still images + $time$.
# 3D Meshes
- Surface: Just a plane or a quad, or triangles. Just the exterior of the mesh.
- Volume: The exterior and interior filled: A cube.
- Graph:
	- Vertex: $v_{i}=(x_{i},y_{i},z_{i})\in R^3$
	- Neighbors: $e_{i}=(i_{1},i_{2,\dots})$
	- Attributes (color, texture,...) $A_{i}=(A_{i_{1}},A_{i_{2}},\dots)$