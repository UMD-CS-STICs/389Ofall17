### ICI #2: Sorting and Searching - Dolphin
___
#### Problem Statement
Given an array of unique, unsorted integers (positive and negative), return the two integers (in an array) whose sum is closest to 0.

##### Assumptions
- The array is never null
- The array will always have at least 2 values
- You can use `Arrays.sort()` or whatever equivalent to sort an array. The runtime of this function is `O(nlogn)`.

*Target:* Please describe an `O(nlogn)` solution for this problem.

##### Examples

Let us call the function that does this `zero_sum(int[])`. Consider the following examples:

```java
zero_sum([9, 2, -4, 32, 2, 5]) // [-4, 5]
zero_sum([3, 2]) // [3, 2]
zero_sum([2, -2, 3, -3]) // either [2, -2] or [3, -3] would be correct 
```

____

#### Hints

1. Let us think about what the brute force method would be. If we simply examine every single pair of integers, we could keep track of the sums and save the one that is closest to 0. However, this is pretty expensive with a runtime of `O(n^2)`. Why can't we do any better than this with the current state of the array? Because we don't know anything about the order. Perhaps sorting could help us.
2. After we have sorted our array, we know certain things about our array. We know that `arr[0] + arr[1] <= arr[0] + arr[2]` because `arr[2] >= arr[1]` because our array is sorted. We also know that `arr[arr.length - 1] + arr[arr.length - 2] >= arr[arr.length - 1] + arr[arr.length - 3]` because `arr[arr.length - 2] >= arr[arr.length - 3]`. How can we use this idea in our solution?
3. Say we have 2 pointers to the first and last elements in the array. If we sum these up and get a number greater than 0, that means that we want to find a smaller sum. How can we modify one of the pointers to achieve that? What do we do if we get a sum less than 0?
4. What about when we get the sum is equal to 0?

___

#### Solution

1. Sort the array. (`O(nlogn)`)
2. Put a pointer at the front of the array (left) and a pointer at the end of the array (right).
3. Obtain the sum. If it is greater than 0, move the right pointer left by one. If it is less than 0, move the left pointer right by one. 
4. Recur with new pointer locations. (`O(n)`)
5. Return when the sum is 0, or when the pointers pass each other.

Runtime: `O(nlogn)`

```java
public int[] zero_sum(int [] nums) {
    // Initialize left and right pointers
    int left = 0;
    int right = nums.length - 1;
    // Initialize array to be returned
    int[] return_array = new int[2];
    // Initialize running sum of your best sum
    int current_dist_from_0 = Integer.MAX_INTEGER;
    Arrays.sort(nums);
    while (left < right) {
        int sum = nums[left] + nums[right];
        // Check to see if the current pair is better than what is saved
        if (Math.abs(sum) < current_dist_from_0) {
            current_dist_from_0 = Math.abs(sum);
            return_array[0] = nums[left];
            return_array[1] = nums[right];
            // Unecessary step, but saves us some runtime
            if (sum == 0) return return_array;
        }
        // If the sum is greater than 0, we should decrement the right pointer to make the next sum smaller. Otherwise, we should increment the left pointer to make the next sum larger.
        if (sum > 0) {
            right -= 1;
        } else {
            left += 1;
        }
    }    
    return return_array;
}
```