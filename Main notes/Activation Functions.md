2026-07-08 08:43

#Machine-Learning 

> To make the model non-linear.

# For the output layer,
If binary classification then use sigmoid.
If multi classification then use softmax.
If positive value then use $ReLU(z)=\max(0,z)$.
If pos/neg value then use linear $g(z)=z$.
# For other layers, $ReLU$
Better than linear because $linear(linear)=linear$.
Better than sigmoid because it's less flat => [[Gradient Descent]] faster.

$ReLU$ allows us to turn function off at certain segments allowing modeling of any curve from assembling lines.
![[ReLU.png]]