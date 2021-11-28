### General Depth First Search
The knight's tour is a special case of a depth first search where the goal is to create the deepest depth first tree, without any branches. The more general depth first search is actually easier. Its goal is to search as deeply as possible, connecting as many nodes in the graph as possible and branching where necessary.

It is even possible that a depth first search will create more than one tree. When the depth first search algorithm creates a group of trees we call this a **depth first forest**. As with the breadth first search the depth first search makes use of predecessor links to construct the tree. In addition, the depth first search will make use of two additional instance variables in the `Vertex` class. The new instance variables are the discovery and finish times. The discovery time tracks the number of steps in the algorithm before a vetex is first encountered. The finish time is the number of steps in the algorithm before a vertex is colored black. As we will see after looking at the algorithm, the discovery and finish times of the nodes provide some interesting properties we can use in later algorithms.

The code for the depth first search is shown in the code below. Since the two functions `dfs` and its helper `dfsvisit` use a variable to keep track of the time across calls to `dfsvisit` we chose to implement the code as methods of a class that inherits from the `Graph` class. This implementation extends the graph class by adding a `time` instance variable and the two methods `dfs` and `dfsvisit`. Looking at line 11 you will notice that the `dfs` method iterates over all of the vertices in the graph  calling `dfsvisit` on the nodes that are white. The reason we iterate over all the nodes, rather than simply searching from a chosen starting node, is to make sure that all nodes in the graph are considered and that no vertices are left out of the depth first forest. It may look unusual to see the statement `for aVertex in self`, but remember that in this case `self` is an instance of the `DFSGraph` class, and iterating over all the vertices in an instance of a graph is a natural thing to do.
```python
from pythonds.graphs import Graph
class DFSGraph(Graph):
    def __init__(self):
        super().__init__()
        self.time = 0

    def dfs(self):
        for aVertex in self:
            aVertex.setColor('white')
            aVertex.setPred(-1)
        for aVertex in self:
            if aVertex.getColor() == 'white':
                self.dfsvisit(aVertex)

    def dfsvisit(self,startVertex):
        startVertex.setColor('gray')
        self.time += 1
        startVertex.setDiscovery(self.time)
        for nextVertex in startVertex.getConnections():
            if nextVertex.getColor() == 'white':
                nextVertex.setPred(startVertex)
                self.dfsvisit(nextVertex)
        startVertex.setColor('black')
        self.time += 1
        startVertex.setFinish(self.time)
```

ALthough the implementation of `bfs` was only interested in considering nodes for which there was a path leading back to the start, it is possible to create a breadth first forest that represents the shortest path between all paris of nodes in the graph. It is left as an exercise. In the next two algorithms we will see why keeping track of the depth first forest is important.

The `dfsvisit` method starts with a single vertex called `startVertex` and explores all of the neighboring white vertices as deeply as possible. If you look carefully at the code for `dfsvisit` and compare it to breadth first search, what you should notice is that the `dfsvisit` algorithm is almost identical to `bfs` except that on the last line of the inner `for` loop, `dfsvist` calls itself recursively to continue the search at a deeper level, whereas `bfs` adds the node to a queue for later exploration. It is interesting to node that where `bfs` uses a queue, `dfsvisit` uses a stack. You don't see a stack in the code, but it is implicit in the recursive call to `dfsvisit`.

The following sequence of figures illustrates the depth first search algorithm in action for a small graph. in these figures, the dotted lines indicate edges that are checked, but the node at the other end of the edge has already been added to the depth first tree. In the code this test is done by checking that the color of the other node is non-white.

The search begins at vertex A of the graph(1). Since all of the vertices are white at the beginning of the search the algorithm visits vertex A. The first step in visiting a vertex is to set the color to gray, which indicates that the vertex is being explored and the discovery time is set to 1. Since vertex A has two adjacent vertices(B, D) each of those need to be visited as well. We'll make the arbitrary decision that we will visit the adjacent vertices in alphabetical order.

Vertex B is visited next(2), so its color is set to gray and its discovery time is set to 2. Vertex B is also adjacent to the two other nodes(C, D) so we will follow the alphabetical order and visit node C next.

