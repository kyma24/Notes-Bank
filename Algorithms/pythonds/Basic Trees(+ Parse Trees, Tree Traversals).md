### Examples of Trees
Now that we've studied linear data structures like stacks and queues and have some experience with recursion, we'll look at a common data structure called the **tree**. Trees are used in many areas of computer science, including operating systems, graphics, database systems, and computer networking. Tree data structures have many things in common with their botanical cousins. A tree data structure has a root, branches, and leaves. The difference between a tree in nature and a tree in computer science is that a tree data structure has its root at the top and its leaves on the bottom.

Before we begin the study of tree data structures, let's look at a few common examples. The first example of a tree is a classification tree from biology. The figure below shows an example of the biological classification of some animals. From this simple example, we learn about several properties of trees. The first property this example demonstrates is that trees are hierarchical. By hierarchical, we mean that trees are structured in layers with the more general things near the top and the more specific things near the bottom. The top of the hierarchy is the Kingdom, the next layer of the tree(the "children" of the layer above) is the Phylum, then the Class, and so on. However, no matter how deep we go in the classification tree, all the organisms are still animals.
![[Pasted image 20210628090631.png]]

Notice that you can start at the top of the tree and folow a path made of circles and arrows all the way to the bottom. At each level of the tree we might ask ourselves a question and then follow the path that agrees with the answer. For example, we may ask, "Is this animal a Chordate or an Anthropod?" If the answer is "Chordate" then we follow that path and ask, "Is this Chordate a Mammal?" If not, we are stuck(but only in this simplified example). When we are at the Mammal level we ask, "Is this Mammal a Primate or a Carnivore?" We can keep following paths until we get to the very bottom of the tree where we have the common name.

A second property of trees is that all of the children of one node are independent of the children of another node. For example, the Genus Felis has the children Domestica and Leo. The Genus Musca also has a child named Domestica, but it is a different node and is independent of the Domestica child of Felis. This means that we can change the node that is the child of Musca without affecting the child of Felis.

A third property is that each leaf node is unique. We can specify a path from the root of the tree to a leaf that uniquely identifies each species in the animal kingdom; for example, Animalia → Chordate → Mammal → Carnivora → Felidae → Felis → Domestica.

Another example of a tree structure that you probably use every day is a file system. In a file system, directories, or folders, are structured as a tree. The figure below illustrates a small part of a Unix file system hierarchy.
![[Pasted image 20210628091311.png]]

The file system tree has much in common with the biological classification tree. You can follow a path from the root to any directory. That path will uniquely identify that subdirectory(and all the filew within). Another important property of trees, derived from their hierarchical nature, is that you can move entire sections of a tree(called a **subtree**) to a different position in the tree without affecting the lower levels of the hierarchy. For example, we could take the entire subtree starting with /etc/, detach etc/ from the root and reattach it under usr/. This would change the unique pathname to httpd from /etc/httpd to /usr/etc/httpd, but would not affect the contents or any children of the httpd directory.

A final example of a tree is a web page. The following is an exampl of a simple web page written using HTML. The figure below shows a tree that corresponds to each of the HTML tags used to create the page.
```html
<html xmlns="http://www.w3.org/1999/xhtml"
      xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type"
          content="text/html; charset=utf-8" />
    <title>simple</title>
</head>
<body>
<h1>A simple web page</h1>
<ul>
    <li>List item one</li>
    <li>List item two</li>
</ul>
<h2><a href="http://www.cs.luther.edu">Luther CS </a><h2>
</body>
</html>
```
![[Pasted image 20210628091637.png]]

The HTML source code and the tree accompanying the source illustrate another hierarchy. Notice that each level of the tree corresponds to a level of nesting inside the HTML tags. The first tag in the source is `<html>` and the last is `</html>`. All the rest of the tags in the page are inside the pair. If you check, you will see that this nesting property is true at all levels of the tree.

### Vocabulary and Definitions
Now that we have looked at examples of trees, we'll formally define a tree and its components.

