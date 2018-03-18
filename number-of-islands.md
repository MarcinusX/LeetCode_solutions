# [Number of Islands](https://leetcode.com/problems/number-of-islands/description/) [Medium]

Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

Example 1:
```
11110
11010
11000
00000
```
Answer: `1`

Example 2:
```
11000
11000
00100
00011
```
Answer: `3`

## [Java solution](https://leetcode.com/submissions/detail/145081723/)
```
class Solution {
    public int numIslands(char[][] grid) {
        if (grid.length == 0 || grid[0].length==0) {
            return 0;
        }
        
        int counter = 0;
        
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[0].length; j++) {
                if (grid[i][j] == '1') {
                    counter++;
                    markIsland(i,j,grid);
                }
            }
        }
        return counter;
    }
    
    private void markIsland(int i, int j, char[][] grid) {
        if (grid[i][j] == '2' || grid[i][j] == '0') {
            return;
        }
        grid[i][j] = '2';
        if (i > 0) {
            markIsland(i-1, j, grid);
        }
        if (i+1 < grid.length) {
            markIsland(i+1, j, grid);
        }
        if (j > 0) {
            markIsland(i, j-1, grid);
        }
        if (j +1 < grid[0].length) {
            markIsland(i, j+1, grid);
        }
    }
}
```
