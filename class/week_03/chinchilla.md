### ICI #2: Sorting and Searching - Chinchilla
___
#### Problem Statement
Given an unsorted array nums, reorder it such that `nums[0] < nums[1] > nums[2] < nums[3]...`.

##### Assumptions
- The array is never null
- The array will always have at least 1 value
- You can use `Arrays.sort()` or whatever equivalent to sort an array. The runtime of this function is `O(nlogn)`.

*Target:* Please describe an `O(nlogn)` solution for this problem.

##### Examples

Let us call the function that does this `wiggle_sort(int[])`. Consider the following examples:

```java
wiggle_sort([9]) // [9]
wiggle_sort([1, 5, 1, 1, 6, 4]) // a potential answer is [1, 4, 1, 5, 1, 6]. 
wiggle_sort([1, 3, 2, 2, 3, 1]) // a potential answer is [2, 3, 1, 3, 1, 2].
```

____

#### Hints

1. When we have the ordering as `nums[0] < nums[1] > nums[2] < nums[3]...`, nothing explicitly says that `nums[1] > nums[3]`. For example, `[0, 1, 0, 4]` is completely valid. However, perhaps it may be useful for us to enforce some sort of ordering such that `nums[1] > nums[3]` does always hold true.
2. The brute force solution could be to find the minimum number first, add it to a holder array, and then remove it from the initial array. Then, find the maximum number in the initial array, add it to the holder array, and remove it. You can continue repeating this process. However, this is not too efficient, as you are traversing the entire array each time. This would be `O(n^2)`.
2. Think about what we are picking in the previous hint. Let us say we pick `min_i` or `max_i` at the i-th step. Is there a way for us to not have to search each time? Could `max_i` somehow easily lead us to `max_i+1`? 

___

#### Solution

1. Sort the array.
2. Put a pointer at the front of the array (left) and a pointer at the end of the array (right).
3. Add `nums[left]` followed by `nums[right]`.
4. Increment the left pointer and decrement the right pointer.
5. Keep following this process until pointers pass each other. You must have a check if the left and right pointers point to the same thing, as you do not want to add the element twice.

```java
public int[] zeroSum(int [] nums) {
    // Initialize left and right pointers
    int left = 0;
    int right = nums.length - 1;
    // Initialize array to be returned
    int[] return_array = new int[nums.length];
    // Initialize holder variable to keep track of where you are in return array
    int current_spot = 0;
    while (left < right) {
        // Check to make sure we do not add the same thing twice
        if (left == right) {
            return_array[current_spot] = nums[left]; // Could do nums[left] as well
        } else {
            return_array[current_spot] = nums[left];
            left += 1;
            current_spot += 1;
            return_array[current_spot] = nums[right];
            right -= 1;
            current_spot += 1;
        }
    }    
    return return_array;
}
```

For a challenge, try to do this in `O(n)` time! Think medians...

____

Source: https://leetcode.com/problems/wiggle-sort-ii/