**Node** - A node is a fundamental part of a tree. It can have a name, which we call the "key". A node may also have additional information. We call this additional information the "payload". While the payload information isn't central to many tree algorithms, it is often critical in applications that make use of trees.

**Edge** - An edge is another fundamental part of a tree. An edge connects two nodes to show that there is a relationship between them. Every node(except the root) is connected by exactly one incoming edge from another node. Each node may have several outgoing edges.

**Root** - The root of the tree is the only node in the tree that has  no incoming edges. In the last figure above, / is the root of the tree.

**Path** - A path is an ordered list of nodes that are connected by edges. For example, Mammal → Carnivora → Felidae → Felis → Domestica is a path.

**Children** - The set of nodes ${c}$ that have incoming edges from the same node are said to be the children of that node. In the last figure above, nodes log/, spool/, and yp/ are the children of node var/.

**Parent** - A nodes is the parent of all the nodes it connects to with outgoing edges. In the last figure above the node var/ is the parent of nodes log/, spool/, and yp/.

**Sibling** - Nodes in the tree that are children of the same parent are said to be siblings. The nodes etc/ and usr/ are siblings in the filesystem tree.

**Subtree** - A subtree is a set of nodes and edges comprised of a parent and all the descendants of that parent.

**Leaf Node** - A leaf node is a node that has no children. For example, Human and Chimpanzee are leaf nodes in the first example of animal hierarchy.

**Level** - The level of a node ${n}$ is the number of edges on the path from the root node to ${n}$. For example, the level of the Felis node in the first figure of animal hierarchy is five. By definition, the level of the root node is zero.

**Height** - The height of a tree is equal to the maximum level of any node in the tree. The height of the tree in the last figure above is two.

With the base vocabulary now defined, we can move on to a more formal definition of a tree. In fact, we'll provide two definitions of a tree. One definition involves nodes and edges. The second definition, which will prove to be very useful, is a recursive definition

*Definition One*: A tree consists of a set of nodes and a set of edges that connect pairs of nodes. A tree has the following properties:
- One node of the tree is designated as the root node.
- Every node ${n}$, except the root node, is connected by an edge from exactly one other node ${p}$, where ${p}$ is the parent of ${n}$.
- A unique path traverses from the root to each node.
- If each node in the tree has a maximum of two children, we say that the tree is a **binary tree**.

The figure below illustrates a tree that fits the first definition. The arrowheads on the edges indicate the direction of the connection.
![[Pasted image 20210628205238.png]]

*Definition Two*: A tree is either empty or consists of a root and zero or more subtrees, each of which is also a tree. The root of each subtree is connected to the root of the parent tree by an edge. The figure below illustrates this recursive definition of a tree. Using the recursive definition of a tree, we know that the tree below has at least four nodes, since each of the triangles representing a subtree must have a root. It may have many more nodes than that, but we don't know unless we look deeper into the tree.
![[Pasted image 20210628205415.png]]

### List of Lists Representation
In a tree represented by a list of lists, we'll begin with Python's list data structure and write the functions defined above. Although writing the interface as a set of operations on a list is a bit different from the other abstract data types we have implemented, it is interesting to do so because it provides us with a simple recursive data structure that we can look at and examine directly. In a list of lists tree, we'll store the value of the root node as the first element of the list. The second element of the list will itself be a list that represents the left subtree. The third element of the list will be another list that represents the right subtree. To illustrate this storage technique, let's look at an example. The figure below shows a simple tree and the corresponding list implementation:
![[Pasted image 20210628205636.png]]

```python
myTree = ['a',   #root
      ['b',  #left subtree
       ['d', [], []],
       ['e', [], []] ],
      ['c',  #right subtree
       ['f', [], []],
       [] ]
     ]
```

