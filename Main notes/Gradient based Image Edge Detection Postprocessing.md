2025-11-22 13:23

#Computer-Vision 

> To improve edge maps
# 1. Non-Maximum Suppression
> Remove artifacts (noise, thick edges).

Since noise does not have directional consistency and thick edges violate the [[Image Edge Detection Using Finite Difference Filters|local maximum contrast property]], we can check if the definition of an [[Image Edge Detection Using Gradients|edge point]] holds to filter:
for all pixel x in edge map:
1. [[Interpolation|Interpolate]] $|\nabla L|$ along edge normal ($\nabla L$) at neighboring points in the 8-connected neighborhood of x.
2. If $|\nabla L(x)|$ is not local maximum along $\nabla L$, remove x from edge map.
# 2. Hysteresis Thresholding
> Reconnect close edge fragments (edgels).

Short gaps in edgels are often weakly contrasted edge parts not detected due to high threshold. But lowering the threshold could include noise, textures => Filter using a connectivity constraint:
Add to the edge map any $x$ such that:
1. $|\nabla L(x)|$ is a local directional maximum.
2. $|\nabla L(x)|\geq \lambda_{low}$
3. $x$ is connected to some $y$ in the edge map such that $|\nabla L(y)|\geq \lambda_{high}$
$\lambda_{low}$ and $\lambda_{high}$ are set empirically or using noise estimates. Usually $\lambda_{high}=k\lambda_{low}\ |\ k \in [2,3]$.

This algorithm can fill 15-20 pixel gaps => Improve robustness.
# 3. Linking
> Reconnect distance edge fragments.

From segment endpoints, propagate a front and move along its normal $\mathbf{n}$ over $\Omega$ until reconnection. Frontlines are level sets of some connection cost function $V$ which is minimal over edges. Starting from endpoint, iterate until connection:
$$
\mathbf{x}(t+1) = \mathbf{x}(t) + \delta \mathbf{n}(\mathbf{x}(t))
$$
This can be uni- or bi-directional.

Some cost functions:
Gradient based:
$$\nabla V = \nabla^\perp L$$
Morphological: Use the Closing operator with increasing structuring element size (larger radius).
Distance based: Digital distance from a pixel to binary edge map.
Minimal path methods:
$$\text{Image cost} + \text{Edge cost} + \text{Smoothness term}$$