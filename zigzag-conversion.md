# [ZigZag Conversion](https://leetcode.com/problems/zigzag-conversion/description/) [Medium]
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: `"PAHNAPLSIIGYIR"`
Write the code that will take a string and make this conversion given a number of rows:
```
string convert(string text, int nRows);
```
`convert("PAYPALISHIRING", 3)` should return `"PAHNAPLSIIGYIR"`.

## [Java solution](https://leetcode.com/submissions/detail/139512638/)
```
class Solution {
    public String convert(String s, int numRows) {
        if (numRows == 1 || s.length() == 0) {
            return s;
        }
        
        StringBuilder builder = new StringBuilder();
        
        for (int row = 0; row < numRows; row++) {
            for (int index = row; index < s.length(); index += (2*numRows-2)) {
                addIfPossible(builder, index, s);
                if (row != 0 && row != numRows-1) {
                  addIfPossible(builder, index+(numRows-row-1)*2, s);
                }
            }
        }
        return builder.toString();
    }
    
    private void addIfPossible(StringBuilder builder, int index, String s) {
        if (index < s.length()) {
            builder.append(s.charAt(index));
        }
    }
}
```
