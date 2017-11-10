### Homework #7: Dynamic Programming SOLUTION
___

One possible solution is the following:

```python
def word_break(s, wordDict):
        # lst is the memoization array, where we set the base case at index = 0 to True
        lst = [None] * (len(s) + 1)
        lst[0] = True
        
        # iterate throught the string, checking if any of the words in your 
        # wordDict could "right align" with the current substring. If it can, 
        # check to see if the remainder of the string has already been covered
        # by another word in your wordDict
        for c in xrange(1, len(s) + 1):
            for word in wordDict:
                if len(word) <= c:
                    # Say s = 'leetcode' and you are currently considering the
                    # last index of the word, and the variable word = 'code'.
                    # The first part of this if statement is checking 
                    # everything except for 'code' was memoized as a valid 
                    # combination of words in wordDict. In other words, this is
                    # checking if 'leet' was successfully matched. The second
                    # part of the if statement is checking if 'code' matches 
                    # with the substring in question (from the right side).
                    if lst[c - len(word)] and s[c - len(word):c] == word:
                        lst[c] = True
                        # we break because if it is valid, we do not have to 
                        # look at any other word in wordDict
                        break

        return lst[len(s)] == True
                
            
```

This solution uses memoization with an array of the same size of the given word. At an index `i` of the memoized array, call it `opt`, `opt[i]` tells you whether or not the substring to index `i` can be created with items from the wordDict. We iterate through all substrings in our string and each step check two things for each word in wordDict:
1. Does the word match with the substring (from the right)? This means that the word 'code' would match with 'dafscode'.
2. Can you construct the remainder of substring (of the substring) out of your wordDict? Using the above example, since 'code' matched, can you now create 'dafs' out of the wordDict? You can look this answer up in `O(1)` using your memoization array.
