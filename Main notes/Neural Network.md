2026-07-07 16:10

#Machine-Learning 

![[Neural Network.excalidraw]]
# Network architecture
The idea is that each layer (and neuron) uses features to predict the probability of a higher level concept which is then used for even higher level concept.

Each neuron is a [[Supervised Learning|logistic regression model]] $a^{[i]}_{j}=g(a^{[i-1]}\theta^{[i]}_{j}+b^{[i]}_{j})$ with different [[Activation Functions]] $g$ depending on what we want to predict.

A typical choice is to have the numbers of neurons in layers decrease left to right.
## Types of layers
- Dense: a neuron is connected to all outputs of the previous layer.
- [[Convolution]]: a neuron is connected to a region of outputs of the previous layer => Faster, less overfitting.
# Forward propagation
Predict by computing layers by layers left to right to get to the output.
$$
a^{[i]}=g(a^{[i-1]}\theta^{[i]}+b^{[i]})
$$
# Back propagation
To learn by optimizing a cost function for classification or regression using [[Gradient Descent]] which requires calculating the derivatives of $J$ with respect to all parameters. To do so, we apply the chain rule from right to left.