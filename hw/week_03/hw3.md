### Homework #3: Sorting and Searching
##### Out: 9/15/17 | Due: 9/22/17 @ 2:00 PM
___
#### Problem
Given an array of unsorted integers, and an integer k, return the kth largest element in the array. If the array is empty or null, return `null`.

You may **NOT** use any native sorting method like `Arrays.sort` in java or `.sort()` in python to solve this problem. However, if you would like to implement a sort yourself, or use part of a sorting algorithm (such as the partition algorithm in quicksort, you may do so.

Your solution should be `O(nlogn)`.

##### Assumptions
- Integers may be positive or negative
- k will always be greater than or equal to 1 and less than the number of elements in the array

____

#### Examples

Let us call the function that does this `kthLargest(arr, k)`. Consider the following examples:

___

```java
kthLargest([3,2,1,5,6,4], 2) // returns 5 because 5 is the 2nd largest element in the array
kthLargest(null, 3) // returns null because the array is null
kthLargest([], 4) // returns null because the array is null
```

___

#### Grading

- Explanation of thought process before marker hits the board [5 pts.]
- Explanation of what you are writing as you are writing it [5 pts.]
- Explanation of runtime [5 pts.]
	+ `O(nlogn)` solution [2 pts.]
- Walk-through of sample "good" case [5 pts.]
- Walk-through of **all** edge cases mentioned above (array is null, array is empty) [3 pts.]
    + Your program must address all edge cases. We will take off 1 point for every case not addressed.

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
