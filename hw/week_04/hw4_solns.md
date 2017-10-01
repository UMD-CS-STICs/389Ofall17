### Homework #4: Linked List SOLUTION
___

One possible solution is the following:

```python
def hasCycle(head):
    """ Check to make sure we don't have a null list """
    if head == None:
        return False

    """ Create our slow (tortoise) and fast (hare) pointers """
    hare, tortoise = head, head

    """ Make sure that we are not about to hit a dead-end """
    while hare.next != None:
        """ Move both forward """
        tortoise = tortoise.next
        hare = hare.next
        """ Move hare forward one more because it moves 2 at a time """
        if hare.next != None:
            hare = hare.next
        else:
            return False

        """ If they are ever the same, we have a hit a loop! """
        if tortoise == hare:
            return True
    return False
```

Think about if we had two nodes in a looped linked list - it does not matter where in this circle there are. If you make one move one step at a time and the other move two steps at a time, they will eventually meet! So, we just send these pointers down in this fashion, and as long as the hare never terminates, we will find a meeting point aka a cycle!