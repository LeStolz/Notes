2026-01-01 10:13

#Computer-Vision  #Image-Recognition 
# Number of protrusions and depressions
Calculating first derivative of each point along the parameterized curve then check sign change at extrema, can test neighboring pixels. Sensible to noise. 
# Curvature
# Normalized elliptical skeleton
Simple forms => less branches and vice versa: ![[Skeleton Descriptor|300]]$$\text{NES} = \frac{\text{\#simple + \#multiple + \#terminal}}{\text{Perimeter of equivalent ellipse}}$$$$\text{SEP (noise sensitive)}=\#\text{terminal}$$
# Normalize Radial Length (NRL)
Distance from center to points on the boundary normalized. Some measures: std, mean, entropy, surface ratio (actual surface area / projected flat area), roughness,  zero-crossing rate.

Modified NRL: Same as NRL but for local. Some measures: difference in std, entropy, surface ratio between regions, zero-crossing local rate.

Both are sensible to noise and not unique, also, center can be outside boundary.
# Spiculated Mass Descriptor (SMD)
Detect number of spiculation on the contour by translating a line along the mass and sum the number of intersections over each translation. 
![[Spiculated Mass Descriptor.png]]
Only count non-redundant points (if current translation and the next one have the same number of intersections, don't count this one) to ensure scale invariant. This list is called $T(k)$ calculated from $S(k)$ which ($T$) is the variation of the model.

Needs to also rotate the line and recalculate (take the mean of all of the result of each rotations) to ensure rotation invariant. An optimal rotation angle $\beta$ needs to be found such that the descriptor is robust to noise while invariant. To find this, we try all $\beta$ then choose the one which produces the minimal variation between its largest and smallest SMD for the most number of images. The larger the DB, the more constant $\beta_{opt}$ is.