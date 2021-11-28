### Overfitting
so far have built a model with all of the data and then seen how well it performed on the same data. This is artificially inflating the numbers since the model, in effect, got to see the answers to the quiz before gave it the quiz. This can lead to what is called **overfitting**. Overfitting is when perform well on the data the model has already seen, but don't perform well on new data.

can visually see an overfit model as follows. The line is too closely trying to get every single datapoint on the correct side of the line but is missing the essence of the data.
![contentImage](https://api.sololearn.com/DownloadFile?id=3781)

in the graph can see that have done a good job of getting the yellow dots on the top and the purple dots on the bottom, but it isn't capturing what's going on. A single outlier point could throw off the location of the line. While the model would get a great score on the data it's already seen, it's unlikely to perform well on new data.

note tha tthe more features that have in the dataset, the more prone will be to overfitting.

### Training Set and Test Set
to give a model a fair assessment, will like to know how well the data would perform on data it hasn't seen yet.

in action, the model will be making predictions on data don't know the ansewr to, so will like to evaluate how well the model does on new data, not just the data it's already seen. To simulate making predictions on new unseen data, can break the dataset into a **training set** and a **test set**. The **training set** is used for building the models. The **test set** is used for evaluating the models. Split the data before building the model, thus the model has no knowledge of the test set and will be giving it a fair assessment.

if the dataset has 200 datapoints in it, breaking it into a training set and test set might look as follows.
![contentImage](https://api.sololearn.com/DownloadFile?id=3796)

note that a standard breakdown is to put 70-80% of the data in the training set and 20-30% in the test set. Using less data in the training set means that the model won't have as much data to learn from, so want to give it as much as possible while still leaving enough for evaluation.

### Training and Testing in Sklearn
Scikit-learn has a function built in for splitting the data into a training set and a test set.

assuming have a 2-dimensional numpy array X of the features and a 1-dimensional numpy array y of the target, can use the **train_test_split** function. By default the training set is 75% of the data and the test set is the remaining 25% of the data.
```python
from sklearn.model\_selection import train\_test\_split  
X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, y)
```

use the shape attribute to see the sizes of the datasets.
```python
print("whole dataset:", X.shape, y.shape)
print("training set:", X_train.shape, y_train.shape)
print("test set:", X_test.shape, y_test.shape)
```

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(X, y)

print("whole dataset:", X.shape, y.shape)
print("training set:", X_train.shape, y_train.shape)
print("test set:", X_test.shape, y_test.shape)
```

can see that of the 887 datapoints in the dataset, 665 of them are in the training set and 222 are in the test set. Every datapoint from the dataset is used exactly once, either in the training set or the test set. Note that have 6 features in the dataset, so still have 6 features in both the training set and the test set.

note that can change the size of the training set by using the train_size parameter; e.g. train_test_split(X, y, train_size=0.6) would put 60% of the data in the training set and 40% in the test set.

```python
#i.e. output of this code is (75, 4)(75,) assuming have a 2d numpy array X of 100 datapoints and 4 features and a 1d array of y of 100 target values
X_train, X_test, y_train, y_test = train_test_split(X, y)
print(X_train.shape, y_train.shape)
```

### Build a Scikit-learn Model Using a Training Set
now that know how to split the data into a training set and a test set, need to modify how to build and evaluate the model. All of the model building is done with the training set and all of the evaluation is done with the test set.

before, build a model and evaluated it on the same dataset. Now build the model using the training set.
```python
model = LogisticRegression()
model.fit(X_train, y_train)
```

and evaluate the model using the test set.
```python
print(model.score(X_test, y_test))
```

in fact, all of the metrics calculated in previous parts should be calculated on the test set.
```python
y_pred = model.predict(X_test)
print("accuracy:", accuracy_score(y_test, y_pred))
print("precision:", precision_score(y_test, y_pred))
print("recall:", recall_score(y_test, y_pred))
print("f1 score:", f1_score(y_test, y_pred))
```

the accuracy, precision, recall and F1 score values are actually very similar to the values when used the entire dataset. This is a sign that the model isn't overfit.

note that if run the code, notice that get different scores each time. This is because the train test split is done randomly, and depending on which points land in the training set and test, the scores will be different. There are more accurate means of measuring these scores.

### Using a Random State
as noticed in the previous part, when randomly split the data into a training set and a test set, end up with different datapoints in each set each time the code is run. This is a result of randomness, and need it to be random to be effective, but it can also sometimes make it difficult to test the code.

i.e. each time run the following code, will get different results.
```python
from sklearn.model_selection import train_test_split

X = [[1, 1], [2, 2], [3, 3], [4, 4]]
y = [0, 0, 1, 1]

X_train, X_test, y_train, y_test = train_test_split(X, y)
print('X_train', X_train)
print('X_test', X_test)
```

to get the same split every time, can use the random_state attribute. Choose an arbitrary number to give it, and then every time the code is run, will get the same split.
```python
from sklearn.model_selection import train_test_split

X = [[1, 1], [2, 2], [3, 3], [4, 4]]
y = [0, 0, 1, 1]

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=27)
print('X_train', X_train)
print('X_test', X_test)
```

note that the random state is also called a seed.