2025-11-23 15:48

#Computer-Vision 

Consider a 1D edge model: A noisy step edge at $\mathbf{x}_{0}$ with contrast $\rho$ (min = 0, max = $\rho$):
$$L(x) = \rho H(\mathbf{x}-\mathbf{x_{0}})+\text{noise(x)}$$
![[1D Noisy Edge.png|200]]
We can detect this by applying a filter with kernel $K$ which has a high magnitude at edges:
$$\phi_{K}(L)(\mathbf{x_{0}})=\int K(\mathbf{x}-\mathbf{x_{0}})L(\mathbf{x})d\mathbf{x}$$
But what is $K$? It should respect some performance criteria expressed in functions of kernel $K$ and its derivatives:
## Good detection (High specificity)
> Low probability of [[Confusion Matrix and ROC|false alarms]] => maximize Signal-Noise Ratio:

$$\Sigma(K)= \frac{\rho \int K(x)dx}{n_{0} \left( \int K(x)^2dx \right)^{1/2}}$$
## Good localization (High accuracy)
> The detected edge points must be close to the real ones => maximize inverse standard deviation of expected edge location (Derivative-Derivative Noise Ratio):

$$\Lambda(K') = \frac{\rho|K'(0)|}{n_{0} \left( \int K'(x)^2dx \right)^{1/2}}$$
## Single response at edge points (No ambiguity)
> Filter response at edge points must be unique => minimize mean distance between ZC of filter response:

$$\xi(K',K'')=2\pi\left( \frac{\int K'(x)^2dx}{\int K''(x)^2dx} \right)^{1/2}$$
# Performance optimization
This is a constrained optimization problem over the kernel space:
- Maximize $\Sigma \Lambda$ while keeping $\xi$ at minimum.
- A closed-form expression for the optimal kernel $K$ is derived using variational optimization techniques such as FIR or IIR.

## FIR
Thus, an optimal FIR filter is:
$$K(x)=\exp(\alpha|x|)(a_{1}\sin(\omega x) + a_{2}\cos(\omega x)) + \exp(-\alpha|x|)(a_{3}\sin(\omega x) + a_{4}\cos(\omega x))$$

This has 6 hyperparameters and can be approximated using the Gaussian 1st derivative kernel:
$$K(x)=-\frac{x}{\sigma^2}\exp\left( -\frac{x^2}{2\sigma^2} \right)$$
With performance of $\Sigma \Lambda=0.92$, But has no recursive implementation.
## IIR
An optimal IIR filter is:
$$K(x)=\frac{a}{\omega}\exp(-\alpha|x|)\sin(\omega x)$$
Performance assessment:
- $\Sigma=\sqrt{ 2\alpha/(\alpha^2+\omega^2) }$
- $\Lambda=\sqrt{ 2\alpha }$
- $\Sigma \Lambda$
- $\xi=\sqrt{ (\alpha^2+\omega^2)/(5\alpha^2+\omega^2) }$

Assume $\alpha=m\omega$, optimal kernel is obtained when $m\to \infty$.
# Optimal 1-D derivation filter kernel
Exact solution of the IIR yields a One-parameter ($\alpha$ which controls smoothing / level of detail, $\alpha$ increases = LoD increases) kernel (1st order Canny-Deriche filter):
$$D_{x}(x)=K_{1}x\exp(-\alpha|x|)$$
IIR Filters can be implemented recursively via 2nd order recursive scheme:
![[Canny-Diriche Recursive Scheme.png]]
These schemes work for multi-dimensional as well as they are separable.

To get the smoothing kernel, we can integrate the above:
$$S(x)=K_{0}(1+\alpha|x|)\exp(-\alpha|x|)$$
Likewise, higher orders are obtained by differentiation, for example, 2nd order:
$$D_{xx}(x)=K_{2}(1-\alpha|x|)\exp(-\alpha|x|)$$
These can be implemented recursively also:
![[Canny-Diriche Recursive Scheme for n-th Order.png]]
# Canny-Diriche image filters
Built by tensor product of Canny-Diriche kernels (differentiation) and smoothing filters in the other orthogonal direction:
- 2D:
	- $L_{x}\to D_{x}S_{y}L$.
	- $L_{x}\to S_{x}D_{y}L$.
	- $L_{x}\to D_{xx}S_{y}L$.
	- $L_{x}\to D_{x}D_{y}L$.
- 3D:
	- $L_{x}\to D_{x}S_{y}S_{z}L$.
	- $L_{y}\to S_{x}D_{y}S_{z}$
	- $L_{xx}\to D_{xx}S_{y}S_{z}L$
	- $L_{xy}\to D_{x}D_{y}S_{z}L$
These filters can be applied separately, i.e. 1 pass for the $D_{x}$ in the $x$ direction then another for the $S_y$ in the $y$ direction.
# Shen-Castan filtering
Using quasi-optimal 1D derivative filter:
$$D_{x}(x)=K_{1}\exp(-\alpha|x|)$$
Basically same performance and properties.