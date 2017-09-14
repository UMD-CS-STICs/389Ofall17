### Homework #2: String Manipulation
##### Out: 9/8/17 | Due: 9/15/17 
___
#### Problem
Given a sentence and a target word, search the sentence for the word. If the target word is detected in the sentence, reverse the target within the sentence, and return the sentence. If the target is not detected, you can return the original sentence. We discuss more of the specifications in the 'assumptions' section below.

**Note:** If the target is a substring of another string, it is **not** a match. For example, if the target is `"ate"`, and the string is `"I created ice cream after I ate pizza."`, then `reverseOne("I created ice cream after I ate pizza", "ate")` will return `"I created ice cream after I eta pizza"`, even though `"ate"` is a substring of `"created."`

Please describe an O(n) solution for this problem.

#### Assumptions
- Everything is lowercase
- There is at most one instance of the target word within the sentence
- Both strings will never be empty, but they **could** be null
+ If either input is null, you must return the string `"BAD INPUT"`
- The target does not have any spaces

#### Examples

Let us call the function that does this `reverseOne(sentence, word)`. Consider the following examples:

___

```java
reverseOne("oreos are my favorite food", "favorite")
```

This will return:
```java
"oreos are my etirovaf food"
```
because `favorite` is detected in the string.

___

```java
reverseOne("oreos are my favorite food", "notinstring")
```

This will return:
```java
"oreos are my favorite food"
```
because `notinstring` is **NOT** detected in the string.

___

```java
reverseOne("oreos are my favorite food", null)
```

This will return:
```java
"BAD INPUT"
```
because null is not a valid input, and we want `"BAD INPUT"` in this case.

___

```java
reverseOne(null, "hello")
```

This will return:
```java
"BAD INPUT"
```
because null is not a valid input, and we want `"BAD INPUT"` in this case.

#### Grading

- Explanation of thought process before marker hits the board [5 pts.]
- Explanation of what you are writing as you are writing it [5 pts.]
- Explanation of runtime [5 pts.]
	+ O(n) solution [2 pts.]
- Walk-through of sample "good" case [5 pts.]
- Walk-through of **all** edge cases mentioned above (not in string, first input is null, second input is null) [3 pts.]
    + Your program must address all edge cases. We will take off 1 point for every case not addressed.

#### Submission

Please **record** yourself doing this problem out on a whiteboard. **There should NOT be cuts in this video.** This means that you must do this entire thing in one run-through. Please upload this video to YouTube **unlisted**, and submit a text file on the CS submit server with the link for us to watch.

Please remember that this video does not need to be perfect. You can stumble a few times/repeat yourself/have to start sentences over and you will NOT get points off! Everyone is human.
