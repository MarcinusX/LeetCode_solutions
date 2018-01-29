# [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/) [Easy]

Write a function to find the longest common prefix string amongst an array of strings.

## [Java solution](https://leetcode.com/submissions/detail/138440612/)

```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        char currentChar = 'c';
        if (strs.length == 0) {
            return "";
        }
        for (int index=0; index<strs[0].length(); index++) {
                currentChar = strs[0].charAt(index);
                for (int i=1; i<strs.length; i++) {
                    if (index==strs[i].length() || strs[i].charAt(index) != currentChar) {
                        return strs[i].substring(0,index);
                    }
                }
            
        }
        return strs[0];
    }
}
```
