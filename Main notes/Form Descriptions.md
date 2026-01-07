2025-12-31 20:22

#Computer-Vision  #Image-Recognition 

> Extracting informations on the forms in the image -> Descriptors <- which have to be invariant to translation, rotation, and homothety (plane similarities), and unique:

Types:
- Global: Of the entire object: Circularity, Elongation,...
- Local: Of parts of the object: Corners, Vertices, Segments, Regions,...
- Generic: For all systems: Hu's Invariants, Fourier, Fourier-Mellin.
- Specific: For our purposes: Circularity, Elongation, Compactness,...
# Hu's Invariants
> 7 algebraic, moments-based invariants calculated based on normalized moments and are invariant to translation, rotation and scale.

Raw moment:
$$m_{pq}=\sum_{x}\sum_{y}x^py^qI(x,y)$$
Is position dependent with $m_{00}=\text{area}$ and centroid $x_{0}=\frac{m_{1,0}}{m_{0,0}},y_{0}=\frac{m_{0,1}}{m_{0,0}}$

Based on this, we can use central moment:
$$
v_{pq}=\sum_{x}\sum_{y}(x-x_{0})^p(y-y_{0})^qI(x,y)
$$
Which is not position dependent (when object moves, centroid moves, moment same). But still scale dependent, so we normalize it:
$$\mu_{pq}=\frac{v_{pq}}{v_{0,0}^{1+(p+q)/2}}$$
![[Hu's invariants.png|500]]

Used in [[Image Pattern recognition]].
# Geometric Descriptor
Area, Perimeter,... can be used to build geometric descriptors. But these are not invariant to scale: area increase by a factor of $k^2$ while others, $k$, so we build descriptors invariant to scale:
- Isoperimetric ratio (compactness): $$\frac{4\pi\times\text{area}}{\text{perimeter}^2}$$
- Circularity: $$\frac{\text{Area of smallest circle encapsulating the object}}{\text{Area of largest circle inside the object}}$$
- Elongation: $$\frac{\text{Long axis}^2}{Area}$$
- Compactness: $$\frac{\text{Area}}{\frac{\text{Long axis}}{2}^2\times \pi}$$
- Rectangularity (not rotation invariant):![[Rectangularity Descriptor.png]]
- Modified Rectangularity.
# [[Morphographic Descriptions|Morphographic Descriptor]]
# Evaluation
DB => Train, Test sets with same number of each class in it.
We can test all combination of descriptors and learning models to see what is best using [[ROC Curve]] or [[Fischer Criterion (Discriminant Ratio)]].