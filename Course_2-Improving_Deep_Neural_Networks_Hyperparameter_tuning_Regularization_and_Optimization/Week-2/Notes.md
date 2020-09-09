# Optimization Algorithms

## Mini-Batch Gradient Descent

Split training data into mini-batches of mini-training datasets. Allows you to run gradient descent on large very large training data sets.

--> Most people will use this when they have a large trining dataset adn allow you to train you model much faster.

### Overall Process

1. Loop through the mini-batches
    - Forward-prop to compute the cost function
    - Back-prop to compute the gradients
    - Update the weights

--> This is one pass through or 1 epoch of training (pass through the training set)

Batch gradient descent:
- The cost will go down with every iteration

Mini-batch gradient descent:
- The cost will go up or down with every iteration, but will still trend downwards overall

### How to choose the size fo the mini-batch
- If mini-batch size = m : Batch gradient descent
- If mini-batch size = 1 : Stochastic gradient descent, every example is its own mini-batch.

--> In practice, the mini-batch size will be between m and 1.

- If small training set, then use Batch gradient descent (less than 2,000)
- If big training set, use a mini-batch size of 64, 128, 256, 512 (or a power of 2).
- Make sure mini-batch fits in the CPU/GPU memory

--> The mini-batch size is a hyperparameter that can also be optimized

## Exponentially Weighted (moving) Averages

- The higher the beta, the lower amount of number of data points that it's averaged over.
- Takes very little memory to perform

### Bias Correction

- Set Vt = Vt/(1-B^t)
- Can help you get a better estimate early on

## Gradient Descent with Momentum

- Compute an exponentially weighted average of your gradients, and then use that gradient to update your weights instead.
- This smooths out the oscillations in the vertical direction and will tend to average out to something closer to 0.
- Will typically not use bias correction w/gradient descent with momentum.
- Very popular --> most used

## RMSProp (Root-mean squared)

- Squaring the derivatives and taking the square root when computing W and b (Sdw and Sdb)
- It has the effects of dampening out the oscillations and speed up the learning algorithm.

## Adam Optimization Algorithm

- Typically performed with mini-batch gradient descent
- Perform the momentum update hyperparameter (V)
- Perform the RMSProp update hyperparameter (S)
- Perform bias correction (both V and S)
- Perform the update to W

- Hyper-parameters used:
  - alpha: needs to be tuned
  - beta 1 : 0.9
  - beta 2: 0.999
  - epsilon : 10^-8

## Learning Rate Decay

- Slowly reducing your learning rate over time
- During the initial steps of learning, you can take bigger steps, but as you approach convergence, you take smaller steps.

## The problem of local optima

- Saddle points happen to have a derivative of 0.
- Unlikely to get stuck in a bad local optima
- Plateaus can make learning slow and these optimization algorithms can help speed them up
