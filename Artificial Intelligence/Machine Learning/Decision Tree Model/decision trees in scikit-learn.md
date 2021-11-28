### DecisionTreeClassifier Class
Just like with logistic regression, scikit-learn has a decision tree class. The code for building a decision tree model is very similar to building a logistic regression model. Scikit-learn did this intentionally so that it is easy to build and compare different models for the same dataset.

**Here's the import statement.**
```python
from sklearn.tree import DecisionTreeClassifier
```

Now we can apply the same methods that we used with the LogisticRegression class: **fit**(to train the model), **score**(to calculate the accuracy score) and **predict**(to make predictions).

We first create a DecisionTreeClassifier object.
```python
model = DecisionTreeClassifier()
```

We do a train/test split using a random_state so that every time we run the code we will get the same split.
```python
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=22)
```

Then we use the fit method to train the model.
```python
model.fit(X_train, y_train)
```

We can use the predict method to see what the model predicts. Here we can see the prediction for a male passenger in Pclas 3, who's 22 years old, has 1 sibling/spouse on board, has 0 parents/children on board, and paid a fare of 7.25.
```python
print(model.predict([[3, True, 22, 1, 0, 7.25]]))
# [0]
```

We see that the model predicts that the passenger didn't survive. This is the same prediction that the Logistic Regression model gave.

Note that we have the same methods for a DecisionTreeClassifier as we did for a LogisticRegression object.

### Scoring a Decision Tree Model
We can use the **score** and **predict** methods to get the accuracy, precision and recall scores.
```python
print("accuracy:", model.score(X_test, y_test))
y_pred = model.predict(X_test)
print("precision:", precision_score(y_test, y_pred))
print("recall:", recall_score(y_test, y_pred))

# Decision Tree
#  accuracy: 0.7733701517171333
#  precision: 0.7113072331933618
#  recall: 0.6936385918003565

# Logistic Regression
#  accuracy: 0.7970354853043865
#  precision: 0.7618898922983288
#  recall: 0.6900529617441382
```

can use k-fold cross validation to get an accurate measure of the metrics and compare the values with a Logistic Regression model. We use a random_state when creating the KFold object so that we will get the same results every time.

You can see that the accuracy and precision of the Logistic Regression model is higher, and the recalls of the two models are about the same.

note that the logistic regression model performs better, though we may still want to use a decision tree for its interpretability.

### Gini vs. Entropy
The default impurity **criterion** in scikit-learn's Decision Tree algorithm is the Gini Impurity. However, they've also implemented entropy and you can choose which one you'd like to use when creating the DecisionTreeClassifier object.

