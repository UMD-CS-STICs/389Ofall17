### ICI: Graphs I - Dolphin
___
#### Problem Statement
A graph is considered "2-colorable" if you can color each node in the graph one of two colors such that no adjacent nodes share the same color. Given a graph with `n` nodes and `m` edges, determine whether the graph is 2-colorable. Your response should return `true` or `false`.

##### Assumptions
- The graph will be given to you as a head node that contains a color property (head.color) and a list of its neighbors
- The color property is initially null for all nodes
- The graph will not be null

*Target:* Please describe a solution with `O(n + m)` runtime and `O(1)` space.

##### Examples

Let us call the function that does this `two_colorable(Node head)`. Consider the following examples:

```
  1   5
 / \ / \
0   3   6
 \ / \ /
  2   4
```
is two colorable because `[0, 3, 6]` can be one color (say, red) and `[1, 2, 4, 5]` can be a different color (say, blue), and no node will have an adjacent neighbor of the same color.

```
0 ------- 1
| \     / |
|  \   /  |
|    4    |
|  /   \  |
| /     \ |
2 ------- 3

```
is not two colorable because no matter how you configure `[0, 1, 2, 3]`, node `4` is adjacent to every node, so it will always have a neighbor that is of the same color.



____

#### Hints

1. How can we use a search to solve this problem? Should we use DFS or BFS? Why? (We should use BFS so we can keep track of "layers")
2. What do we need to know about our neighbors to determine whether we should keep going or stop? (If we have neighbors with differing colors, then we are stuck and should stop and return false).


___

#### Solution

1. Construct a red set and a blue set initialized to empty
2. Add the start node to the red set
3. Begin a DFS from the start node
4. At each layer of the DFS, check to make sure all of your neighbors are the opposite color. If you have a neighbor with the same color, then you can return 'false.' Otherwise if you exhaust the entire graph, return 'true.'

```python
from collections import deque

def two_colorable(head):
    queue = deque()
    visited = []
    queue.append((head, red))
    while queue:
        current, color = queue.popleft()
        if not current in visited:
            # assign the current color to current.color and then 
            # flip it for the next layer
            visited.append(current)
            current.color = color
            color = blue if color is red else red
            for neighbor in current.neighbors:
                if neighbor.color == current.color:
                    return False
                queue.append((neighbor, color))
    # If we reach the end of the BFS, then we've successfully
    # 2-colored the graph, so we can return true
    return True

```

____

Source: CMSC451 (which I highly recommend everyone take)