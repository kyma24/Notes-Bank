Graphs are a more general structure than the trees studied in the last chapter; in fact you can think of a tree as a special kind of graph. Graphs can be used to represent many interesting things about our world, including systems of roads, airline flights from city to city, how the Internet is connected, or even the sequence of classes you must take to complete a major in computer science. We will see that cone we have a good representation for a problem, we can use some standard graph algorithms to solve what otherwise might seem to be a very difficult problem.

While it is relatively easy for humans to look at a road map and understand the relationships between different places, a computer has no such knowledge. However, we can also think of a road map as a graph. When we do so we can have the computer do interesting things for us. If you have ever used one of the Internet map sites, you know that a computer can find the shortest, quickest, or easiest path from one place to another.

A graph is a good way to represent the prerequisites and other independencies among courses. The figure below shows another graph. This one represents the courses and the order in which they must be taken to complete a major in computer science at Luther College.
![[Prerequisites for a Computer Science Major.png]]

### Vocabulary and Definitions
Now that we have looked at some examples of graphs, we will more formally define a graph and its components. We already know some of these terms from the discussion of trees.

**Vertex**
A vertex (also called a "node") is a fundamental part of a graph. It can have a name, which will be called the "key". A vertex may also have additional information. This additional information will be called the "payload".

**Edge**
An edge ( also called an "arc") is another fundamental part of a graph. An edge connects two vertices to show that there is a relationship between them. Edges may be one-way or two-way. If the edges in a graph are all one way, we say that the graph is a **directed graph**, or a **digraph**. The class prerequisites graph shown is clearly a digraph since you must take some classes before others.

**Weight**
Edges may be weighted to show that there is a cost to go from one vertex to another. For example in a graph of roads that connect one city to another, the weight on the edge might represent the distance between the two cities.

With those definitions in hand we can formally define a graph. A graph can be represented by ${G}$ where ${G = (V, E)}$. For the graph ${G}$, ${V}$ is a set of vertices and ${E}$ is a set of edges. Each edge is a tuple ${(v, w)}$ where ${w, v ∈ V}$ We can add a third component to the edge tuple to represent a weight. A subgraph ${s}$ is a set of edges ${e}$ and vertices ${v}$ such that ${e ⊂ E}$ and ${v ⊂ V}$.

The figure below shows another example of a simple weghted digraph. Formally we can represent this graph as the set of six vertices:
$$
V = \{V0, V1, V2, V3, V4, V5\}
$$

and the set of nine edges:
$$
E = \Bigg\{ \begin{multline}(v0,v1,5), (v1,v2,4), (v2,v3,9), (v3,v4,7), (v4,v0,1),\\ (v0,v5,2), (v5,v4,8), (v3,v5,3), (v5,v2,1) \end{multline}\Bigg\}
$$

![[A Simple Example of a Directed Graph.png]]

The example graph above helps illustrate two other key graph terms:

**Path**
A path in a graph is a sequence of vertices that are connected by edges. Formally we would define a path as ${w_{1},w_{2}, ... ,w_{n}}$ such that ${(w_{i},w_{i+1}) ∈ E}$ for all ${1 ≤ i ≤ n-1}$. The unweighted path length is the number of edges in the path, specifically ${n-1}$. The weighted path length is the sum of the weights of all the edges in the path. For example in the figure above the path from ${V3}$ to ${V1}$ is the sequence of vertices ${(V3, V4, V0, V1)}$. The edges are ${\{(v3, v4, 7), (v4, v0, 1), (v0, v1, 5)\}}$.

**Cycle**
A cycle in a directed graph is a path that starts and ends at the same vertex. For example, in the figure above the path ${(V5, V2, V3, V5)}$ is a cycle. A graph with no cycles is called an **acyclic graph**. A directed graph with no cycles is called a **directed acyclic graph** or a **DAG**. We will see that we can solve several important problems if the problem can be represented as a DAG.

### The Graph Abstract Data Type
The graph abstract data type(ADT) is defined as follows:
- `Graph()` creates a new, empty graph.
- `addVertex(vert)` adds an instance of `Vertex` to the graph.
- `addEdge(fromVert, toVert)` Adds a new, directed edge to the graph that connects two vertices.
- `addEdge(fromVert, toVert, weight)` Adds a new, weighted, directed edge to the graph that connects two vertices.
- `getVertex(vertKey)` finds the vertex in the graph named `vertKey`.
- `getVertices()` returns the list of all vertices in the graph.
- `in` returns `True` for a statement of the form `vertex in graph`, if the given vertex is in the graph, `False` otherwise.

