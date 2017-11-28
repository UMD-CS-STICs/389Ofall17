### Homework #8: Dynamic Programming SOLUTION
___

One possible solution is the following:

```python
def rob(nums):
    return helper(nums, 0, [None] * len(nums))

def helper(arr, i, opt):
    if i < len(arr):
        if opt[i] is None:
            opt[i] = max(arr[i] + helper(arr, i + 2, opt), helper(arr, i + 1, opt))
        return opt[i]
    else:
        return 0
```

Our recurrence is:

```
opt(i) = max(i + opt(i + 2), opt(i + 1))
```

`opt(i)` is the maximum value of robbing the houses starting at index `i` and going to the end of the array. We know that for any house at index `i`, you can either choose to rob the house or not. If you rob the house, your value is going to be `v_i + opt(i + 2)` where `v_i` is the value of the house at index `i`. We have `opt(i + 2)` because we now care about the optimal solution for the house two down from the ith house. We don't care about the house next door because we know that if we rob that, the alarm will sound. However, if we choose to not rob the house, then our value is going to be `opt(i + 1)` because we just care about the optimal solution starting at the house nextdoor (and we can rob it). Since our two options are `opt(i + 1)` and `v_i + opt(i + 2)` and we want to maximize, the recurrence naturally follows as what is noted above.

In order to 'code' this recurrence and keep track of a memoized array, we use a helper function. We pass in an array of length `n` to the function `helper` and populate it as our program progresses. We can think of a call to `helper(arr, i, opt)` as asking "What is `opt(i)`?". We check if we have already stored that in `opt` (our memoization array), and if we have we return it. Otherwise, we assign `opt[i] = max(arr[i] + helper(arr, i + 2, opt), helper(arr, i + 1, opt))` to memoize the result, and then we return it. The right side of that expression shold look very similar to the recurrence described earlier.

The reason we check for `if i < len(arr)` is to make sure that we are not checking for the optimal solution starting with a house that is out of bounds. We just return 0 because this does not add any value to our current obbing schemes.