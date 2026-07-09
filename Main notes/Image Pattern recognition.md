2025-11-23 23:31

#Computer-Vision

![[Image Classification System|600]]

> Image retrieval, Object recognition (identify specific instance of a class) and Object categorization (classify image/region into predefined classes).

Image recognition is how to automatically create visual models and learn interpretation methods of data to recognize and categorize objects. Used in Computer Vision, Biometry and CAD.

Difficulties concerns heterogenic multisource data, what attributes to pick, hard to find attributes that are general but discriminative, data too specific which requires domain knowledge, needs to select and tune learning models to work multisource.

Approaches:
- [[Feature Extraction and Description]]: How to represent image info for recognition. For example, texture can be represented as standard deviation of gray-scale values, smoothness as variation in radius lengths,...
- Image/Video Indexing: How to organize data, maybe based on features from [[Image Matching]].
# Case Studies
Photos > color correction, gray-scale conversion, noise reduction > preprocessed image.

Preprocessed image 
- > global descriptions.
- > [[Active Contour Segmentation]] > edges, interest points/regions > local descriptions.

These [[Form Descriptions|descriptions]] > object modeling > classification learning, predicting.

## Sickle cell disease
> Deformed blood cells can clog the blood vessels. How to detect these cells using images.

We can test [[Form Descriptions|Hu's invariants]] on healthy cells which are the same. Except for the first invariant, the other 6 are almost 0 for healthy cells, differentiable to unhealthy ones. However, using [[Form Descriptions|other geometric descriptors]] seems better for this case. Health cells seem to be more homogenic while unhealthy ones are less so due to many possible forms.
## Mammography
> The worse the disease, the more spiky the cell becomes.

Try all [[Form Descriptions|descriptors]]. The one that count the number of depression and intrusion seems good but is heavily dependent on thresholds. SMD is probably best.