2025-10-05 21:35

#Computer-Vision

# From pixels to semantics
![[Image Processing Pipeline|600]]
1. Image acquisition: image sensor => [[Digital Media Contents & Data representation|Image data]]
2. Image understanding: partition image data into homogeneous (similar) spatiotemporal regions
3. Computer vision: abstraction into 3D objects + spatiotemporal relationships
4. Pattern recognition: describe scene into semantics
## Image acquisition
1. Calibration: Finding intrinsic/extrinsic camera parameters
2. Image reconstruction: Convert sensor data => image. ex: 3D image from slices
## [[Image Understanding Paradigms|Image understanding]]
1. [[Image Noise|Preprocess]] (denoising/image restoration)
2. Feature (could be edges, corners, textures, key points,...) extraction for matching, tracking, or recognition
3. [[Image Segmentation & Classification|Segmentation]]: Divide image into meaningful regions (ex: foreground & background, person & not person,...)
4. Fusion: Combine multiple images into 1
5. Registration: Align multiple images (different time/view point) of the same scene
6. Tracking: Track an object over time
## Computer vision
1. Shape from X (could be shading, stereo, motion,...): Infer 3D shape, structure from 2D images
2. 3D reconstruction: Build 3D model from multiple images or depth data
## Pattern recognition
1. Categorization: Classify image/region into predefined classes (ex: dogs, cats,...)
2. Recognition: Identify specific instances or patterns (ex: recognizing a specific face, not just any face)
3. Learning: ex: Training a neural network to detect objects,...