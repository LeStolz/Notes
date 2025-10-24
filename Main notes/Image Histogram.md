2025-10-12 10:31

#Computer-Vision

The histogram $H_{L}(\lambda)$ accounts for luminance ($\lambda$) distribution (statistical properties in general) over $\Omega$:
$$H_{L}(\lambda)=\text{number of } \{x\in \Omega\ |\ L(x)=\lambda\}$$

Histogram can be binned (put into bins) (quantized):
$$H_{L}(\lambda)=\text{number of } \{x\in \Omega\ |\ L(x)\in B_{\lambda}\}$$
=> Easier to process, detect peaks (because less noise). Optimal (uniform) bin size selection rules: Sturges | Scott | Freedman-Diaconis Knuth | Wand.

This definition can easily be generalized to: 
- Multichannel/-view images: Multidimensional histogram, co-occurence matrix.
- Arbitrary domains: A single region, pixel neighborhood => regional/local histogram.
- Arbitrary (quantified features): local orientation, motion => feature histogram.

Empirical density estimator (probability):
$$p^L(\lambda)\approx \frac{1}{|\Omega|}H_{L}(\lambda)$$
# Luminance statistics 
## Central Moments
The shape/distribution of data around its mean.
$$
\text{Mean: } \overline{L}=\sum p^L(\lambda)\lambda
$$
$$
\text{Variance: } \sigma^2=\sum (\lambda-\overline{L})^2p^L(\lambda)
$$
$$
\text{Skewness: } L_{S}=\underbrace{\frac{1}{\sigma^3}}_{\text{Normalize result}} \sum \underbrace{(\lambda-\overline{L})^3}_{\text{Exaggerate outliers}} \underbrace{p^L(\lambda)}_{\text{Count}}
$$
$$
\text{Kurtosis (tailness, peakness): } L_{K}=\underbrace{\frac{1}{\sigma^4}}_{\text{Normalize result}} \sum \underbrace{(\lambda-\overline{L})^4}_{\text{Exaggerate outliers}} \underbrace{p^L(\lambda)}_{\text{Count}}-\underbrace{3}_{\text{Shift so normal dist. is 0}}
$$
![[Skewness and Kurtosis|500]]
## Texture indices
$$
\text{Entropy (chaosness): }H(L)=-\sum p^L(\lambda)\log_{2}p^L(\lambda)
$$
$$
\text{Energy (orderliness): }E(L)=\sum p^L(\lambda)^2
$$
# Qualitative properties
- Skewed / narrow = low contrast: Skewed right = overexposed.
- $H_{L}$ contains no spatial info, just the colors.