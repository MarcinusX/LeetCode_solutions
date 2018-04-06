# [Unique Paths](https://leetcode.com/problems/unique-paths/description/) [Medium]

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![img](https://leetcode.com/static/images/problemset/robot_maze.png)  
Above is a 3 x 7 grid. How many possible unique paths are there?

Note: m and n will be at most 100.

## [Java solution](https://leetcode.com/submissions/detail/148750023/)
```
class Solution {
    public int uniquePaths(int m, int n) {
        if (n == 0 || m == 0) {
            return 0;
        } else if (n == 1 || m == 1) {
            return 1;
        } 
        
        int[][] tab = new int[m][n];
        for (int i = n-1; i > -1; i--) {
            tab[m-1][i] = 1;
        }
        for (int i = m-2; i > -1; i--) {
            tab[i][n-1] = 1;
            for (int j = n-2; j > -1; j--) {
                tab[i][j] = tab[i+1][j] + tab[i][j+1];
            }
        }
        return tab[0][0];
        
    }
}
```
