### Homework #4: Linked List
##### Out: 9/22/17 | Due: 9/29/17 @ 2:00 PM
___
#### Problem
Given a linked list, find out whether or not there is a cycle. For example, a linked list with a cycle would look like:

![Image](https://allaboutalgorithms.files.wordpress.com/2011/10/linked-list-with-loop.jpg)

It is also possible we could have a normal linked list that ends with a `null`.

Please return `true` if it has a cycle, and `false` if it does not.

**Your solution should use `O(1)` space**.

##### Assumptions
- You will be given the head of a linked list that __could__ be `null`.

____

#### Examples

Let us call the function that does this `linked_list_has_cycle(head)`. Consider the following examples:

___

Let us pretend we had the image from above as our input.
```java
linked_list_has_cycle(head) // returns true because there is a cycle that begins at node #4
```

Let us pretend we had a normal linked list that terminated at `null`.
```java
linked_list_has_cycle(head) // returns false because there is no cycle
linked_list_has_cycle(null) // returns false beacuse null has no cycle
```

___

#### Grading

- Explanation of what you are writing as you are writing it and correctness of algorithm [3 pts.]
- Explanation of `O(n)` runtime [5 pts.]
- Algorithms uses `O(1)` space [3 pts.]
- Walk-through of sample cycle linked list [2 pts.]
- Walk-through of sample terminating linked list [2 pts.]
- Walk-through of `null` case [1 pt.]

___

#### Submission

Please **record** yourself talking this problem through and handwriting the solution on a whiteboard. **There should NOT be cuts in this video.** This means that you must do this entire thing in one run-through. Please upload this video to YouTube (unlisted), and submit the link for us to watch. In the description, please add the time stamps for each of the rubric points above. For example, the following could be a valid description.

```text
- P1 correct algorithm: 0:24
- P1 runtime + explanation: 2:10
- P1 happy case: 3:01
- P1 edge cases: 3:45
```

**If you do not submit a timestamped description, we will need you to resubmit for 5% off!**

Please remember that this video does not need to be perfect. You can stumble a few times/repeat yourself maybe/have to start sentences over and you will NOT get points off!