Beginning with the formal definition for a graph there are several ways we can implement the graph ADT in Python. We will see that there are trade-offs in using different representations to implement the ADT described above. There are two well-known implementations of a graph, the **adjacency matrix** and the **adjacency list**. We will explain both of these options, and then implement one as a Python class.

### An Adjacency Matrix
One of the easiest ways to implement a graph is to use a two-dimensional matrix. In this matrix implementation, each of the rows and columns represent a vertex in the graph. The value that is stored in the cell at the intersection of row ${v}$ and column ${w}$ indicates if there is an edge from vertex ${v}$ to vertex ${w}$. When two vertices are connected by an edge, we say that they are **adjacent**. The figure below illustrates the adjacency matrix for the graph in the last figure above. A value in a cell represents the weight of the edge from vertex ${v}$ to vertex ${w}$.
![[An Adjacency Matrix Representation for a Graph.png]]

The advantage of the adjacency matrix is that it is simple, and for small graphs it is easy to see which nodes are connected to other nodes. However, notice that most of the cells in the matrix are empty. Because most of the cells are empty we say that this matrix is "sparse". A matrix is not a very efficient way to store sparse data. In fact, in Python you must go out of your way to even create a matrix structure like the one above.

The adjacency matrix is a good implementation for a graph when the number of edges is large. But what do we mean by large? How many edges would be needed to fill the matrix? Since there is one row and one column for every vertex in the graph, the number of edges required to fill the matrix is ${|V|^{2}}$. A matrix is full when every vertex is connected to every other vertex. There are few real problems that approach this sort of connectivity. The problems that will usually be looked at will involve graphs that are sparsely connected.

### An Adjacency List
A more space-efficient way to implement a sparsely connected graph is to use an adjacency list. In an adjacency list implementation we keep a master list of all the vertices in the Graph object and then each vertex object in the graph maintains a list of the other vertices that it is connected to. In the implementation of the `Vertex` class we will use a dictionary rather than a list where the dcitionary keys are the vertices, and the values are the weights. The figure below illustrates the adjacency list representation for the Simple Example of a Directed Graph.
![[An Adjacency List Representation of a Graph.png]]

The advantage of the adjacency list implementation is that it allows us to compactly represent a sparse graph. The adjacency list also allows us to easily find all the links that are directly connected to a particular vertex.

### Implementation
Using dictionaries, it is easy to implement the adjacency list in Python. In the implementation of the Graph abstract data type we will create two classes(see the code below), `Graph`, which holds the master list of vertices, and `Vertex`, which will represent each vertex in the graph.

Each `Vertex` uses a dictionary to keep track of the vertices to which it is connected, and the weight of each edge. This dictionary is called `connectedTo`. The listing below shows the code for the `Vertex` class. The constructor simply initializes the `id`, which will typically be a string, and the `connectedTo` dictionary. The `addNeighbor` method is used to add a connection from this vertex to another. The `getConnections` method returns all of the vertices in the adjacency list, as represented by the `connectedTo` instance variable. The `getWeight` method returns the weight of the edge from this vertex to the vertex passed as a parameter.
```python
class Vertex:
    def __init__(self,key):
        self.id = key
        self.connectedTo = {}

    def addNeighbor(self,nbr,weight=0):
        self.connectedTo[nbr] = weight

    def __str__(self):
        return str(self.id) + ' connectedTo: ' + str([x.id for x in self.connectedTo])

    def getConnections(self):
        return self.connectedTo.keys()

    def getId(self):
        return self.id

    def getWeight(self,nbr):
        return self.connectedTo[nbr]
```