Visiting vertex C(3) brings us to the end of one branch of the tree. After coloring the node gray and setting its discovery time to 3, the algorithm also determines that there are no adjacent vertices to C. This means that we are done exploring node C and so we can color the vertex black, and set the finish time to 4. You can see the state of the search at this point in figure 4.

Since vertex C was the end of one branch we now return to vertex B and continue exploring the nodes adjacent to B. The only additional vertex to explore from B is D, so we can now visit D(5) and continue the search from vertex D. Vertex D quickly leads us to vertex E(6). Vertex E has two adjacent vertices, B and F. Normally we would explore these adjacent vertices alphabetically, but since B is already colored gray the algorithm recognizes that it should not visit B since doing so would put the algorithm in a loop. So exploration continues with the next vertex in the list, namely F(7).

Vertex F has only one adjacent vertex, C, but since C is colored black there is nothing else to explore, and the algorithm has reached the end of another branch. From here on, you will see in figure 8 - 12 that the algorithm works its way back to the first node, setting finish times and coloring vertices black.

![[1 - Constructing the Depth First Search Tree-10.png]]

![[2 - Constructing the Depth First Search Tree-11.png]]

![[3 - Constructing the Depth First Search Tree-12.png]]

![[4 - Constructing the Depth First Search Tree-13.png]]

![[5 - Constructing the Depth First Search Tree-14.png]]

![[6 - Constructing the Depth First Search Tree-15.png]]

![[7 - Constructing the Depth First Search Tree-16.png]]

![[8 - Constructing the Depth First Search Tree-17.png]]

![[9 - Constructing the Depth First Search Tree-18.png]]

![[10 - Constructing the Depth First Search Tree-19.png]]

![[11 - Constructing the Depth First Search Tree-20.png]]

![[12 - Constructing the Depth First Search Tree-21.png]]

The starting and finishing times for each node display a property called the **parenthesis property**. This property means that all the children of a particular node in the depth first tree have a later discovery time and an earlier finish time than their parent. The figure below shows the tree constructed by the depth first search algorithm.

![[The Resulting Depth First Search Tree.png]]

### Depth First Search Analysis
The general running time for depth first search is as follows. The loops in `dfs` both run in ${O(V)}$, not counting what happens in `dfsvisit`, since they are executed once for each vertex in the graph. In `dfsvisit` the loop is executed once for each edge in the adjacency list of the current vertex. Since `dfsvisit` is only called recursively if the vertex is white, the loop will execute a maximum of once for every edge in the graph or ${O(E)}$. So, the total time for depth first search is ${O(V + E)}$.

### Topological Sorting
To demonstrate that computer scientists can turn just about anything into a graph problem, let's consider the difficult problem of stirring up a batch of pancakes. The recipe is really quite simple: 1 egg, 1 cup of pancake mix, 1 tablespoon oil, and ${\frac{3}{4}}$ cup of milk. To make pancakes you must heat the griddle, mix all the ingredients together and spoon the mix onto a hot griddle. When the pancakes start to bubble you turn them over and let them cook until they are golden brown on the bottom. Before you eat your pancakes you are going to want to heat up some syrup. The figure below illustrates this process as a graph.
![[The Steps for making Pancakes.png]]

The difficult thing about making pancakes is knowing what to do first. .As you can see from the figure above you might start by heating the griddle or by adding any of the ingredients to the pancake mix. To help us decide the precise order in which we should do each of the steps required to make the pancakes we turn to a graph algorithm called the **topological sort**.

A topological sort takes a directed acyclic graph and produces a linear ordering of all its vertices such that if the graph ${G}$ contains an edge ${(v,w)}$ then the vertex ${v}$ comes before the vertex ${w}$ in the ordering. Directed acyclic graphs are used in many applications to indicate the precedence of events. Making pancakes is just one example; other examples inclued software project schedules, precedence charts for optimizing database queries, and multiplying matrices.

The topological sort is a simple but useful adaptation of a depth first search. The algorithm for the topological sort is as follows:
1. Call `dfs(g)` for some graph `g`. The main reason we want to call depth first search is to compute the finish times for each of the vertices.
2. Store the vertices in a list in decreasing order of finish time
3. Return the ordered list as a result of the topological sort

