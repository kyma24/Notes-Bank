### Improving on Decision Trees
As learnt in the previous module, the main drawback of decision trees are that they have a tendency to overfit. We saw that we could improve their performance with pruning, but in this part we'll see a way of using decision trees to make a better model.

**Decision Trees** are very susceptible to random idiosyncrasies in the training dataset. We say that Decision Trees have high variance since if you randomly change the training dataset, you may end up with a very different looking tree.

One of the advantages of decision trees over a model like logistic regression is that they make no assumptions about how the data is structured. In logistic regression, we assume that we can draw a line to split the data. Sometimes the data isn't structured like that. A decision tree has the potential to get at the essence of the data no matter how it is structured.

**Random Forests** is a model built with multiple trees. The goal of this is to take advantage of decision trees while mitigating the variance issues.

note that a random forest is an example of an **ensemble** because it uses multiple machine learning models to create a single model.

### Bootstrapping
a **bootstrapped sample** is a random sample of datapoints where we randomly select with replacement datapoints from the original dataset to create a dataset of the same size. Randomly selecting with replacement means that we can choose the same datapoint multiple times. This means that in a bootstrapped sample, some datapoints from the original dataset will appear multpile times and some will not appear at all.

For example if we have four datapoints A, B, C, D, these could be 3 resamples:

A, A, B, C
B, B, B, D
A, A, C, C

We would rather be able to get more samples of data from the population, but as all we have is the training set, we use that to generate additional datasets.

note that we use bootstrapping to mimic creating multiple statements.

### Bagging Decision Trees
**Bootstrap Aggregation**(or **Bagging**) is a technique for reducing the variance in an individual model by creating an ensemble from multiple models built on bootstrapped samples.

To bag decision trees, we create multiple(say 10) bootstrapped resamples of the training dataset. So if we have 100 datapoints in the training set, each of the resamples will have 100 datapoints randomly chosen from the training set. Recall that we randomly select with replacement, meaning that some datapoints will appear multiple times and some not at all.

We create a decision tree with each of these 10 resamples.

We make a **prediction** with each of the 10 decision trees and then each decision tree gets a vote. The prediction with the most votes is the final prediction.

When we bootstrap the training set, we're trying to wash out the variance of the decision tree. The average of several trees that have different training sets will create a model that more accurately gets at the essence of the data.

note that bagging decision trees is a way of reducing the variance in the model.

### Decorrelate the Trees
With bagged decision trees, the trees may still be too similar to have fully created the ideal model. They are built on different resamples, but they all have access to the same features. Thus we will add some restrictions to the model when building each decision tree so the trees have more variation. We call this **decorrelating the trees**.

When building a decision tree, at every node, we compare all the split thresholds for each feature to find the single best feature & split threshold. In a decision tree for a random forest, at each node, we randomly select a subset of the features to consider. This will result in us choosing a good, but not the best, feature to split on at each step. It's important to note that the random selection of features happens at each node. So maybe at the first node we consider the Sex and Fare features and then at the second node, the Fare and Age features.

A standard choice for the number of features to consider at each split is the square root of the number of features. So if we have 9 features, we will consider 3 of them at each node(randomly chosen).

If we bag these decision trees, we get a **random forest**.

note that each decision tree within a random forest is probably worse than a standard decision tree. But, when we average them, we get a very strong model.