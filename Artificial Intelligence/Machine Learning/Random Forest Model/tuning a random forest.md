### Random Forest Parameters
When you look at the scikit-learn docs for the **RandomForestClassifier**, you will see quite a few parameters that you can control. We will be looking at a few of them, but you can learn about all of them in the [docs](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html).

Since a random forest is made up of decision trees, we have all the same tuning parameters for prepruning as we did for decision trees: **max_depth**, **min_samples_leaf**, and **max_leaf_nodes**. With random forests, it is generally not important to tune these as overfitting is generally not an issue.

We will look at two new tuning parameters: **n_estimators**(the number of trees) and **max_features**(the number of features to consider at each split).

The default for the max features is the square root of p, where p is the number of features(or predictors). The default is generally a good choice for max features and we usually won't need to change it, but you can set it to a fixed number with the following code.
```python
rf = RandomForestClassifier(max_features=5)
```

the default number of estimators(decision trees) is 10. This often works well but may in some cases be too small. You can set it to another number as follows.
```python
rf = RandomForestClassifier(n_estimators=15)
```

note that one of the big advantages of Random Forests is that they rarely require much tuning. The default values will work well on most datasets.

### Grid Search
If you recall from the Decision Tree module, scikit-learn has built in a Grid Search class to help us find the optimal choice of parameters.

Let's use Grid Search to compare the performance of a random forest with different numbers of trees.

Recall that we need to define the **parameter grid** of the parameters we want to vary and give a list of the values to try.
```python
param_grid = {
	'n_estimators': [10, 25, 50, 75, 100],
}
```

Now we can create a **Random Forest Classifier** and a **Grid Search**. Recall that the Grid Search will do a k-fold cross validation for us. We set cv=5 for 5-fold cross validation.
```python
rf = RandomForestClassifier()
gs = GridSearchCV(rf, param_grid, cv=5)
```

Now we use the **fit** method to run the grid search. The best parameters will be stored in the best_params_ attribute.
```python
gs.fit(X, y)
print("best params:", gs.best_params_)
# best params: {'n_estimators': 50}
```

These are the parameters which yield the highest accuracy as that is the default metric. Note that you may get slightly different results each time you run this as the random split in the 5 folds may affect which has the best accuracy score.

Accuracy will work okay for us in this case as the classes in the breast cancer dataset are reasonably balanced. If the classes are imbalanced, we would want to use an alternative metric, like the f1-score. We can change the metric by scoring parameter to "f1" as follows. To avoid outputting a different best parameter each time, one can set the random_state in the classifier.
```python
rf = RandomForestClassifier(random_state=123)
gs = GridSearchCV(rf, param_grid, scoring='f1', cv=5)
gs.fit(X, y)
print("best params:", gs.best_params_)
# best params: {'n_estimators': 25}
```

note that you can add additional parameters, e.g. max_features, and parameter values to the param_grid dictionary to compare more decision trees.

### Elbow Graph
With a parameter like the number of trees in a random forest, increasing the number of trees will never hurt performance. Increasing the number of trees will **increase performance** until a point where it levels out. The more trees, ohwever, the more complicated the algorithm. A more complicated algorithm is more resource intensive to use. Generally it is worth adding complexity to the model if it improves performance but we don't want to unecessarily add complexity.

We can use what is called an **Elbow Graph** to find the sweet spot. Elbow Graph is a model that optimizes performance without adding unnecessary complexity.

To find the optimal value, let's do a Grid Search trying all the values from 1 to 100 for n_estimators.
```python
n_estimators = list(range(1, 101))
param_grid = {
	'n_estimators': n_estimators,
}
rf = RandomForestClassifier()
gs = GridSearchCV(rf, param_grid, cv=5)
gs.fit(X, y)
```

Instead of just looking at the best params like we did before, we are going to use the entire result from the grid search. The values are located in the **cv_results_** attribute. This is a dictionary with a lot of data; however, we will only need one of the keys: **mean_test_score**. Let's pull out these values and store them as a variable.
```python
scores = gs.cv_results_['mean_test_score']
# [0.91564148, 0.90685413, ...]
```

Now use matplotlib to graph the results.
```python
import matplotlib.pyplot as plt

scores = gs.cv_results_['mean_test_score']
plt.plot(n_estimators, scores)
plt.xlabel("n_estimators")
plt.ylabel("accuracy")
plt.xlim(0, 100)
plt.ylim(0.9, 1)
plt.show()
```
![contentImage](https://api.sololearn.com/DownloadFile?id=3943)

If we look at this graph, we see that at around 10 trees the graph levels out. The best model occured at n_estimators=33 and n_estimators=64, but given how volatile it is, that was probably due to random chance. We should choose about 10 to be the number of estimators, because we want the minimum number of estimators that still yield maximum performance.
![contentImage](https://api.sololearn.com/DownloadFile?id=3944)

Now we can build the random forest model with the optimal number of trees.
```python
rf = RandomForestClassifier(n_estimators=10)
rf.fit(X, y)
```

You'll see elbow graphs pop up in lots of different situations when we are adding complexity to a model and want to determine the minimal amount of complexity that will yield optimal performance.