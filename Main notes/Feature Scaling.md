2026-07-06 23:28

#Machine-Learning 

> Features with larger *ranges and values* affect calculation more than features with smaller ones, so we must scale them to similar *ranges and values*.

# Mean normalization
If feature $\mathbf{X}_{i}$ is in range $[l_{i},r_{i}]$ with mean $\mu_{i}$, we normalize its data by applying:
$$
\mathbf{X}_{i}^{(j)}=\frac{\mathbf{X}_{i}^{(j)}-\mu_{i}}{r_{i}-l_{i}}
$$
# Z-score normalization
If we have std $\sigma_{i}$, we normalize by:
$$
\mathbf{X}_{i}^{(j)}=\frac{\mathbf{X}_{i}^{(j)}-\mu_{i}}{\sigma_{i}}
$$