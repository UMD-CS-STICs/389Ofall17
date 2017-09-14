### Homework #1: Big O SOLUTION
___
#### Problem 1

One possible solution is the following:

```java
public int findLargest(int[] arr) {
  int max = Integer.MIN_VALUE;
  for (int num : arr) {
    if (num > max) max = num;
  }
  return max;
}
```

This solution has one for loop that iterates through the entire array. Since each iteration of the for loop only makes a constant time (`(O(1)`) calculation, this means we will make a constant time calculation for all `n` elements in the array, bringing the solution to `O(n)`.

___
#### Problem 2

One possible solution is the following:

```java
public int binaryToInteger(String number) {
  int result = 0;
  int power = 0;
  for (int i = number.length - 1; i >= 0; i -= 1) {
    if (number.charAt(i) == '1') {
      result += Math.pow(2, power);
    }
    power += 1;
  }
  return result;
}
```

This solution has one for loop that iterates through each character in the String that is given to us. At each step in the for loop, we make a constant time calculation (`O(1)`), which brings us to an `O(n)` solution, where `n` is the number of characters in the input String.

___