The figure below shows the depth first forest constructed by `dfs` on the pancake making graph shown in the first figure.
![[Result of Depth First Search on the Pancake Graph.png]]

Finally, the last figure below shows the results of applying the topological sort algorithm to the graph. Now all the ambiguity has been removed and we know exactly the order in which to perform the pancake making steps.
![[Result of Topological Sort on Directed Acyclic Graph.png]]

### Strongly Connected Components
For the remainder of the chapter we will turn our attention to some extremely large graphs. The graphs that will be used to study some additional algorithms are the graphs produced by the connections between hosts on the Internet and the links between web pages. We will begin with web pages.

Search engines like Google and Bing exploit the fact that the pages on the web form a very large directed graph. To transform the World Wide Web into a graph, we will treat a page as a vertex, and the hyperlinks on the page produced by following the links from one page to the next, beginning at some home page. Of course, this graph could be huge, so it has been limited to websites that are no more than 10 links away from the specified homepage.
![[The Graph Produced by Links from the Luther Computer Science Home Page.png]]

If you study the graph above you might make some interesting observations. First you might notice that many of the other websites on the graph are other Luther College websites. Second, you might notice that there are several links to the other colleges in Iowa. Third, you might notice that there are several links to other liberal arts colleges. You might conclude that there is some underlying structure to the web that clusters together websites that are similar on some level.

One graph algorithm that can help find clusters of highly interconnected vertices in a graph is called the strongly connected components algorithm(**SCC**). We formally define a **strongly connected component**, ${C}$, of a graph ${G}$, as the largest subset of vertices ${C ⊂ V}$ such that for every pair of vertices ${v}$, ${w ∈ C}$ we have a path from ${v}$ to ${w}$ and a path from ${w}$ to ${v}$. The figure below shows a simple graph with three strongly connected components. The strongly connected components are identified by the different shaded areas.
![[A Directed Graph with Three Strongly Connected Components.png]]

Once the strongly connected components have been identified we can show a simplified view of the graph by combining all the vertices in one strongly connected component into a single larger vertex. The simplified version of the graph above is shown in the graph below.
![[The Reduced Graph.png]]

Once again we will see that we can create a very powerful and efficient algorithm by making use of a depth first search. Before we tackle the main SCC algorithm we must look at one other definition. The transposition of a graph ${G}$ is defined as the graph ${G^{T}}$ where all the edges in the graph have been reversed. That is, if there is a directed edge from node A to node B in the original graph then ${G^{T}}$ will contain an edge from node B to node A. The figures below show a simple graph and its transposition.
![[A Graph G.png]]

![[Transpose of G.png]]

Look at the figures again. Notice that the graph in the graph of ${G}$ has two strongly connected components. Now look at the graph of ${G^{T}}$. Notice that it has the same two strongly connected components.

We can now describe the algorithm to compute the strongly connected components for a graph.
1. Call `dfs` for the graph ${G}$ to compute the finish times for each vertex.
2. Compute ${G^{T}}$
3. Call `dfs` for the graph ${G^{T}}$ but in the main loop of DFS explore each vertex in decreasing order of finish time.
4. Each tree in the forest computed in step 3 is a strongly connected component. Output the vertex ids for each vertex in each tree in the forest to identify the component.

Let's trace the operation of the steps described above on the first example graph. The first figure below shows the starting and finishing times computed for the original graph by the DFS algorithm. The second figure shows the starting and finishing times computed by running DFS on the transposed graph.
![[Finishing times for the original graph G.png]]

![[Finishing times for Transposed Graph of G.png]]

Finally, the last figure below shows the forest of three trees produced in step 3 of the strongly connected component algorithm.
![[Strongly Connected Components.png]]

