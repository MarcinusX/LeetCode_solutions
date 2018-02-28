# [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description/) [Medium]

Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in place.

**Follow up:**  
Did you use extra space?  
A straight forward solution using O(mn) space is probably a bad idea.  
A simple improvement uses O(m + n) space, but still not the best solution.  
Could you devise a constant space solution?

## [Java solution](https://leetcode.com/submissions/detail/142824029/)
```
class Solution {
    public void setZeroes(int[][] matrix) {
        if (matrix.length == 0) {
            return;
        }
        boolean shouldCleanFirstRow = false;
        boolean shouldCleanFirstColumn = false;
        
         for (int i = 0; i < matrix.length; i++) {
            if (matrix[i][0] == 0) {
                shouldCleanFirstColumn = true;
            }
        }
        for (int i = 0; i < matrix[0].length; i++) {
            if (matrix[0][i] == 0) {
                shouldCleanFirstRow = true;
            }
        }
        
        for (int i = 1; i < matrix.length; i++) {
            for (int j = 1; j < matrix[0].length; j++) {
                if (matrix[i][j] == 0) {
                    matrix[0][j] = 0;
                    matrix[i][0] = 0;
                }
            }
        }
        for (int i = 1; i < matrix.length; i++) {
            for (int j = 1; j < matrix[0].length; j++) {
                if (matrix[0][j] == 0 || matrix[i][0] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }
        
        if (shouldCleanFirstColumn) {
            for (int i = 0; i < matrix.length; i++) {
                matrix[i][0] = 0;
            }
        }
        if (shouldCleanFirstRow) {
            for (int i = 0; i < matrix[0].length; i++) {
                matrix[0][i] = 0;
            }
        }
        
    
    }
}
```
