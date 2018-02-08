# [Implement strStr](https://leetcode.com/problems/implement-strstr/description/) [Easy]

Implement strStr().

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**
```
Input: haystack = "hello", needle = "ll"
Output: 2
```
**Example 2:**
```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

## [Java solution](https://leetcode.com/submissions/detail/140021496/)
```
class Solution {
    public int strStr(String haystack, String needle) {
        if (needle.length() == 0) {
            return 0;
        }
        for(int i = 0; i < haystack.length()-needle.length()+1; i++) {
            if (haystack.substring(i, i+needle.length()).equals(needle)) {
                return i;
             }
        }
        return -1;
    }
}
```
