2026-07-06 16:22

#Machine-Learning 

> To find local minimum.

We use [[Machine Learning Notation]].

Before doing gradient descent, we should [[Feature Scaling|scale the features]] to converge faster.
To check convergence, we use the [[Model Development Cycle|learning curve]] (if it increases a lot, we decrease $\alpha$), or set an $\epsilon$.
# Standard
We repeat until local minimum is reached:
$$
\theta_{t}=\theta_{t-1}-\alpha \nabla J(\theta_{t-1})
$$
Computing $\nabla$ for entire dataset is too much.
# Stochastic
Instead, minimize the loss $J^{(i)}(\theta)$ only for one or some random data points.
We repeat until local minimum is reached:
$$
\theta_{t}=\theta_{t-1}-\alpha \nabla J^{(i)}(\theta_{t-1})
$$
Slow at the end as the surface levels out.
# Momentum
If we are going in the same direction, we should be more confident in taking bigger steps, i.e. keep the momentum:
$$
V_{t}=\beta V_{t-1}+(1-\beta)\nabla J^{(i)}(\theta_{t-1}) \quad | \quad \beta \approx 0.9
$$
$$
\theta_{t}=\theta_{t-1}-\alpha V_{t}
$$
# NAG
But momentum can overshoot, NAG solves this.
# RMSProp
With normal GD, parameters with large gradients jump around a lot and are optimized first, leading us to flat surfaces => diverge + slow. Therefore, learning rate should be increased for low gradient parameters and dampened for high gradient parameters:
$$
V_{t}=\beta V_{t-1}+(1-\beta)\nabla J^{(i)}(\theta_{t-1})^2 \quad | \quad \beta \approx 0.9
$$
$$
\theta_{t}=\theta_{t-1}-\alpha \frac{\nabla J^{(i)}(\theta_{t-1})}{\sqrt{ V_{t} }}
$$
# ADAM
Combines momentum and RMSProp:
$$
M_{t}=\beta_{1} M_{t-1}+(1-\beta_{1})\nabla J^{(i)}(\theta_{t-1}) \quad | \quad \beta \approx 0.9
$$
$$
V_{t}=\beta_{2} V_{t-1}+(1-\beta)\nabla J^{(i)}(\theta_{t-1})^2 \quad | \quad \beta \approx 0.99
$$
But we need bias correction to speed up the GD at the start:
$$
\hat{M_{t}}=\frac{M_{t}}{1-\beta_{1}^t}
$$
$$
\hat{V_{t}}=\frac{V_{t}}{1-\beta_{2}^t}
$$