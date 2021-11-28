### Accuracy
in the previous module, calculated how well the model performed using accuracy. **Accuracy** is the percent of predictions that are correct.

if have 100 datapoints and predict 70 of them correctly and 30 incorrectly, the accuracy is 70%.

Accuracy is a very straightforward and easy to understand metric, however it's not always the best one. i.e. say that have a model to predict whether a credit card charge is fraudulent. Of 10000 credit card charges, have 9900 legitimate charges and 100 fraudulent charges. Could build a model that just predicts that every single charge is legitimate and it would get 9900/10000(99%) of the predictions correct!

Accuracy is a good measure if the classes are evenly split, but is very misleading if have imbalanced classes. <- this means that when there are more negative cases than positive cases and vice versa, it's not the most appealing choice.

Always use accuracy with caution. Need to know the distribution of the classes to know how to interpret the value.

### Confusion Matrix
as noticed in the previous part, care not only abt how many datapoints predict for the correct class, care about how many of the positive datapoints correctly as well as how many of the negative datapoints predict correctly.

can see all the important values in what is called the **Confusion Matrix**(or Error Matrix or Table of Confusion).

the Confusion Matrix is a table showing four values:
- datapoints predicted positive that are actually positive
- datapoints predicted positive that are actually negative
- datapoints predicted negative that are actually positive
- datapoints predicted negative that are actually negative.

the first and fourth are the datapoints predicted correctly and the second and third are the datapoints predicted incorrectly.

in the Titanic dataset, have 887 passengers, 342 survived (positive) and 545 didn't survive (negative). the model built has the following confusion matrix:

![contentImage](https://api.sololearn.com/DownloadFile?id=3790)

the blue shaded squares are the counts of the predictions that were correct. So of the 342 passengers that survived, predicted 233 of them correctly(and 109 incorrectly). Of the 545 passengers that didn't survive, predicted 480 correctly(and 65 incorrectly).

can use the confusion matrix to compute the accuracy. As a reminder, the accuracy is the number of datapoints predicted correctly divided by the total number of datapoints.
```python
(233 + 480) / (233 + 65 + 109 + 480) = 713 / 887 = 80.38%
```

this is indeed the same value that has been achieved previously.

note that the confusion matrix fully describes how a model performs on a dataset, though it is difficult to use to compare models.

### True Positives, True Negatives, False Positives, False Negatives
have names for each square of the confusion matrix.

a **true positive(TP)** is a datapoint predicted positively that were correct abt.
a **true negative(TN)** is a datapoint predicted negatively that were correct abt.
a **false positive(FP)** is a datapoint predicted positively that were incorrect abt.
a **false negative(FN)** is a datapoint predicted negatively that were incorrect abt.

often see the confusion matrix described as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=3791)

the four values of the confusion matrix are used to compute several different metrics.