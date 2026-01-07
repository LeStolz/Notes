2026-01-01 11:50

#Computer-Vision  #Image-Recognition 

# Features
Color: average (RGB, HSV, HMMD, YCrCb), [[Image Histogram|histogram]], autocorrelogram (Given a pixel of a certain color, how likely is it to find another pixel of the same color at a specific distance?).
Texture: First order derivatives, co-occurence matrix (how often pairs of gray levels occur at a given spatial relationship in an image), Daubeshy transformation (to analyze data at multiple scales (subbands) we can then calculate their energies), GIST (summarize overall layout and texture of scene).
Form: Gradient norm matrix, [[Form Descriptions|Hu's Moments]].
# Feature Selection
Not all features are relevant, so we:
- Filter (fast, not relevant): [[Principal Component Analysis (PCA)]].
- Enveloppes (keep the overall shape of data instead of all of raw data, better recognition rate but slower): [[Genetic Algorithms (GA)]].
- > Adaptive Feature Selection (AFS) > Fast, can adapt to the DB, and can select best features with 2 steps: Learn with [[Support Vector Machine (SVM)]] then use [[Linear Discrimination Analysis]]:
	- Each image set $X_{i}$ gives feature set $M_{i}$ then use SVM to learn and find the recognition rate which is the performance of this set $Per(M_{i})$.
	- Choose the best ones which creates a subspace which maximize class separability.
# [[Machine Learning|Learning]]
Run PCA first.
## Hierarchical Multi-Model Classification Method
Since database is heterogeneous, using a single model based on some features is not good enough, so we use many models based on different features => non-linear, flexible combinaison of features. The test images are then tested iteratively through a hierarchy of models, ordered by their increasing training performance so the prediction is refined progressively. The method can also provide dynamic feature weighting based on the query image.

If 2 consecutive hierarchical level classify the image to be the same class, we are good, if there is conflict, we use [[Nearest Cluster Center (NCC)]] to classify the query image Iq in the feature space Fm, through the two evaluated classes Ci and Cj. We can also use SLA.

This classification process is called generalization, affected by the ordering of the models: increasing (normal), decreasing, max-models (class chosen by most models).

Advantages:
- Uses multiple models, combining their strengths for better accuracy.
- Works well for content-based image recognition in heterogeneous databases.
- Progressive (“ascending”) recognition, improving results step by step.
- Very fast because it only uses the most relevant features.
Limitations:
- Not suitable for single-model systems.
- Struggles when images have a very large feature description based on many features.