Notice that we can access subtrees of the list using standard list indexing. The root of the tree is `myTree[0]`, the left subtree of the root is `myTree[1]`, and the right subtree `myTree[2]`. The code below illustrates creating a simple tree using a list. Once the tree is constructed, we can access the root and the left and right subtrees. One very nice property of this list of lists approach is that the structure of a list representing a subtree adheres to the structure defined for a tree; the structure itself is recursive! A subtree that has a root value and two empty lists is a leaf node. Another nice feature of the list of lists approach is that it generalizes to a tree that has many subtrees. In the case where the tree is more than a binary tree, another subtree is just a list.
```python
myTree = ['a', ['b', ['d',[],[]], ['e',[],[]] ], ['c', ['f',[],[]], []] ]
print(myTree)
print('left subtree = ', myTree[1])
print('root = ', myTree[0])
print('right subtree = ', myTree[2])
```

Let's formalize this definition of the tree data structure by providing some functions that make it easy for us to use lists as trees. Note that we aren't going to define a binary tree class. The functions we will write will just help us manipulate a standard list as though we are working with a tree.
```python
def BinaryTree(r):
	return [r, [], []]
```

The `BinaryTree` function simply constructs a list with a root node and two empty sublists for the children. To add a left subtree to the root of a tree, we need to insert a new list into the second position of the root list. We must be careful. If the list already has something in the second position, we need to keep track of it and push it down the tree as the left child of the list we are adding. The code below shows the Python program for inserting a left child.
```python
def insertLeft(root,newBranch):
	t = root.pop(1)
	if len(t) > 1:
		root.insert(1,[newBranch,t,[]])
	else:
		root.insert(1,[newBranch,[],[]])
	return root
```

Notice that to insert a left child, we first obtain the (possibly empty) list that corresponds to the current left child. We then add the new left child, installing the old left child as the left child of the new one. This allows us to splice a new node into the tree at any position. The code for `insertRight` is similar to `insertLeft` and is shown below.
```python
def insertRight(root,newBranch):
	t = root.pop(2)
	if len(t) > 1:
		root.insert(2,[newBranch,[],t]))
	else:
		root.insert(2,[newBranch,[],[]])
	return root
```

To round out this set of tree-making functions(see below), let's write a couple of access functions for getting and setting the root value, as well as getting the left or right subtree.
```python
def getRootVal(root):
	return root[0]

def setRootVal(root,newVal):
	root[0] = newVal

def getLeftChild(root):
	return root[1]

def getRightChild(root):
	return root[2]
```

The code below exercises the tree functions we've just written.
```python
def BinaryTree(r):
    return [r, [], []]

def insertLeft(root,newBranch):
    t = root.pop(1)
    if len(t) > 1:
        root.insert(1,[newBranch,t,[]])
    else:
        root.insert(1,[newBranch, [], []])
    return root

def insertRight(root,newBranch):
    t = root.pop(2)
    if len(t) > 1:
        root.insert(2,[newBranch,[],t])
    else:
        root.insert(2,[newBranch,[],[]])
    return root

def getRootVal(root):
    return root[0]

def setRootVal(root,newVal):
    root[0] = newVal

def getLeftChild(root):
    return root[1]

def getRightChild(root):
    return root[2]

r = BinaryTree(3)
insertLeft(r,4)
insertLeft(r,5)
insertRight(r,6)
insertRight(r,7)
l = getLeftChild(r)
print(l)

setRootVal(l,9)
print(r)
insertLeft(l,11)
print(r)
print(getRightChild(getRightChild(r)))
```

### Nodes and References
The second method to represent a tree uses nodes and references. In this case we'll define a class that has attributes for the root value, as well as the left and right subtrees. Since this representation more closely follows the object-oriented programming paradigm, we'll continue to use this representation for the remainder of the chapter.

Using nodes and references, we might think of a tree being structured like the one shown below.
![[Pasted image 20210702085311.png]]

We'll start out with a simple class definition for the nodes and references approach as shown in the code below. The important thing to remember about this representation is that the attributes `left` and `right` will become references to other instances of the `BinaryTree` class. For example, when we insert a new left child into the tree we create another instance of `BinaryTree` and modify `self.leftChild` in the root to reference the new tree.
```python
class BinaryTree:
	def __init__(self,rootObj):
		self.key = rootObj
		self.leftChild = None
		self.rightChild = None
```

