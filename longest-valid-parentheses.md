# [Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/description/) [Hard]
Given a string containing just the characters `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.

For `"(()"`, the longest valid parentheses substring is `"()"`, which has length = `2`.

Another example is `")()())"`, where the longest valid parentheses substring is `"()()"`, which has length = `4`.

## [Java solution](https://leetcode.com/submissions/detail/149498368/)
```
class Solution {
    public int longestValidParentheses(String s) {
        
        int maxValid = 0;
        int lastExtraCloseIndex = -1;
        Stack<Integer> openIndexes = new Stack<>();
        for (int i = 0 ; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                openIndexes.push(i);
            } else if (!openIndexes.empty()) {
                openIndexes.pop();
            } else {
                int currentLength = i - lastExtraCloseIndex - 1;
                if (currentLength > maxValid) {
                    maxValid = currentLength;
                }
                lastExtraCloseIndex = i;
            }
        }
        
        int lastIndex = s.length();
        while (!openIndexes.empty()) {
            int openIndex = openIndexes.pop();
            int diff = lastIndex = lastIndex - openIndex - 1;
            if (diff > maxValid) {
                maxValid = diff;
            }
            lastIndex = openIndex;
        }
        
        int lastDiff = lastIndex - lastExtraCloseIndex -1;
        if (lastDiff > maxValid) {
            maxValid = lastDiff;
        }
        
        return maxValid;
    }
}
```
