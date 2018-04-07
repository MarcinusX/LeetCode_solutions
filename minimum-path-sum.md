# [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/description/) [Medium]

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example 1:
```
[[1,3,1],
 [1,5,1],
 [4,2,1]]
```
Given the above grid map, return `7`. Because the path `1→3→1→1→1` minimizes the sum.

## [Java solution](https://leetcode.com/submissions/detail/148879594/)
```
class Solution {
    public int minPathSum(int[][] grid) {
        int rows = grid.length;
        int cols = grid[0].length;
        
        for (int j = cols-2; j > -1; j--) {
            grid[rows-1][j] += grid[rows-1][j+1];
        }
            
        for (int i = rows-2; i > -1; i--) {
            grid[i][cols-1] += grid[i+1][cols-1];
            for (int j = cols-2; j > -1; j--) {
                grid[i][j] += Math.min(grid[i+1][j], grid[i][j+1]);
            }
        }
        return grid[0][0];
    }
}
```
