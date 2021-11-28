### Decision Tree Diagram
Let's look at an example Decision Tree from the Titanic dataset. Within each internal node, we have the feature and threshold to split on, the number of samples and the distribution of the sames(# of didn't survive vs survived).
![contentImage](https://api.sololearn.com/DownloadFile?id=3893)

To interpret this, let's start by looking at the root node. It says:

male <= 0.5
samples = 887
value = \[545, 342\]

This means that the first split will be on the male column. If the value is <= 0.5(meaning the passenger is female) we go to the left child and if the value is > 0.5(meaning the passenger is male) we go to the right child.

There are 887 datapoints to start and 545 are negative cases(didn't survive) and 342 afre positive(did survive).

If you look at the two children of the root node, we can see how many datapoints were sent each way based on splitting on Sex. There are 314 female passengers in the dataset and 573 male passengers.

You can see that the second split for female passengers is different from the second split for male passengers.

### How to Make a Prediction
Look at the same decision tree diagram again.
![contentImage](https://api.sololearn.com/DownloadFile?id=3894)

Let's say would like to use this Decision Tree to make a prediction for a passenger with these values:

Sex: female
Pclass: 3
Fare: 25
Age: 30

We ask the question at each node and go to the left child if the answer is yes and to the right if the answer is no.

We start at the **root node**.

Is the value for the male feature <= 0.5? (this question could also be asked as "Is the passenger female?")
Since the answer is yes, we go to the left child.

Is the Pclass <= 0.5?
Since the answer is no, we go to the right child.

Is the Fare <= 23.35?
Since the answer is no, we go to the right child.

Now we're at a leaf node. Here's the path we took highlighted.
![contentImage](https://api.sololearn.com/DownloadFile?id=3895)

The leaf node that we end at has the following text:
```python
27
[24, 3]
```

This means there are 27 datapoints in the dataset that also land at this leaf node. 24 of them didn't survive and 3 of them survived. This means the prediction is that the passenger didn't survive.

note that because there are no rules as to how the tree is developed, the decision tree asks completely different questions of a female passenger than a male passenger.