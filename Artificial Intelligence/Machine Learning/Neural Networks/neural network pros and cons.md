### Interpretability
While we can visualize the nodes in the hidden layer to understand on a high level what the neurla network is doing, it is impossible to answer the question "Why did datapoint x get prediction y?" Since there are so many nodes, each with their own coefficients, it isn't feasible to get a simple explanation of what the neural network is doing. This makes it a difficult model to **interpret** and use in certain business use cases.

### Computation
Neural networks can take a decent amount of **time to train**. Each node has its own coefficients and to train they are iteratively updated, so this can be time consuming. However, they are parallelizable, so it is possible to throw computer power at them to make them train faster.

note that once they're built, neural networks aren't slow to make predictions; however, they aren't as fast as some of the other models.

### Performance
The main draw to neural networks is their **performance**. On many problems, their performance simply can't be beat by other models. They can take some tuning of parameters to find the optimal performance, but they benefit from needing minimal feature engineering prior to building the model.

A lot of simpler problems, you can achieve equivalent performance with a simpler model like logistic regression, but with large unstructured datasets, neural networks outperform other models.