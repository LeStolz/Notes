2025-10-12 09:11

#Computer-Vision

Denoising is often used in the preprocessing step, before any [[Image Segmentation & Classification|segmentation]] *or* can be integrated into segmentation => robust segmentation
# Denoising
- Deblurring / (Contrast) [[Global Image Enhancement]]. ex: histogram equalization
- Photometric calibration: Find relationship between intensity recorded by a camera and a light source in the real world, making measurements better.
- Statistics & [[Machine Learning]] are used for modeling & dealing with noise:
  *Hard assignment* to *disjoint intervals* (i.e. dividing the intensity range $[0\dots255]$ into $[0\dots 50], [51\dots 150],\dots$ to represent an object) is replaced by *probabilistic/statistical assignment* to *overlapping clusters*
  => *Intensity mixtures*: Intensities, instead of "either/or" of hard assignment, can be in many clusters at the same time, better capture real world.
# Noise models
## Additive $L=L_{0}+n$
Optical, thermal imaging, quantization noise: IR.
## Multiplicative $L=L_{0}n$
Speckle noise (interferometric imaging): US, OCT, SAR, PC microscopy, PC X-Ray.
## Complex models
Shot noise (photon counting imaging), Impulse noise (salt-and-pepper): X-Ray, TEP/SPECT.
# Noise distribution
Gaussian: Optical, thermal: IR.
Heavy tailed (Laplace, negative exponential, $\alpha$-stable): Speckle (same as noise model)
Poisson: Shot noise (same as noise model)
Rician / Rayleigh: Thermal noise: MRI.
Uniform: Quantization noise: IR.
Impulse: Salt-and-pepper noise.
# Modeling issues
A consistent noise model for a sensor/imaging chain is a key point:
- For methodology design, realistic noise priors (noise distribution model) leads to optimal denoising & robust image analysis estimator.
- For performance assessment, use noise generators for simulated tests with controlled SNR.