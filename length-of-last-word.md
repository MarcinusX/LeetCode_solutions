# [Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/) [Easy]

Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

**Example:**
```
Input: "Hello World"
Output: 5
```

## [Java solution](https://leetcode.com/submissions/detail/147372311/)
```
class Solution {
    public int lengthOfLastWord(String s) {
        if (s.isEmpty()) {
            return 0;
        }
        int index = s.length()-1;
        while (index >= 0 && s.charAt(index) == ' ') {
            index--;
        }
        if (index < 0) {
            return 0;
        }
        int lastIndex = index;
        while (index >= 0 && s.charAt(index) != ' ') {
            index--;
        }
        return lastIndex - index;
    }
}
```
