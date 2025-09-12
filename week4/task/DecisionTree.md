# Decision Trees

- Decision Trees are a type of supervised machine learning algorithm used for classification and regression tasks
- They work by asking a series of yes/no questions about the features of the data, splitting the data into branches, and making predictions at the leaves

## Main Idea

- The goal is to split the data into groups that are as pure as possible (i.e., each group contains mostly one class)
- At each step, the tree chooses the best question to split the data, aiming to maximize the reduction in impurity

## Step 1: Measuring Impurity

Before we can find the best splits, we need a way to calculate impurity

### Gini Impurity

- Formula: Gini = 1 - sum(pi^2)
- Where pi is the probability of each class
- getting 0 means that it is pure

## Step 2: Finding the Best Split

Now we need to find the split that gives us the lowest weighted Gini impurity

### How Splitting Works

- For each possible split, we calculate the weighted average Gini impurity of the resulting branches
- We want the split that gives us the lowest weighted Gini impurity
- Lower weighted Gini means better split

### Example: Splitting Process

Let's say we have this data about cats and dogs:

- Total: 100 animals (60 cats, 40 dogs)

**Trying split: "Weight > 5kg"**

- Left branch: 70 animals (55 cats, 15 dogs)
- Right branch: 30 animals (5 cats, 25 dogs)

**Calculate Gini for each branch:**

- Left Gini = 1 - (55/70)^2 - (15/70)^2 = 1 - 0.617 - 0.046 = 0.337
- Right Gini = 1 - (5/30)^2 - (25/30)^2 = 1 - 0.028 - 0.694 = 0.278

**Calculate Weighted Average Gini:**

- Weighted Gini = (70/100) \* 0.337 + (30/100) \* 0.278 = 0.236 + 0.083 = 0.319

We repeat this process for all possible splits and choose the one with the lowest weighted Gini impurity

## Step 3: Building the Tree

1. Start with all data at the root node
2. Calculate the Gini impurity of the current node
3. Try all possible splits for all features
4. Choose the split with the lowest weighted Gini impurity
5. Create two child nodes and divide the data
6. Repeat steps 2-5 for each child node
7. Stop when stopping criteria are met

### Stopping Criteria:

- Pure node: All samples belong to the same class (Gini = 0)
- Maximum depth: Tree has reached max_depth levels
- No improvement: No split reduces the Gini impurity enough

## Step 4: Making Predictions

- To classify a new sample, start at the root and follow the branches based on the sample's feature values.
- When you reach a leaf the prediction is the majority class of samples in that leaf

## Example

- Suppose we want to classify animals as "cat" or "dog" based on features like weight and ear shape.
- The tree might first ask: "Is weight > 10kg?"
  - If yes, go to the right branch (likely a dog)
  - If no, go to the left branch (could be a cat)
- Next, it might ask: "Are ears pointy?"
  - If yes, go to one branch
  - If no, go to another
- Continue until reaching a leaf node with a prediction.

## Overfitting

- Decision Trees can easily overfit the training data, especially if allowed to grow deep.
- Pruning: Cutting back branches that do not improve performance on validation data.
- pruning ways:

  - Limiting tree depth (max_depth)
  - Requiring a minimum number of samples to split (min_samples_split)
  - Removing branches with little information gain

- max_depth: Maximum depth of the tree
- min_samples_split: Minimum samples required to split a node
- min_samples_leaf: Minimum samples required at a leaf node

## Advantages

- Easy to understand and interpret (can visualize the tree)
- Handles both numerical and categorical data
- Can capture non-linear relationships

## Disadvantages

- Can easily overfit (especially with deep trees)
- Unstable: small changes in data can lead to very different trees

## Sources

- StatQuest YouTube channel
- GeeksforGeeks.org
