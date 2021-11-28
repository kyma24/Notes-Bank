### Computation
When talking about how much **computation** is required for a machine learning algorithm, we separate it into two questions: how much computation is required to build the model and how much is required to predict.

A decision tree is very computationally expensive to build. This is because at every node we are trying every single feature and threshold as a possible split. We have to calculate the information gain of each of these possible splits each time. This is computationally very expensive.

Predicting with a decision tree on the other hand, is computationally very inexpensive. You just need to ask a series of yes/no questions about the datapoint to get to the prediction.

note that generally we care much more about the computation time for prediction than training. Predictions often need to happen in real time while a user is waiting for a result.

### Performance
Decision Trees can perform decently well depending on the data, though as we have discussed, they are prone to **overfitting**. Since a leaf node can have just one datapoint that lands there, it gives too much power to individual datapoints.

To remedy the overfitting issues, decision trees generally require some tuning to get the best possible model. Pruning techniques are used to limit the size of the gree and they help mitigate overfitting.

note that decision trees often take work to perform on par with how other models perform with no tuning.

### Interpretability
The biggest reason that people like choosing decision trees is because they are easily interpretable. Depending on what you're building a model for, you might need to give a reason why you made a certain prediction. A non-technical person can interpret a Decision Tree so it's easy to give an **explanation of a prediction**.

This particularly comes into play in legal situations. Say you are a bank and have a model to predict whether a person should be given a loan or not. It is important to be able to explain why the model made the decision, otherwise you could hide discriminatory practices within the model.

note that interpretability is the biggest advantage of Decision Trees. It will depend on the situation whether this is important for the problem.