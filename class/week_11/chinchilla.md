### ICI: Dynamic Programming - Chinchilla
___
#### Problem Statement
Given a set of coin values and a target value, what is the least number of coins that can be used to make up the target value?

##### Assumptions
- There will always be a coin of value 1 in your value set
- Coin values are given to you in ascending order
- Target is always >= 1
- You can repeat coins as many times as you like

*Target:* Please describe a solution with `O(nV)` runtime where `n` is the number of possible coin values and `V` is the target value. You may use up to `O(nV)` space as well.

##### Examples

Let us call the function that does this `make_change(int[] values, int target)`. Consider the following examples:

`make_change([1, 6, 10], 18)` returns `3` because you can make 18 with three coins of value 6.
`make_change([1, 2, 10, 25], 60)` returns `3` because you can make 60 with 2 25 coins and a 10 coin.


____

#### Hints

1. What do we want to store here? How can we break this down into subproblems.
2. If we create an n x V table, what does the value at (n, V) represent?
3. How do we set up our recursion to handle repeats?
4. We need to watch out for the case where our current coin value is less than, equals, or is greater than our current target

___

#### Solution

1. The first thing we want to do is create an `nV` table to store our optimum values
2. We then want to initialize our first row to represent our base cases (if you only have a penny, then you need x amount of pennies to make value x)
3. For every other cell in the array, we compute the value `n, V` to be the minimum of `(n - 1, V)` and `1 + (n, V - v)` where `v` is the value of coin `n`
4. Finally, we want to return the value of the cell in the bottom right corner.

```python
def make_change(values, target):
  table = [[0] * (target) for x in values]
  # since we always have a 1-valued coin, we set the first row
  # to be the value of its index + 1 (we add 1 to represent the
  # value at the index. i.e., index (target - 1) represents target)
  for i in range(target):
    table[0][i] = i + 1

  for i in range(1, len(values)):
    for j in range(target):
      # if the value is less than the target, we call our recurrence
      # on min((n - 1, V), (n, V - v)
      if values[i] < (j + 1):
        table[i][j] = min(table[i - 1][j], 1 + table[i][j - values[i]])
      # if the value is equal to the target, then obviously its cell should be 1
      elif values[i] == (j + 1):
        table[i][j] = 1
      # if the value is greater than the target, then we cannot add it
      # so we immediately set it to the value of (n - 1, V)
      else:
        table[i][j] = table[i - 1][j]

  return table[len(values) - 1][target - 1]

```

____

#### Alternate Solution

While we originally specified this problem to be `O(nV)` space, we can also do a more optimized version in `O(V)` space. At each step of our iteration, we simply run through the coin values and check the indeces of the current slot minus the current coin value in order to determine the current max like so:

```python
def make_change(values, target):
  # we can't use any coins to make 0, and we always have a penny
  # so we can make 1 with 1 coin
  values = [0, 1]
  for i in range(2, target + 1):
    min_val = float('inf')
    for value in values:
      if (i - value) >= 0:
        min_val = min(min_val, 1 + values[i - value])
      else:
        min_val = values[i - 1]
    values.append(min_val)
    
  return values[target]
```
