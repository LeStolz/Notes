2026-01-03 18:41

#3D-Graphics 

> Maybe used in [[Digital Twin]]s. 

# Surface Model (Boundary Representation, B-Rep)
Continuous using implicit ($f(x,y,z)=\dots$) or parametric (Bézier, B-Spline,...) equations => concise but calculation-heavy.

=> Discrete representation: Vertices, Edges, Faces  => Simple implementation with hardwares.

Surface intersection is Complex.
# Volume Model (Voxels)
Discrete, simple query but too much data, not good for hardware rendering because needs to recalculate a surface.

Volume Intersection is Simple.
# Hierarchization
## Constructive Solid Geometry
![[Constructive Solid Geometry.png|400]]
Objects and sub-objects are related via [[3D Transformation Matrices|matrix transformations]].
## Scene Graph
Hierarchical ordering of elements making up a 3D scene.
Many types: 
- CSG construction tree (SolidWorks, Blender),
- Octrees (partitioning space into increasingly smaller pieces for collision detection, finite element method), 
- Inventor/VRML-like (most used in 3D API) (VRML, Open Inventor,...).
- Used in 3DExperience, Unity, Unreal as Hierarchy manager.
### Inventor/VRML-like
Graph is tree with geometric elements, rendering properties, camera parameters, illumination, geometric transformations.
#### Inventor-like
Depth-first-search and update a "rendering state" variable piloting graphical libraries.
![[Inventor-like Scene Graph.png|400]]
#### VRML-like
Traversal order does not matter anymore, hierarchical does. Includes:
- Group nodes (transform, group).
- Terminal nodes (are/with modifiable fields e.g. sphere has radius).
Still use DFS but add transform when going into a node, subtracting it when going out.
![[VRML-like Scene Graph.png|400]]
#### Three.js
![[Three.js Scene Graph.png]]
### Dynamic scene graph
Values can be changed:
- Edges represent a propagation mechanism of values => Streams.
- The sources of these streams generate dynamic data during the execution through callbacks, scripts, sensors, UI events, specific engine node or node + mentioned elements.
![[Dynamic Scene Graph.png]]
# Rendering
Diffuse > Specular > Texture > Ambient occlusion > Shadows > Sub-surface scattering.
## Order
Z-Buffer algo: Draw background onto screen, for each polygon, for each of its pixel projection on to the screen, if the current z of this pixel is higher than the polygon's pixel, draw the polygon's pixel.
## Color
RGB 8bits x 3 = 16M colors. Does not represent all possible colors.
## Luminosity
Ambiant, localization, intensity, direct, color,...

Light intensity is modeled by:
$$I=I_{ambiance} + \underbrace{I_{light}\cos(\theta_{light-normal})}_{diffuse} + \underbrace{I_{light}\cos(\theta_{refected\ light-view})}_{specular}$$
Smooth shading is done by interpolating surface normals to vertices and interpolating colors based on normals.
## Transparency
$$
\alpha = opacity_{max}-(opacity_{max}-opacity_{min})\cos(\theta_{view-normal})^n
$$
We use this to change the surface color:
$$
C_{\text{final}}=\alpha C_{\text{surface}}+(1-\alpha)C_{\text{background}}
$$
## Texture
Textures (color, transparency, normal) are generated procedurally 2D or 3D or from image fragments using UV mapping (map from each mesh vertex to image coordinates).
## Shadow
## Anti-aliasing
## Depth index
# Collision
Must consider: 
- Realtime, 
- Intersection between non-convex objects,
- Multiple contact points,
- Local deformation.
2 steps: Gross detection > Precise detection.
# Animation
Keyframes or physics (derivation of constraint or dynamic movement equations).
# Tools
Standard graphical library: GL, OpenGL.
3D DB:
3D Digitizer: Mira Imaging.
CAO: AutoCAD, Blender.
VR modelers: Unity, Unreal.