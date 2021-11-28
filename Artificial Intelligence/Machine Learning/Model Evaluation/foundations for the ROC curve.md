talked abt the trade-off between precision and recall before. W/ a **Logistic Regression** model, have an easy way of shifting between emphasizing precision and emphasizing recall. The Logistic Regression model doesn't return a prediction, but it returns a probability value between 0 and 1. Typically it is said that if the value is >= 0.5, the prediction is that the passenger survived, and if the value is < 0.5, the passenger didn't survive. However, could choose any threshold between 0 and 1.

if make the threshold higher, will have fewer positive predictions, but the positive predictions are more likely to be correct. This means that the **precision** would be higher and the recall lower. On the other hand, if make the theshold lower, will have more positive predictions, so will be more likely to catch all the positive cases. This means that the recall would be higher and the precision lower.

note that each choice of a threshold is a different model. **An ROC(Receiver operating characteristic) Curve is a graph showing all of the possible models and their performance.**

### Sensitivity & Specificity
An ROC Curve is a graph of the **sensitivity** vs. the**specificity**. These values demonstrate the same trade-off that precision and recall demonstrate.

look back at the Confusion Matrix, as will be using it to define sensitivity and specificity.
![contentImage](https://api.sololearn.com/DownloadFile?id=3797)

the sensitivity is another term for recall, which is the true positive rate. Recall that it is calculated as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=4083)

the specificity is the true negative rate. It's calculated as follows.
![contentImage](https://api.sololearn.com/DownloadFile?id=4084)

have done a train test split on the Titanic dataset and gotten the following confusion matrix. Have 96 positive cases and 126 negative cases in the test set.
![contentImage](https://api.sololearn.com/DownloadFile?id=3798)

calculate the sensitivity and specificity.
```python
Sensitivity = 61/96 = 0.6354
Specificity = 105/126 = 0.8333
```

the goal is to maximize these two values, though generally making one larger makes the other lower. It will depend on the situation whether going to put more emphasis on sensitivity or specificity.

note that while generally look at precision and recall values, for graphing the standard is to use the sensitivity and specificity. It is possible to build a precision-recall curve, but it isn't commonly done.

### Sensitivity & Specificity in Scikit-learn
Scikit-learn has not defined functions for sensitivity and specificity, but can do it ourselves. Sensitivity is the same as recall, so it's easy to define.
```python
from sklearn.metrics import recall_score
sensitivity_score = recall_score
print(sensitivity_score(y_test, y_pred))
# 0.6829268292682927
```

now to define specificity, if realize that it is also the recall of the negative class, can get the value from the sklearn function precision_recall_fscore_support.

look at the output of precision_recall_fscore_support.
```python
from sklearn.metrics import
precision_recall_fscore_support
print(precision_recall_fscore_support(y, y_pred))
```

the second array is the recall, so can ignore the other three arrays. There are two values. The first is the recall of the negative class and the second is the recall of the positive class. The second value is the standard recall or sensitivity value, and can see the value matches what is achieved above. The first value is the specificity. So write a function to get just that value.
```python
def specificity_score(y_true, y_pred):
	p, r, f, s = precision_recall_fscore_support(y_true, y_pred)
	return r[0]

print(specificity_score(y_test, y_pred))
# 0.9214285714285714
```

note that in the code sample a random state in the train test split is used so that every run of the code will get the same results.
```python
import pandas as pd
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import recall_score, precision_recall_fscore_support

sensitivity_score = recall_score
def specificity_score(y_true, y_pred):
	p, r, f, s = precision_recall_fscore_support(y_true, y_pred)
	return r[0]
	
df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df [['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=5)

model = LogisticRegression()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)

print("sensitivity:", sensitivity_score(y_test, y_pred))
print("specificity:", specificity_score(y_test, y_pred))
```

### Adjusting the Logistic Regression Threshold in Sklearn
when using scikit-learn's predict method, are given 0 and 1 values of the prediction. However, behind the scenes the Logistic Regression model is getting a probability value between 0 and 1 for each datapoint and then rounding to either 0 or 1. If want to choose a different threshold besides 0.5, will want those probability values. Can use the **predict_proba** function to get them.
```python
(model.predict_proba(X_test))
```

the result is a numpy array with 2 values for each datapoint(e.g.\[0.78, 0.22]).
will notice that the two values sum to 1. The first value is the probability that the datapoint is in the 0 class(didn't survive) and the second is the probability that the datapoint is in the 1 class(survived). Only need the second column of this result, which can pull with the following numpy syntax.
```python
model.predict_proba(X_test)[:, 1]
```

now just want to compare these probability values with the threshold. Say want a threshold of 0.75. Will compare the above array to 0.75. This will give an array of True/False values which will be the array of predicted target values.
```python
y_pred = model.predict_proba(X_test)[:, 1] > 0.75
```

A threshold of 0.75 means need to be more confident in order to make a positive prediction. This results in fewer positive predictions and more negative predictions.

now can use any scikit-learn metrics from before using y_test as the true values and y_pred as the predicted values.
```python
print("precision:", precision_score(y_test, y_pred))
print("recall:", recall_score(y_test, y_pred))
```


```python
import pandas as pd
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import precision_score, recall_score
from sklearn.model_selection import train_test_split

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(X, y)

model = LogisticRegression()
model.fit(X_train, y_train)

print("predict proba:")
print(model.predict_proba(X_test))

y_pred = model.predicty_proba(X_test)[:, 1] > 0.75

print("precision:", precision_score(y_test, y_pred))
print("recall:", recall_score(y_test, y_pred))
```

note that setting the threshold to 0.5 would get the original Logistic Regression model. Any other threshold value yields an alternative model.