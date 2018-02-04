# [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) [Medium]

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example:**
```
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
 ```

**Example:**
```
Input: "cbbd"

Output: "bb"
```

## [Java solution](https://leetcode.com/submissions/detail/139357486/)
```
class Solution {
    int index = 0;
    int maxLength = 1;
    
    public String longestPalindrome(String s) {
        for (int i = 0; i < s.length()-1; i++) {
            extend(s,i,i);
            extend(s,i,i+1);
        }
        
        return s.substring(index, index+maxLength);
    }
    
    public void extend(String s, int start, int end) {
        while(start >= 0 && end < s.length() && s.charAt(start) == s.charAt(end)) {
            start--;
            end++;
        }
        int length = end-start-1;
        if (length > maxLength) {
            maxLength = length;
            index = start+1;
        }
    }
}

```
