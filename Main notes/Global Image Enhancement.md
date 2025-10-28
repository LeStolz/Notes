2025-10-27 15:38

#Computer-Vision 

# Point-based image histogram transformation
Transform $T(L)(x)=f(L(x))$ acts on image $L$ with value at pixel $x\in \Omega$ depending on luminance $L(x)$, thus, luminance remapping. Efficiently computed using LUT (Look-Up Tables): $LUT(i)=f(i)\ \forall\ i \in \Lambda$.

Quantification: $T(L)(x)=(int)[f(L(x))+0.5]$
Clipping: $T(L)(x)=max[min[f(L(x)),2^b-1],0]$
## Linear transformation
$$T(L)(x)=\alpha L(x)+\beta$$
- $\alpha<1$: Contraction (windowing), used in medical imaging for visualization (16-bit data to 12-bit range to 8-bit display).
- $\alpha>1$: Expansion, global contrast enhancement.
### Stretching to full range
$$T_{S}(L)(x) = \frac{2^b-1}{max(L)-min(L)}[L(x)-min(L)]$$The magnitude of enhancement depends on the initial intensity range. *Does not work for wide histograms*.
## Non-linear
### Log stretching
$$
T_{LS}(L)(x)=T_{S}(Log(1+L))(x)
$$
Contrast enhancement of dark structures. Used for wide histogram images. *But can cause artifacts*.
## Information-theoretic
[[Entropy]] = Information and [[PDF|Uniform distributions]] maximize [[Entropy]]. Thus, we can find a transformation which yield approximately flat-histogram (data more spread-out).

First, we compute the cumulated normalized histogram:
$$
\forall k \in \Lambda\quad\quad \overline{H}_{L}(k)=\frac{1}{|\Omega|}\sum_{1\leq i\leq k}H_{L}(i)
$$
Which is an estimate for cumulative distribution:
$$Pr(L(x)\leq k)\approx\overline{H}_{L}(k)$$
Define the transformation:
$$T_{U}(L)(x)=\overline{H}_{L}(L(x))$$
And since:
$$
\begin{align}
\overline{H}_{T_{U}(L)}(k)=& Pr(T_{U}(L)(x)\leq k) \\
=& Pr(\overline{H}_L(L)(k)\leq k) \\
=& Pr(L(k)\leq \overline{H}_L^{-1}(k)) \\
=& \overline{H}_L(\overline{H}_L^{-1}(k))=k \\
\end{align}
$$
The cumulated histogram is linear, the histogram itself is approximately uniform.
However, since the values of $T_{U}(L)(x)$ ranges from 0 to 1, we should stretch it to be from 0 to $2^b-1$:
$$
T_{EQ}(L)(x)=T_{S}(T_{U}(L))(x)
$$
This is the *histogram equalization*, which enhance the image (by spreading out its luminances) contrast *but can still have artifacts*.
### Generalization to arbitrarily shaped histogram
Instead of uniform, we want arbitrarily shaped histogram. Let $H_{ref}$ be a reference histogram built on image $L_{ref}$ and assume that $\overline H_{ref}$ is invertible, we define the transform as:
$$T_{Sp}(L)(x) = T_{ref}(L)(x)=\overline H^{-1}_{ref}(\overline H_{L}(L(x)))$$
Then $\overline H_{T_{ref}(L)}=\overline H_{ref}$, proof:
$$
\begin{align}
\overline H_{T_{ref}(L)}(k)=& Pr(\overline H^{-1}_{ref}(\overline H_{L}(L(x)))\leq k) \\
=& Pr(L(x)\leq \overline H^{-1}_{L}(\overline H_{ref}(k))) \\
=& \overline H_{L} \overline H^{-1}_{L}(\overline H_{ref}(k)) \\
=& \overline H_{ref}(k)
\end{align}
$$
In practice, $\overline H_{ref}$ is not usually strictly increasing so inverse is not guaranteed. We can ensure injectivity (monotonicity) by using:
$$
\overline H_{ref}^{-1}=min_{p}(p\ |\ \overline H_{ref}(p)\geq k)
$$