**Full Binary Tree**
every node has 0 or 2 children; all nodes except leaf nodes have two children
```
               18
           /       \  
         15         30  
        /  \        /  \
      40    50    100   40

             18
           /    \   
         15     20    
        /  \       
      40    50   
    /   \
   30   50

               18
            /     \  
          40       30  
                   /  \
                 100   40
```

**Complete Binary Tree**
all levels are completely filled except possibly the last level, and all nodes are as far left as possible
```
               18
           /       \  
         15         30  
        /  \        /  \
      40    50    100   40


               18
           /       \  
         15         30  
        /  \        /  \
      40    50    100   40
     /  \   /
    8   7  9 
```

**Perfect Binary Tree**
all the interval nodes have two children and all leaf nodes are at the same level
```
               18
           /       \  
         15         30  
        /  \        /  \
      40    50    100   40


               18
           /       \  
         15         30  
```

$$
L = l + 1
$$
where L = number of leaf nodes, l = number of internal nodes

Internal nodes: any node of a tree that has child nodes and is (thus) not a leaf node

Perfect Binary Tree of height ${h}$ has ${2^{h}-1}$ nodes

**Balanced Binary Tree**
height of the tree is ${O(\log{n})}$ where ${n}$ is the number of nodes

i.e. AVL tree maintains ${O(\log{n})}$ height by making sure that the difference btwn heights of left and right subtrees is at most 1

Red-Black trees maintain ${O(\log{n})}$ height by making sure that the number of Black nodes on every root to leaf paths is the same and there is no adjacent red nodes.

Balanced Binary Search trees are performance-wise good as they provide ${O(\log{n})}$ time for search, insert, and delete.

**Degenerate/Pathological Tree**
every internal node has one child. Such trees are performance-wise same as linked list
```
      10
      /
    20
     \
     30
      \
      40  
```