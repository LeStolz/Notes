2025-11-22 13:55

#Calculus 

# 1D interpolation
## 0th order: Nearest Neighbor
$$L(x) \approx L(\lfloor x + 0.5 \rfloor)$$
## 1st order: Linear
Basically just draw a line connecting $L(i)$ and $L(i+1)$ then use the line to predict $x$:
$$L(x) \approx (1-u)L(i)+uL(i+1)$$
Where $u=x-i$
## Higher order: Polynomial
Spline, B-Spline,...
# 2D interpolation
## 0th order: Nearest Neighbor
$$L(x) \approx L(\lfloor x + 0.5 \rfloor)$$
## 1st order: Bilinear
Basically just draw a line connecting $L(i)$ and $L(i+1)$ then use the line to predict $x$:
$$L(x) \approx (1-u)(1-v)L(i,j)+u(1-v)L(i+1,j)+(1-u)vL(i,j+1)+uvL(i+1,j+1)$$
Where $u=x_{x}-i$ and $v=x_{y}-j$.
## Higher order: Polynomial
Spline, B-Spline,...