```python
from collections import defaultdict
   
#This class represents a directed graph using adjacency list representation
class Graph:
   
    def __init__(self,vertices):
        self.V= vertices #No. of vertices
        self.graph = defaultdict(list) # default dictionary to store graph
   
    # function to add an edge to graph
    def addEdge(self,u,v):
        self.graph[u].append(v)
   
    # A function used by DFS
    def DFSUtil(self,v,visited):
        # Mark the current node as visited and print it
        visited[v]= True
        print v,
        #Recur for all the vertices adjacent to this vertex
        for i in self.graph[v]:
            if visited[i]==False:
                self.DFSUtil(i,visited)
  
  
    def fillOrder(self,v,visited, stack):
        # Mark the current node as visited 
        visited[v]= True
        #Recur for all the vertices adjacent to this vertex
        for i in self.graph[v]:
            if visited[i]==False:
                self.fillOrder(i, visited, stack)
        stack = stack.append(v)
      
  
    # Function that returns reverse (or transpose) of this graph
    def getTranspose(self):
        g = Graph(self.V)
  
        # Recur for all the vertices adjacent to this vertex
        for i in self.graph:
            for j in self.graph[i]:
                g.addEdge(j,i)
        return g
  
   
   
    # The main function that finds and prints all strongly
    # connected components
    def printSCCs(self):
          
         stack = []
        # Mark all the vertices as not visited (For first DFS)
        visited =[False]*(self.V)
        # Fill vertices in stack according to their finishing
        # times
        for i in range(self.V):
            if visited[i]==False:
                self.fillOrder(i, visited, stack)
  
        # Create a reversed graph
         gr = self.getTranspose()
           
         # Mark all the vertices as not visited (For second DFS)
         visited =[False]*(self.V)
  
         # Now process all vertices in order defined by Stack
         while stack:
             i = stack.pop()
             if visited[i]==False:
                gr.DFSUtil(i, visited)
                print""
   
# Create a graph given in the above diagram
g = Graph(5)
g.addEdge(1, 0)
g.addEdge(0, 2)
g.addEdge(2, 1)
g.addEdge(0, 3)
g.addEdge(3, 4)
  
   
print ("Following are strongly connected components " +
                           "in given graph")
g.printSCCs()
```
https://www.geeksforgeeks.org/strongly-connected-components/

### Shortest Path Problems
When you surf the web, send an email, or log in to a laboratory computer from another location on campus a lot of work is going on behind the scenes to get the information on your computer transferred to another computer. The in-depth study of how information flows from one computer to another over the Internet is the primary topic for a class in computer networking. However, we will talk about how the Internet works just enough to understand another very important graph algorithm.
![[Overview of Connectivity in the Internet.png]]

The figure above shows you a high-level overview of how communication on the Internet works. When you use your browser to request a webpage from a server, the request must travel over your local area network and out onto the Internet through a router. The request travels over the Internet and eventually arrives at a router for the local area network where the server is located. The webpage you requested then travels back through the same routers to get to your browser. Inside the cloud labelled "Internet" in the figure are additional routers. The job of al of these routers is to work together to get your information from place to place. You can see there are many routers for yourself if your computer supports the `traceroute` command. The text below shows the output of the `traceroute` command which illustrates that there are 13 routers between the web server at a certain college and the mail server at a different one.
```
1  192.203.196.1
2  hilda.luther.edu (216.159.75.1)
3  ICN-Luther-Ether.icn.state.ia.us (207.165.237.137)
4  ICN-ISP-1.icn.state.ia.us (209.56.255.1)
5  p3-0.hsa1.chi1.bbnplanet.net (4.24.202.13)
6  ae-1-54.bbr2.Chicago1.Level3.net (4.68.101.97)
7  so-3-0-0.mpls2.Minneapolis1.Level3.net (64.159.4.214)
8  ge-3-0.hsa2.Minneapolis1.Level3.net (4.68.112.18)
9  p1-0.minnesota.bbnplanet.net (4.24.226.74)
10  TelecomB-BR-01-V4002.ggnet.umn.edu (192.42.152.37)
11  TelecomB-BN-01-Vlan-3000.ggnet.umn.edu (128.101.58.1)
12  TelecomB-CN-01-Vlan-710.ggnet.umn.edu (128.101.80.158)
13  baldrick.cs.umn.edu (128.101.80.129)(N!)  88.631 ms (N!)


Routers from One Host to the Next over the Internet
```

