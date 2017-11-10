### ICI: Trees - Chinchilla
___
#### Problem Statement
Given a tree, a value j, and a depth k, insert the value at the kth row in the tree. You should modify the tree in-place. Your tree will be defined as follows:

```java
class Tree {
    public int label;
    public Tree left;
    public Tree right;
}
```

##### Assumptions
- The depth k will not be greater than the depth of the tree
- The value will not be null
- We are using a 1-based depth (depth 1 is the root)

*Target:* Please describe a solution with `O(n)` runtime, where `n` is the number of nodes in the tree.

##### Examples

Let us call the function that does this `void add_row(Tree tree, int value, int depth)`. Consider the following tree.

```
       4
      / \
     /   \
    2     6
   / \     \
  /   \     \
 3     1     5
```

`add_row(tree, 1, 2)` should return the following:

```
           4                      4
          / \                    / \
         /   \                  /   \
        1     1     or         1     1
       /     /                /       \
      /     /                /         \
     2     6                2           6
    / \     \              / \           \
   /   \     \            /   \           \
  3     1     5          3     1           5
```

**It does not matter what side you choose to continue the tree on from the inserted node, but you must maintain the original structure of the tree after the inserted node.**

____

#### Hints

1. We want to add the node to a specific "row," so we can do a DFS or BFS.
2. Once we find the row, we need to store the nodes in the tree that are supposed to come after. How can we do this?

___

#### Solution

1. We use recursion to begin a depth-first search of the tree.
2. At each layer, we decrement our depth until we are at the layer before our depth.
3. When we are at the correct depth, we create a temp node and then continue the tree after the temp node.

```java
public void add_row(Tree root, int v, int d) {
    if (root == null) {
        return;
    }

    if (currentDepth == 1) {
        Tree temp = root.left;
        root.left = new Tree(v);
        root.left.left = temp;
        // "root.left.right = temp" would also work

        temp = root.right;
        root.right = new Tree(v);
        root.right.right = temp;
        // "root.right.left = temp" would also work
        return;
    }

    add(node.left, v, d - 1);
    add(node.right, v, d - 1);
}

```

____