### A Nonparametric ML Algorithm
So far we've been dealing with Logistic Regression. In Logistic Regression, we look at the data graphically and draw a line to separate the data. The model is determined by the coefficients that define the line. These coefficients are called **parameters**. Since the model is defined by these parameters, Logistic Regression is a **parametric** machine learning algorithm.

In this module, we'll introduce **Decision Trees**, which are an example of a **nonparametric** machine learning algorithm. Decision Trees won't be defined by a list of parameters.

### Tree Terminology
the reason many people love decision trees is bc they are very easy to interpret. It's basically a flow chart of questions that you answer about a datapoint until you get to a prediction.

Here's an example of a Decision Tree for the Titanic dataset. Will see later how the tree is constructed.

Each of the rectangles is called a **node**. The nodes which have a feature to split on are called **internal nodes**. The very first internal node at the top is called the **root node**. The final nodes where we make the predictions of the survived/didn't survive are called **leaf nodes**. Internal nodes all have two nodes below them, which we call the node's **children**.![contentImage](https://api.sololearn.com/DownloadFile?id=3841)

note that the terms for trees(root, leaf) come from the actual tree, though it's upside down since we generally draw the root at the top. We also use terms that view the tree as a family tree(child node & parent node).

### Interpreting a Decision Tree
To interpret the Decision Tree, let's run through an example. Let's say we want to know the prediction for a 10 year old male passenger in Pclass 2. At the first node, since the passenger's sex is male, we go to the right child. Then, since their age 10 which is <= 13 we go to the left child, and at the third node we go to the right child since the Pclass is 2. In the following diagram we highlight the path for this passenger.
![contentImage](https://api.sololearn.com/DownloadFile?id=3842)

Note that there are no rules that we use every feature, or what order we use the features, or for a continuous value(like Age), where we do the split. It is standard in a Decision Tree to have each split just have 2 options.

Decision Trees are often favored if you have a non-technical audience since they can easily interpret the model.

### How did we get the Decision Tree?
When building the Decision Tree, we don't just randomly choose which feature to split on first. We want to start by choosing the feature with the most **predictive power**. Look at the Decision Tree again.
![contentImage](https://api.sololearn.com/DownloadFile?id=3843)

Intuitively for the Titanic dataset, since women were often given priority on lifeboats, we expect the Sex to be a very important feature. So using this feature first makes sense. On each side of the Decision Tree, we will independently determine which feature to split on next. In the example above, the second split for women is on Pclass. The second split for men is on Age. We also note for some cases we do three splits and for some just two.

note that for any given dataset, there's a lot of different possible Decision Trees that could be created depending on the order you use the features. There are mathematical ways to choose the best Decision Tree.