Each router on the Internet is connected to one or more other routers. So if you run the `tracerouter` command at different times of the day, you are likely to see that your information flows through different routers at different times. This is because there is a cost associated with each connection between a pair of routers that depends on the volume of traffic, the time of day, and many other factors. By this time it will not surprise you to learn that we can represent the network of routers as a graph with weighted edges.
![[Connections and Weights between Routers in the Internet.png]]

The figure above shows a small example of a weighted graph that represents the interconnection of routers in the Internet. The problem that we want to solve is to find the path with the smallest total weight along which to route any given message. This problem should sound familiar because it is similar to the problem we solved using a breadth first search, except that here we are concerned with the total weight of the path rather than the number of hops in the path. It should be noted that if all the weights are equal, the problem is the same.

### Dijkstra's Algorithm
The algorithm we are going to use to determine the shortest path is called "Dijkstra's algorithm". Dijkstra's algorithm is an iterative algorithm that provides us with the shortest path from one particular starting node to all other nodes in the graph. Again this is similar to the results of a breadth first search.

To keep track of the total cost from the start node to each destination we will make use of the `dist` instance variable in the Vertex class. The `dist` instance variable will contain the current total weight of the smallest weight path from the start to the vertex in question. The algorithm iterates once for every vertex in the graph; however, the order that we iterate over the vertices is controlled by a priority queue. the value that is used to determine the order of the objects in the priority queue is `dist`. When a vertex is first created `dist` is set to a very large number. Theoretically you would set `dist` to infinity, but in practice we just set it to a number that is larger than any real distance we would have in the problem we are trying to solve.

The code for Dijkstra's algorithm is shown in the listing below. When the algorithm finishes the distances are set correctly as are the predecessor links for each vertex in the graph.
```python
from pythonds.graphs import PriorityQueue, Graph, Vertex
def dijkstra(aGraph,start):
    pq = PriorityQueue()
    start.setDistance(0)
    pq.buildHeap([(v.getDistance(),v) for v in aGraph])
    while not pq.isEmpty():
        currentVert = pq.delMin()
        for nextVert in currentVert.getConnections():
            newDist = currentVert.getDistance() \
                    + currentVert.getWeight(nextVert)
            if newDist < nextVert.getDistance():
                nextVert.setDistance( newDist )
                nextVert.setPred(currentVert)
                pq.decreaseKey(nextVert,newDist)
```

Dijkstra's algorithm uses a priority queue. You may recall that a priority queue is based on the heap that was implemented in the Tree Chapter. There are a couple of differences between that simple implementation and the implementation we use for Dijkstra's algorithm. First, the `PriorityQueue` class stores tuples of key, value pairs. This is important for Dijkstra's algorithm as the key in the priority queue must match the key of the vertex in the graph. Secondly the value is used for deciding the priority, and thus the position of the key in the priority queue. In this implementation we use the distance to the vertex as the priority because as will be seen when we are exploring the next vertex, we always want to explore the vertex that has the smallest distance. The second difference is the addition of the `decreaseKey` method. As you can see, this method is used when the distance to a vertex that is already in the queue is reduced, and thus moves that vertex toward the front of the queue.

Let's walk through an application of Dijkstra's algorithm one vertex at a time using the following sequence of figures as our guide. We begin with the vertex ${u}$. The three vertices adjacent to ${u}$ are ${v}$, ${w}$, and ${x}$. Since the initial distances to ${v}$, ${w}$, and ${x}$ are initialized to `sys.maxint`, the new costs to get to them through the start node are all their direct roots. So we update the costs to each of these three nodes. We also set the predecessor for each node to ${u}$ and we add each node to the priority queue. We use the distance as the key for the priority queue. The state of the algorithm is shown in figure 1 below.

In the next iteration of the `while` loop we examine the vertices that are adjacent to ${x}$. The vertex ${x}$ is next because it has the lowest overall cosst and therefore bubbled its way to the beginning of the priority queue. At ${x}$ we look at its neighbors ${u}$, ${v}$, ${w}$, and ${y}$. For each neighboring vertex we check to see if the distance to that vertex through ${x}$ is smaller than the previously known distance. Obviously this is the case for ${y}$ since its distane was `sys.maxint`. It is not the case for ${u}$ or ${v}$ since their distances are 0 and 2 respectively. However, we now learn that the distance to ${w}$ is smaller if we go through ${x}$ than from ${u}$ directly to ${w}$. Since that is the case we update ${w}$ with a new distance and change the predecessor for ${w}$ from ${u}$ to ${x}$ See figure 2 below for the state of all the vertices.

