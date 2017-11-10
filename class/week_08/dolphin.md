### ICI: Trees - Dolphin
___
#### Problem Statement
Given a binary search tree's (BST) root and an arbitrary node in the tree, return the node that appears next in the infix ordering of the tree. Assume that all the values in the tree are unique.

Your tree's nodes will be defined as follows:

```java
class Node {
    public int val;
    public Node left;
    public Node right;
}
```

##### Assumptions
- The root and arbitrary node (`n`) are both not `null`
- `n` may be the max element in the tree
- If you have the max element in the tree, return `null`

*Target:* Please describe a solution with `O(log(n))` runtime and `O(1)` space, where `n` is the number of nodes in the tree.

##### Examples

Let us call the function that does this `Node next_largest(Node root, Node n)`. Consider the following BST, where `a`, `b`, and `c` correspond to the nodes they are next to.

```
       4
      / \
     /   \
    2     5(a)
   / \     \
  /   \     \
 1     3(b)  6(c)
```

```java
next_largest(root, a) // returns the node that contains 6.
next_largest(root, b) // returns the node that contains 4.
next_largest(root, c) // returns null.
```

____

#### Hints

1. Think about what we know about the tree if it is a BST. What do we know about everything to the left of me? What do we know about everything to the right of me?
2. If we have a right subtree, we know that everything in this tree is larger than me. Do we know that our value is here? Where is it?
3. If we do not have a right subtree, we can still have a value greater than us (see `b` above). How do we know where this is?
4. We know that if we are not the max element and we do not have a right subtree, something somewhere must have taken a left child to get to us. How can we leverage this?

___

#### Solution

1. If we have a right subtree, return the smallest element in the right subtree.
2. If we do not have a right subtree, look for the node and return the node with the smallest value larger than the inputted node.

```java
public void next_largest(Node root, Node n) {
  int val = n.val;
  
  // check for right subtree
  if (n.right) {
    Node curr = n.right;
    while (curr.left != null) {
      curr = curr.left;
    }
    return curr;
  }

  // if we do not have the right subtree, keep track of max node in search
  Node curr = root;
  Node to_return = null;
  while (curr != n) {
    if (curr.val > val) {
      if (to_return == null || curr.val < to_return.val) to_return = curr;   
      curr = curr.left;
    } else {
      curr = curr.right;  
    }
  }

  return to_return;
}
```

____