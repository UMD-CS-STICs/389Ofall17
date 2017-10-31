### Homework #6: Dynamic Programming
##### Out: 10/27/17 | Due: 11/3/17 @ 2:00 PM
___
#### Problem Statement
Given a knapsack of capacity `W`, and `n` items, return a subset of these `n` items that give the knapsack maximum value. The item class is defined below:

```java
class Item {
  public int weight;
  public int value;
}
```

##### Assumptions
- The capacity of the knapsack is greater than 0

*Target:* Please describe a solution with `O(nW)` runtime and `O(nW)` space.

##### Examples

Let us call the function that does this `max_value(int capacity, Items[] items)`. Consider the following examples:

```
items = [{weight: 2, value: 4}, {weight: 2, value: 5}, {weight: 5, value: 3}]
max_value(5, items) // should return [0, 1] because items 0 and 1 can fit in the knapsack and create the highest value.

items = [{weight: 2, value: 4}, {weight: 2, value: 5}, {weight: 5, value: 10}]
max_value(5, items) // should return [2] because item 2 can fit in the knapsack and create the highest value.
```

____

#### Grading

- Explanation of what you are writing as you are writing it and correctness of algorithm [3 pts.]
- Explanation of `O(nW)` runtime [5 pts.]
- Algorithms uses `O(nW)` space [3 pts.]
- Walk-through of sample knapsack

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