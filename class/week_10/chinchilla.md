### ICI: Dynamic Programming - Chinchilla
___
#### Problem Statement
Given a chess board (of size 8 x 8), a starting point `(x, y)` a length `l`, return the number of possible knights tours of length `l` starting at coordinate `(x, y)`.

**Background:** In chess, a knight's behavior is a bit odd. The movement of a knight is restricted to two squares in any non-diagonal direction (i.e., up, down, left, or right), followed by one square in a perpendicular direction. (In other words, if you move two squares up or down, you must then move one square to the left or right. Likewise, if you move two squares left or right, then the following square must be up or down.) We define a neighbor to be any square reachable from square x via one knight's move.

##### Assumptions
- `l` will be greater than or equal to 0
- You can repeat squares in the path
- `(x, y)` will be in bounds of the chess board

*Target:* Please describe a solution with `O(mnl)` runtime where `mn` is the size of the board. You may use up to `O(mnl)` space as well.

##### Examples

Let us call the function that does this `tour(x, y, l)`. Consider the following examples:

**THIS EXAMPLE IS IMPORTANT:** `tour(5, 4, 0)` returns `1` because you can only "travel" to yourself with 0 moves.

`tour(5, 4, 1)` returns `8` because you can take 8 possible knights paths away from the point `(5, 4)` on a chessboard.


____

#### Hints

**It will help you out tremendously to break this problem down into several components or helper methods:**

1. What do we want to store here? If we know which squares we can reach from (x, y), what does that tell us about how many paths there are to each of (x, y)'s neighbors?
2. Once we know how which squares can reach (x, y), how do we then determine how many paths reach (x, y)?

___

#### Solution

1. The first thing we want to do is create a hash that maps a coordinates to their neighbors (remember we're using the term 'neighbor' to mean one knight's move away)
2. Once our hash is constructed, we want to loop from 1 to l
3. At each iteration, we want to update the board by looping through the entire board and updating each coordinate x with the sum of all its neighbors
4. Finally, we want to total all squares from the final board and return it

```python
def tour(x, y, l):
    neighbors = dict()
    dirs = [(-2, -1), (-2, 1), (2, -1), (2, 1),
            (-1, -2), (-1, 2), (1, -2), (1, 2)]
    # create hash mapping coordinates x to set of coordinates
    # that can reach x via one knight's move
    for i in range(8):
        for j in range(8):
            for vert, horiz in dirs:
                if 0 <= i + vert < 8 and 0 <= j + horiz < 8:
                    if ((i + vert, j + horiz)) not in neighbors:
                        neighbors[(i + vert, j + horiz)] = set()
                    neighbors[(i + vert, j + horiz)].add((i, j))

    blank = [[0] * 8 for _ in range(8)]
    curr_board = [row[:] for row in blank]
    curr_board[x][y] = 1

    # Steps 2 & 3. This nested loop is what gives us O(mnl) runtime.
    for k in range(l):
        new_board = [row[:] for row in blank]
        for i in range(8):
            for j in range(8):
                for neighbor in neighbors[(i, j)]:
                    row, col = neighbor
                    new_board[i][j] += curr_board[row][col]
        curr_board = new_board

    # Step 4
    sum = 0
    for i in range(8):
        for j in range(8):
            sum += curr_board[i][j]
    return sum

```

____