# [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/) [Medium]

Given a string, find the length of the **longest substring** without repeating characters.

**Examples:**

Given `"abcabcbb"`, the answer is `"abc"`, which the length is 3.

Given `"bbbbb"`, the answer is `"b"`, with the length of 1.

Given `"pwwkew"`, the answer is `"wke"`, with the length of 3. Note that the answer must be a **substring**, `"pwke"` is a subsequence and not a substring.

## [Java solution](https://leetcode.com/submissions/detail/139072989/)

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Integer array[] = new Integer[256];
        int repeatIndex = 0;
        int maxLength = 0;
        int currentLength = 0;
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            Integer lastTimeSeenIndex = array[c];
            if (lastTimeSeenIndex == null || lastTimeSeenIndex < repeatIndex) {
                currentLength++;
                if (currentLength > maxLength) {
                    maxLength = currentLength;
                }
            } else {
                currentLength = i - lastTimeSeenIndex;
                repeatIndex = lastTimeSeenIndex;
            }
            
            array[c] = i;
        }
        return maxLength;
    }
}
```