If you go to the docs, you can see that one of the parameters is criterion.
![contentImage](https://api.sololearn.com/DownloadFile?id=3896)
(docs located [here](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html))

To build a Decision Tree that uses entropy, will need to set the criterion parameter to entropy. Here's the code for building a Decision Tree that uses entropy instead of the Gini Impurity.
```python
dt = DecisionTreeClassifier(criterion='entropy')
```

Now we can compare a Decision Tree using gini with a Decision Tree using entropy. We first create a **k-fold split** since when we're comparing two models we want them to use the same train/test splits to be fair. Then we do a k-fold cross validation with each of the two possible models. We calculate accuracy, precision and recall for each of the two options.
```python
kf = KFold(n_splits=5, shuffle=True)
for criterion in ['gini', 'entropy']:
	print("Decision Tree - {}".format(criterion))
	accuracy = []
	precision = []
	recall = []
	for train_index, test_index in kf.split(X):
		X_train, X_test = X[train_index], X[test_index]
		y_train, y_test = y[train_index], y[test_index]
		dt = DecisionTreeClassifier(criterion=criterion)
		dt.fit(X_train, y_train)
		y_pred = dt.predict(X_test)
		accuracy.append(accuracy_score(y_test, y_pred))
		precision.append(precision_score(y_test, y_pred))
		recall.append(recall_score(y_test, y_pred))
	
	print("accuracy:", np.mean(accuracy))
	print("precision:", np.mean(precision))
	print("recall:", np.mean(recall))
```

note that very little difference is seen in the performance of Gini vs Entropy. This is expected as they aren't really very different functions. It's rare to find a dataset where the choice would make a difference.

### Visualizing Decision Trees
How to create a png image of the graph using scikit-learn's **export_graphviz** function:
1. import it.
```python
from sklearn.tree import export_graphviz
```

```python
dot_file = export_graphviz(dt, feature_names=feature_names)
```

2. Then we use the export_graphviz function. Here dt is a Decision Tree object and feature_names is a list of the feature names. Graph objects are stored as .dot files which can be the GraphViz program. The goal is to save a png image file. Will be able to convert the dot file into a png file, so first save the dot file to a variable, so we save the dot file created by the export_graphviz function so that we can convert it to a png.
3. Then use the graphviz module to convert it to a png image format.
```python
import graphviz
graph = graphviz.Source(dot_file)
```
4. Finally, ew can use the render method to create the file. We tell it the filename and file format. By default, it will create extra files that we're not interested in, so we add cleanup to tell it to get rid of them.
```python
graph.render(filename='tree', format='png', cleanup=True)
```

Now should have a file called tree.png on the computer. Here's the code for visualizing the tree for the Titanic dataset with just the Sex and Pclass features.
```python
from sklearn.tree import export_graphviz
import graphviz
from IPython.display import Image

feature_names = ['Pclass', 'male']
X = df[feature_names].values
y = df['Survived'].values

dt = DecisionTreeClassifier()
dt.fit(X, y)

dot_file = export_graphviz(dt, feature_names=feature_names)
graph = graphviz.Source(dot_file)
graph.render(filename='tree', format='png', cleanup=True)
```

Here is the result:
![contentImage](https://api.sololearn.com/DownloadFile?id=3913)

note that if you're going to run this on the compuer, make sure to install graphviz first. You can do this with "pip install graphviz" in the terminal.

### Tendency to Overfit
Recall that **overfitting** is when we do a good job of building a model for the training set, but it doesn't perform well on the test set. Decision Trees are incredibly prone to overfitting. Since they can keep having additional nodes in the tree that splits on features, the models can really dig deep into the specifics of the training set. Depending on the data, this might result in a model that doesn't capture the true nature of the data nad doesn't generalize.

Maybe we just have a single datapoint that goes to a leaf node. It might not make sense to have that additional split.

Look at a diagram of a Decision Tree for the Titanic dataset. This is the resulting tree when we build a Decision Tree with scikit-learn on the entire dataset. We're just looking at a portion of the Decision Tree since it's so large. A particular path of interest has been highlighted.
![contentImage](https://api.sololearn.com/DownloadFile?id=3914)

If you follow the highlighted path, you'll see that we split on Sex, Pclass, and then split on Age 9 times in a row with different thresholds. This results in a graph that's very nitpicky about age. A female passenger in Pclass 3 of age 31 goes to a different leaf node than a similar passenger of age 30.5 or 30 or 29. The model predicts that the female passenger of 35 survives, age 32 doesn't survive, age 31 survives, and age 30 doesn't survive. This is probably too fine-grained and is giving single datapoints from the dataset too much power. You can see that the leaf nodes all have few datapoints and often only one.

note that if you let a Decision Tree keep building, it may create a tree that's overfit and doesn't capture the essence of the data.

### Pruning
In order to solve these issues, will do what's called **pruning the tree**. This means that we make the tree smaller with the goal of reducing overfitting.

There are two types of pruning: pre-pruning and post-pruning. In pre-pruning, we have rules of when to stop building the tree, so we stop building before the tree is too big. In post-pruning we build the whole tree and then we review the tree and decide which leaves to remove to make the tree smaller.

note that the term pruning comes from the same term in gardening. Gardeners cut off branches of trees and we are doing the same to the decision tree.

### Pre-pruning
We're going to focus on pre-pruning techniques since they are easier to implement. We have a few options for how to limit the tree growth. Here are some commonly used pre-pruning techniques:

- **Max depth**: Only grow the tree up to a certain depth, or height of the tree. If the max depth is 3, there will be at most 3 splits for each datapoint.
- **Leaf size**: Don't split a node if the number of samples at that node is under a threshold
- **Number of leaf nodes**: Limit the total number of leaf nodes allowed in the tree

Pruning is a balance; i.e., if you set the max depth too small, you won't have much of a tree and you won't have any predictive power. This is called **underfitting**. Similarly if the leaf size is too large, or the number of leaf nodes too small, you'll have an underfit model.

note that there's no hard science as to which pre-pruning method will yield better results. In practice, we try a few different values for each parameter and cross validate to compare their performance.