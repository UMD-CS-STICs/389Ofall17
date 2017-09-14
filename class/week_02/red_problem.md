### ICI #1: String Manipulation - RED
___
#### Red Problem
Given a string, find the length of the longest substring without repeating characters.

#### Assumptions
- The string could be null or empty, in which case you should return 0

*Target:* Please describe an O(n) solution for this problem.

#### Examples

Let us call the function that does this `lengthOfLongestSubstring(s)`. Consider the following examples:

```java
lengthOfLongestSubstring("abcabcbb") // would return 3 because of "abc"
lengthOfLongestSubstring("bbbbb") // would return 1 because of "b"
lengthOfLongestSubstring("pwwkew") // would return 3 because of "wke" or "kew"
```

____

#### Solution

We want to slide a window across the word by moving the right bound. At every step, we ensure that we still have a valid window by checking if the new letter introduced my moving the right bound is already in our word (we keep track of this with a set). If it is not valid, we move the left bound until it is valid again. At every step, we check the length to potentially update the value to return.

```python
def lengthOfLongestSubstring(s):
    # left_pointer is the left bound of the current word (inclusive)
    # right_pointer is the right bound of the current word (inclusive)
    left_pointer = 0
    right_pointer = 0
    # running max length we find
    length = 0
    # running hashset of current characters in word
    taken = set()
    # handling null/empty string cases
    if s == '' or s is None:
        return 0
    # begin moving the right pointer until we hit the end
    while right_pointer < len(s):
        # if we run into a duplicate character, we increment the left pointer to the next valid spot
        if s[right_pointer] in taken:
            # move left bound until you find the duplicate
            while s[left_pointer] != s[right_pointer]:
                # need to remove all the characters you are removing from the window
                taken.remove(s[left_pointer])
                left_pointer += 1
            # need to increment one more, as you currently have the duplicate letter in the string
            left_pointer += 1
        else:
            # add the new letter to the set
            taken.add(s[right_pointer])
        # calculate new length
        length = max(length, right_pointer - left_pointer + 1)
        # move right pointer
        right_pointer += 1
    return length
```

[Source](https://leetcode.com/problems/longest-substring-without-repeating-characters/)