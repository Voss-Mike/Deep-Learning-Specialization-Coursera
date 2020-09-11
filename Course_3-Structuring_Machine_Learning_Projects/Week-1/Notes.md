# Introduction to ML Strategy

## Orthogonalization

Each nob (node) only does one thing, having one control for each thing that you what change/tune

Chain of assumptions in ML:
1. Fit training set well on cost function (similar to human level)
    - Bigger Network
    - Adam
2. Fit dev set well on cost function
    - Regularization
    - Bigger train set
3. FIt test set well on cost function
    - Bigger test set
4. Performs well in real world
    - Change dev set or cost function

ML Nobs (examples used above):
- Bigger network/training set/dev set
- Different optimization technique (regularization)
- Change the cost function

# Setting Up Your Goal

## Using a Single Number Evaluation Metric

There is often a trade-off between precision and recall. The problem with these metrics is that is one classifier has a better precision and the othe has a better recall, it'a hard to choose which one is best.
- Instead, use one metric that combines both: *F1 Score*
- Consider the *F1 Score* as the "Average" of precision and recall
- It speeds up the iterative process of choosing a model/classifier

*You can also compute the average for each class* 

## Satisfying and Optimizing Metric

Sometimes we care about accuracy and running time of a classifier. Again, you can combine these into one metric.
- Example: Maximize accuracy (optimize) subject to running time <= 100ms (satisfying)
- Example: Maximize accuracy (optimize) where false positive is <= 1.

## Train/Dev/Test Distributions

- Dev and Test sets should come from the same distribution

### Old way of Splitting Data

- 70/30 split (train/test)
- 60/20/20 (train/dev/test)

### Modern way with much larger training sets

- With large data sets, you can use a 98/1/1 (train/dev/test)
- Set your test to be big enough to give high confidence in the overall performance of your system. 
- Dev sets are used for tuning the model/classifier
- Test sets are used for evaluating the final model/classifier


# Comparing to Human Level Performance

Bayes optimal error - best possible error
- As long as your performance is worse that a human, there are ways to improve the algorithm. 
    - You can have people look at the examples and classify them. 
    - Why did a human get this right?
    - Update/understand bias and variance

## Avoidable Bias

Avoidable Bias: There is some bias that you can not get below. Human Level error as a proxy for Bayes error (if we can perform as well as a human then we are good).

- Bias reduction tactics can help reduce the variance between the human and model error rate
- Variance reduction techniques can help differences in the train and dev error. 

In Summary:
- Avoidable bias: DIfference in the human-level error and training error
- Variance: Difference in the training error and dev error

## Surpassing human-level performance

Problems where ML significantly surpasses human-level performance:
- Online advertising
- Product recommendations
- Logistics (predicting transit time)
- Loan approvals

Essentially, in areas where there is more data than a human can possible look at, it is possible to be better than a human.

## Improving your model performance

- Reducing avoidable bias: 
    - Train bigger model
    - Train longer/better optimization algorithms (adam, rmsprop)
    - NN architecture
- Reducing variance:
    - More data
    - Regularization


# Quiz

1. True
2. 98%, 9 sec, 9MB
3. Accuracy is an optimizing metric, running time and memory are satisfying metrics
4. 9.5 m, 250,000, 250,000
5. False (dev and test must have the same distributino)
6. This would cause the dev and test set distributions to be different. 
7. No, because there is insufficient infromation to tell.
8. 0.3%
9. A learning algo performance can be better than human, but it can't be better than Bayes error.
10. Train a bigger model, decreasing regularization
11. You have overfit the dev set
12. Harder to measure avoidable bias, Bayes is less than 0.05
13. Rethink the apporiate metric for the task.
14. Add the images to the train,dev,test
15.100,000,000, faster computers

















