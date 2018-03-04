# Deep Learning
Ref from - http://sundog-education.com/deep-learning/

#### Gradient - Descent
technique to find Local Mininma optimized or given a certain set of parameters

#### autodiff
if the way of accelerating the process of finding optimized local minima

#### softmax 
converts the end result weights of individual neural network into a probability then at the end pick the class that has highest probability


## Perceptron
- A layer of LTU's.
- A perceptron can learn by reinforcing the weights that lead to correct behaviour during training

"cells that fire together wire together"

## Muilti Layer Perceptrons
Addition of hidden layers
This is a deep neural network

## Modern deep neural network
-  Replace step function with something better
- Apply softmax to the output
- Training using the gradient descent

### tensorflow playground
playground.tensorflow.org

### how do we train multi layer perceptron?
Back propogation or more specificaly Gradient descent using reverse mode auto-diff

###### For each training step
- compute the output error
- compute how much each neuron in the previous hidden layer contributed
- Back propogate that error in a reverse pass
- tweak weights to reduce the error using gradient descent

### Activation functions
- Step functions (dont work with gradient descent)
- Logistic function
- Hyperbolic tangent function
- exponential linear unit ELU
- Rectified Linear unit ReLU = Leaky ReLU / Noisy ReLU

some times ELU can be faster

### Other optimization functions than Gradient Descent
- Momentum Optimization - So it slows down as things starts to flatten, and speeds up as the slope is steep 
- Nesterov Accelerated Gradient - small tweak on Momentum Optimization, computes momentum based on the gradient slightly ahead of you, not where you are 
- RMS prop - Adaptive Learning Rate to help point towards the minimum
- Adam - Adaptive moment estimation - Momentum + RMS prop combined - Popular choice today easy to use.

## Avoiding Overfitting
with thousands of weights over fitting is a problem
- Early stopping
- Regularization terms added to cost function during training
- Drop out 50% of neurons randomly at each step , works surprisingly, forces your model to spread out its learning

## Tuning your Topology
- Trial & Error in one way
- more layers can yield faster learning
- use more layers & neurons , dont care as you do early stopping
- use model zoos





