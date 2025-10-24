2025-10-23 09:29

#Computer-Vision #Extended-Reality 

# Objective
> To learn from data features (points, lines,...) (precondition) to determine physical (focal length,...) and geometric (transforms,...) informations (postcondition) depending on the sensor type:

- Camera => Image superposition (overlay/align).
- 3D device => 3D measurements (geometries/scanning).
- Robot => 3D measurements, auto calibration.
![[Calibration]]

> For camera, objective is to determine the transform of an object in space from its position in our image.
# Image formation
- Pinhole (ideal) (represent camera aperture as just a point) => Not enough light.
- Real camera (wider than a point, a circle, thus more light) => Blurry => Use lens.
- Using lens => Spherical and chromatic aberrations, radial distortions (cushion, barrel)
![[Pinhole vs Real]]
# [[Camera Internal and External Models]]

# Image distortion
## Radial distortion (Cushion or Barrel)
Because lens are imperfect. Distortion worse at the borders.
![[Image Distortion.png]]
