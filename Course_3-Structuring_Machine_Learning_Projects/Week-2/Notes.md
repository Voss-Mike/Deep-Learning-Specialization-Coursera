# Error Analysis

Try to figure out what the best case is or the "ceiling" of the error rate. To do this, you should find a set of mislabeled examples, either in your dev set, of in your development set. And look at the mislabeled examples for false positives and false negatives and count up the number of errors that fall into different categories. During this process, your might be inspired to generate new categories of errors.

1. Cleaning up incorrectly labeled data
    - Apply same process to your dev and test sets to make sure they continue to come from the same distribution.
    - Consider examining examples your algorithm got right as well sa ones it got wrong.
    - Train and dev/test data may now come from slightly different distributions.

## Build Your First System Quickly, Then Iterate

- Use Bias/Variance analysis & error analysis to prioritize next steps.

# Mismatched training and dev/test set

How to handle training and testing on different distributions:
- Have training set all from the 1 source and have the dev/test sets all from the 2nd source.
- Do not combine the two together and split them both.
- Alternatively, you can split the data from source 1 evenly between the train and dev/test set.

## How does this impact the bias and variance?

- Use a training-dev set which has the same distribution as the training set, but is not used for training.
- Data mismatch: when the training-dev and dev error differ greatly.

Look at the following:
- Human level error vs training set error
    - Used for avoidable bias
- Training set error vs training-dev set error
    - Used for variance
- Training-dev error vs dev set error
    - Used for data mismatch
- Dev set error vs test set error
    - Degree of over-fitting

## Addressing Data Mismatch

- Carry out manual analysis to try to understand difference between training and dev/test sets.
- Make training data more similar or collect more dta similar to dev/test sets
    - Artificial data synthesis

# Learning From Multiple Tasks

## Transfer Learning

When does transfer learning make sense?
- When task A & B have the same input X. 
- You have a lot more data for Task A than Task B.
- Low level features from A could be helpful for learning B.

## Multi-Task Learning

Neural network architecture that aims to predict multiple tasks or items. For example:
1. Pedestrian
2. Car
3. Stop sign
4. Traffic Light

The resulting model is trying to identify if each of the above exists in each image. You could have trained a model for each one, but the results might not be the same. 

When does it make sense?
- If you are training on a set of tasks that could benefit from having shared lower-level features.
- Usually: Amount of data you have for each task is quite similar.
- Can train a big enough neural network to do well on all the tasks. 

# End-to-deep learning

Takes all stages of a complex pipeline and replace it with one neural network (speech recognition)

Example:
- audio --> feature --> phonemes --L> words --> transcript
- audio --------------------------------------> transcript

Pros:
- Let the data speak
- Less hand-designing of components needed

Cons:
- zMay need large amount of data
- Excludes potentially useful hand-designed components