Notice that in the code above, the constructor function expects to get some kind of object to store the root. Just like you can store any object you like in a list, the root object of a tree can be a reference to any object. For the early examples, we'll store the name in the node as the root value. Using nodes and references to represent the tree above, we would create six instances of the BinaryTree class.

Next let's look at the functions we need to build the tree beyond the root node. To add a left child to the tree, we will create a new binary tree object and set the `left` attribute of the root to refer to this new object. The code for `insertLeft` is shown below.
```python
def insertLeft(self,newNode):
	if self.leftChild == None:
		self.leftChild = BinaryTree(newNode)
	else:
		t = BinaryTree(newNode)
		t.leftChild = self.leftChild
		self.leftChild = t
```

We must consider two cases for insertion. The first case is characterized by a node with no existing left child. When there is no left child, simply add a node to the tree. The second case is charactarized by a node with an existing left child. In the second case, we insert a node and push the existing child down one level in the tree. The second case is handled by the `else` statement on line 4 of the code above.

The code for `insertRight` must consider a symmetric set of cases. There will either be no right child, or we must insert the node between the root and an existing right child. The insertion code is shown below.
```python
def insertRight(self,newNode):
	if self.rightChild == None:
		self.rightChild = BinaryTree(newNode)
	else:
		t = BinaryTree(newNode)
		t.rightChild = self.rightChild
		self.rightChild = t
```

To round out the definition for a simple binary tree data structure, we will write accessor methods(see below) for the left and right children, as well as the root values.
```python
def getRightChild(self):
	return self.rightChild

def getLeftChild(self):
	return self.leftChild

def setRootVal(self,obj):
	self.key = obj

def getRootVal(self):
	return self.key
```

Now that we have all the pieces to create and manipulate a binary tree, let's use them to check on the structure a bit more. Let's make a simple tree with node a as the root, and add nodes b and c as children. The code below creates a tree and looks at some of the values stored in `key`, `left`, and `right`. Notice that both the left and right children of the root are themselves distinct instances of the `BinaryTree` class. As we said in the original recursive definition for a tree, this allows us to treat any child of a binary tree as a binary tree iself.
```python
class BinaryTree:
    def __init__(self,rootObj):
        self.key = rootObj
        self.leftChild = None
        self.rightChild = None

    def insertLeft(self,newNode):
        if self.leftChild == None:
            self.leftChild = BinaryTree(newNode)
        else:
            t = BinaryTree(newNode)
            t.leftChild = self.leftChild
            self.leftChild = t

    def insertRight(self,newNode):
        if self.rightChild == None:
            self.rightChild = BinaryTree(newNode)
        else:
            t = BinaryTree(newNode)
            t.rightChild = self.rightChild
            self.rightChild = t


    def getRightChild(self):
        return self.rightChild

    def getLeftChild(self):
        return self.leftChild

    def setRootVal(self,obj):
        self.key = obj

    def getRootVal(self):
        return self.key


r = BinaryTree('a')
print(r.getRootVal())
print(r.getLeftChild())
r.insertLeft('b')
print(r.getLeftChild())
print(r.getLeftChild().getRootVal())
r.insertRight('c')
print(r.getRightChild())
print(r.getRightChild().getRootVal())
r.getRightChild().setRootVal('hello')
print(r.getRightChild().getRootVal())
```

### Parse Tree
With the implementation of the tree data structure complete, we now look at an example of how a tree can be used to solve some real problems. In this section we'll look at parse trees. Parse trees can be used to represent real-world constructions like sentences or mathematical expressions.
![[Pasted image 20210702090605.png]]

The figure above shows the hierarchical structure of a simple sentence. Representing a sentence as a tree structure allows us to work with the individual parts of the sentece by using subtrees.
![[Pasted image 20210702090740.png]]

