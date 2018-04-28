# [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/description/) [Medium]
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

* Integers in each row are sorted from left to right.
* The first integer of each row is greater than the last integer of the previous row.

Example 1:
```
Input:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
Output: true
```
Example 2:
```
Input:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
Output: false
```

## [Java solution](https://leetcode.com/submissions/detail/151970131/)
```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix.length == 0 || matrix[0].length == 0) {
            return false;
        }
        int row = findRow(matrix, target);
        if (row == -1) {
            return false;
        }
        return quickSelect(matrix[row], target, 0, matrix[row].length);
        
    }
    
    int findRow(int[][] matrix, int target) {
        for (int i = 0; i < matrix.length; i++) {
            if (matrix[i][0] > target) {
                return i-1;
            }
        }
        return matrix.length - 1;
    }
    
    boolean quickSelect(int[] matrix, int target, int start, int end) {
        if (start == end) {
            return false;
        }
        int middle = (start+end)/2;
        if (matrix[middle] == target) {
            return true;
        } else if (target > matrix[middle]) {
            return quickSelect(matrix, target, middle+1, end);
        } else {
            return quickSelect(matrix, target, start, middle);
        }
    }
    
}
```
