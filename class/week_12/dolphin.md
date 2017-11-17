### ICI: Dynamic Programming - Dolphin
___
#### Problem Statement
A message containing letters from A-Z is being encoded to numbers using the following mapping:
```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```
Given an encoded message containing digits, determine the total number of ways to decode it.

##### Assumptions
- The given string will not be null or empty
- You may get a string that has no possible ways to decode
  + For example, '000' cannot be turned into anything

*Target:* Please describe a solution with `O(n)` runtime where `n` is the size of the input string.

##### Examples

Let us call the function that does this `decode_ways(String s)`:
```java
decode_ways('12') // would return 2 because could be 'AB' or 'L'
decode_ways('0') // would return 0 because 0 does not map to anything
decode_ways('112') // would return 3 because it could be any of {'AAB', 'AL', 'KB'}
```


____

#### Hints
- We have to differentiate between 1 and 2 digit letters, so how can we do that?
- When considering position i, how can we use the solutions to the subproblems i - 1 (a 1 digit letter at i) and i - 2 (a 2 digit letter at i)?


___

#### Solution
```python
def decode_ways(str):
    # If the string starts with a 0, we return false because 01 does not decode to anything
    if str == None or str == '' or str[0] == '0':
        return 0

    # At each step of our algorithm, we want to grab both the character in front of us and
    # the two characters in front of us. We then want to sum the solution at our current
    # index, and, if we have a valid 2-digit number, the solution at the index behind us
    # as well. (Keep in mind that if the character in front of us is 0 then we will not 
    # add the solution at the current index.)
    solution = [1]
    for index, _ in enumerate(str[1:]):
        current = int(str[index + 1])
        two_dig = int(str[index + 1] + str([index + 2]))
        solution.append(0)
        if current > 0:
            solution[index + 1] += solution[index]
        if two_dig <= 26 and two_dig >= 10:
            if index - 2 >= 0:
                solution[index + 1] += solution[index - 1]
            else:
                solution[index + 1] += 1
    return solution[len(solution) - 1]
```
___
Source: https://leetcode.com/problems/decode-ways/description/