The `Graph` class, shown in the next listing, contains a dictionary that maps vertex names to vertex objects. In the last figure above, this dictionary object is represented by the shaded box. `Graph` also provides methods for adding vertices to a graph and connecting one vertex to another. The `getVertices` method returns the names of all of the vertices in the graph. In addition, we have implemented the `__iter__` method to make it easy to iterate over all the vertex objects in a particular graph. Together, the two methods allow you to iterate over the vertices in a graph by name, or by the objects themselves.
```python
class Graph:
    def __init__(self):
        self.vertList = {}
        self.numVertices = 0

    def addVertex(self,key):
        self.numVertices = self.numVertices + 1
        newVertex = Vertex(key)
        self.vertList[key] = newVertex
        return newVertex

    def getVertex(self,n):
        if n in self.vertList:
            return self.vertList[n]
        else:
            return None

    def __contains__(self,n):
        return n in self.vertList

    def addEdge(self,f,t,weight=0):
        if f not in self.vertList:
            nv = self.addVertex(f)
        if t not in self.vertList:
            nv = self.addVertex(t)
        self.vertList[f].addNeighbor(self.vertList[t], weight)

    def getVertices(self):
        return self.vertList.keys()

    def __iter__(self):
        return iter(self.vertList.values())
```

Using the `Graph` and `Vertex` classes just defined, the following Python session creates the graph in the third figure above. First we create six vertices numbered 0 through 5. Then we display the vertex dictionary. Notice that for each key 0 through 5 we have created an instance of a `Vertex`. Next, we add the edges that connect the vertices together. Finally, a nested loop verifies that each edge in the graph is properly stored. You should check the output of the edge list at the end of this session against the third figure above.
```python
>>> g = Graph()
>>> for i in range(6):
...    g.addVertex(i)
>>> g.vertList
{0: <adjGraph.Vertex instance at 0x41e18>,
 1: <adjGraph.Vertex instance at 0x7f2b0>,
 2: <adjGraph.Vertex instance at 0x7f288>,
 3: <adjGraph.Vertex instance at 0x7f350>,
 4: <adjGraph.Vertex instance at 0x7f328>,
 5: <adjGraph.Vertex instance at 0x7f300>}
>>> g.addEdge(0,1,5)
>>> g.addEdge(0,5,2)
>>> g.addEdge(1,2,4)
>>> g.addEdge(2,3,9)
>>> g.addEdge(3,4,7)
>>> g.addEdge(3,5,3)
>>> g.addEdge(4,0,1)
>>> g.addEdge(5,4,8)
>>> g.addEdge(5,2,1)
>>> for v in g:
...    for w in v.getConnections():
...        print("( %s , %s )" % (v.getId(), w.getId()))
...
( 0 , 5 )
( 0 , 1 )
( 1 , 2 )
( 2 , 3 )
( 3 , 4 )
( 3 , 5 )
( 4 , 0 )
( 5 , 4 )
( 5 , 2 )
```

### The Word Ladder Problem
To begin the study of graph algorithms, let's consider the following puzzle called a word ladder. Transform the word "FOOL" into the word "SAGE". In a word ladder puzzle you must make the change occur gradually by changing one letter at a time. At each step you must transform one word into another word, you are not allowed to transform a word into a non-word. The word ladder puzzle was invented in 1878 by Lewis Carroll, the author of *Alice in Wonderland*. The following sequence of words shows one possible solution to the problem posed above.
```
FOOL
POOL
POLL
POLE
PALE
SALE
SAGE
```

There are many variations of the word ladder puzzle. For example you might be given a particular number of steps in which to accomplish the transformation, or you might need to use a particular word. In this section we are interested in figuring out the smallest number of transformations needed to turn the starting word into the ending word.

Not surprisingly, since this chapter is on graphs, we can solve this problem using a graph algorithm. Here is the outline of where we are going:
- Represent the relationships between the words as a graph
- Use the graph algorithm known as breadth first search to find an efficient path from the starting word to the ending word

### Building the Word Ladder Graph
The first problem is to figure out how to turn a large collection of words into a graph. What we would like is to have an edge from one word to another if the two words are only different by a single letter. If we can create such a graph, then any path from one word to another is a solution to the word ladder puzzle. The figure below shows a small graph of some words that solve the FOOL to SAGE word ladder problem. Notice that the graph is an undirected graph and that the edges are unweighted.
![[A Small Word Ladder Graph.png]]

