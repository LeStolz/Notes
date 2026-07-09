2025-12-31 18:34

#Computer-Vision

> A method for finding contour in a noisy image.

Our image as intensity function of pixels:
$$f(x,y)=I(x,y)+\text{noise}(x,y)$$
Where:
$$I=I_{1} \text{ if } (x,y)\in D_{1} \text{ else } I_{2}$$
We would like to define an initial random contour and let this contour move toward the actual contours of the object like a rubber band or a balloon over time.

We are looking for an image which evolves over time:
$$
g(x,y,t)=\begin{cases}
I_{1} \text{ if } (x,y)\in D_{1}(t)\\ \\
I_{2} \text{ if } (x,y)\in D_{2}(t)
\end{cases}
$$
Let the contour of this image be $\Gamma(t)=D_1(t)\ \cap\ D_{2}(t)$, we would like the convergence $g(x,y,t=t_{c}) \approx I(x,y)$.

To make the points move toward the actual contours, we move them in the direction of the gradient squared and smoothed (for higher area of effect).

In the end, we want all the points to be on the edge, so the sum of the gradient squared of all points should be maximized.

We can also add [[Generalization and Regularization]] terms to force smoothness of the contour (least perimeter), or rubber-band-like (to avoid noises).