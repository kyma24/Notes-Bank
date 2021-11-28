### Concerns with Training and Test Set
We are doing evaluation because we want to get an accurate measure of how well the model performs. If the dataset is small, the test set is going to be small. Thus, it might not be a good random assortment of datapoints, and by random chance, may end up with easy or difficult datapoints in the evaluation set.

Since the goal is to get the best possible measure of the metrics(accuracy, precision, recall and F1 score), we can do a little better than just a single training and test set.

Recall that the training and test split looks as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=3801)

As seen, all the values in the training set are never used to evaluate. It would be unfair to build the model with the training set and then evaluate with the training set, but we aren't getting as full a picture of the model performance as possible.

To see this empirically, try running the code which does a train/test split from before. We'll re-run it a few times and see the results. Each row is the result of a different random train/test split.
![contentImage](https://api.sololearn.com/DownloadFile?id=3802)

It can be seen that each time it is run, we get different values for the metrics. The accuracy ranges from 0.79 to 0.84, the precision from 0.75 to 0.81 and the recall from 0.63 to 0.75. These are wide ranges that just depend on how lucky or unlucky we were in which datapoints ended up in the test set.

Here's the code if you want to try running yourself and seeing the varying values of the metrics.
```python
import pandas as pd
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
from sklearn.model_selection import train_test_split
import numpy as np

df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
df['male'] = df['Sex'] == 'male'
X = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(X, y)

# building the model
model = LogisticRegression()
model.fit(X_train, y_train)

# evaluating the model
y_pred = model.predict(X_test)
print("accuracy: {0:.5f}".format(accuracy_score(y_test, y_pred)))
print("precision: {0:.5f}".format(precision_score(y_test, y_pred)))
print("recall: {0:.5f}".format(recall_score(y_test, y_pred)))
print("f1 score: {0:.5f}".format(f1_score(y_test, y_pred)))
```

note that instead of doing a single train/test split, we will split the data into a training set and test set multiple times.

### Multiple Training and Test Sets
We learned in the previous part that depending on the test set, we can get different values for the evaluation metrics. We want to get a measure of how well the model does in general, not just a measure of how well it does on one specific test set.

Instead of just taking a chunk of the data as the test set, let's break the dataset into 5 chunks. Let's assume we have 200 datapoints in the dataset.
![contentImage](https://api.sololearn.com/DownloadFile?id=3803)

Each of these 5 chunks will serve as a test set. When Chunk 1 is the test set, we use the remaining 4 chunks as the training set. Thus we have 5 training and test sets as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=3804)

Each of the 5 times we have a test set of 20%(40 datapoints) and a training set of 80%(160 datapoints). Thus, every datapoint is in exactly 1 test set.

### Building and Evaluating with Multiple Training and Test Sets
In the previous part we saw how we could make 5 test sets, each with a different training set.

Now for each training set, we build a model and evaluate it using the associated test set. Thus we build 5 models and calculate 5 scores.

Let's say we are trying to calculate the accuracy score for the model.
![contentImage](https://api.sololearn.com/DownloadFile?id=3916)

We report the accuracy as the mean of the 5 values:
```python
(0.83+0.79+0.78+0.80+0.75)/5 = 0.79
```

If we had just done a single training and test set and had randomly gotten the first one, we would have reported an accuracy of 0.83. If we had randomly gotten the last one, we would have reported an accuracy of 0.75. Averaging all these possible values helps eliminate the impact of which test set a datapoint lands in.

You will only see values this different when you have a small dataset. With large datasets we often just do a training and test set for simplicity.

This process for creating multiple training and test sets is called **k-fold cross validation**. The k is the number of chunks we split the dataset into. The standard number is 5, as we did in the example above.

The goal in cross validation is to get accurate measures for the metrics(accuracy, precision, recall). We are building extra models in order to feel confident in the numbers we calculate and report.

### Final Model Choice in k-fold Cross Validation
Now we have built 5 models instead of just one. How do we decide on a single model to use?

These 5 models were built just for evaluation purposes, so that we can report the metric values. We don't actually need these models and want to build the best possible model. The best possible model is going to be a model that uses all of the data. So we keep track of the calculated values for the evaluation metrics and then build a model using all of the data.

This may seem incredibly wasteful, but computers have a lot of computation power, so it's worth using a little extra to make sure we're reporting the right values for the evaluation metrics. We'll be using these values to make decisions, so calculating them correctly is very important.

note that Computation power for building a model can be a concern when the dataset is large; in these cases, we just do a train test split.