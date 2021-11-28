### How to Build an ROC Curve
the ROC curve is a graph of the **specificity** vs the **sensitivity**. Build a Logistic Regression model and then calculate the specificity and sensitivity for every possible threshold. Every predicted probability is a threshold. If have 5 datapoints with the following predicted probabilities: 0.3, 0.4, 0.6, 0.7, 0.8, would use each of those 5 values as a threshold.

note that actually plot the sensitivity vs (1-specificity). There is no strong reason for doing it this way besides that it's the standard.

start by looking at the code to build the ROC curve. Scikit-learn has a roc_curve function that can be used. The function takes the true target values and the predicted probabilities from the model.

first use the predict_proba method on the model to get the probabilities. Then call the roc_curve function. The roc_curve function returns an array of the false positive rates, an array of the true positive rates and the thresholds. the false positive rate is 1-specificity(x-axis) and the true positive rate is another term for the sensitivity(y-axis). The threshold values won't be needed in the graph.

here's the code for plotting the ROC curve in matplotlib. Note that also have code for plotting a diagonal line. This can help visually see how far the model is from a model that predicts randomly.

assume that already have a dataset that has been split into a training set and test set.
```python
model = LogisticRegression()
model.fit(X_train, y_train)
y_pred_proba = model.predict_proba(X_test)
fpr, tpr, thresholds = roc_curve(y_test, y_pred_proba[:,1])

plt.plot(fpr, tpr)
plt.plot([0, 1], [0, 1], linestyle='--')
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.0])
plt.xlabel('1 - specificity')
plt.ylabel('sensitivity')
plt.show()
```
![contentImage](https://api.sololearn.com/DownloadFile?id=3784)

note that as don't use the threshold values to build the graph, the graph doesn't tell the user what threshold would yield each of the possible models.

### ROC Curve Interpretation
the ROC curve is showing the performance, not of a single model, but of many models. Each choice of threshold is a different model.

look at the ROC curve with these points highlighted.
![contentImage](https://api.sololearn.com/DownloadFile?id=3869)

each point A, B & C refers to a model with a different threshold.

Model A has a sensitivity of 0.6 and a specificity of 0.9 (recall that the graph is showing 1-specificity)
Model B has a sensitivity of 0.8 and a specificity of 0.7.
Model C has a sensitivity of 0.9 and a specificity of 0.5.

how to choose between these models will depend on the specifics of the situation.

note that the closer the curve gets to the upper left corner, the better the performance. The line should never fall below the diagonal line as that would mean it performs worse than a random model.

### Picking a Model from the ROC Curve
when ready to finalize the model, have to choose a single threshold that wll be used to make predictions. The ROC curve is a way of helping the user choose the ideal threshold for the problem.

look again at the ROC curve with three points highlighted:
![contentImage](https://api.sololearn.com/DownloadFile?id=3870)

if are in a situation where it's more important that all of the positive predictions are correct than catch all the positive cases(meaning that predict most of the negative cases correctly), should choose the model with higher specificity(model A)

if are in a situation where it's important to catch as many of the positive cases as possible, should choose the model with the higher sensitivity(model C).

if want a balance between sensitivity and specificity, should choose model B.

### Area Under the Curve
sometimes want to use the ROC curve to compare two different models.
here's a comparison of the ROC curves of two models.
![contentImage](https://api.sololearn.com/DownloadFile?id=3788)

can see that the blue curve outperforms the orange one since the blue line is almost always above the orange line.

to get an empirical measure of this, will calculate the Area Under the Curve, also called the AUC. This is the area under the ROC curve. It's a value between 0 and 1, the higher the better.

Since the ROC is a graph of all the different Logistic Regression models with different thresholds, the AUC doesn't measure the performance of a single model. It gives a general sense of how well the Logistic Regression model is performing. To get a single model, still need to find the optimal threshold for the problem.

will use scikit-learn to help calculate the area under the curve. Can use the roc_auc_score function.
```python
(roc_auc_score(y_test, y_pred_proba[:,1]))
```

here are the values for the two lines:
```python
Blue AUC: 0.8379
Orange AUC: 0.7385
```

can see empirically that the blue is better.

can use the roc_auc_score function to calculate the AUC score of a Logistic Regression model on the Titanic dataset. Build two Logistic Regression models, model1 with 6 features and model2 with just Pclass and male features. See that the AUC score of model1 is higher.

```python
import pandas as pd
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import roc_auc_score

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(X, y)

model1 = LogisticRegression()
model1.fit(X_train, y_train)
y_pred_proba1 = model1.predict_proba(X_test)
print("model 1 AUC score:", roc_auc_score(y_test, y_pred_proba1[:, 1]))

model2 = LogisticRegression()
model2.fit(X_train[:, 0:2], y_train)
y_pred_proba2 = model2.predict_proba(X_test[:, 0:2])
print("model 2 AUC score:", roc_auc_score(y_test, y_pred_proba2[:, 1]))
```

note that this metric tells the user how well in general a Logistic Regression model performs on the data. As an ROC curve shows the performance of multiple models, the AUC is not measuring the performance of a single model.