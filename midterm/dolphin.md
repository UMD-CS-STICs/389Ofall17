### Dolphin Problem
##### Out: 10/7/17 | Due: 10/20/17 @ 2:00 PM
___
### Problem
Given a board with `m` by `n` cells, each cell has an initial state live (1) or dead (0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules:

- Any live cell with fewer than two live neighbors dies, as if caused by under-population.
- Any live cell with two or three live neighbors lives on to the next generation.
- Any live cell with more than three live neighbors dies, as if by over-population.
- Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.

Write a function to compute the next state (after one update) of the board given its current state.

Remember that the board needs to be updated at the same time: You cannot update some cells first and then use their updated values to update other cells.

We would also like you to explain in what cases your solution would fail. We are not going to be "stress testing" your program, and so as long as your solution works on inputs like the one in the example, you will be fine. **Please look at the "Retrospective" section to see more information on this.**

#### Input
Your input will be a `m` by `n` 2D integer array full of 0s and 1s:

```python
board = [[1,0,1,0],
         [1,1,0,0],
         [0,1,1,1]]
```

#### Output
You should not return anything, but the inputted 2D array should be modified to what the next state is.

**Your solution should run in `O(n*m)` time.**

#### Assumptions
- You will not be given an empty game board 
- You will not be given a `null` game board

____

### Examples   
Let us call the function that does this `get_next_state(board)`. Consider the following examples:

```python
board = [[1,0,1,0],
         [1,1,0,0],
         [0,1,1,1]]
```
Calling `get_next_state(board)` changes `board` to:
```python
[[1,0,0,0],
 [1,0,0,1],
 [1,1,1,0]]
```

___
### Retrospective
We want you to explain two things.

1. Explanation of what cases would break your program. Think about what would happen if we passed in a stream.
2. Explanation of modifications to improve runtime. For example, we can implement mergesort in `O(nlogn)` and that's awesome, but we could still improve the time. For example, because each recursive call to mergesort is an independent problem, we could send each call to a different computer and have a faster overall computation time. This way all of the recursive calls aren't all waiting for each other to finish in the stack.

Please include timestamps for these in your YouTube descriptions.

___
### Hints
Don't go out of bounds!

___
### Grading
- Explanation of what you are writing as you are writing it and correctness of algorithm [5 pts.]
- Explanation of `O(n*m)` runtime [5 pts.]
- Walk-through of a sample case sample [3 pts.]
- Submitted code that is runnable and works correctly [5 pts.]
- Explanation of breaking cases [5 pts.]
- Explanation of helpful modifications [5 pts.]

___
### Clarifications
If you have any questions about clarification, please post in Piazza! We want to make sure everyone understands the problem. If you have a question, chances are several other people do as well. We will clarify on Piazza and make corrections to this document.

___
### Submission
Please check the `submission.md` file in the `midterm/` directory of this repository.

___

While I am providing the [source](https://leetcode.com/problems/game-of-life/description/) because LeetCode makes it easy to see if your solution is correct or not, I urge you not to look for the correct answer online! You are cheating yourself, and going through the problem solving process is the only real way to get better!