### Homework #2: String Manipulation SOLUTION
___

One possible solution is the following:

```python
def reverseOne(sentence, word):
  # Equivalent to (sentence == null || word == null)
  if sentence is None or word is None:
    return 'BAD INPUT'

  found = False
  currrent_position_in_target = 0
  for i in range(0, len(sentence)):
    """
    If I come across a character that is in my target,
    I want to start incrementing currrent_position_in_target to check the
    next character in the target. If the characters do not match,
    I set it back to zero to start over again
    """
    if sentence[i] == word[currPos]:
      currPos += 1
    else:
      currPos = 0

    if currPos == len(word):
      start = i - len(word) + 1
      end = i
      for j in range(start, int(len(word) / 2) + start):
        temp = sentence[start]
        sentence[start] = sentence[end]
        sentence[end] = temp
        end -= 1
      return sentence
      
  return sentence
```

This solution has a for loop that iterates through the entire sentence. Since each iteration of the for loop only makes a few constant time (`(O(1)`) calculations, this means we will only make constant time calculations for all `n` elements in the original sentence, bringing the solution to `O(n)` so far. Then there is another for loop that is half the size of the target word if we've found it; however the target can only be contained in the sentence if its length is less than or equal to the sentence, so this for loop will not increase the runtime. This brings the runtime of the total algorithm to `O(n)`, where `n` is the number of characters in the original sentence.
