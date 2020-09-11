# Hyperparameter Tuning

## Common Hyperparameters to Tune
Alpha - most important hyperparameter to tune
The number of hidden units
The number of layers
Learning rate decay
Mini-batch size

## Tuning Process

1. Try random values: don't use a grid
    - It's difficult to know which hyperparameters are the most important to tune.
2. Coarse to fine sampling scheme
    - Zoom into a smaller region and sample more densely 

Choosing random variables might not be the best way and instead you'll want to use grid search.

Search for hyperparameters at the logarithmic scale rather than a linear scale.
    - log scale of a and then log scale of b

Example: Sampling the hyperparameter beta

beta = 0.9 ... 0.999
    - It doesn't make sense to sample using a linear scale (instead use a log)
1 - beta = 10^r
beta = 1 - 10^r

## Hyperparameter Tuning in Practice

    - Babysitting one model
        - Every day you look at it and adjust the learning rate/hyperparameters
    - Training many models in parallel
        - Pick the one that works the best

# Batch Normalization

- Can we normalize any layer so that we can train the weights and bias faster.
- Normalizes Z before

## Implementing Batch Normalization

- Given some intermediate values in NN (z(1)) 
- It makes your NN much more robust
- Normalizes the mean and variances of some of the hidden values Z
   - Use parameters gamma and beta to ensure hidden values have standardized mean and variances

- Set bias variable to 0 since it will be subtracted out anyway when subtracting the mean
    - Because batch norm zeros out the value of the bias, set it to 0 and replace it with beta

- "Covariant Shift" --> if the ground truth function changes, you will need to retrain your model.
    - Batch norm reduces the amount of the distribution of Z (the mean and variance will remain the same)
- Each mini-batch is scaled by the mean/variance computed on just that mini-batch
- This adds some noise to the values Z within that mini-batch. So similar to dropout, it adds some noise to each hidden layer's activations
- This has a slight regularization effect.

# Softmax Regression

A generalization of logistic regression to C classes where C is the number of classes - good for classification where you have multiple classes.
    - Output is the probability for each class that all add up to 1.
    - Takes in a vector of inputs and outputs a vector (different from relu or sigmoid function)

# Deep Learning Frameworks - TensorFlow
1. False
2. False
3. The number of hyperparameters
4. beta = r*.9 +0.09
5. False
6. z[l]
7. To avoid division by 0