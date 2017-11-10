### Homework #7: Dynamic Programming
##### Out: 11/10/17 | Due: 11/17/17 @ 2:00 PM
___
#### Problem Statement
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

##### Assumptions
- `house_arr` is not null

*Target:* Please describe a solution with `O(n)` runtime, where `n` is the size of the `house_arr` array.

##### Examples

Let us call the function that does this `int rob(int[] house_arr)`. Consider the following examples:

```python
rob([]) # would return 0 because there is nothing to rob
rob([1,3,4,1]) # would return 5 because you can rob the 1st and 3rd houses
rob([8,10,8,15,2]) # would return 25 because you can rob the 2nd and 4th houses
```

____

#### Grading

- Explanation of what you are writing as you are writing it and correctness of algorithm [3 pts.]
- Write out the recurrence [3 pts.]
- Explanation of `O(n)` runtime [5 pts.]
- Walk-through of sample case [2 pts.]

___

#### Submission

**Please use [HireFlock](https://www.hireflock.com/) for this assignment**. This means you will be typing your code, not writing it on a whiteboard. **There should NOT be cuts in this video.** This means that you must do this entire thing in one run-through. Please upload this video to YouTube (unlisted), and submit the link for us to watch. In the description, please add the time stamps for each of the rubric points above. For example, the following could be a valid description.

```text
- P1 correct algorithm: 0:24
- P1 runtime + explanation: 2:10
- P1 happy case: 3:01
- P1 edge cases: 3:45
```

**If you do not submit a timestamped description, we will need you to resubmit for 5% off!**

Please remember that this video does not need to be perfect. You can stumble a few times/repeat yourself maybe/have to start sentences over and you will NOT get points off!

___

[Source](https://leetcode.com/problems/house-robber/description/)