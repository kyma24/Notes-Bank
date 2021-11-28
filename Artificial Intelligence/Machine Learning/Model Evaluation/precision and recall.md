### Precision
two commonly used metrics for classification are **precision** and **recall**.
Conceptually, **precision** refers to the percentage of positive results which are relevant and **recall** to the percentage of positive cases correctly classified.

both can be defined using quadrants from the confusion matrix, which recall as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=3792)

precision is the percent of the model's positive predictions that are correct, which is defined as follows:
![contentImage](https://api.sololearn.com/DownloadFile?id=4079)

if look at the confusion matrix for the model for the Titanic dataset, the precision can be calculated.
![contentImage](https://api.sololearn.com/DownloadFile?id=3793)

```python
precision = 233 / (233 + 65) = 0.7819
```

note that Precision is a measure of how precise the model is with its positive predictions.

### Recall
Recall is the percent of positive cases that the model predicts correctly. Will be using the confusion matrix to compute the result.
![contentImage](https://api.sololearn.com/DownloadFile?id=3794)

Mathematical definition of the recall:
![contentImage](https://api.sololearn.com/DownloadFile?id=4081)

calculate the recall for the model for the Titanic dataset.
![contentImage](https://api.sololearn.com/DownloadFile?id=3795)

![contentImage](https://api.sololearn.com/DownloadFile?id=4080)

note that Recall is a measure of how many of the positive cases the model can recall.

### Precision & Recall Trade-off
often will be in the situation of choosing between increasing the recall(while lowering the precision) or increasing the precision(and lowering the recall). It will depend on the situation which will want to maximize.

i.e. say that building a model to predict if a credit card charge is fraudulent. The positive cases for the model are fraudulent charges and the negative cases are legitimate charges.

consider two scenarios:
1. If predict the charge is fraudulent, will reject the charge.
2. If predict the charge is fraudulent, will call the customer to confirm the charge.

in case 1, will be a huge inconvenience for the customer when the model predicts fraud incorrectly(a false positive). In case 2, a false positive is a minor inconvenience for the customer.

the higher the false positives, the lower the precision. Because of the high cost to false positives in the first case, it would be worth having a low recall in order to have a very high precision. In case 2, would want more of a balance between precision and recall.

note that there isn't a hard and fast rule on what values of precision and recall are shooting for. It always depends on the dataset and the application.

### F1 Score
Accuracy was an appealing metric bc it was a single number. Precision and recall are two numbers so it's not always obvious how to choose between two models if one has a higher precision and the other has a higher recall.
The F1 score is an average of precision and recall so that have a single score for the model.

here's the mathematical formula for the F1 score:
![contentImage](https://api.sololearn.com/DownloadFile?id=4082)

calculate the F1 score for the model for the Titanic dataset.

will use the precision and recall numbers that previously calculated. The precision is 0.7819 and the recall is 0.6813.

the F1 score is as follows.
```python
2 (0.7819) (0.6813) / (0.7819 + 0.6813) = 0.7281
```

note that the F1 score is the harmonic mean of the precision and recall values.