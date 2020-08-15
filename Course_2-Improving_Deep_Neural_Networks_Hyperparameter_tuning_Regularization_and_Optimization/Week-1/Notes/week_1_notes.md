# Week 1 Notes 

## Steps to Build a Neural Network

1. Initialize all parameters
2. Forward propagation -> Predictions
3. Cost Function
4. Backward propagation
    - Calculate the gradient of the loss function
    - Calculate the derivatives
5. Update the parameters using gradient descent
6. Predict

## Bias and Variance

### High Bias

- Under-fitting the data
- How to fix?
  - Create a bigger network
  - Train longer model
  - NN architecture search

### High Variance

- Over-fitting the data
  - If the train/dev data set errors differ significantly (train is better then the dev), then you have High Variance.
- How to fix?
  - More data
  - Regularization
  - NN architecture search

## Regularization

Regularization prevents over-fitting

### L1 and l2 regularization

- Most common
- L2 is also known as "weight decay" and will update the cost function
- L2 makes the model so that `Z` is a small value and the network becomes more linear.
What is L2-regularization actually doing?:

L2-regularization relies on the assumption that a model with small weights is simpler than a model
with large weights. Thus, by penalizing the square values of the weights in the cost function you
drive all the weights to smaller values. It becomes too costly for the cost to have large weights!
This leads to a smoother model in which the output changes more slowly as the input changes.

### What you should remember -- the implications of L2-regularization on

- The cost computation:
  - A regularization term is added to the cost
- The backpropagation function:
  - There are extra terms in the gradients with respect to weight matrices
  - Weights end up smaller ("weight decay"):
  - Weights are pushed to smaller values.

### Dropout Regularization

Randomly removes (drops out) units/nodes from layers

- Inverted Dropout
  - Set the `keep_prob` parameter: probability that a hidden unit/node is kept and will set each unit/node to a value of 1 or 0.

Why does drop-out work?

- Intention: Can't rely on any one feature, so we have to spread out the weights --> shrinks the weights
- `keep_prob` parameter can be different for each layer.
  - Can be scaled to the length of a layer
  - Can be done for some layers, but not others

Downside to drop-out: Cost function `J` is less defined.

Note:

A common mistake when using dropout is to use it both in training and testing. You should use dropout (randomly eliminate nodes) only in training.
Deep learning frameworks like tensorflow, PaddlePaddle, keras or caffe come with a dropout layer implementation. Don't stress - you will soon learn some of these frameworks.
What you should remember about dropout:

Dropout is a regularization technique. You only use dropout during training. Don't use dropout
(randomly eliminate nodes) during test time. Apply dropout both during forward and backward
propagation. During training time, divide each dropout layer by keep_prob to keep the same expected
value for the activations. For example, if keep_prob is 0.5, then we will on average shut down half
the nodes, so the output will be scaled by 0.5 since only the remaining half are contributing to
the solution. Dividing by 0.5 is equivalent to multiplying by 2. Hence, the output now has the same
expected value. You can check that this works even when keep_prob is other values than 0.5.

### Other Regularization Methods

1. Data Augmentation
    - Made additional "fake" data samples
2. Early Stopping
    - Stop training before the dev test error rises

## Normalizing Inputs

### Why Normalize

- If features have different scales, then the cost function might not converge, or it will take very long

### Common Approaches

1. Subtract Mean
2. Normalize Variance

## Vanishing/Exploding Gradients

The longer/deeper the network, the more likely this becomes an issue.

### Partial Solution

- Optimize weight initialization (larger n --> smaller weights)

## Gradient Checking

- Don't use in training --> only to debug
- If algorithm fails gradient checking, look at the components to try adn identify bugs
- Remember regularization
- It doesn't work with dropout
- Run at random initialization and perhaps again after some training

What you should remember from this notebook:

Gradient checking verifies closeness between the gradients from backpropagation and the numerical
approximation of the gradient (computed using forward propagation). Gradient checking is slow, so we
don't run it in every iteration of training. You would usually run it only to make sure your code is
correct, then turn it off and use backprop for the actual learning process.
