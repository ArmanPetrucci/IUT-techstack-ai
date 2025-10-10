# Model Complexity and Generalization

- in machine learning we want our models to perform well on new unseen data which is called generalization
- model complexity is the key factor that determines how well our model generalizes
- if model is too simple it cannot capture patterns in data (underfitting)
- if model is too complex it memorizes training data instead of learning patterns (overfitting)
- the goal is to find the right balance between bias and variance

## Underfitting

- underfitting happens when our model is too simple to capture the underlying patterns in data
- characteristics of underfitting:
- high bias: model makes strong assumptions and cannot learn complex patterns
- low variance: predictions are consistent but consistently wrong
- poor performance on both training and test sets
- to fix underfitting we can:
- increase model complexity (more layers, neurons, features)
- train for more epochs

## Overfitting

- overfitting happens when our model is too complex and memorizes training data instead of learning patterns
- characteristics of overfitting:
- low bias: model can learn complex patterns
- high variance: small changes in training data cause large changes in predictions
- good performance on training set but bad performance on test set
- to fix overfitting we can:
- reduce model complexity
- add regularization
- use dropout
- get more training data
- use early stopping

# Regularization

- regularization is a technique to prevent overfitting by adding penalty terms to the loss function
- it forces the model to keep weights small which reduces model complexity
- regularization helps the model generalize better to new data

## L1 Regularization

- L1 regularization adds penalty for the absolute values of weights
- penalty term = lambda \* sum(|wi|) where lambda is the regularization parameter
- L1 regularization tends to make some weights exactly zero
- this leads to feature selection as unimportant features get zero weights

## L2 Regularization

- L2 regularization adds penalty for the squared values of weights
- penalty term = lambda \* sum(wi^2) where lambda is the regularization parameter

# Dropout

- dropout is a regularization technique specifically designed for neural networks
- during training randomly sets some neurons to zero with probability p
- dropout is only used while training, not when making predictions
- reduces overfitting

## How Dropout Works

- during forward pass randomly select neurons to "drop out" (like bernoulli distribution)
- dropped neurons do not contribute to forward or backward pass
- when making predictions all neurons are active but outputs are scaled

# Hyperparameter Tuning

- hyperparameters are parameters that are not learned by the model but set before training
- examples include learning rate, batch size, number of epochs, regularization strength
- hyperparameter tuning means finding the optimal hyperparameters

## Common Hyperparameters

- learning rate: controls how fast the model learns
- batch size: number of samples processed together
- epochs: number of times model sees entire dataset
- regularization strength (lambda): controls amount of regularization
- dropout rate: fraction of neurons to drop during training
- network architecture: number of layers and neurons

## Tuning Strategies

- grid search: try all combinations of predefined hyperparameter values
- random search: randomly sample hyperparameter values

### Learning Rate

- if learning rate is too small convergence will be very slow
- if learning rate is too large model might overshoot optimal solution
- adaptive learning rate schedules can help (reducing the rate over time)

### Batch Size

- larger batch size: faster training per epoch, more stable gradients, needs more memory
- smaller batch size: slower training, noisier gradients
- typical batch sizes are powers of 2 because of architecture

## Early Stopping

- early stopping monitors validation performance during training
- stops training when validation performance stops improving
- prevents overfitting and saves computation time
- typically uses patience parameter (how many epochs to wait)
