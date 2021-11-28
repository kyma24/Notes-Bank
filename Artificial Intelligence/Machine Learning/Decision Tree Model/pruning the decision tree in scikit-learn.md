### Pre-pruning Parameters
Scikit-learn has implemented quite a few techniques for pre-pruning. In particular, we will look at three of the parameters: max_depth, min_samples_leaf, and max_leaf_nodes. Look at the [docs](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html) for Decision Trees to find full explanations to these three parameters.

**Prepruning Technique 1**: Limiting the depth
We use the max_depth parameter to limit the number of steps the tree can have between the root node and the leaf nodes.

**Prepruning Technique 2**: Avoiding leaves with few datapoints
We use the min_samples_leaf parameter to tell the model to stop building the tree early if the number of datapoints in a leaf will be below a threshold.

**Prepruning Technique 3**: Limiting the number of leaf nodes
We use max_leaf_nodes to set a limit on the number of leaf nodes in the tree.

Here's the code for creating a Decision Tree with the following properties:
- max depth of 3
- minimum samples per leaf of 2
- maximum number of leaf nodes of 10

```python
dt = DecisionTreeClassifier(max_depth=3, min_samples_leaf=2, max_leaf_nodes=10)
```

You can now train the model and test it as we've done before.

You can use as many or as few of the parameters as you'd like.

note that to determine the best values for the pre-pruning parameters, we'll use cross validation to compare several potential options.

### Grid Search
We're not going to be able to intuit best values for the pre-pruning parameters. In order to decide on which to use, we use **cross validation** and compare metrics. We could loop through the different options, but scikit-learn has a grid search class built in that will do this for us.

The class is called GridSearchCV. We start by importing it.
```python
from sklearn.model_selection import GridSearchCV
```

GridSearchCV has four parameters that we'll use:

1. the model(in this case a DecisionTreeClassifier)
2. Param grid: a dictionary of the parameters names and all the possible values
3. What metric to use(default is accuracy)
4. How many folds for k-fold cross validation

Let's create the param grid variable. We'll give a list of all the possible values for each parameter that we want to try.
```python
param_grid = {
	'max_depth': [5, 15, 25],
	'min_samples_leaf': [1, 3],
	'max_leaf_nodes': [10, 20, 35, 50]
}
```

Now we create the grid search object. We'll use the above parameter grid, set the scoring metric to the F1 score, and do a 5-fold cross validation.
```python
dt = DecisionTreeClassifier()
gs = GridSearchCV(dt, param_grid, scoring='f1', cv=5)
```

Now we can fit the grid search object This can take a little time to run as it's trying every possible combination of the parameters
```python
gs.fit(X, y)
```

Since we have 3 possible values for max_depth, 2 for min_samples_leaf and 4 for max_leaf_nodes, we have 3 * 2 * 4 = 24 different combinations to try:

max_depth: 5, min_samples_leaf: 1, max_leaf_nodes: 10
max_depth: 15, min_samples_leaf: 1, max_leaf_nodes: 10
max_depth: 25, min_samples_leaf: 1, max_leaf_nodes: 10
max_depth: 5, min_samples_leaf: 3, max_leaf_nodes: 10
...

We use the **best_params_** attribute to see which model won.
```python
print("best params:", gs.best_params_)
# best parameters: {'max_depth': 15, 'max_leaf_nodes': 35, 'min_samples_leaf': 1}
```

Thus we see that the best model has a maximum depth of 15, maximum number of leaf nodes as 35 and minimum samples per leaf of 1.

The **best_score_** attribute tells us the score of the winning model.
```python
print("best score:", gs.best_score_)
# best score: 0.775712742630669
```

note that there are often a few models that have very similar performance. If you run this multiple times you might get slightly different results depending on the randomness of how the points are distributed among the folds. Generally if we have multiple modes with comparable performance, we'd choose the simpler model.