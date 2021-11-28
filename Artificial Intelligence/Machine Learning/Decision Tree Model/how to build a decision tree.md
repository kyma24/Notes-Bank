### What makes a Good Split
In order to determine which feature we should split on first, we need to score every possible split so we can choose the split with the highest score. The goal would be to perfectly split the data. If, for instance, all women survived the crash and all men didn't survive, splitting on Sex would be a perfect split. This is rarely going to happen with a real dataset, but we want to get as close to this as possible.

The mathematical term that will be measured is called **information gain**. This will be a value from 0 to 1 where 0 is the information gain of a useless split and 1 is the information gain of a perfect split.

First will discuss the intuition of what makes a good split.

Consider a couple of possible splits for the Titanic dataset. Will see how it splits the data and why one is better than the other.

First, try splitting on Age. Since Age is a numerical feature, need to pick a threshold to split on. Let's say we split on Age <= 30 and Age > 30. Let's see how many passengers we have on each side, and how many of them survived and how many didn't.
![contentImage](https://api.sololearn.com/DownloadFile?id=3844)

On both sides, we have about 40% of the passengers surviving. Thus we haven't really gained anything from splitting thedata this way.

Now let's try splitting on Sex.
![contentImage](https://api.sololearn.com/DownloadFile?id=3845)

We can see on the female side that the vast majority survived. On the male side, the vast majority didn't survive. This is a good split.

What we're going for is **homogeneity**(or **purity**) on each side. Ideally we would send all the passengers who survived to one side and those who didn't survive to the other side. We'll look at two different mathematical measurements of purity. We'll use the purity values to calculate the information gain.

Note that a good choice of a feature to split on results in each side of the split being pure. A set is pure if all the datapoints belong to the same class(either survived or didn't survive).

### Gini Impurity
**Gini Impurity** is a measure of how pure a set is. Will later see how we can use the gini impurity to calculate the information gain.

We calculate the gini impurity on a subset of the data based on how many datapoints in the set are passengers that survived and how many are passengers who didn't survive. It will be a value between 0 and 0.5 where 0.5 is completely impure(50% survived and 50% didn't survive) and 0 is completely pure(100% in the same class).

The formula for gini is as follows. p is the percent of passengers who survived. Thus (1-p) is the percent of passengers who didn't survive.
![contentImage](https://api.sololearn.com/DownloadFile?id=4085)

**Here's a graph of the gini impurity.**
![contentImage](https://api.sololearn.com/DownloadFile?id=3890)

We can see that the maximum value is 0.5 when exactly 50% of the passengers in the set survived. If all the passengers survived or didn't survive(percent is 0 or 1), then the value is 0.

Let's calculate the gini impurity for the examples from the previous part. First we had a split on Age <= 30 and Age > 30. Let's calculate the gini impurities of the two sets that we create.
![contentImage](https://api.sololearn.com/DownloadFile?id=3848)

on the left, for the passengers with Age <= 30, let's first calculate the percent of passengers who survived:

Percent of passengers who survived = 197/(197+328) = 0.3752
Percent of passengers who didn't survive = 1 - 0.375 = 0.6248

Now let's use that to calculate the gini impurity:
```python
2 * 0.3752 * 0.6248 = 0.4689
```

We can see that this value is close to 0.5, the maximum value for gini impurity. This means that the set is impure.

Now let's calculate the gini impurity for the right side, passengers with Age > 30.
```python
2 * 145/(145+217) * 217/(145+217) = 0.4802
```

This value is also close to 0.5, so again we have an impure set.

Now let's look at the gini values for the other split we tried, splitting on Sex.
![contentImage](https://api.sololearn.com/DownloadFile?id=3849)

On the left side, for female passengers, we calculate the following value for the gini impurity.
```python
2 * 233/(233+81) * 81/(233+81) = 0.3828
```

On the right side, for male passengers, we get the following value.
```python
2 * 109/(109+464) * 464/(109+464) = 0.3081
```

Both of these values are smaller than the gini values for splitting on Age, so we determine that splitting on the Sex feature is a better choice.

Right now we have two values for each potential split. The information gain will be a way of combining them into a single value.

### Entropy
**Entropy** is another measure of purity. It will be a value between 0 and 1 where 1 is completely impure(50% survived and 50% didn't survive) and 0 is completely pure(100% the same class).

The formula for entropy comes from physics. p again is the percent of passengers who survived.
![contentImage](https://api.sololearn.com/DownloadFile?id=4086)

**Here's a graph of the entropy function.**
![contentImage](https://api.sololearn.com/DownloadFile?id=3892)

You can see it has a similar shape to the gini function. Like the gini impurity, the maximum value is when 50% of the passengers in the set survived, and the minimum value is when either all or none of the passengers survived. The shape of the graphs are a little different. You can see that the entropy graph is a little fatter.

Now let's calculate the entropy values for the same two potential splits.
![contentImage](https://api.sololearn.com/DownloadFile?id=3852)
```python
On the left (Age<=30):
p = 197/(197+328) = 0.3752
Entropy = -(0.375 * log(0.375) + (1-0.375) * log(1-0.375)) = 0.9546
```
```python
And on the right (Age>30):
p = 145/(145+217) = 0.4006
Entropy =  -(0.401 * log(0.401) + (1-0.401) * log(1-0.401)) =  0.9713
```

These values are both close to 1, which means the sets are impure.

Now let's do the same calculation for the split on the Sex feature.
![contentImage](https://api.sololearn.com/DownloadFile?id=3853)
```python
On the left (female):
p = 233/(233+81) = 0.7420
Entropy = -(p * log(p) + (1-p) * log(1-p)) = 0.8237
```
```python
And on the right (male):
p = 109/(109+464) = 0.1902
Entropy =  -(p * log(p) + (1-p) * log(1-p)) = 0.7019
```

You can see that these entropy values are smaller than the entropy values above, so this is a better split.

Note that it's not obvious whether gini or entropy is a better choice. It often won't make a difference, but you can always cross validate to compare a Decision Tree with entropy and a Decision Tree with gini to see which performs better.

### Information Gain
Now that we have a way of calculating a numerical value for impurity, we can define **information gain**.
![contentImage](https://api.sololearn.com/DownloadFile?id=4087)

H is the impurity measure(either Gini impurity or entropy). S is the original dataset and A and B are the two sets we're splitting the dataset S into. In the first example abv, A is passengers with Age <= 30 and B is passengers with Age > 30. In the second example, A is female passengers and B is male passengers. |A| means the size of A.

Let's calculate this value for the two examples. Let's use Gini impurity as the impurity measure.

Have already calculated most of the Gini impurity values, though we need to calculate the Gini impurity of the whole set. THere are 342 passengers who survived and 545 passengers who didn't survive, out of a total of 887 passengers, so the gini impurity is as follows:
```python
Gini = 2 * 342/887 * 545/887 = 0.4738
```

Again, here's the first potential split.
![contentImage](https://api.sololearn.com/DownloadFile?id=3855)

Note that we have 197 + 328 = 525 passengers on the left(Age <= 30) and 145 + 217 = 362 passengers on the right(Age > 30). THus, pulling in the gini impurity values that have been calculated before, we get the following information gain:
```python
Information gain = 0.4738 - 525/887 * 0.4689 - 362/887 * 0.4802 = 0.0003
```

This value is very small, meaning we gain very little from this split.

Now let's calculate the information gain for splitting on Sex.
![contentImage](https://api.sololearn.com/DownloadFile?id=3856)

We have 233 + 81 = 314 passengers on the left(female) and 109 + 464 = 573 passengers on the right(male). Here is the information gain:
```python
Information gain = 0.4738 - 314/887 * 0.3828 - 573/887 * 0.3081 = 0.1393
```

Thus we can see that the information gain is much better for this split.
Therefore, splitting on Sex is a much better choice when building the decision tree than splitting on Age with threshold 30.

Note that the work we did was just to compare two possible splits. Will need to do the same calculations for every possible split in order to find the best one; however, don't have to do these computations by hand.

### Building the Decision Tree
We've built up the foundations we need for building the Decision Tree. Here's the process we go through:

To determine how to do the **first split**, we go over every possible split and calculate the information gain if we used that split. For numerical features like Age, PClass and Fare, we try every possible **threshold**. Splitting on the Age threshold of 50 means that datapoints with Age <= 50 are one group and those with Age > 50 are the other. Thus since there are 89 different ages in the dataset, we have 88 different splits to try for the age feature.

We need to try all of these potential splits:
1. Sex (male | female)
2. Pclass (1 or 2 | 3)
3. Pclass (1 | 2 or 3)
4. Age (0 | > 0)
5. Age (<= 1 | > 1)
6. Age (<= 2 | > 2)
7. etc...

There is 1 potential split for Sex, 2 potential splits for Pclass, and 88 potential splits for Age. There are 248 different values for Fare, so there are 247 potential splits for this feature. If we're only considering these four features, we have 338 potential splits to consider.

For each of these splits we calculate the information gain and we choose the split with the highest value.

Now, we do the same thing for the next level. Say we did the first split on Sex. Now for all the female passengers, we try all of the possible splits for each of the features and choose the one with the highest information gain. We can split on the same feature twice if that feature has multiple possible thresholds. Sex can only be split on once, but the Fare and Age features can be split on many times.

Independently, we do a similar calculation for the male passengers and choose the split with the **highest information gain**. Thus we may have a different second split for male passengers and female passengers.

We continue conducting this process until we have no more features to split on.

Note that this is a lot of things to try, but we just need to throw computation power at it. It does make Decision Trees a little slow to build, but once the tree is built, it is very fast to make a prediction.