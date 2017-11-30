### FINAL
##### Out: 11/19/17 | Due: 12/8/17 @ 11:59:59 PM
___
#### Problem Statement
You are a scientist at the world famous, cutting-edge genetics lab *Genix*. Your project is to determine similarities between species in order to draw conclusions about evolutionary progressions and the relationships between organisms. As part of your work, you are responsible for matching DNA sequences. DNA sequences are composed of the following characters: 'A', 'T', 'C', and 'G'. When determining how related two organisms are, you compare two sequences of DNA, and output a number that represents the *cost* of matching these two sequences. There are three actions you can take when matching sequences: ignore (occlude) the current character in sequence 1, ignore (occlude) the current character in sequence 2, or match the current character in both sequences. Each action comes with a specific cost, so you want to minimize this cost over the entire sequence in order to get an accurate reading. 

Formally put, the problem is as follows:

You will be given as input two DNA sequences of equal length, an occlusion cost for sequence 1, and an occlusion cost for sequence 2. If you choose to match characters, the cost will be the absolute value of the ASCII difference between the two characters. All characters in both sequences must be accounted for (in other words, if you occlude some of the characters of one sequence and reach the end of that sequence, you still need to take care of the rest of the characters in the other sequence).

##### Assumptions
- The sequences are not necessarily of equal length
- More than one combination of occlusions and matches may result in the same answer

*Target:* Please describe a solution with `O(mn)` runtime, where `n` is the length of one DNA sequence, and `m` is the length of the other (remember, they are not always the same length). You may also use `O(mn)` space.

##### Examples

Let us call the function that does this `match_DNA(DNA_1, DNA_2, occlusion_1, occlusion_2)`. Consider the following examples:

`match('AACG', 'ATCG', 15, 17)` would return 19 (the ASCII difference between 'A' and 'T') because every character can match with a cost of 0 except the 2nd position ('A' and 'T').
  
`match('ATAC', 'ATCT', 2, 3)` would return 5 because of the following:
```
|A| |T| A /C/
|A| |T| /C/ T
```

This is the cheapest matching here, because occluding T and occluding A only costs 5, whereas if we had matched every character at its index, we would have ended up with a cost of 19, which is not the most accurate reading.
____

### Grading
- Explanation of what you are writing as you are writing it and correctness of algorithm [5 pts.]
- Explanation of `O(mn)` runtime [5 pts.]
- Algorithms uses `O(mn)` space [5 pts.]
- Walk-through of at least 2 sample cases [10 pts.]
- Submitted code that is runnable and works correctly [5 pts.]

___

### Clarifications
If you have any questions about clarification, please post in Piazza! We want to make sure everyone understands the problem. If you have a question, chances are several other people do as well. We will clarify on Piazza and make corrections to this document.

___
### Submission
Please check the `submission.md` file in the `final/` directory of this repository.
