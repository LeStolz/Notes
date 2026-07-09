2026-01-07 19:08

#Statistics 

> Matrix of TP, FP, TN, FN To measure success rate.

$$
\text{Recall} = \frac{TP}{TP + FN}\quad \nearrow \text{ when } FN\ \searrow
$$
$$
\text{Precision} = \frac{TP}{TP + FP}\quad \nearrow \text{ when } FP\ \searrow
$$
$$
\text{Specificity} = \frac{TN}{TN + FP}\quad \nearrow \text{ when } FP\ \searrow
$$
$$
\text{NPV} = \frac{TN}{TN + FN}\quad \nearrow \text{ when } FN\ \searrow
$$
# Good
For both detection and rejection:
$$
\text{ACC} = \frac{TP + TN}{TP+TN+FP+FN}
$$
For detection:
$$
F = 2 \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}} 
$$
# ROC
ROC is plot of $TPR$ (y-axis) vs $FPR$ (x-axis) *where each point corresponds to a threshold value*. The area under the curve is the probability of $TP$ and is used to measure how good a classifier is.