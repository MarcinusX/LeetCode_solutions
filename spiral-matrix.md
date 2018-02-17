# [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/description/) [Medium]

Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

For example,

Given the following matrix:
```
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
```
You should return `[1,2,3,6,9,8,7,4,5]`.

## [Java solution](https://leetcode.com/submissions/detail/141178418/)
```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        if (matrix.length == 0 || matrix[0].length == 0) {
            return new ArrayList<>();
        }
        
        int minX = 0;
        int minY = 0;
        int maxX = matrix[0].length - 1;
        int maxY = matrix.length - 1;
        int x = 0;
        int y = 0;
        int directionX = 1;
        int directionY = 0;
        
        List<Integer> result = new LinkedList<>();
        
        while (minY <= maxY && minX <= maxX) {
            result.add(matrix[y][x]);
            if (directionY == -1 && directionX == 0 && x == minX && y == minY) {
                directionY = 0;
                directionX = 1;
                minX++;
            } else if (directionY == 0 && directionX == 1 && x == maxX && y == minY) {
                directionY = 1;
                directionX = 0;
                minY++;
            } else if (directionY == 1 && directionX == 0 && x == maxX && y == maxY) {
                directionY = 0;
                directionX = -1;
                maxX--;
            } else if (directionY == 0 && directionX == -1 && x == minX && y == maxY) {
                directionY = -1;
                directionX = 0;
                maxY--;
            }
            x += directionX;
            y += directionY;
        }
        return result;
    }
}
```