We could use several different approaches to create the graph we need to solv this problem. Let's start with the assumption that we have a list of words that are all the same length. As a starting point, we can create a vertex in the graph for every word in the list. To figure out how to connect the words, we could compare each word in the list with every other. When we compare we are looking to see how many letters are different. if the two words in question are different by only one letter, we can create an edge between them in the graph. For a small set of words that approach would work fine; however let's suppose we have a list of 5, 110 words. Roughly speaking, comparing one word to every other word on the list is an ${O(n^{2})}$ algorithm. For 5,110 words, ${n^{2}}$ is more than 26 million comparisons.

We can do much better by using the following approach. Suppose that we have a huge number of buckets, each of them with a four-letter word on the outside, except that one of the letters in the label has been replaced by an underscore. For example, consider the figure below, we might have a byucket labeled "pop_". As we process each word in the list we compare the word with each bucket, using the '\_' as a wildcard, so both "pope" and "pops" would match "pop_". Every time we find a matching bucket, we put the word in that bucket. Once we have all the words in the appropriate buckets we know that all the words in the bucket must be connected.
![[Word Buckets for Words That are Different by One Letter.png]]

In Python, we can implement the scheme we have just described by using a dictionary. The labels on the buckets we have just described are the keys in the dictionary. The value stored for that key is a list of words. Once we have the dictionary build we can create the graph. We start the graph by creating a vertex for each word in the graph. Then we create edges between all the vertices we find for words found under the same key in the dictionary. The listing below shows the Python code required to build the graph.
```python
from pythonds.graphs import Graph

def buildGraph(wordFile):
    d = {}
    g = Graph()
    wfile = open(wordFile,'r')
    # create buckets of words that differ by one letter
    for line in wfile:
        word = line[:-1]
        for i in range(len(word)):
            bucket = word[:i] + '_' + word[i+1:]
            if bucket in d:
                d[bucket].append(word)
            else:
                d[bucket] = [word]
    # add vertices and edges for words in the same bucket
    for bucket in d.keys():
        for word1 in d[bucket]:
            for word2 in d[bucket]:
                if word1 != word2:
                    g.addEdge(word1,word2)
    return g
```

Since this is our first real-world graph problem, you may be wondering how sparse is the graph? The list of four-letter words we have for this problem is 5,110 words long. If we were to use an adjacency matrix, the matrix would have 5,110 * 5,110 = 26,112,100 cells. The graph constructed by the `buildGraph` function has exactly 53,286 edges, so the matrix would have only 0.20% of the cells filled(very sparse matrix).

### Implementing Breadth First Search
With the graph constructed we can now turn our attention to the algorithm we will use to find the shortest solution to the word ladder problem. The graph algorithm we are going to use is called the "breadth first search" algorithm. **Breadth first search (BFS)** is one of the easiest algorithms for searching a graph. It also serves as a prototype for several other important graph algorithms that will be studied later.

Given a graph ${G}$ and a starting vertex ${s}$, a breadth first search proceeds by exploring edges in the graph to find all the vertices in ${G}$ for which there is a path from ${s}$. The remarkable thing about a breadth first search is that it finds *all* the vertices that are a distance ${k}$ from ${s}$ before it finds *any* vertices that are a distance ${k + 1}$. One good way to visualize what the breadth first search algorithm does is to imagine that it is building a tree, one level of the tree at a time. A breadth first search adds all children of the starting vertex before it begins to discover any grandchildren.

To keep track of its progress, BFS colors each of the vertices white, gray, or black. All the vertices are initialized to white when they are constructed. A white vertex is an undiscovered vertex. When a vertex is initially discovered it is colored gray, and when BFS has completely explored a vertex it is colored black. This means that once a vertex is colored black, it has no white vertices adjacent to it. A gray node, on the other hand, may have some white vertices adjacent to it, indicating that there are still additional vertices to explore.

The breadth first search algorithm shown in the listing below uses the adjacency list graph representation developed earlier. In addition it uses a `Queue`, a crucial point as will be seen, to decide which vertex to explore next.

In addition the BFS algorithm uses an extended version of the `Vertex` class. This new vertex class adds three new instance variables: distance, predecessor, and color. Each of these instance variables also has the appropriate getter and setter methods. The code for this expanded Vertex class is included in the `pythonds` package.(nothing new to learn though)

