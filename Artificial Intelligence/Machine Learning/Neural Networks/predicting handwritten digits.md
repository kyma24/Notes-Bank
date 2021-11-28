### The MNIST Dataset
In this lesson we will be working with a new dataset, the **MNIST database of handwritten digits**. NIST is the National Institute of Standards and Technology and the M stands for Modified.

This is a database of images of handwritten digits. We will build a classifier to determine which digit is in the image.

We will start with the version of the MNISt dataset that is built into scikit-learn. This has the images with only 8 by 8 pixels, so they are blurry.

in scikit-learn we can load the dataset using the **load_digits function**. To simplify the problem, we will initially only be working with two digits (0 and 1) so we use the n_class parameter to limit the number of target values to 2.
```python
from sklearn.datasets import load_digits
X, y = load_digits(n_class=2, return_X_y=True)
```

We can see the dimensions of X and y and what the values look like as follows.
```python
print(X.shape, y.shape)
print(X[0])
print(y[0])
```

**Output:**
```python
(360, 64) (360,)
[ 0.  0.  5. 13.  9.  1.  0.  0.  0.  0. 13. 15. 10. 15.  5.  0.  0.  3.
 15.  2.  0. 11.  8.  0.  0.  4. 12.  0.  0.  8.  8.  0.  0.  5.  8.  0.
  0.  9.  8.  0.  0.  4. 11.  0.  1. 12.  7.  0.  0.  2. 14.  5. 10. 12.
  0.  0.  0.  0.  6. 13. 10.  0.  0.  0.]
0
```

We see that we have 300 **datapoints** and each datapoint has 64 **features**. We have 64 features because the image is 8x8 pixels and we have 1 feature per pixel. The value is on a grayscale where 0 is black and 16 is white.

To get a more intuitive view of the datapoint, reshape the array to be 8x8.
```python
print(X[0].reshape(8, 8))
```

**Output:**
```python
[[ 0.  0.  5. 13.  9.  1.  0.  0.]
 [ 0.  0. 13. 15. 10. 15.  5.  0.]
 [ 0.  3. 15.  2.  0. 11.  8.  0.]
 [ 0.  4. 12.  0.  0.  8.  8.  0.]
 [ 0.  5.  8.  0.  0.  9.  8.  0.]
 [ 0.  4. 11.  0.  1. 12.  7.  0.]
 [ 0.  2. 14.  5. 10. 12.  0.  0.]
 [ 0.  0.  6. 13. 10.  0.  0.  0.]]
 ```
 
We can see that this is a 0, though we will see in the next part that we can draw the image more clearly.
 ```python
 from sklearn.datasets import load_digits
 X, y = load_digits(n_class=2, return_X_y=True)
 print(X.shape, y.shape)
 print(X[0])
 print(y[0])
 print(X[0].reshape(8, 8))
 ```
 
 note that there are different versions of this dataset with more pixels and with colors(not grayscale). We will see that even with these simplified images, we can build a good classifier.
 
 ### Drawing the Digits
 You can build a model w/o ever looking at a visual representation of the images, but it can sometimes be helpful to draw the image.
 
 We use the matplotlib function **matshow** to draw the image. The **cmap** parameter is used to indicate that the image should be in grayscale rather than colored.
 ```python
 import matplotlib.pyplot as plt
 from sklearn.datasets import load_digits
 
 X, y = load_digits(n_class=2, return_X_y=True)
 plt.matshow(X[0].reshape(8, 8), cmap=plt.cm.gray)
 plt.xticks(()) # remove x tick marks
 plt.yticks(()) # remove y tick marks
 plt.show()
```

![contentImage](https://api.sololearn.com/DownloadFile?id=3968)

### MLP for MNIST Dataset
Now let's use the MLPClassifier to build a model for the MNIST dataset.

We will do a **train/test split** and train a MLPClassifier on the training set.
```python
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=2)
mlp = MLPClassifier()
mlp.fit(X_train, y_train)
```

We don't get a warning, so the default number of iterations is adequate in this case.

Let's look at how the model predicts the first datapoint in the test set. We use **matplotlib** to draw the images and then show the model's prediction.
```python
x = X_test[0]
plt.matshow(x.reshape(8, 8), cmap=plt.cm.gray)
plt.xticks(())
plt.yticks(())
plt.show()
print(mlp.predict([x]))
# 0
```
![contentImage](https://api.sololearn.com/DownloadFile?id=3969)

We can see that this is a 0 and that the model correctly predicts 0.

Similarly, let's look at the second datapoint.
```python
x = X_test[1]
plt.matshow(x.reshape(8, 8), cmap=plt.cm.gray)
plt.xticks(())
plt.yticks(())
plt.show()
print(mlp.predict([x]))
# 1
```

![contentImage](https://api.sololearn.com/DownloadFile?id=3970)

This is clearly a 1 and the model again gets the correct prediction.

We can also see the model's accuracy on the entire test set.
```python
print(mlp.score(X_test, y_test))
# 1.0
```

We can also see the model's accuracy on the entire test set. Thus the model gets 100% accuracy.

note that 0 and 1 are two of the easier digits to distinguish, but we will see that the model can also perform well with distinguishing harder examples.

### Classifying all 10 Digits
Since **neural networks** are easily generalized to handle multiple outputs, we can just use the same code to build a classifier to distinguish between all ten digits.

This time when we load the digits, we don't limit the number of classes.
```python
X, y = load_digits(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=2)
mlp = MLPClassifier(random_state=2)
mlp.fit(X_train, y_train)

print(mlp.score(X_test, y_test))
# 0.96
```

So we got 96% of the datapoints in the test set correct. Let's look at the ones we got incorrect We use a numpy mask to pull out just the datapoints we got incorrect. We pull the x values, the true y value as well as the predicted value.
```python
y_pred = mlp.predict(X_test)
incorrect = X_test[y_pred != y_test]
incorrect_true = y_test[y_pred != y_test]
incorrect_pred = y_pred[y_pred != y_test]
```

Let's look at the first image that we got wrong and what the prediction was.
```python
j = 0
plt.matshow(incorrect[j].reshape(8, 8), cmap=plt.cm.gray)
plt.xticks(())
plt.yticks(())
plt.show()
print("true value:", incorrect_true[j])
print("predicted value:", incorrect_pred[j])
```
![contentImage](https://api.sololearn.com/DownloadFile?id=3971)
true value: 4
predicted value: 9

```python
from sklearn.datasets import load_digits
from sklearn.model_selection import train_test_split
from sklearn.neural_network import MLPClassifier

X, y = load_digits(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=2)
mlp = MLPClassifier(random_state=2)
mlp.fit(X_train, y_train)

print(mlp.score(X_test, y_test))

y_pred = mlp.predict(X_test)
incorrect = X_test[y_pred != y_test]
incorrect_true = y_test[y_pred != y_test]
incorrect_pred = y_pred[y_pred != y_test]

j = 0
print(incorrect[j].reshape(8, 8).astype(int))
print("true value:", incorrect_true[j])
print("predicted value:", incorrect_pred[j])
```

note that you can modify the code to see all of the datapoints the model predicted incorrectly.