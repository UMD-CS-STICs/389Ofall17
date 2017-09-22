### Homework #3: Sorting and Searching SOLUTION
___

One possible solution is the following:

```java
public int findKthLargest(int[] nums, int k) {
    /* we want to find the kth largest, so to make it a little
     * easier to read, we can reset k to match with the index
     */
    k = nums.length - k;

    /* initialize the initial lower and upper bounds, the same way
     * you would have done with quicksort
     */
    int lo = 0;
    int hi = nums.length - 1;
    
    /* parition your array until we have the correct index 
     * aka the kth largest element.
     */
    while (lo < hi) {
        int j = partition(nums, lo, hi);
        if (j == k) return nums[k];
        if(j < k) {
            lo = j + 1;
        } else {
            hi = j - 1;
        }
    }
    
    return nums[k];
}

private int partition(int[] arr, int lo, int hi) {
    /* get your pivot value
     * create your low_swap_index and your temp variable
     */
    int pivot_val = arr[hi];
    int low_swap_index = lo;
    int temp_for_swap;

    /* move all the values lower than our pivot to 
     * the left of our pivot.
     */
    for(int i = lo; i < hi; i++) {
        if(arr[i] <= pivot_val) {
            temp_for_swap = arr[low_swap_index];
            arr[low_swap_index] = arr[i];
            arr[i] = temp_for_swap;
            low_swap_index += 1;
        }
    }

    /* swap your pivot to make it in the correct location
     */
    temp_for_swap = arr[low_swap_index];
    arr[low_swap_index] = arr[hi];
    arr[hi] = temp_for_swap;
    
    /* return the location
     */
    return low_swap_index;
}
```

This solution uses quicksort's partition method to find the kth largest element. Recall that the partition method works by picking an element `pivot_val`, and then rearranging the array so that all elements less than `pivot_val` are on the left side of `pivot_val`, and all elements greater than `ele` are on the right side. It then returns the new index of `pivot_val`. This algorithm therefore has an `O(n)` runtime in the best case, because if we get lucky and pick the kth largest element to partition on first, we will rearrange the elements once, and the new index of the kth largest element will be k, and we can just return that. However, the downside to this algorithm is that in the worst case, we have a reverse order array (i.e., `[6, 5, 4, 3, 2, 1]`), and a k of n, so we need to run partition n times in order to find the nth largest element. This would have the same runtime as the worst case quicksort, which is `O(n^2)`.

Note: An interesting optimization of this algorithm would be to randomize the input before performing the algorithm. This would effectively eliminate the possibility of having a reverse sorted array, so the runtime would be cut down to `O(nlog(n))` on average. However, randomizing the input also sabotages the best case, so the algorithm becomes `O(nlog(n))` in the best and worst case.

___

Source: https://leetcode.com/problems/kth-largest-element-in-an-array/discuss/