BFS begins at the starting vertex `s` and colors `start` gray to show that it is currently being explored. Two other values, the distance and the predecessor, are initialized to 0 and `None` respectively for the starting vertex. Finally, `start` is placed on a `Queue`. The next step is to begin to systematically explore vertices at the front of the queue. We explore each new node at the front of the queue by iterating over its adjacency list. As each node on the adjacency list is examined its color is checked. if it is white, the vertex is unexplored, and four things happen:
1. The new, unexplored vertex `nbr`, is colored gray.
2. The predecessor of `nbr` is set to the current node `currentVert`
3. The distance to `nbr` is set to the distance to `currentVert + 1`
4. `nbr` is added to the end of a queue. Adding `nbr` to the end of the queue effectively schedules this node for further exploration, but not until all the other vertices on the adjacency list of `currentVert` have been explored.

```python
from pythonds.graphs import Graph, Vertex
from pythonds.basic import Queue

def bfs(g,start):
  start.setDistance(0)
  start.setPred(None)
  vertQueue = Queue()
  vertQueue.enqueue(start)
  while (vertQueue.size() > 0):
    currentVert = vertQueue.dequeue()
    for nbr in currentVert.getConnections():
      if (nbr.getColor() == 'white'):
        nbr.setColor('gray')
        nbr.setDistance(currentVert.getDistance() + 1)
        nbr.setPred(currentVert)
        vertQueue.enqueue(nbr)
    currentVert.setColor('black')
```

Let's look at how the `bfs` function would construct the breadth first tree corresponding to the graph in the small word ladder graph. Starting from fool we take all nodes that are adjacent to fool and add them to the tree. The adjacent nodes include pool, foil, foul, and cool. Each of these nodes are added to the queue of new nodes to expand. The figure below shows the state of the in-progress tree along with the queue after this step.
![[The First Step in the Breadth First Search.png]]

In the next step `bfs` removes the next node(pool) from the front of the queue and repeats the process for all of its adjacent nodes. However, when `bfs` examines the node cool, it finds that the color of cool has already been changed to gray. This indicates that there is a shorter path to cool and that cool is already on the queue for further expansion. The only new node added to the queue while examining pool is poll. The new state of the tree and queue is shown in the figure below.
![[The Second Step in the Breadth First Search.png]]

The next vertex on the queue is foil. The only new node that foil can add to the tree is fail. As `bfs` continues to process the queue, neither of the next two nodes add anything new to the queue or the tree. The figure below shows the tree and the queue after expanding all the vertices on the second level of the tree.
![[Breadth First Search Tree After Completing One Level.png]]

![[Final Breadth First Search Tree.png]]

The figure above shows the final breadth first search tree after all the vertices in the first figure in this section have been expanded. The amazing thing about the breadth first search solution is that we have not only solved the FOOL-SAGE problem we started out with, but we have solved many other problems along the way. We can start at any vertex in the breadth first search tree and follow the predecessor arrows back to the root to find the shortest word ladder from any word back to fool. The function below shows how to follow the predecessor links to print out the word ladder.
```python
def traverse(y):
    x = y
    while (x.getPred()):
        print(x.getId())
        x = x.getPred()
    print(x.getId())

traverse(g.getVertex('sage'))
```

### Breadth First Search Analysis
Before we continue with other graph algorithms let us analyze the run time performance of the breadth first search algorithm. The first thing to observe is that the while loop is executed, at most, one time for each vertex in theg graph ${| V |}$. You can see that this is true because a vertex must be white before it can be examined and added to the queue. This gives us ${O(V)}$ for the while loop. The for loop, which is nested inside the while is executed at most one for each edge in the graph, ${| E |}$. The reason is that every vertex is dequeued at most once and we examine an edge from node ${u}$ to node ${v}$ only when node ${u}$ is dequeued. This gives us ${O(E)}$ for the for loop, combining the two loops gives us ${O(V + E)}$.

Of course doing the breadth first search is only part of the task. Following the links from the starting node to the goal node is the other part of the task. The worst case for this would be if the graph was a single long chain. In this case traversing through all of the vertices would be ${O(V)}$. The normal case is going to be some fraction of ${| V |}$ but we would still write ${O(V)}$.

Finally, at least for this problem, there is the time required to build the initial graph.(left as exercise)