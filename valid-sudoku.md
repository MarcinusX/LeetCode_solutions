# [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/) [Medium]
Determine if a Sudoku is valid, according to: [Sudoku Puzzles - The Rules](http://sudoku.com.au/TheRules.aspx).

The Sudoku board could be partially filled, where empty cells are filled with the character `'.'`.

![img](http://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

A partially filled sudoku which is valid.

**Note:**  
A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.

## [Java solution](https://leetcode.com/submissions/detail/142143151/)
```
class Solution {
    public boolean isValidSudoku(char[][] board) {
        //first index is number of coulmn/row/square, second index is number of digit, true if has occured
        boolean[][] columns = new boolean[9][9];
        boolean[][] rows = new boolean[9][9]; 
        boolean[][] squares = new boolean[9][9]; 
        for (int row = 0; row < 9; row++) {
            for (int col = 0; col < 9; col++) {
                if (board[row][col] != '.') {
                    // calculated every time for better runtime
                    // int number = board[row][col] - '1';//numbers are from 0 to 8 to match indexes
                    
                    //check row
                    if (rows[row][board[row][col] - '1']) {
                        return false;
                    } else {
                        rows[row][board[row][col] - '1'] = true;
                    }
                    
                    //check column
                    if (columns[col][board[row][col] - '1']) {
                        return false;
                    } else {
                        columns[col][board[row][col] - '1'] = true;
                    }
                    
                    //check square
                    // calculated every time for better runtime
                    // int square = (row/3) * 3 + col/3;
                    if (squares[(row/3) * 3 + col/3][board[row][col] - '1']) {
                        return false;
                    } else {
                        squares[(row/3) * 3 + col/3][board[row][col] - '1'] = true;
                    }
                }
            }
        }
        return true;
    }
}
```
