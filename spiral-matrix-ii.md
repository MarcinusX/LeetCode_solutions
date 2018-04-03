# [Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/) [Medium]

Given an integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.

For example,  
Given n = `3`,

You should return the following matrix:
```
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```

## [Java solution](https://leetcode.com/submissions/detail/148333201/)
```
class Solution {
    public int[][] generateMatrix(int n) {
        if (n == 0) {
            return new int[0][0];
        }
        int xDirection = 1;
        int yDirection = 0;
        int x = 0, y = 0;
        int xMin = 0, yMin = 0;
        int xMax = n-1, yMax = n-1;
        
        int[][] result = new int[n][n];
        
        int nSquared = n*n;
        for (int i = 1; i <= nSquared; i++) {
            result[y][x] = i;
            if (xDirection == 1 && x == xMax) {
                yMin++;
                xDirection = 0;
                yDirection = 1;
            } else if (yDirection == 1 && y == yMax) {
                xMax--;
                xDirection = -1;
                yDirection = 0;
            } else if (xDirection == -1 && x == xMin) {
                yMax--;
                xDirection = 0;
                yDirection = -1;
            } else if (yDirection == -1 && y == yMin) {
                xMin++;
                xDirection = 1;
                yDirection = 0;
            }
            x += xDirection;
            y += yDirection;
        }
        
        return result;
    }
}
```
