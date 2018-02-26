# [Rotate Image](https://leetcode.com/problems/rotate-image/description/) [Medium]

You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

**Note:**  
You have to rotate the image **in-place**, which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

**Example 1:**
```
Given input matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],

rotate the input matrix in-place such that it becomes:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]
```
**Example 2:**
```
Given input matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

rotate the input matrix in-place such that it becomes:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]
```

## [Java solution](https://leetcode.com/submissions/detail/142455131/)
```
class Solution {
    public void rotate(int[][] matrix) {
        for (int i = 0; i < matrix.length / 2; i++) {
            int n = matrix.length - 2*i;
            for (int j = 0; j < n-1; j++) {
                int el1 = matrix[i][i+j];
                int el2 = matrix[i+j][i+n-1];
                int el3 = matrix[i+n-1][i+n-1-j];
                int el4 = matrix[i+n-1-j][i];

                matrix[i+j][i+n-1] = el1;
                matrix[i+n-1][i+n-1-j] = el2;
                matrix[i+n-1-j][i] = el3;
                matrix[i][i+j] = el4;
            }
        }
    }
}
```
