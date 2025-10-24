2025-10-08 00:58

#Computer-Vision

# Preprocessing
Must always [[Image Noise|preprocess]] first to reduce noise.
# Image segmentation
Finding a partition of the data domain (image grid) $\Omega$ into a collection $R_{i}\ | \ 0\leq i\leq n$ of connected, non-overlapping subsets. $R_{0}$ is background. $\partial R_{i}$ is boundary of $R_{i}$.

Images can be segmented by detecting regions, edges, or hybrid.

Can be used in industrial imaging, computer-aided design, or diagnosis.

Segmentation into regions => overlapping issue.
# Scene segmentation
Segmentation into planes (+ indexed plane set) instead of regions can fix overlapping issue.

Same as image segmentation but associated with a family $C_{i}$ of ordered maps representing depth, volume maps, plane indices,... => layered media representation.
# Image classification
Finding a labeling $(i, \lambda_{i})_{i\in \Omega}\ |\ \lambda\in\Lambda$ => A partition of $\Omega$ with non-overlapping *but not necessarily connected* subsets: Segmentation into objects.
Ex: Segment video into semantic images.
# Usages
- Isolating objects of interest.
- Object-based compression (keeping objects of interest).