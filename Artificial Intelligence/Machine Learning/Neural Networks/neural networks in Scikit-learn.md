### Creating Artificial Dataset
Sometimes in order to test models, it is helpful to create an **artificial dataset**. We can create a dataset of the size and complexity needed. Thus we can make a dataset that is easier to work with than a real life dataset. This can help us understand how models work before we apply them to messy real world data.

We will use the **make_classification** function in scikit-learn. It generates a features matrix X and target array y. We will give it these parameters:

- **n_samples**: number of datapoints
- **n_features**: number of features
- **n_informative**: number of informative features
- **n_redundant**: number of redundant features
- **random_state**: random state to guarantee same result every time.

You can look at the [full documentation](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_classification.html#sklearn.datasets.make_classification) to see other parameters that you can tweak to change the result.

Here is the code to generate a dataset.
```python
from sklearn.datasets import make_classification
X, y = make_classification(n_features=2, n_redundant=0, n_informative=2, random_state=3)
```

Here's the code to plot the data so we can look at it visually.
```python
from matplotlib import pyplot as plt
plt.scatter(X[y==0][:, 0], X[y==0][:, 1], s=100, edgecolors='k')
plt.scatter(X[y==1][:, 0], X[y==1][:, 1], s=100, edgecolors='k', marker='^')
plt.show()
```

![contentImage](https://api.sololearn.com/DownloadFile?id=3966)

note that scikit-learn has a couple other functions besides make_classification for making classification datasets with different priorities. Look at make_circles and make_moons if you want to play around with more artificial datasets.

### MLPClassifier
Scikit-learn has a **MLPClassifier** class which is a multi-layer perceptron for classification. We can import the class from scikit-learn, create an MLPClassifier object and use the **fit method** to train.
```python
from sklearn.model_selection import train_test_split
from sklearn.neural_network import MLPClassifier
from sklearn.datasets import make_classification

X, y = make_classification(n_features=2, n_redundant=0, n_informative=2, random_state=3)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=3)
mlp = MLPClassifier()
mlp.fit(X_train, y_train)
```

**Output**:
```python
ConvergenceWarning: Stochastic Optimizer: Maximum iterations (200) reached and the optimization hasn't converged yet.
	% self.max_iter, ConvergenceWarning)
```

Youj will notice that we get a **ConvergenceWarning**. This means that the neural network needs more interations to converge on the optimal coefficients. The default number of iterations is 200. Let's up this value to 1000.
```python
mlp = MLPClassifier(max_iter=1000)
```

Now when we run this code, the neural network will converge. We can now use the score method to calculate the accuracy on the test set.
```python
from sklearn.model_selection import train_test_split
from sklearn.neural_network import MLPClassifier

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=3)
mlp = MLPClassifier(max_iter=1000)
mlp.fit(X_train, y_train)
print("accuracy:", mlp.score(X_test, y_test))
```

### Parameters for MLPClassifier
There are a couple of parameters that you may find yourself needing to change in the MLPClassifier.

You can configure the number of **hidden layers** and how many **nodes** in each layer. The default MLPClassifier will have a single hidden layer of 100 nodes. This often works really well, but we can experiment with different values. This will create an MLPClassifier with two hidden layers, one of 100 nodes and one of 50 nodes.
```python
mlp = MLPClassifier(max_iter=1000, hidden_layer_sizes=(100, 50))
```

We saw **max_iter** in the previous part. This is the number of iterations. In general, the more data you have, the fewer iterations you need to converge. If the value is too large, it will take too long to run the code. If the value is too small, the neural network won't converge on the optimal solution.

We also sometimes need to change **alpha**, which is the step size. This is how much the neural network changes the coefficients at each iteration. If the value is too small, you may never converge on the optimal solution. If the value is too large, you may miss the optimal solution. Initially you can leave this at the default. The default value of alpha is 0.0001. Note that decreasing **alpha** often requires an increase in **max_iter**.

Sometimes you will want to change the **solver**. This is what algorithm is used to find the optimal solution. All the solvers work, but you may find for your dataset that a different solver finds the optimal solution faster. The options for solver are 'lbfgs', 'sgd' and 'adam'.

Run this code and try changing the parameters for the MLPClassifier. The code uses a **random_state** to ensure that every time you run the code with the same parameters you will get the same output.
```python
from sklearn.model_selection import train_test_split
from sklearn.neural_network import MLPClassifier

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=3)
mlp = MLPClassifier(max_iter=1000, hidden_layer_sizes=(100, 50), alpha=0.0001, solver='adam', random_state=3)
mlp.fit(X_train, y_train)
print("accuracy:", mlp.score(X_test, y_test))
```

If you look at [the docs](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html), you can read abt several more parameters that you can tune in the neural network.