We can also represent a mathematical expression such as ${((7 + 3) * (5 - 2))}$ as a parse tree, as shown in the figure above. We already looked at fully parenthesized expressions, so what do we know about this expression? We know that multiplication has a higher precedence than either addition or subtraction. Because of the parentheses, we know that before we can do the multiplication we must evaluate the parenthesized addition and subtraction expressions. The hierarchy of the tree helps us understand the order of evaluation for the whole expression. Before we can evaluate the top-level multiplication, we must evaluate the addition and subtraction in the subtrees. The addition, which is the left subtree, evaluates to 10. The subtraction, which is the right subtree, evaluates to 3. Using the hierarchical structure of trees, we can simply replaces an entire subtree with one node once we have evaluated the expressions in the children. Applying this replacement procedure gives us the simplified tree shown below.
![[Pasted image 20210702092202.png]]

In the rest of this section we're going to examine parse trees in more detail. In particular we'll look at:
- how to build a parse tree from a fully parenthesized mathematical expression
- how to evaluate the expression stored in a parse tree
- how to recover the original mathematical expression from a parse tree

The first step in building a parse tree is to break up the expression string into a list of tokens. There are four different kinds of tokens to consider: left parentheses, right parentheses, operators, and operands. We know that whenever we read a left parenthesis we are starting a new expression, and hence we should create a new tree to correspond to that expression.Conversely, whenever we read a right parenthesis, we have finished an expression. We also know that operands are going to be leaf nodes and children of their operators. Finally, we know that every operator is going to have both a left and a right child.

Using the information from above we can define four rules as follows:
1. If the current token is a `'('`, add a new node as the left child of the current node, and descend to the left child.
2. If the current token is in the list `['+','-','/','*']`, set the root value of the current node to the operator represented by the current token. Add a new node as the right child of the current node and descend to the right child.
3. If the current token is a number, set the root value of the current node to the number and return to the parent.
4. If the current token is a `')'`, go to the parent of the current node.

Before writing the Python code, let's look at an example of the rules outlined above in action. We will use the expression ${(3+(4*5))}$. We will parse this expression into the following list of character tokens `['(','3','+','(','4','*','5',')',')']`. Initially we'll start out with a parse tree that consists of an empty root node. The figure below illustrates the structure and contents of the parse tree, as each new token is processed.
![[Pasted image 20210703105754.png]]
![[Pasted image 20210703105807.png]]
![[Pasted image 20210703105852.png]]
![[Pasted image 20210703105908.png]]
![[Pasted image 20210703105914.png]]
![[Pasted image 20210703105918.png]]
![[Pasted image 20210703105924.png]]
![[Pasted image 20210703105928.png]]

Using the figure above, let's walk through the example step by step:

a. Create an empty tree
b. Read ( as the first token. By rule 1, create a new node as the left child of the root. Make the current node this new child.
c. Read 3 as the next token. By rule 3, set the root value of the current node to 3 and go back up the tree to the parent.
d. Read + as the next token. By rule 2, set the root value of the current node to + and add a new node as the right child. The new right child becomes the current node.
e. Read a ( as the next token. By rule 1, create a new node as the left child of the current node. The new left child becomes the current node.
f. Read a 4 as the next token. By rule 3, set the value of the current node to 4. Make the parent of 4 the current node.
g. Read \* as the next token. By rule 2, set the root value of the current node to \* and create a new right child. The new right child becomes the current node.
h. Read 5 as the next token. By rule 3, set the root value of the current node to 5. Make the parent of 5 the current node.
i. Read ) as the next token. By rule 4 we make the parent of * the current node.
j. Read ) as the next token. By rule 4 we make the parent of + the current node. At this point there is no parent for + so we are done.

From the example above, it is clear that we need to keep track of the current node as well as the parent of the current node. The tree interface provides us with a way to get children of a node, through the `getLeftChild` and `getRightChild` methods, but how can we keep track of the parent? A simple solution to keeping track of parents as we traverse the tree is to use a stack. Whenever we want to descend to a child of the current node, we first push the current node on the stack. When we want to return to the parent of the current node, we pop the parent off the stack.

