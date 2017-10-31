### Homework #5: Stacks and Queues SOLUTION
___

One possible solution is the following:

```python
def post_order_math(arr):
    stack = []
    for elem in arr:
        if elem.isdigit():
            stack.append(int(elem))
        # isdigit() only works with positive integers, so we
        # add a check for negative integers
        elif elem[1:].isdigit:
            stack.append((int(elem[1:])) * -1)
        elif elem == '+':
            add2 = stack.pop()
            add1 = stack.pop()
            stack.append(add2 + add1)
        elif elem == '-':
            sub2 = stack.pop()
            sub1 = stack.pop()
            stack.append(sub1 - sub2)
        elif elem == '*':
            mul2 = stack.pop()
            mul1 = stack.pop()
            stack.append(mul1 * mul2)
        elif elem == '/':
            div2 = stack.pop()
            div1 = stack.pop()
            stack.append(div1 / div2)
    return stack[0]
```

This solution uses a stack to keep track of our most recent operations. We iterate through the array, and if we have a number, we simply push it onto our stack. Otherwise we've encountered an operator, so we need to pop the last two elements off the stack and replace them with the result of their operation. When we finish running through the entire array, we will have one element left in our stack, so we return it. Since we examine every element exactly once, we have `O(n)` time. We keep a separate stack whose storage varies depending on the size of `n`, so we use `O(n)` space.