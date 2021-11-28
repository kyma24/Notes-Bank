### Comparing Different Models
So far we've used the evaluation techniques to get scores for a single model. These techniques will become incredibly useful as we introduce more models and want to determine which one performs the best for a specific problem.

Let's use the techniques to compare three models:
 - A logistic regression model using all of the features in the dataset
 - A logistic regression model using just the Pclass, Age, and Sex columns
 - A logistic regression model using just the Fare and Age columns
 
 We wouldn't expect the second or third model to do better since it has less info, but we might determine that using just those two or three columns yields comparable performance to using all the columns.
 
 note that Evaluation techniques are essential for deciding between multiple model options.
 
 ### Building the Models with Scikit-learn
 Let's write the code to build the two models in scikit-learn. Then we'll use k-fold cross validation to calculate the accuracy, precision, recall and F1 score for the two models so that we can compare them.
 
 First, we import the necessary modules and prep the data as we've done before.
 ```python
 from sklearn.model_selection import KFold
 from sklearn.linear_model import LogisticRegression
 from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
 import pandas as pd
 import numpy as np
 
 df = pd.read_csv('https://sololearn.com/uploads/files/titanic.csv')
 df['male'] = df['Sex'] == 'male'
```

now we can bulid the KFold object. We'll use 5 splits as that is the standard. Note that we want to create a single KFold object that all of the models will use. It would be unfair if different models got a different split of the data.
```python
kf = KFold(n_splits=5, shuffle=True)
```

Now we'll create three different feature matrices: X1, X2, and X3. All will have the same target y.
```python
X1 = df[['Pclass', 'male', 'Age', 'Siblings/Spouses', 'Parents/Children', 'Fare']].values
X2 = df[['Pclass', 'male', 'Age']].values
X3 = df[['Fare', 'Age']].values
y = df['Survived'].values
```

Since we'll be doing it several times, let's write a function to score the model. This function uses the KFold object to calculate the accuracy, precision, recall and F1 score for a Logistic Regression model with the given feature matrix X and target array y.

Then we call the function three times for each of the three feature matrices and see the results.
```python
print("Logistic Regression with all features")
score_model(X1, y, kf)
print()
print("Logistic Regression with Pclass, Sex & Age features")
score_model(X2, y, kf)
print()
print("Logistic Regression with Fare & Age features")
score_model(X3, y, kf)
```

note that you should expect to get slightly different results every time you run the code. The k-fold splits are chosen randomly, so there will be a little variation depending on what split each datapoint ends up in.

### Choosing a Best Model
Look at the results from the previous part.
```python
Logistic Regression with all features
accuracy: 0.7959055418015616
precision: 0.764272127669388
recall: 0.6783206767486641
f1 score: 0.7163036778464393

Logistic Regression with Pclass, Sex & Age features
accuracy: 0.7981908207960389
precision: 0.7715749823848419
recall: 0.6830371999703425
f1 score: 0.7232930032930033

Logistic Regression with Fare & Age features
accuracy: 0.6538944962864216
precision: 0.6519918328980114
recall: 0.23722965720416847
f1 score: 0.34438594236494796
```

If we compare the first two models, they have almost identical scores. The third model has lower scores for all four metrics. The first two are thus much better options than the third. This matches intuition since the third model doesn't have access to the sex of the passenger. Our expectation is that women are more likely to survive, so having the sex would be a very valuable predictor.

Since the first two models have equivalent results, it makes sense to choose the simpler model, the one that uses the Pclass, Sex & Age features.

Now that we've made a choice of a best model, we build a single final model using all of the data.
```python
model = LogisticRegression()
model.fit(X1, y)
```

Now we can make a prediction with the model.
```python
model.predict([[3, False, 25, 0, 1, 2]])
# Output: [1]
```

Note that we have only tried three different combinations of features. It's possible a different combination would also work.