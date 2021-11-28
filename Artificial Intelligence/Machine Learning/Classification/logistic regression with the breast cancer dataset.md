Now that built up the tools to build a Logistic Regression model for a classification dataset, will introduce a new dataset.

in the breast cancer dataset, each datapoint has measurements from an image of a breast mass and whether or not it's cancerous. The goal will be to use these measurements to predict if the mass is cancerous.

this dataset is built right into scikit-learn so don't need to read in an csv.

start by loading the dataset and taking a peek at the data and how it's formatted.
```python
from sklearn.datasets import load_breast_cancer
cancer_data = load_breast_cancer()
```

the object returned(which was stored in the cancer_data variable) is an object similar to a Python dictionary. Can see the available keys with the keys method.
```python
print(cancer_data.keys())
```

start by looking at DESCR, which gives a detailed description of the dataset.
```python
print(cancer_data['DESCR'])
```

```python
import pandas as pd
from sklearn.datasets import load_breast_cancer

cancer_data = load_breast_cancer()
print(cancer_data.keys())
print(cancer_data['DESCR'])
```

can see that there are 30 features, 569 datapoints, and target is either Malignant(cancerous) or Benign(not cancerous). For each of the datapoints have measurements of the breast mass(radius, texture, perimeter, etc.).
For each of the 10 measurements, multiple values were computed, so have the mean, standard error and the worst value. This results in 10 * 3 or 30 total features.

note that in the breast cancer dataset, there are several features that are calculated based on other columns. The process of figuring out what additional features to calculate is **feature engineering**.

### Loading the Data into Pandas
pull the feature and target data out of the **cancer_data** object.

first, the feature data is stored with the 'data' key. When looking at it, see that it's a numpy array with 569 rows and 30 columns. That's bc have 569 datapoints and 30 features.

the following is a numpy array of the data.
```python
cancer_data['data']
```

use the shape to see that it's an array with 569 rows and 30 columns.
```python
cancer_data['data'].shape
```

in order to put this in a Pandas DataFrame and make it more human readable, want the columns names. These are stored with the 'feature_names' key.
```python
cancer_data['feature_names']
```

now can create a Pandas DataFrame with all of the feature data.
```python
df = pd.DataFrame(cancer_data['data'], columns=cancer_data['feature_names'])
print(df.head())
```

![contentImage](https://api.sololearn.com/DownloadFile?id=3746)

can see that have 30 columns in the DataFrame, since have 30 features. THe output is truncated so that it'll fit on the screen. Used the head method, so the result only has 5 datapoints.

still need to put the target data in the DataFrame, which can be found with the 'target' key. Can see that the target is a 1-dimensional numpy array of 1's and 0's.
```python
cancer_data['target']
```

if we look at the shape of the array, see that it's a 1-dimensional array with 569 values(which was how many datapoints had).
```python
cancer_data['target'].shape
```

in order to interpret these 1's and 0's, need to know whether 1 or 0 is benign or malignant. This is given by the target_names data in the DataFrame.
```python
cancer_data['target_names']
```

this gives the array \['malignant' 'benign'] which tells the user that 0 means malignant and 1 means benign. Add this data to the Pandas DataFrame.
```python
df['target'] = cancer_data['target']
df.head()
```

```python
import pandas as pd
from sklearn.datasets import load_breast_cancer

cancer_data = load_breast_cancer()

df = pd.DataFrame(cancer_data['data'], columns=cancer_data['feature_names'])
df['target'] = cancer_data['target']
print(df.head())
```

result:
![contentImage](https://api.sololearn.com/DownloadFile?id=3747)

in this case, 0 means malignant and 1 means benign.

### Build a Logistic Regression Model
now that have taken a look at the data and gotten it into a comfortable format, can build the feature matrix X and target array y so that can build a Logistic Regression model.
```python
X = df[cancer_data.feature_names].values
y = df['target'].values
```

now create a Logistic Regression object and use the fit method to build the model.
```python
model = LogisticRegression()
model.fit(X, y)
```

when run this code get a Convergence Warning. this means that the model needs more time to find the optimal solution. One option is to increase the number of iterations. Can also switch to a different solver, which is what will do. The solver is the algorithm that the model uses to find the equation of the line. Can see possible solvers in the Logistic Regression [documentation](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html).
```python
model = LogisticRegression(solver='liblinear')
model.fit(X, y)
```

see what the model predicts for the first datapoint in the dataset. Recall that the predict method takes a 2-dimensional array so must put the datapoint in a list.
```python
model.predict([X[0]])
```

so the model predicts that the first datapoint is benign.

to see how well the model performs over the whole dataset, use the score method to see the accuracy of the model.
```python
model.score(X, y)
```

```python
import pandas as pd
from sklearn.datasets import load_breast_cancer
from sklearn.linear_model import LogisticRegression

cancer_data = load_breast_cancer()
df = pd.DataFrame(cancer_data['data'], columns=cancer_data['feature_names'])
df['target'] = cancer_data['target']

X = df[cancer_data.feature_names].values
y = df['target'].values

model = LogisticRegression(solver='liblinear')
model.fit(X, y)
print("prediction for datapoint 0:", model.predict([X[0]]))
print(model.score(X, y))
```

see that the model gets 96% of the datapoints correct.