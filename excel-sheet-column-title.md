# [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/description/) [Easy]
Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:
```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...
```
Example 1:
```
Input: 1
Output: "A"
```
Example 2:
```
Input: 28
Output: "AB"
```
Example 3:
```
Input: 701
Output: "ZY"
```

## [Java solution](https://leetcode.com/submissions/detail/152330969/)
```
class Solution {
    public String convertToTitle(int n) {
        StringBuilder sb = new StringBuilder();
        while (n > 0) {
            sb.insert(0, (char) ('A' + ((n-1) % 26)) );
            n = (n-1) / 26;
        }
        return sb.toString();
    }
}
```
