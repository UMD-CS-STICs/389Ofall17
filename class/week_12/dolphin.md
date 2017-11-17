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



___

#### Solution
```python
def decode_ways(s):
    if s == None or s == '' or s[0] == '0':
        return 0
    sol = [1 if int(s[0]) != 0 else 0]
    for idx, c in enumerate(s[1:]):
        current = int(s[idx + 1])
        two_dig = int(s[idx:idx + 2])
        sol.append(0)
        if current > 0:
            sol[idx + 1] += sol[idx]
        if two_dig <= 26 and two_dig >= 10:
            if idx - 2 >= 0:
                sol[idx + 1] += sol[idx - 1]
            else:
                sol[idx + 1] += 1
    return sol[len(sol) - 1]
```
___
Source: https://leetcode.com/problems/decode-ways/description/