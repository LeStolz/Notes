2026-07-06 11:09

#Machine-Learning 

> Predict target $y$ from features $x$ by learning from correct examples.

We use [[Machine Learning Notation]].

# Feature engineering
Using intuition to design new features (e.g. $\mathbf{x}_{3}=\mathbf{x}_{1}\mathbf{x}_{2}$) to better the model.
One important application is polynomial regression: $\mathbf{x_{i}}=\mathbf{x_{1}}^i$.
# Regression (continuous)
## Mean Squared Error
The most used for regression because it's convex:
$$J^{(i)}(\theta)=(\hat{y}^{(i)}-y^{(i)})^2$$
$$J(\theta)=\frac{1}{2n}\sum_{i=1}^nJ^{(i)}(\theta)=\frac{1}{2n}(y-\hat{y})^T(y-\hat{y})$$
## Linear Regression
To find linear functions:
$$
f(\mathbf{x})=\theta_{0} + \theta_{1}\mathbf{x}_{1} + \theta_{2}\mathbf{x}_{2} + \dots=\begin{bmatrix}
\theta_{0} \\
\theta_{1} \\
\vdots
\end{bmatrix}
\begin{bmatrix}
1 \\
\mathbf{x}_{1} \\
\vdots
\end{bmatrix}
$$
That best fit data, in short:
$$
\hat{y}=\mathbf{X}\theta
$$
Train by minimizing the MSE by solving the normal equation or [[Gradient Descent]] for:
$$\frac{\partial}{\partial \theta_{j}}J(\theta) = \frac{1}{n}\sum_{i=1}^n (\hat{y}^{(i)}-y^{(i)})\mathbf{X}^{(i)}_{j}$$
$$\nabla J(\theta) = \begin{bmatrix}
\vdots \\
\frac{\partial}{\partial \theta_{j}}J(\theta) \\
\vdots
\end{bmatrix} = \frac{1}{n} \mathbf{X}^T(\hat{y}-y)$$
*Problem: Sensitive to outliers => Not good for classification.*
# Classification (discrete)
2 approaches:
- Intrinsic (Nearest Class Centroid): Create a model which best characterize each class. Classification is based on measuring similarity to each class.
- Discriminative ([[Support Vector Machine (SVM)|SVM]]): Find decision boundaries which optimally separate classes. Classification is based on which class region the input is in.
## Logistic Regression (Binary case)
The linear regression $z=\mathbf{X}\theta$ is used to predict a score, large (> 0) if likely to be class 1 and small (< 0) if likely to be class 0. It is then put into the sigmoid:
$$\hat{y}=g(z)=\frac{1}{1+e^{-z}}$$
Which gives the probability in range 0 to 1.
### Logistic cost function
This is also convex and derived from maximum likelihood estimation:
$$J^{(i)}(\theta)=\begin{cases}
-\log(\hat{y}^{(i)}) \text{ if } y^{(i)}=1 \\
-\log(1-\hat{y}^{(i)}) \text{ if } y^{(i)}=0
\end{cases}$$
or equivalently:
$$J^{(i)}(\theta)=
-\log(\hat{y}^{(i)}) \times y^{(i)}
-\log(1-\hat{y}^{(i)}) \times (1 - y^{(i)})
$$
$$J(\theta)=\frac{1}{n}\sum_{i=1}^nJ^{(i)}(\theta)$$
Train by minimizing the logistic cost:
$$\frac{\partial}{\partial \theta_{j}}J(\theta) = \frac{1}{n}\sum_{i=1}^n (\hat{y}^{(i)}-y^{(i)})\mathbf{X}^{(i)}_{j}$$
$$\nabla J(\theta) = \begin{bmatrix}
\vdots \\
\frac{\partial}{\partial \theta_{j}}J(\theta) \\
\vdots
\end{bmatrix} = \frac{1}{n} \mathbf{X}^T(\hat{y}-y)$$
## Softmax Regression (Multi case)
Calculate $z_{c} = \mathbf{X}\theta_{c}$ for each class $c$ and also the probability:
$$
a_{c}=P(y=c|x) = \frac{e^{z_{c}}}{\sum e^{z_{i}}}
$$
### Softmax cost function
This is also convex and derived from maximum likelihood estimation:
$$J^{(i)}(\theta)=\begin{cases}
-\log(a_{c}^{(i)}) \text{ if } y^{(i)}=c
\end{cases}$$