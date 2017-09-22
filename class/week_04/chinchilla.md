### ICI #3: Linked Lists - Chinchilla
___
#### Problem Statement
Given a linked list, a start index, and an end index, reverse the nodes in the list between the start and end index.

##### Assumptions
- The linked list is never null.
- The start and end indeces will be within the bounds of the linked list.

*Target:* Please describe a solution with `O(n)` runtime and `O(1)` space.

##### Examples

Let us call the function that does this `reverse_between(Node head, int start, int end)`. Consider the following examples:

```java
reverse_between((1->2->3->4->5), 1, 3) // returns 1->4->3->2->5
reverse_between((1->2->3->4->5), 0, 4) // returns 5->4->3->2->1
reverse_between((1->2->3->4->5), 3, 4) // returns 1->2->3->5->4
```

____

#### Hints

1. How would we reverse any arbitrary linked list, where we don't have to worry about indeces?
2. How do we know when we've seen the first node that needs to be reversed? What do we have to keep track of about the previous node? What do we have to keep track of after we're done reversing?
2. Think about what we know about the start index. We have to go at least `start` nodes in, so we can start there. Once we're there, we have to keep track of the previous node's next pointer. Then we run the reverse step (end - start) times, and relink the pointers appropriately.

___

#### Solution

1. Start traversing linked list.
2. After `start` steps, store the previous node in a variable; in this case we've delegated to a helper method, so `node` will keep track of the initial node.
3. Run the reverse step of the algorithm `end - start` times.
4. Set `node` to be the `prev` node, and then loop through until `prev.next` is null. Set `prev.next` to be current, which is now the node we started with (remember we've reversed it, so current is at the end now).

```java
public Node reverseBetween(Node head, int start, int end) {
    if (head == null) return head;
    if (start == 0){
        return reverse(head, end);
    } else {
        head.next = reverseBetween(head.next, start - 1, end - 1);
        return head;
    }

}
    
public Node reverse(ListNode node, int n) {
    Node prev = null;
    Node current = node;
    Node next = null;
    while (n > 0) {
        next = current.next;
        current.next = prev;
        prev = current;
        current = next;
        n--;
    }
    node = prev;
    while (prev.next != null){
        prev = prev.next;
    }
    prev.next = current;
    return node;
}
```

____

Source: https://leetcode.com/problems/reverse-linked-list-ii/description/