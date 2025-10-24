Images with objects / background with clearly distinct average intensity gives Bimodal [[Image Histogram]] (2 modes) => easily separable using [[Color-based Image Segmentation|Thresholding]].
![[Bimodal Histogram.png|500]]
# Statistical approach
Let background (object) pixels be distributed according to a random variable $X_{b}$ ($X_{o}$) with density $p_{b}$ ($p_{o}$). We have [[Bayes Classifier]]:
$$P(\lambda|X_{o})p_{o}>P(\lambda|X_{b})p_{b} \implies \lambda\in\text{Object, otherwise, Background}$$
[[Bayes Classifier|Conditional probabilities]] are estimated using a prior model fitted on the histogram: For each mode, a Gaussian model is fitted => *Gaussian mixture model*:
![[Gaussian Mixture Model|500]]
This approach readily extends to multiple objects.
## Robust nonparametric (not a specific PDF) density estimation
Probability density estimation is hard.
### Empirical (data based) estimator (histogram)
$$
p^L(\lambda)\approx \frac{1}{|\Omega|}\underbrace{\int_{\Omega}\delta(\lambda-L(x))dx}_{H_{L}(\lambda)}
$$
But this method is non-smooth.
### Kernel estimator
Smoothed, normalized histogram.
$$
p^L(\lambda)\approx \frac{1}{|\Omega|}\int_{\Omega}K_{\sigma}(\lambda-L(x))dx
$$
Where $K_{\sigma}$ is the kernel which must be positive, symmetric, decreasing, and unit mass (integrate to 1) (usually Gaussian with fixed bandwidth $\sigma$ correspond to Parzen estimator).