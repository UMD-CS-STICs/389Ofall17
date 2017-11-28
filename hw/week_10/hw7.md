### Homework #7: Dynamic Programming
##### Out: 11/3/17 | Due: 11/10/17 @ 2:00 PM
___
#### Problem Statement
Given a non-empty string `s` and a dictionary (array) `word_list` containing a list of non-empty words, determine if `s` can be made up of a combination of words from `word_list`. You may assume the dictionary does not contain duplicate words.

##### Assumptions
- `word_list` is not empty
- `s` is not `null` or empty

*Target:* Please describe a solution with `O(nm)` runtime, where `n` is the size of the `word_list` array and `m` is the length of the string.

##### Examples

Let us call the function that does this `boolean word_break(String[] word_list, String s)`. Consider the following examples:

```java
String s = "leetcode";
String[] word_list = ["leet", "code"];
word_break(word_list, s) // would return true because leetcode can be made out of "leet" and "code", which are both in the word_list

String s = "leetcodecode";
String[] word_list = ["leet", "code"];
word_break(word_list, s) // would return true because leetcode can be made out of "leet", "code", and "code", which are both in the word_list

String s = "leetcodeco";
String[] word_list = ["leet", "code"];
word_break(word_list, s) // would return false
```

____

#### Grading

- Explanation of what you are writing as you are writing it and correctness of algorithm [3 pts.]
- Explanation of `O(nm)` runtime [5 pts.]
- Walk-through of sample true case [1 pts.]
- Walk-through of sample false case [1 pts.]

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