Using the rules described above, along with the `Stack` and `BinaryTree` operations, we are now ready to write a Python function to create a parse tree. The code for the parse tree builder is presented in the code below.
```python
from pythonds.basic import Stack
from pythonds.trees import BinaryTree

def buildParseTree(fpexp):
    fplist = fpexp.split()
    pStack = Stack()
    eTree = BinaryTree('')
    pStack.push(eTree)
    currentTree = eTree

    for i in fplist:
        if i == '(':
            currentTree.insertLeft('')
            pStack.push(currentTree)
            currentTree = currentTree.getLeftChild()

        elif i in ['+', '-', '*', '/']:
            currentTree.setRootVal(i)
            currentTree.insertRight('')
            pStack.push(currentTree)
            currentTree = currentTree.getRightChild()

        elif i == ')':
            currentTree = pStack.pop()

        elif i not in ['+', '-', '*', '/', ')']:
            try:
                currentTree.setRootVal(int(i))
                parent = pStack.pop()
                currentTree = parent

            except ValueError:
                raise ValueError("token '{}' is not a valid integer".format(i))

    return eTree

pt = buildParseTree("( ( 10 + 5 ) * 3 )")
pt.postorder()  #defined and explained in the next section
```

The four rules for building a parse tree are coded as the first four clauses of the `if` statement on lines 12, 17, 23, and 26 of the code above. In each case you can see that the code implements the rule, as described above, with a few calls to the `BinaryTree` or `Stack` methods. The only error checking we do in this function is in the `else` clause where a `ValueError` exception will be raised if we get a token from the list that we don't recognize.

Now that we have built a parse tree, what can we do with it? As a first example, we'll write a function to evaluate the parse tree, returning the numerical result. To write this function, we'll make use of the hierarchical nature of the tree. Look back at the second figure in this section. Recall that we can replace the original tree with the simplified tree shown in the figure after. This suggests that we can write an algorithm that evaluates a parse tree by recursively evaluating each subtree.

As we have done with past recursive algorithms, we'll begin the design for the recursive evaluation function by identifying the base case. A natural base case for recursive algorithms that operate on tree is to check for a leaf node. In a parse tree, the leaf nodes will always be operands. Since numerical objects like integers and floating points require no further interpretation, the `evaluate` function can simply return the value stored in the leaf node. The recursive step that moves the function toward the base case is to call `evaluate` on both the left and the right children of the current node. The recursive call effectively moves us down the tree, toward a leaf node.

To put the results of the two recursive calls together, we can simply apply the operator stored in the parent node to the results returned from evaluating both children. In the example from the third figure in this section we see that the two children of the root evaluate to themselves, namely 10 and 3. Applying the multiplication operator gives us a final result of 30.

The code for a recursive `evaluate` function is shown in the code below. First, we obtain references to the left and the right children of the current node. If both the left and right children evaluate to `None`, then we know that the current node is really a leaf node. This check is on the seventh line. If the current node isn't a leaf node, look up in the operator in the current node and apply it to the results from recursively evaluating the left and right children.

To implement the arithmetic, we use a dictionary with the keys `'+', '-', '*'`, and `'/'`. The values stored in the dictionary are functions from Python's operator module. The operator module provides us with the functional versions of many commonly used operators. When we look up an operator in the dictionary, the corresponding function object is retrieved. Since the retrieved object is a function, we can call it in the usual way `function(param1, param2)`. So the lookup `opers['+'](2,2)` is equivalent to `operator.add(2,2)`.
```python
import operator
def evaluate(parseTree):
	opers = {'+':operator.add, '-':operator.sub, '*':operator.mul, '/':operator.truediv}
	
	leftC = parseTree.getLeftChild()
	rightC = parseTree.getRightChild()
	
	if leftC and rightC:
		fn = opers[parseTree.getRootVal()]
		return fn(evaluate(leftC), evaluate(rightC))
	else:
		return parseTree.getRootVal()
```

