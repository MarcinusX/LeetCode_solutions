# [Unique Paths II](https://leetcode.com/problems/unique-paths-ii/description/) [Medium]

Follow up for "Unique Paths":

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as 1 and 0 respectively in the grid.

For example,
There is one obstacle in the middle of a 3x3 grid as illustrated below.
```
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
```
The total number of unique paths is 2.

Note: m and n will be at most 100.

## [Java solution]()
```
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int n = obstacleGrid.length;
        int m = obstacleGrid[0].length;
        if (n == 1 || m == 1) {
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    if(obstacleGrid[i][j]==1) {
                        return 0;
                    }
                }
            }
            return 1;
        }
        
        if (obstacleGrid[n-1][m-1] == 1) {
            return 0;
        }
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (obstacleGrid[i][j] == 0) {
                    obstacleGrid[i][j] = 1;
                } else {
                    obstacleGrid[i][j] = 0;
                }
            }
        }
        
        for (int i = n-2; i > -1; i--) {
            if (obstacleGrid[i][m-1] == 0) {
                int j = m-1;
                while (j > -1 && obstacleGrid[i][j] == 0) {
                    for (int k = i; k > -1; k--) {
                        obstacleGrid[k][j] = 0;
                    }
                    j--;
                }
                break;
            }
        }
        
        for (int j = m-2; j > -1; j--) {
            if (obstacleGrid[n-1][j] == 0) {
                int i = n-1;
                while (i > -1 && obstacleGrid[i][j] == 0) {
                    for (int k = j; k > -1; k--) {
                        obstacleGrid[i][k] = 0;
                    }
                    i--;
                }
                break;
            }
        }
    
        for (int i = n-2; i > -1; i--) {
            for (int j = m-2; j > -1; j--) {
                if (obstacleGrid[i][j] != 0) {
                    obstacleGrid[i][j] = obstacleGrid[i+1][j] + obstacleGrid[i][j+1];
                }
            }
        }
    
        return obstacleGrid[0][0];
    }
}
```
