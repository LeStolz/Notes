2026-07-08 14:14

#Machine-Learning 

> How to fix a bad model?

# Choose a model
# Evaluate the model
We can split data into 60% Training + 20% Cross validation + 20% Testing.
Then calculate the training and testing [[Supervised Learning|errors]] (no [[Generalization and Regularization|regularization]]); or count % misclassified.

If we choose our model based on $J_{test}$, it's kinda biased and the error is too optimistic.
Instead, pick the model based on the best $J_{cv}$.
## Learning curve
Iteration/Data vs. loss graphs to see a model's limitations.
![[Learning Curve|700x500]]
## Bias Variant trade offs
[[Neural Network]] don't have this, just regularize good!
## Error analysis
We can manually check misclassified items to see the problem.
## Skewed data
If a or some classes have very little data (rare), getting a small error isn't saying much, e.g. if a disease being positive is rare, you can just always predict negative and have a good error rate => check error rate for each class.
### [[Confusion Matrix and ROC]]
# Fix the model
High variance? [[Data Engineering|More data]], regularize, less feature, simplify model.
High bias? regularize, more feature, complexify model.