Finally, we will trace the `evaluate` function on the parse tree we created in the fourth figure in the section. When we first call `evaluate`, we pass the root of the entire tree as the parameter `parseTree`. Then we obtain references to the left and right children to make sure they exist. The recursive call takes place on the ninth line. We begin by looking up the operator in the root of the tree, which is `'+'`. The `'+'` operator maps to the `operator.add` function call, which takes two parameters. As usual for a Python function call, the first thing Python does is to evaluate the parameters that are passed to the function. In this case both parameters are recursive function calls to the `evaluate` function. Using left-to-right evaluation, the first recursive call goes to the left. In the first recursive call the `evaluate` function is given the left subtree. We find that the node has no left or right children, so we are in a leaf node. When we are in a leaf node we just return the value stored in the leaf node as a result of the evaluation. In this case we return the integer 3.

At this point we have one parameter evaluated for our top-level call to `operator.add`. But we aren't done yet. Continuing the left-to-right evaluation of the parameters, we now make a recursive call to evaluate the right child of the root. We find that the node has both a left and right child so we look up the operator stored in this node, `'*'`, and call this function using the left and right children as the parameters. At this point you can see that both recursive calls will be to leaf nodes, which will evaluate to the integers four and five respectively. With the two parameters evaluated, we return the result of `operator.mul(4,5)`. At this point we have evaluated the operands for the top level `'+'` operator and all that is left to do is finish the call to `operator.add(3,20)`. The result of the evaluation of the entire expression tree for ${(3 + (4 * 5))}$ is 23.

### Tree Traversals
Now that we've examined the basic functionality of the tree data structure, it is time to look at some additional usage patterns for trees. These usage patterns can be divided into the three ways that we access the nodes of the tree. There are three comonly used patterns to visit all the nodes in a tree. The difference between these patterns is the order in which each node is visited. We call this visitation of the nodes a "traversal". The three traversals we will look at are called **preorder**, **inorder**, and **postorder**. Let's start out by defining these three traversals more carefully, then look at some examples where these patterns are useful.

**preorder**
In a preorder traversal, we visit the root node first, then recursively do a preorder traversal of the left subtree, followed by a recursive preorder traversal of the right subtree.

**inorder**
In an inorder traversal, we recursively do an inorder traversal on the left subtree, visit the root node, and finally do a recursive inorder traversal of the right subtree.

**postorder**
In a postorder traversal, we recursively do a postorder traversal of the left subtree and the right subtree followed by a visit to the root node.

Let's look at some examples that illustrate each of these three kinds of traversals. First let's look at the preorder traversal. As an example of a tree to traverse, we'll represent this book as a tree. The book is the root of the tree, and each chapter is a child of the root. Each section within a chapter is a child of the chapter, and each subsection is a child of its section, and so on. The figure below shows a limited version of a book with only two chapters. Note that the traversal algorithm works for trees with any number of children, but we will stick with binary trees for now.
![[Representing a Book as a Tree.png]]

Suppose that you wanted to read this book from front to back. The preorder traversal gives you exactly that ordering. Starting at the root of the tree(the Book node) we'll follow the preorder traversal instructions. We recursively call `preorder` on the left child, in this case Chapter1. We again recursively call `preorder` on the left child to get to Section 1.1. Since Section 1.1 has no children, we don't make any additional recursive calls. When we are finished with Section 1.1, we move up the tree to Chapter 1. At this point we still need to visit the right subtree of Chapter 1, which is Section 1.2. As before we visit the left subtree, which brings us to Section 1.2.1, then we visit the node for Section 1.2.2. With section 1.2 finished, we return to Chapter 1. then we return to the Book node and follow the same procedure for Chapter 2.

The code for writing tree traversals is surprisingly elegant, largely because the traversals are written recursively. The code below shows the Python code for a preorder traversal of a binary tree.

