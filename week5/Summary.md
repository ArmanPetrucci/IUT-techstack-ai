# Linear Regression

- linear regression is a regression model which means that it solves regression problems
- Regression problem: a problem in which we try to predict a number so the target variable (y) is a number
- it assumes the relation between the target (y) and features (X) is linear and creates a function like this:
- f(x1,...,xn) = w1 \* x1 + w2 \* x2 + ... + wn \* xn + b
- each xi is a feature and wi is the corresponding weight that linear regression assumes.
- to find the best line that fits our data we must find the best (w1,w2,...,wn,b)
- to do that we need a metric to compare each line (also called loss function)
- we use MSE (Mean Squared Error) which we define:
- J(w1,...,wn,b) = sum((y(i) - f(x1(i),x2(i),...,xn(i)))^2) / n for i = 1 to n where n is the number of rows in the training set
- now that we have a loss function we must find a way to minimize the loss and to do that we can use gradient descent

## Gradient Descent

- in the gradient descent algorithm we first initialize random values to weights and the bias (b)
- then at each step we update weights and the bias simultaneously using this formula:
- wi := wi - gradient(J(wi)) \* learning_rate
- b := b - gradient(J(b)) \* learning_rate
- we continue until convergence which means that we have reached a local minimum
- when we use linear regression the cost function is always a convex function which means that there is only one global minimum which is also the only local minimum
- therefore in linear regression, using gradient descent guarantees that we get to the global minimum

### Value of the learning rate

- according to the formula if learning rate is too small then it will cause the algorithm to run very slowly because it will need more updates to reach the global minimum.
- if the learning rate is too large it might overshoot meaning that it can totally miss the global minimum and never reach it.

### Feature scaling

- when features have very different ranges gradient descent can have problems.
- features with larger values will dominate the cost function and cause the algorithm to take longer to converge.
- to fix this we scale all features to similar ranges usually between 0 and 1 or with mean 0 and standard deviation 1.
- this makes gradient descent converge faster to the global minimum.

---

# Evaluation Metrics

## Confusion matrices

- after training any model we need to evaluate how well it performs
- confusion matrix is a matrix that shows how good a classifier does.
- it does that by comparing the predicted result with the actual label.
- there are four categories in this matrix, namely: TP (True Positive), FP (False Positive), TN (True Negative), FN (False Negative)
- TP means positive label was predicted as positive
- FP means negative label was predicted as positive
- TN means negative label was predicted as negative
- FN means positive label was predicted as negative

## Precision and recall

- two of the most used metrics in ML
- precision focuses on the quality of the model's positive predictions
- precision = TP / (TP + FP)
- recall measures how good the model is at predicting positives
- recall = TP / (TP + FN)

## F1 Score

- F1 Score combines precision and recall into a single metric
- F1 Score = 2 \* precision \* recall / (precision + recall)
- it gives equal weight to both precision and recall

---

# Learning curve

- learning curve is a representation of the model performance on both training and validation sets
- the x-axis values are the training examples and the y-axis values are the scores of the model
- they help us understand if our model is learning properly
- they can be used to:

1. recognize overfitting or underfitting
2. help adjust parameters to converge faster
