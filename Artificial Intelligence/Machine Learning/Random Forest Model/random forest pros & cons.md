### Performance
Probably the biggest advantage of Random Forests is that they generally perform well without any tuning. They will also perform decently well on almost every dataset.

A linear model, for example, can't perform well on a dataset that can't be split with a line. It isn't possible to split the following dataset into a line without manipulating the features. However, a random forest will perform just fine on this dataset.
![contentImage](https://api.sololearn.com/DownloadFile?id=3945)

We can see this by looking at the code to generate the fake dataset above and comparing a Logistic Regression model with a Random Forest model. The function **make_circles** makes a classification dataset with concentric circles. We use kfold cross validation to compare the accuracy scores and see that the Logistic Regression model performs worse than random guessing but the Random Forest model performs quite well.
```python
from sklearn.datasets import make_circles
from sklearn.model_selection import KFold
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
import numpy as np

X, y = make_circles(noise=0.2, factor=0.5, random_state=1)

kf = KFold(n_splits=5, shuffle=True, random_state=1)
lr_scores = []
rf_scores = []
for train_index, test_index in kf.split(X):
	X_train, X_test = X[train_index], X[test_index]
	y_train, y_test = y[train_index], y[test_index]
	lr = LogisticRegression(solver='lbfgs')
	lr.fit(X_train, y_train)
	lr_scores.append(lr.score(X_test, y_test))
	rf = RandomForestClassifier(n_estimators=100)
	rf.fit(X_train, y_train)
	rf_scores.append(rf.score(X_test, y_test))
print("LR accuracy:", np.mean(lr_scores))
print("RF accuracy:", np.mean(rf_scores))
```

Output:
```python
LR accuracy: 0.36
RF accuracy: 0.8299999999999998
```

note that when looking to get a benchmark for a new classification problem, it is common practice to start by building a Logistic Regression model and a Random Forest model as these two models both have potential to perform well without any tuning. This will give you values for the metrics to try to beat. Oftentimes it is almost impossible to do better than these benchmarks.

### Interpretability
Random Forests, despite being made up of Decision Trees, aren't easy to interpret. A **random forest** has several decision trees, each of which is not a very good model, but when averaged, create an excellent model. Thus Random Forests aren't a good choice when looking for interpretability.

note that in most cases, interpretability isn't important.

### Computation
Random Forests can be a little slow to build, especially if you have a lot of trees in the random forest. Building a random forest involves building 10 - 100 (usually) decision trees. Each of the decision trees is faster to build than a standard decision tree because of how we don't compare every feature at every split, however given the quantity of decision trees it is often slow to build.

Similarly, predicting with a Random Forest will be slower than a Decision Tree since we have to do a prediction with each of the 10 - 100 decision trees in order to get the final prediction.

note that Random Forests aren't the fastest model, but generally this isn't a problem because computers have large computational power.