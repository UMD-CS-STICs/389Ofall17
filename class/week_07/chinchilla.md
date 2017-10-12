### ICI: Graphs 2 - Chinchilla
___
#### Problem Statement
Equations are given in the format `A / B = k`, where `A` and `B` are variables represented as strings, and `k` is a float. Given some equations, their corresponding values, and a list of queries, return the answers to the queries. If the answer does not exist, return `-1.0`.

##### Assumptions
- You will not have to divide by 0
- You will not have any division conflicts (i.e, `[a / b = 3, b / c = 2, c / a = 5]`)

*Target:* Please describe a solution with `O(V + E)` runtime, where `V` is the number of unique variables and `E` is the number of equations given to you. You may use up to `O(V + E)` space as well.

##### Examples

Let us call the function that does this `calculate(equations, values, queries)`. Consider the following input:

```
equations = [["a", "b"], ["b", "c"]],
values = [2.0, 3.0],
queries = [["a", "c"], ["b", "a"], ["a", "e"], ["a", "a"], ["x", "x"]]. 
```

`calculate(equations, values, queries)` returns `[6.0, 0.5, -1.0, 1.0, -1.0 ]`.


____

#### Hints

**It will help you out tremendously to break this problem down into several components or helper methods:**

1. We want a runtime of `O(V + E)`. This implies that we should probably create a graph of some sort.
    * Should our graph be directed or undirected?
    * Should our graph be weighted or unweighted?
2. Once we've created our graph, how can we examine the relationship between two nodes in the graph (i.e., if `a` and `l` are nodes, how can we figure out `a / l` if we know `a / b`, `b / c`, `c / d`, `...`, `k / l`)?
3. Once we know how to examine the relationships between variables, **then** we can go about examining the queries.

___

#### Solution

1. The first thing we want to do is create a graph:
    * The graph we create here is going to be directed **and** weighted
    * We want to create the graph by creating two edges between every pair `(m, n)` of variables given to us in our equation list (one from `m -> n`, and one from `n -> m`). 
    * Since we are given `m / n`, we want to simply make the weight of the edge `m -> n` equal to `m / n`. However, the edge from `n / m` should be the *inverse* of `m / n` (it should be `n / m`). Think about it: if `a / b = 2.0`, it follows that `b / a = 0.5`; so if we have a query `["b", "a"]`, we'll be ready for it.
2. Once our graph is created, we want to create our DFS:
    * When we do a DFS from node `i` to node `j`, the important thing is that we keep track of the value as we go, since this is what we want to return.
    * Keeping track of this will rely on a key principle of division: If `a / b = x` and `b / c = y`, then `a / c = xy`.
    * Therefore, as we do our DFS, we can simply multiply our current value by our neighbor's weight, and then add the neighbor and its value back onto our DFS stack
    * If we ever find our destination, we can return the vlaue. If we don't, we simply return -1.0
3. Now that our DFS is done, we can look through the queries:
    * For each query we want to do the following:
        * if either the source or the destination is not in the graph, we can return `-1.0` immediately
        * if the source and destination are the same (and are in the graph), we can just return `1.0` since `a / a = 1`.
        * otherwise, we can call our DFS on the source and destination, and just add that result to our running list of query results

```python
def calcEquation(self, equations, values, queries):
        nodes, edges = self.makeGraph(equations, values)
        results = []
        for query in queries:
            src, dest = query
            # convert to avoid unicode errors
            src = str(src); dest = str(dest)
            if src not in nodes or dest not in nodes:
                results.append(-1.0)
            else:
                if src == dest:
                    results.append(1.0)
                else:
                    result = self.DFS(src, dest, nodes, edges)
                    results.append(result)
        return results
    
    def DFS(self, src, dest, nodes, edges):
        stack = []
        # I use Python's tuples here to keep track of a node and
        # its value, but you could also just use an array of two
        # elements
        stack.append((src, 1.0))
        visited = set()
        while stack:
            node, value = stack.pop()
            if node not in visited:
                visited.add(node)
                for neighbor, weight in edges[node]:
                    if neighbor == dest:
                        return weight * value
                    else:
                        # when we push a new neighbor onto the stack,
                        # we have to make sure that we multiply its weight
                        # by the current value so that we account for its
                        # "cost" moving forward
                        stack.append((neighbor, weight * value))
        return -1.0

        
    def makeGraph(self, equations, values):
        # list of all nodes
        nodes = set()
        # I choose to store my edges in the following structure
        # using Python tuples, but you could just as easily map
        # each node to an array of arrays:
        # {node -> [(node, weight), (node, weight), ...],
        #  node -> [(node, weight), (node, weight), ...],
        #  ...
        # }
        edges = dict()
        for i in range(len(equations)):
            src, dest = equations[i]
            weight = values[i]
            # This conversion is to avoid unicode errors
            src = str(src); dest = str(dest); weight = float(weight)
            nodes.add(src)
            nodes.add(dest)
            if src not in edges:
                edges[src] = [(dest, weight)]
            else:
                neighbors = edges[src]
                neighbors.append((dest, weight))
                edges[src] = neighbors
            if dest not in edges:
                edges[dest] = [(src, (1 / weight))]
            else:
                neighbors = edges[dest]
                neighbors.append((src, (1 / weight)))
                edges[dest] = neighbors
        
        return list(nodes), edges
```

____