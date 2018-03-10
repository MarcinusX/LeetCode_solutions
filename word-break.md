# [Word Break](https://leetcode.com/problems/word-break/description/) [Medium]

Given a **non-empty** string s and a dictionary wordDict containing a list of **non-empty** words, determine if s can be segmented into a space-separated sequence of one or more dictionary words. You may assume the dictionary does not contain duplicate words.

For example, given  
s = `"leetcode"`,  
dict = `["leet", "code"]`.

Return true because `"leetcode"` can be segmented as `"leet code"`.

## [Java solution](https://leetcode.com/submissions/detail/144354264/)
```
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        boolean[] tab = new boolean[s.length()];
        return dfs(tab, wordDict, s, 0);        
    }
    
    private boolean dfs(boolean[] visited, List<String> dict, String s, int currentIndex) {
        if (currentIndex == s.length()) {
            return true;
        }
        if (visited[currentIndex]) {
            return false;
        }
    
        List<Integer> possibleIndexes = getPossibleIndexes(dict, s , currentIndex);
        for (Integer i : possibleIndexes) {
            if (dfs(visited, dict, s, i)) {
                return true;
            }
        }
        visited[currentIndex] = true;
        return false;
    }
    
    private List<Integer> getPossibleIndexes(List<String> dict, String s, int index) {
        List<Integer> result = new ArrayList<>();
        for (String str : dict) {
            if (s.substring(index).startsWith(str)) {
                result.add(index+str.length());
            }
        }
        return result;
    }
    
}
```
