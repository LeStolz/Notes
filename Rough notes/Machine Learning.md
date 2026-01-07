2026-01-01 14:35

#Machine-Learning  #Image-Recognition 
# Unsupervised
Grouping, finding structures
1 algorithm: Find nearest 2 points, replace them with their average, continue.
![[Unsupervised Grouping]]
# Reinforcement
Agent -action-> environment ; environment -reward-> agent.
Balance between exploring new solution and using memory.
1 algorithm: Echelon
# Supervised
Requires prior knowledge of the meaning of each class. # of class is fixed. Labeled, predict target $y$ from features $x$. 2 types of models to solve this:
- Intrinsic (Nearest Class Centroid): Create a model which best characterize each class. Classification is based on measuring similarity to each class.
- Discriminative ([[Support Vector Machine (SVM)|SVM]]): Find decision boundaries which optimally separate classes. Classification is based on which class region the input is in.
## Classification (discrete)
## Regression (continuous)