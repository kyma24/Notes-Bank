### Accuracy, Precision, Recall & F1 Score in Sklearn
Scikit-learn has a function built in for each of the metrics that have introduced. Have a separate function for each of the accuracy, precision, recall and F1 score.

in order to use them, start by recalling the code from the previous module to build a Logistic Regression model. The code reads in the Titanic dataset from the csv file and puts it in a Pandas DataFrame. Then create a feature matrix X and target values y. Create a Logistic Regression model and fit it to the dataset. Finally, create a variable y_pred of the predictions.
```python
df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values
model = LogisticRegression()
model.fit(X, y)
y_pred = model.predict(X)
```

now ready to use the metric functions. Import them from scikit-learn.
```python
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
```

each function takes two 1-dimensional numpy arrays: the true values of the target & the predicted values of the target. Have the true values of the target and the predicted values of the target. Thus can use the metric functions as follows.
```python
print("accuracy:", accuracy_score(y, y_pred))
print("precision:", precision_score(y, y_pred))
print("recall:", recall_score(y, y_pred))
print("f1 score:", f1_score(y, y_pred))
```

see that the accuracy is 80% which means that 80% of the model's predictions are correct. the precision is 78%, which is the percent of the model's positive predictions that are correct. The recall is 68%, which is the percent of the positive cases that the model is predicted correctly. The F1 score is 73%, which is an average of the precision and recall.

note that w/ a single model, the metric values don't tell a lot. For some problems a value of 60% is good, and for others a value of 90% is good, depending on difficulty of problem. will use the metric values to compare different models to pick the best one.

### Confusion Matrix in Sklearn
Scikit-learn has a confusion matrix function that can use to get the four values in the confusion matrix(true positives, false positives, false negatives, and true negatives). Assuming y is the true target values and y_pred is the predicted values, can use the confusion_matrix function as follows:
```python
from sklearn.metrics import confusion_matrix
print(confusion_matrix(y, y_pred))
# Output:
# [[475 70]
# [103 239]]
```

scikit-learn reverses the confusion matrix to show the negative counts first. Here is how the confusion matrix should be labeled.
![contentImage](https://api.sololearn.com/DownloadFile?id=3923)

this is how would typically draw the confusion matrix.
![contentImage](https://api.sololearn.com/DownloadFile?id=3924)

note that since negative target values correspond to 0 and positive to 1, scikit-learn has ordered them in this order.