The next step is to look at the vertices neighboring ${v}$(3). This step results in no changes to the graph, so we move on to node ${y}$. At node ${y}$(4) we discover that it is cheaper to get to both ${w}$ and ${z}$, so we adjust the distances and predecessor links accordingly. Finally we check nodes ${w}$ and ${z}$ (4-6). However, no additional changes are found and so the priority queue is empty and Dijkstra's algorithm exits.

![[1 - Tracing Dijkstra’s Algorithm.png]]

![[2 - Tracing Dijkstra’s Algorithm.png]]

![[3 - Tracing Dijkstra’s Algorithm.png]]

![[4 - Tracing Dijkstra’s Algorithm.png]]

![[5 - Tracing Dijkstra’s Algorithm.png]]

![[6 - Tracing Dijkstra’s Algorithm.png]]

It is important to note that Dijkstra's algorithm works only when the weights are all positive. You should convince yourself that if you introduced a negative weight on one of the edges to the graph that the algorithm will never exit.

We will note that to route messages through the Internet, other algorithms are used for finding the shortest path. Once of the problems with using Dijkstra's algorithm on the Internet is that you must have a complete representation of the graph in order for the algorithm to run. The implication of this is that every router has a complete map of all the routers in the Internet. in practice this is not the case and other variations of the algorithm allow each router to discover the graph as they go. One such algorithm that you may want to read about is called the "distance vector" routing algorithm.

### Analysis of Dijkstra's Algorithm
Finally, let's look at the running time of Dijkstra's algorithm. We first note that building the priority queue takes ${O(V)}$ time since we initially add every vertex in the graph to the priority queue. Once the queue is constructed the `while` loop is executed once for every vertex since vertices are all added at the beginning and only removed after that. Within that loop each call to `delMin` , takes ${O(\log{V})}$ time. Taken together that part of the loop and the calls to delMin take ${O(V\log{(V)})}$.  The `for` loop is executed once for each edge in the graph, and within the `for` loop the call to `decreaseKey` takes time ${O(E\log{(V)})}$. So the combined running time is ${O((V+E)\log{(V)})}$.

### Prim's Spanning Tree Algorithm
For the last graph algorithm let's consider a problem that online game designers and Internet radio providers face. The problem is that they want to efficiently transfer a piece of information to anyone and everyone who may be listening. This is important in gaming so that all the players know the very latest position of every other player. This is important for Internet radio so that all the listeners that are tuned in are getting all the data they need to reconstruct the song they are listening to. The figure below illustrates the broadcast problem.
![[The Broadcast Problem.png]]

There are some brute force solutions to this problem, so let's look at them first to help understand the broadcast problem better. This will also help you appreciate the solution that we will propose when we are done. To begin, the broadcast host has some information that the listeners all need to receive. The simplest solution is for the broadcasting host to keep a list of all the listeners and send individual messages to each. In the figure above we show a small network with a broadcaster and some listeners. Using this first approach, four copies of every message would be sent. Assuming that the least cost path is used, let's see how many times each router would handle the same message.

All messages from the broadcaster go through router A, so A sees all four copies of every message. Router C sees only one copy of each message for its listener. However, routers B and D would see three copies of every message since routers B and D are on the cheapest path for listeners 1, 2, and 3, When you consider that the broadcast hsot must send hundreds of messages each second for a radio broadcast, that is a lot of traffic.

A brute force solution is for the broadcast host to send a single copy of the broadcast message and let the routers sort things out. In this case, the easiest solution is a strategy called **uncontrolled flooding**. The flooding strategy works as follows. Each message starts with a time to live(`ttl`) value set to some number greater than or equal to the number of edges between the broadcast host and its most distant listener. Each router gets a copy of the message and passes the message on to *all* of its neighboring routers. When the message is passed on the `ttl` is decreased. Each router continues to send copies of the message to all its neighbors until the `ttl` value reaches 0. It is easy to convince yourself that uncontrolled flooding generates many more unnecessary messages than the first strategy.

