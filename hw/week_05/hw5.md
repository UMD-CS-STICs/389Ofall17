### Homework #5: Stacks and Queues
##### Out: 9/29/17 | Due: 10/6/17 @ 2:00 PM
___
#### Problem Statement
Given a post order representation of a mathematical equation, output the result.

##### Assumptions
- The only operators are `+, -, *, and /`
- All numbers will be integers, which may be negative
- There will be the exact amount of operators needed for the numbers in the array
- You will not have to worry about dividing by zero

*Target:* Please describe a solution with `O(n)` runtime and `O(n)` space.

##### Examples

Let us call the function that does this `post_order_math(String[] equation)`. Consider the following examples:


`post_order_math(['7', '3', '+'])` would return `10` because `['7', '3', '+']` translates to `7 + 3 = 10`

`post_order_math(['7', '5', '2', '+', '*'])` would return `49` because `['7', '5', '2', '+', '*']` translates to `7 * (5 + 2) = 49`

`post_order_math(['5', '3', '2', '+', 6, '-', '/'])` would return `-5` because `['5', '3', '2', '+', 6, '-', '/']` translates to `5 / ((3 + 2) - 6) = -5`



____

#### Grading

- Explanation of what you are writing as you are writing it and correctness of algorithm [3 pts.]
- Explanation of `O(n)` runtime [5 pts.]
- Algorithms uses `O(n)` space [3 pts.]
- Walk-through of sample math equation [2 pts.]

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