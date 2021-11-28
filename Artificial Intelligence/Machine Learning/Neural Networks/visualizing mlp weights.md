### Open ML
For this lesson, we will use a more granular version of the MNIST dataset. Instead of using the versino in scikit-learn which has 64 pixel images, we will use a version from Open ML that has 784 pixels(28x28).

[Open ML](www.openml.org) has a database of large datasets that can be used for a variety of machine learning problems. Scikit-learn has a function **fetch_openml** for directly downloading datasets from the Open ML database.

Use the following code to get the dataset.
```python
from sklearn.datasets import fetch_openml
X, y = fetch_openml('mnist_784', version=1, return_X_y=True)
```

We can briefly look at the shape of the arrays, the range of the features' values, and the first few values of the target array to better understand the dataset.
```python
print(X.shape, y.shape)
print(np.min(X), np.max(X))
print(y[0:5])
```

**Output:**
```python
(70000, 784) (70000,)
0.0 255.0
['5' '0' '4' '1' '9']
```

We can see that we have 70,000 datapoints with 784 features. The feature values range from 0 to 255(which we interpret on a gray scale with 0 being white and 255 being black). The target values are the numbers 0-9. Note that the **target values** are stored as strings and not integers.

For the example, we will be using only the digits 0-3, so we can use the following code to segment out that portion of the dataset.
```python
X5 = X[y <= '3']
y5 = y[y <= '3']
```

We will be modifying some of the default parameters in the MLPClassifier to build the model. Since the goal will be to visualize the weights of the hidden layer, we will use only 6 nodes in the hidden layer so that we can look at all of them. We will use '**sgd**'(stochastic gradient descent) as the solver which requires us to decrease alpha(the learning rate).
```python
mlp=MLPClassifier(
	hidden_layer_sizes=(6,),
	max_iter=200, alpha=1e-4,
	solver='sgd', random_state=2)
	
mlp.fit(X5, y5)
```

If we run this code we will see that it converges.

### MLPClassifier Coefficients
The MLPClassifier stores the coefficients in the coefs_ attribute. Let's see what it looks like.
```python
print(mlp.coefs_)
```

**Output:**
```python
[array([[-0.01115571, -0.08262824, 0.00865588, -0.01127292, -0.01387942, -0.02957163],
...
])]
```

First we see that it is a list with two elements.
```python
print(len(mlp.coefs_))
```

**Output:**
```python
2
```

The two elements in the list correspond to the two layers: the **hidden layer** and the **output layer**. We have an array of coefficients for each of these layers. Let's look at the shape of the coefficients for the hidden layer.
```python
print(mlp.coefs_[0].shape)
# Output:
# (784, 6)
```

We see that we have a 2-dimensional array of size 784 x 6. There are 6 nodes and 784 input values feeding into each node, and we have a weight for each of these connections.

note that in order to interpret the values, we will need to use a visual representation.

### Visualizing the Hidden Layer
To get a better understanding of what the neural network is doing, we can visualize the weights of the hidden layer to get some insight into what each node is doing.

We will use the matshow function from matplotlib again to draw the images. In matplotlib we can use the **subplots** function to create multiple plots within a single plot.
```python
fig, axes = plt.subplots(2, 3, figsize=(5, 4))
for i, ax in enumerate(axes.ravel()):
	coef = mlp.coefs_[0][:, i]
	ax.matshow(coef.reshape(28, 28), cmap=plt.cm.gray)
	ax.set_xticks(())
	ax.set_yticks(())
	ax.set_title(i + 1)
plt.show()
```

**Output:**
![contentImage](https://api.sololearn.com/DownloadFile?id=3972)

You can see that nodes 4 and 6 are determining if the digit is a 3. Node 1 is determining if the digit is a 0 or a 2 since you can see both of those values in the image. Not every hidden node will have an obvious use.

note that if you change the random state in the MLPClassifier, you will likely get different results. There are many equivalently optimal neural networks that work differently.