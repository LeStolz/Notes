2026-07-07 14:16

#Machine-Learning 

> Allows models to predict better.

# Underfitting
Underfitting is when the model does not fit the data very well (high bias).
# Overfitting
Overfitting is when the model fits the data too well (high variance) => can't generalize.
Caused by too many feature but not enough data.
## Regularization
Prevents overfitting by reducing effects of features by adding a penalty term to the cost function (we always want to minimize the cost function, in doing so, we minimize the penalty as well):
$$
J'(\theta)=J(\theta)+\frac{\lambda}{2n}\sum_{j=1}^d \theta_{j}^2
$$
This keeps the parameters small => Each feature cannot have too high influence => Less overfit.
The term $\frac{\lambda}{2n}$ allows $\lambda$ to work no matter the dataset size.
# Just right
We want to prevent both of these.