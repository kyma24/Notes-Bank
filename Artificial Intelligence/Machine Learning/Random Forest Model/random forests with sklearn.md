### Review of Breast Cancer Dataset
Recall that the dataset has **measures** of different attributes of a lump in breast tissue and a **label** of whether or not the tumor is cancerous.

Here's the code for pulling the data from sklearn:
```python
import pandas as pd
from sklearn.datasets import load_breast_cancer

cancer_data = load_breast_cancer()
df = pd.DataFrame(cancer_data['data'], columns=cancer_data['feature_names'])
df['target'] = cancer_data['target']

X = df[cancer_data.feature_names].values
y = df['target'].values
print('data dimensions', X.shape)
```
note that the dataset has 569 datapoints and 30 features.

### Random Forest with Sklearn
The syntax for building and using a **Random Forest** model is the same as it was for Logistic Regression and Decision Trees. The builders of scikit-learn intentionally made it so that it would be easy to switch between and compare different models.

Here's the import statement for importing the Random Forest model for classification:
```python
from sklearn.ensemble import RandomForestClassifier
```

We'll first split the dataset into a training set and test set.
```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=101)
```

We have added the **random state** parameter here so that it will do the same split every time we run the code. Without the random state, we'd expect different datapoints in the training and testing sets each time we run the code which can make it harder to test the code.

Then we create the **RandomForestClassifier** object and use the fit method to build the model on the training set.
```python
rf = RandomForestClassifier()
rf.fit(X_train, y_train)
```

Now we can use the model to make a prediction. For example, let's take the first row of the test set and see what the prediction is. Recall that the **predict** method takes an array of points, so even when we have just one point, we have to put it in a list.
```python
first_row = X_test[0]
print("prediction:", rf.predict([first_row]))
print("true value:", y_test[0])
# prediction: [1]
# true value: 1
```

These results mean that the model predicted that the lump was cancerous and that was correct.

We can use the **score** method to calculate the accuracy over the whole test set.
```python
print("random forest accuracy:", rf.score(X_test, y_test))
# random forest accuracy: 0.965034965034965
```

Thus the accuracy is 96.5%. We can see how this compares to the Decision Tree model.
```python
dt = DecisionTreeClassifier()
dt.fit(X_train, y_train)
print("decision tree accuracy:", dt.score(X_test, y_test))
# decision tree accuracy: 0.9020979020979021
```

So the **accuracy** for the decision tree model is 90.2%, much worse than that for the random forest.

Note how similar the scikit-learn code for Logistic Regression is to the Decision Trees. This makes it very easy to try and compare different models.