You may wonder, what is the best way to write an algorithm like preorder traversal? Should it be a function that simply uses a tree as a data structure, or should it be a method of the tree data structure itself? The code below shows a version of the preorder traversal written as an external function that takes a binary tree as a parameter. The external function is particularly elegant because the base case is simply to check if the tree exists. If the tree parameter is `None`, then the function returns without taking any action.
```python
def preorder(tree):
	if tree:
		print(tree.getRootVal())
		preorder(tree.getLeftChild())
		preorder(tree.getRightChild())
```

We can also implement `preorder` as a method of the `BinaryTree` class. The code for implementing `preorder` as an internal method is shown below. Notice what happens when we move the code from internal to external. In general, we just replace `tree` with `self`. However, we also need to modify the base case. The internal method must check for the existence of the left and the right children *before* making the recursive call to `preorder`.
```python
def preorder(self):
	print(self.key)
	if self.leftChild:
		self.leftChild.preorder()
	if self.rightChild:
		self.rightChild.preorder()
```

Which of these two ways to implement `preorder` is best? The answer is that implementing `preorder` as an external function is probably better in this case. The reason is that you very rarely want to just traverse the tree. In most cases you are going to want to accomplish something else while using one of the basic traversal patterns. In fact, we'll see in the next example that the `postorder` traversal pattern follows very closely with the code we wrote earlier to evaluate a parse tree. Therefore we'll write the rest of the traversals as external functions.

The algorithm for the `postorder` traversal, shown in the code below, is nearly identical to `preorder` except that we move the call to print to the end of the function.
```python
def postorder(tree):
	if tree != None:
		postorder(tree.getLeftChild())
		postorder(tree.getRightChild())
		print(tree.getRootVal())
```

We have already seen a common use for the postorder traversal, namely evaluating a parse tree. Look back at the code in the last section. What we are doing is evaluating the left subtree, evaluating the right subtree, and combining them in the root through the function call to an operator. Assume that the binary tree is going to store only expression tree data. Let's rewrite the evaluation function, but model it even more closely on the `postorder` code in the code above(see below).
```python
def postordereval(tree):
	opers = {'+':operator.add, '-':operator.sub, '*':operator.mul, '/':operator.truediv}
	res1 = None
	res2 = None
	if tree:
		res1 = postordereval(tree.getLeftChild())
		res2 = postordereval(tree.getRightChild())
		if res1 and res2:
			return opers[tree.getRootVal()](res1,res2)
		else:
			return tree.getRootVal()
```

Notice that the form in the second code above is the same as the form in the code above, except that instead of printing the key at the end of the function, we return it. This allows us to save the values returned from the recursive calls in lines 6 and 7. We then use these saved values along with the operator on the ninth line.

The final traversal we'll look at in this section is the inorder traversal. In the inorder traversal we visit the left subtree, followed by the root, and finally the right subtree. The code below shows the code for the inorder traversal. Notice that in all three of the traversal functions we're simply changing the position of the `print` statement with respect to the two recursive function calls.
```python
def inorder(tree):
	if tree != None:
		inorder(tree.getLeftChild())
		print(tree.getRootVal())
		inorder(tree.getRightChild())
```

If we perform a simple inroder traversal of a parse tree we get our original expression back, without any parentheses. Let's modify the basic inorder algorithm to allow us to recover the fully parenthesized version of the expression. The only modifications we'll make to the basic template are as follows: print a left parenthesis *before* the recursive call to the left subtree, and print a right parenthesis *after* the recursive call to the right subtree. The modified code is shoiwn below.
```python
def printexp(tree):
	sVal = ""
	if tree:
		sVal = '(' + printexp(tree.getLeftChild())
		sVal = sVal + str(tree.getRootVal())
		sVal = sVal + printexp(tree.getRightChild()) + ')'
	return sVal
```

Notice that the `printexp` function as we have implemented it puts parentheses around each number. While not incorrect, the parentheses are clearly not needed. (Modifying the `printexp` function to remove this set of parentheses can be an exercise).