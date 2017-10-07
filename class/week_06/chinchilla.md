### ICI: Graphs 1 - Chinchilla
___
#### Problem Statement
Given an undirected, connected graph, create a deep copy of it. 

The graph consists of nodes that have a `label` (integer) and `neighbors` (list of Nodes). Your node class looks like the following:

```java
class Node {
    public int label;
    public Node[] neighbors
}
```

##### Assumptions
- The graph is fully connected
- The labels for the nodes are all unique

*Target:* Please describe a solution with `O(V + E)` runtime, where `V` is the number of vertices and `E` the number of edges.

##### Examples

Let us call the function that does this `Node clone_graph(Node s)`. Consider the following graph.

```
       1
      / \
     /   \
    0 --- 2
         / \
         \_/
```

Let us assume that Node `s` refers to the node with label 1. Calling the following function should return the node that is a copy of `s` in the new graph.

```java
clone_graph(s) // returns the node with label 1 in the new, cloned graph
```

____

#### Hints

1. We definitely need to look at every single node in this graph, so how can we do that? One could even say that we need to __traverse__ the graph. It may be easier to not think of this as an iterative DFS/BFS, but rather a recursive one.
2. We are going to need to keep track of which node in the original graph each node in the new graph corresponds to. We need some sort of **map**ping. 
2. We need to make sure that we don't clone the same node twice. How can we do this? Using the data structure we created in hint 2. 

___

#### Solution

1. Most of this solution relies on the `clone` function. The goal of this function is essentially to return the cloned node of the given input in the new graph.
2. We pass a hashmap around to keep track of what we have already created.
3. Each pass of clone checks the inputted value to see if we must create a new node. If we do not have to, we skip the majority of the lines and just return the cloned node with `hashmap[node.label]`.
4. If we have not seen it, we need to iterate across all the original nodes neighbors, and make sure that all the neighbors' clones are added to our cloned nodes neighbors list. How can we get all the neighbors' clones? Recursively using our own method!
5. 

```python
def clone_graph(node): 
    # we immediately return the result of calling our helper function on the 
    # given node and an empty hash (which will end up containing the new graph)
    return clone(node, {})

# This helper function will go through the node and
# 1. Make sure we have never seen it before
# 2. Create a new node for it and
# 3. Begin creating its neighbors. It adds the clone(neighboor, hashmap) to
#    each new nieghbor list because we need to neighbor in the new graph
# 4. Return the new node
def clone(node, hashmap):
    # get the label of the node we are currently considering (unique labels)
    curr_label = node.label
    # this checks to make sure we have not already created a node
    if curr_label not in hashmap:
        # create an empty node
        hashmap[curr_label] = UndirectedGraphNode(curr_label)
        for neighbor in node.neighbors:
            # check to see if the neighbor already has a clone
            if neighbor.label not in hashmap:
                # if node, get it recursively
                hashmap[neighbor.label] = clone(neighbor, hashmap)
            # add all the new neighbors (which all exist in our hashmap now) 
            # to our neighbors list
            hashmap[curr_label].neighbors.append(hashmap[neighbor.label])
    # we can return the clone of the node
    return hashmap[node.label]
```

____