The solution to this problem lies in the construction of a minimum weight **spanning tree**. Formally we define the minimum spanning tree ${T}$ for a graph ${G = (V,E)}$ as follows. ${T}$ is an acyclic subset of ${E}$ that connects all the vertices in ${V}$. The sum of the weights of the edges in ${T}$ is minimized.

The figure below shows a simplified version of the broadcast graph and highlights the edges that form a minimum spanning tree for the graph. Now to solve the broadcast problem, the broadcast host simply sends a single copy of the broadcast message into the network. Each router forwards the message to any neighbor that is part of the spanning tree, excluding the neighbor that just sent it the message. In this example A forwards the message to B. B forwards the message to D and C. D forwards the message to E, which forwards it to F, which forwards it to G. No router sees more than one copy of any message, and all the listeners that are interested see a copy of the message.
![[Minimum Spanning Tree for the Broadcast Graph.png]]

The algorithm that will be used to solve this problem is called Prim's algorithm. Prim's algorithm belongs to a family of algorithms called the "greedy algorithms" because at each step we will choose the cheapest next step. In this case the cheapest next step is to follow the edge with the lowest weight. The last step is to develop Prim's algorithm.

The basic idea in constructing a spanning tree is as follows:
```
While T is not yet a spanning tree
   Find an edge that is safe to add to the tree
   Add the new edge to T
```

The trick is in the step that directs us to "find an edge that is safe". We define a safe edge as any edge that connects a vertex that is in the spanning tree to a vertex that is not in the spanning tree. This ensures that the tree will always remain a tree and therefore have no cycles.

The Python code to implement Prim's algorithm is shown below. Prim's algorithm is similar to Dijkstra's algorithm in that they both use a priority queue to select the next vertex to add to the growing graph.
```python
from pythonds.graphs import PriorityQueue, Graph, Vertex

def prim(G,start):
    pq = PriorityQueue()
    for v in G:
        v.setDistance(sys.maxsize)
        v.setPred(None)
    start.setDistance(0)
    pq.buildHeap([(v.getDistance(),v) for v in G])
    while not pq.isEmpty():
        currentVert = pq.delMin()
        for nextVert in currentVert.getConnections():
          newCost = currentVert.getWeight(nextVert)
          if nextVert in pq and newCost<nextVert.getDistance():
              nextVert.setPred(currentVert)
              nextVert.setDistance(newCost)
              pq.decreaseKey(nextVert,newCost)
```

The following sequence of figures(1-7) shows the algorithm in operation on the sample tree. We begin with the starting vertex as A. The distances to all the other vertices are initialized to infinity. Looking at the neighbors of A we can update distances to two of the additional vertices B and C because the distances to B and C through A are less than infinite. This moves B and C to the front of the priority queue. Update the predecessor links for B and C by setting them to point to A. It is important to note that we have not formally added B or C to the spanning tree yet. A node is not considered to be part of the spanning tree until it is removed from the priority queue.

Since B has the smallest distance we look at B next. Examining B's neighbors we see that D and E can be updated. Both D and E get new distance values and their predecessor links are updated. Moving on to the next node in the priority queue we find C. The only node C is adjacent to that is still in the priority queue is F, thus we can update the distance to F and adjust F's position in the priority queue.

Now we examine the vertices adjacent to node D. We find that we can update E and reduce the distance to E from 6 to 4. When we do this we change the predecessor link on E to point back to D, thus preparing it to be grafted into the spanning tree but in a different location. The rest of the algorithm proceeds as you would expect, adding each new node to the tree.

![[1 - Tracing Prim’s Algorithm.png]]

![[2 - Tracing Prim’s Algorithm.png]]

![[3 - Tracing Prim’s Algorithm.png]]

![[4 - Tracing Prim’s Algorithm.png]]

![[5 - Tracing Prim’s Algorithm.png]]

![[6 - Tracing Prim’s Algorithm.png]]

![[7 - Tracing Prim’s Algorithm.png]]