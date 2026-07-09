2026-01-01 14:58

#Machine-Learning

> Draw a hyperplane which best separate classes (the hyperplane's distance to any point in any class is furthest away). If the problem is not linearly separable, SVM transform the data to a higher dimension.

This hyperplane:
$$
f_{\mathbf{w},\vec{b}}(\vec{x})=\mathbf{w}\vec{x}+\vec{b}=0
$$
In the 2 classes case, if the value $f_{\mathbf{w},\vec{b}}(\vec{x})$ is positive, class 1, else class -1.
If the data is not linearly separable, we perform a transformation on the data using a kernel function (measures similarity) which gives us the decision function:
$$
f(x)=\text{sign}\left( \sum_{i=1}^N y_{i}\alpha_{i}\text{Kernel}(x,x_{i})+b\right)
$$
Where $(x_{i},y_{i})$ are [[Model Development Cycle|training samples]] and the weight $\alpha_{i}$ learnt.
# Multiple classes
In the multiple class case, we can use one-vs-all strategy where we train $N$ binary SVM, each treating one class as positive and the rest negative. During testing, a datapoint is evaluated by all SVMs and assigned to the class with the highest response. This has high training complexity since each SVM is trained using all training samples.

The one-vs-one strategy trains $\frac{N(N-1)}{2}$ classifiers for each pair of classes. During testing, the classifier with max-wins is assigned to the datapoint. Shorter training time but longer classification time (because more classifiers).

We can do better by using a DAG decision graph: each binary classifier eliminates one of the 2 class compared. This clearly only run in $O(N)$. SVM-DAG have similar recognition rate to one-vs-one but faster.
# Which Kernel and parameters? Multi-Kernel!
Popular kernels:
- Polynomial: $(x.x'+ct)^u$.
- Sigmoidal: $\tanh(x.x'+\theta)$
- Laplacian: $e^{-{||x-x'||}/\sigma}$
- Gaussian (RBF): $e^{-{||x-x'||}^2/2\sigma^2}$

Use all of them: $$\text{Kernel}(x,x_{i})=\sum_{m}^M\beta_{m}\text{Kernel}_{m}(x,x_{i})$$
We need to find $\beta_{m}$ => Set it yourself or weight the kernel based on training rates sorted decreasing:
$$
\beta_{m}=2\frac{M-m+1}{M(M+1)}
$$
![[Kernel Weighting.png]]
Evaluated using execution time and recognition rate.
