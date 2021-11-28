### KFold Class
Scikit-learn has already implemented the code to break the dataset into k chunks and create k training and test sets.

For simplicity, let's take a dataset with just 6 datapoints and 2 features and a 3-fold cross validation on the dataset. We'll take the first 6 rows from the Titanic dataset and use just the Age and Fare columns.
```python
X = df[['Age', 'Fare']].values[:6]
y = df['Survived'].values[:6]
```

We start by instantiating a KFold class object. It takes two parameters: **n_splits**(this is k, the number of chunks to create) and **shuffle**(whether or not to randomize the order of the data). It's generally good practice to shuffle the data since you often get a dataset that's in a sorted order.
```python
kf = KFold(n_splits=3, shuffle=True)
```

The KFold class has a split method that creates the 3 splits for the data.

Let's look at the output of the split method. The split method returns a generator, so we use the list function to turn it into a list.
```python
list(kf.split(X))
```

Result:
```python
from sklearn.model_selection import KFold
import pandas as pd

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
X = df[['Age', 'Fare']].values[:6]
y = df['Survived'].values[:6]

kf = KFold(n_splits=3, shuffle=True)
for train, test in kf.split(x):
	print(train, test)
```

As can be seen, there are 3 training and testing sets as expected. The first training set is made up of datapoints 0, 2, 3, 5 and the test set is made up of datapoints 1, 4.

note that the split is done randomly, so expect to see different datapoints in the sets each time the code is run.

### Creating Training and Test Sets with the Folds
We used the KFold class and split method to get the indices that are in each of the splits. Now let's use the result to get the first(of 3) train/test splits.

First, let's pull out the first split:
```python
splits = list(kf.split(X))
first_split = splits[0]
print(first_split)
# (array([0, 2, 3, 5]), array([1, 4]))
```

The first array is the indices for the training set and the second is the indices for the test set. Let's create these variables.
```python
train_indices, test_indices = first_split
print("training set indices:", train_indices)
print("test set indices:", test_indices)
# training set indices: [0, 2, 3, 5]
# test set indices: [1, 4]
```

Now we can create an X_train, y_train, X_test, and y_test based on these indices.
```python
X_train = X[train_indices]
X_test = X[test_indices]
y_train = y[train_indices]
y_test = y[test_indices]
```

If we print each of these out, we'll see that we have four of the datapoints in X_train and their target values in y_train. The remaining 2 datapoints are in X_test and their target values in y_test.
```python
print("X_train")
print(X_train)
print("y_train", y_train)
print("X_test")
print(X_test)
print("y_test", y_test)
```

```python
from sklearn.model_selection import KFold
import pandas as pd
df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
X = df[['Age', 'Fare']].values[:6]
y = df['Survived'].values[:6]

kf = KFold(n_splits=3, shuffle=True)

splits = list(kf.split(X))
first_split = splits[0]
train_indices, test_indices = first_split
print("training set indices:", train_indices)
print("test set indices:", test_indices)

X_train = X[train_indices]
X_test = X[test_indices]
y_train = y[train_indices]
y_test = y[test_indices]
print("X_train")
print(X_train)
print("y_train", y_train)
print("X_test")
print(X_test)
print("y_test", y_test)
```
At this point, have training and test sets in the same format as did using the train_test_split function.

### Build a Model
Now we can use the training and test sets to build a model and make a prediction like before. Let's go back to using the entire dataset(since 4 datapoints is not enough to build a decent model).

Here's the entirety of the code to build and score the model on the first fold of a 5-fold cross validation. Note that the code for fitting and scoring the model is exactly the same as it was when we used the train_test_split function.
```python
from sklearn.model_selection import KFold
from sklearn.linear_model import LogisticRegression
import pandas as pd

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

kf = KFold(n_splits=5, shuffle=True)

splits = list(kf.split(X))
train_indices, test_indices = splits[0]
X_train = X[train_indices]
X_test = X[test_indices]
y_train = y[train_indices]
y_test = y[test_indices]

model = LogisticRegression()
model.fit(X_train, y_train)
print(model.score(X_test, y_test))
```

So far, we've essentially done a single train/test split. In order to do a k-fold cross validation, we need to use each of the other 4 splits to build a model and score the model.

### Loop Over All the Folds
We have been doing one fold at a time, but really we want to loop over all the folds to get all the values. We will put the code from the previous part inside the for loop.
```python
scores = []
kf = KFold(n_splits=5, shuffle=True)
for train_index, test_index in kf.split(X):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]
    model = LogisticRegression()
    model.fit(X_train, y_train)
    scores.append(model.score(X_test, y_test))
print(scores)
# [0.75847, 0.83146, 0.85876, 0.76271, 0.74011]
```

Since we have 5 folds, we get 5 accuracy values. Recall, to get a single final value, we need to take the mean of those values.
```python
print(np.mean(scores))
# 0.79029
```

Now that we've calculated the accuracy, we no longer need the 5 different models that have been built. For future use, we just want a single model. To get the single best possible model, we build a model on the whole dataset. If we're asked the accuracy of this model, we use the accuracy calculated by cross validation(0.79029) even though we haven't actually tested this particular model with a test set.
```python
final_model = LogisticRegression()
final_model.fit(X, y)
```

expect to get slightly different values every time you run the code. The KFold class is randomly splitting up the data each time, so a different split will result in different scores, though you should expect the average of the 5 scores to generally be about the same.