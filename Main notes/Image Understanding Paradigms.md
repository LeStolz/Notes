2025-10-08 15:52

#Computer-Vision

The process from [[Digital Media Contents & Data representation|Image data]] to [[Image Segmentation & Classification|Scene Segmentation]] using some [[Image Processing Model]]: Visual perception is a [[Image Processing|hierarchical process]] from raw data to semantics based on a finite set of principles and image entities (visual features). "Sum is greater than its parts":
1. [[Image Noise|Preprocess]] (denoising/image restoration)
2. Feature (could be [[Image Edge Detection|edges]], corners, textures, key points,...) extraction for [[Image Matching]], Image tracking, or [[Image Pattern recognition]]
3. [[Image Segmentation & Classification|Segmentation]]
4. Fusion: Combine multiple images into 1
5. [[Image Registration]]
6. [[Image Object Tracking]]

Image understanding usually motivates hard problems with no universal solution due to:
- Diversity of sensors & application contexts => use prior knowledge to constrain the solution space & improve performance
- Variability of images for a given application => Stable acquisition protocol to improve robustness; [[Machine Learning]] can help reduce modeling complexity
- Noise => Filter always the core of all image understanding processes