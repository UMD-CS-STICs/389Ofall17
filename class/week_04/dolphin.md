### ICI #3: Linked Lists - Dolphin
___
#### Problem Statement
Given two integers represented as linked lists, return a linked list representation of their sum.

##### Assumptions
- Either linked list could be null.
- Each node in the linked list will be a single digit integer

*Target:* Please describe a solution with `O(n)` runtime and `O(n)` or better space.

##### Examples

Let us call the function that does this `addTwoNumbers(Node n1, Node n2)`. Consider the following examples:

```java
addTwoNumbers((1->2->3->4->5), (4->2->2)) // returns 1->2->7->6->7
addTwoNumbers((7->2->4->3), (5->6->4)) // returns 7->8->0->7
addTwoNumbers(null, (3->4->5)) // returns 3->4->5
addTwoNumbers(null, null) // returns 0
```

____

#### Hints

1. Would it be easier to add the numbers from beginning to end or end from beginning? (End to beginning is easier)
2. How would we examine the lists in reverse order? What data structures can we use? How about a stack?
3. How would we keep track of the carry? Can we store an extra variable?

___

#### Solution

1. Push both linked lists onto their own stacks
2. Begin popping elements off of the stacks. Add them together along with the carry, and then mod by 10 to get the digit for that place. Update the carry variable by dividing the elements + carry by 10
3. At each step, create a new temp node with the value of the current digit. Set temp's next to the node you already have, and then set the node you already have to temp.
4. Finally, if there is still a carry at the end, you need to add one more node at the beginning of the list to account for it, and then return the list.

```python
def addTwoNumbers(self, l1, l2):
    # we can use treat arrays in python as stacks
    stack_l1 = []
    stack_l2 = []
    
    # we move all our nodes to two different stacks
    temp = l1
    while temp != None:
        stack_l1.append(temp.val)
        temp = temp.next
    temp = l2
    while temp != None:
        stack_l2.append(temp.val)
        temp = temp.next
 
    # create the return list and carry variable
    return_list = None  
    carry = 0
    
    # arrays are false if they are [], and so this is
    # iterating until both stacks are empty
    while stack_l1 or stack_l2:
        # this is a ternary operator that will grab the next
        # value if it exists, and otherwise it will be 0
        l1_val = stack_l1.pop() if stack_l1 else 0
        l2_val = stack_l2.pop() if stack_l2 else 0
        
        # we add the added value of the the two numbers and the carry
        # mod 10 so our linked list is still valid
        to_add = (l1_val + l2_val + carry) % 10
        
        # update our carry variable
        carry = (l1_val + l2_val + carry) / 10
        
        # update the front of our return list
        temp_node = ListNode(to_add)
        temp_node.next = return_list
        return_list = temp_node
    
    # if our carry var is not 0, we need to append a node
    if carry != 0:
        temp_node = ListNode(carry)
        temp_node.next = return_list
        return_list = temp_node
        
    return return_list
```

Source: https://leetcode.com/problems/add-two-numbers-ii/description/