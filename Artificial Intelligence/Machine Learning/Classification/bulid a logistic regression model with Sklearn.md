[Scikit Website](https://scikit-learn.org)

### What is Scikit-learn
now that have bulit up the foundation of how logistic regression works, dive into some code to build a model.

for this going to introduce a new Python module called **scikit-learn**. Scikit-learn, often shortened to **sklearn**, is the scientific toolkit.

all of the basic machine learning algorithms are implemented in sklearn. Will see that with just a few lines of code can build several different powerful models.

note that scikit-learn is continually being updated. If have a slightly different version of the module installed on the computer, everything will still work correctly, but might see slightly different values than in the playground.

### Prep Data with Pandas
before can use sklearn to build a model, need to prep the data with Pandas. Go back to the full dataset and review the Pandas commands.

here's a Pandas dataframe of data with all the columns:
![contentImage](https://api.sololearn.com/DownloadFile?id=3744)

first, need to make all the columns numerical. Recall how to create the boolean column for Sex.
```python
df['male'] = df['Sex'] == 'male'
```

now, take all the features and create a numpy array called X. First select all the columns are interested in and then use the values method to convert it to a numpy array.
```python
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
```

now take the target(the Survived column) and store it in variable y.
```python
y = df['Survived'].values
```

```python
import pandas as pd
df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values
print(X)
print(y)
```

note: it's standard practice to call the 2d array of features X and the 1d array of target values y.

### Build a Logistic Regression Model with Sklearn
start by importing the Logistic Regression Model:
```python
from sklearn.linear_model import LogisticRegression
```

All sklearn models are built as Python classes. First instantiate the class:
```python
model = LogisticRegression()
```

Now can use the data that has been previously prepared to train the model. The **fit** method is used for building the model. It takes two arguments: X(the features as a 2d numpy array) and y(the target as a 1d numpy array).

for simplicity, first assume that just building a Logistic Regression model using the Fare and Age columns. First define X to be the feature matrix and y the target array.
```python
X = df[['Fare', 'Age']].values
y = df['Survived'].values
```

now use the fit method to build the model.
```python
model.fit(X, y)
```

fitting the model means using the data to choose a line of best fit. Can see the coefficients with the coef_ and intercept_ attributes.
```python
print(model.coef_, model.intercept_)
```

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
X = df[['Fare', 'Age']].values
y = df['Survived'].values

model = LogisticRegression()
model.fit(X, y)

print(model.coef_, model.intercept_)
# [[0.01615949 -0.01549065]] [-0.51037152]
```

These values mean that the equation is as follows:
```python
0 = 0.0161594x + -0.01549065y + -0.51037152
```

Here's the line drawn on the graph. Can see it does a decent(but not great) job of splitting the yellow and purple points.
![contentImage](https://api.sololearn.com/DownloadFile?id=3745)

### Make Predictions with the Model
Let's rebuild the model with all of the features.
```python
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values
model = LogisticRegression()
model.fit(X, y)
```

now can use the **predict** method to make predictions.
```python
model.predict(X)
```

the first passenger in the dataset is:
```python
[3, True, 22.0, 1, 0, 7.25]
```

This means the passenger is in Pclass 3, are male, are 22 years old, have 1 sibling/spouse aboard, 0 parents/children aboard, and paid $7.25. See what the model predicts for this passenger. Note that even with one datapoint, the predict method takes a 2-dimensional numpy array and returns a 1-dimensional numpy array.
```python
print(model.predict([[3, True, 22.0, 1, 0, 7.25]]))
#[0]
```

The result is 0, which means the model predicts that this passenger didn't survive. See what the model predicts for the first 5 rows of data and compare it to the target array. Get the first 5 rows of data with X\[:5] and the first 5 values of the target with y\[:5].
```python
print(model.predict(X[:5]))
# [0 1 1 1 0]
print(y[:5])
# [0 1 1 1 0]
```

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

model = LogisticRegression()
model.fit(X, y)

print(model.predict([[3, True, 22.0, 1, 0, 7.25]]))
print(model.predict(X[:5]))
print(y[:5])
```

### Score the Model
can get a sense of how good the model is by counting the number of datapoints it predicts correctly. This is called the **accuracy** score.

create an array that has the predicted y values.
```python
y_pred = model.predict(X)
```

now create an array of boolean values of whether or not the model predicted each passenger correctly.
```python
y == y_pred
```

to get the numer of these that are true, can use the numpy sum method.
```python
print((y == y_pred).sum())
# 714
```

this means that of the 887 datapoints, the model makes the correct prediction for 714 of them.

to get the percent correct, divide this by the total number of passengers. Get the total number of passengers using the shape attribute.
```python
y.shape[0]
```

thus the accuracy score is computed as follows.
```python
print((y == y_pred).sum() / y.shape[0])
# 0.8038331454340474
```

thus the model's accuracy is 80%. In other words, the model makes the correct prediction on 80% of the datapoints.

this is common enough calculation, that sklearn has already implemented it for the user. So can get the same result by using the **score method**. The score method uses the model to make a prediction for X and counts whatever percent of them match y.
```python
print(model.score(X, y))
# 0.8038331454340474
```

with this alternative method of calculating accuracy, get the same value, 80%.

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

model = LogisticRegression()
model.fit(X, y)

y_pred = model.predict(X)
print((y == y_pred).sum())
print((y == y_pred).sum() / y.shape[0])
print(model.score(X, y))
```