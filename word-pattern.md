# [Word Pattern](https://leetcode.com/problems/word-pattern/description/) [Easy]

Given a `pattern` and a string `str`, find if `str` follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in `pattern` and a **non-empty** word in `str`.

**Examples:**  
pattern = `"abba"`, str = `"dog cat cat dog"` should return true.  
pattern = `"abba"`, str = `"dog cat cat fish"` should return false.  
pattern = `"aaaa"`, str = `"dog cat cat dog"` should return false.  
pattern = `"abba"`, str = `"dog dog dog dog"` should return false.

**Notes:**  
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

## [Java solution](https://leetcode.com/submissions/detail/142035656/)
```
class Solution {
    public boolean wordPattern(String pattern, String str) {
        String[] words = str.split(" ");
        
        if (words.length != pattern.length()) {
            return false;
        }
        
        Map<Character, String> map = new HashMap<>();
        Set<String> usedStrings = new HashSet<>();
        
        for (int i = 0; i < pattern.length(); i++) {
            String fromMap = map.get(pattern.charAt(i));
            if (fromMap == null) {
                if (usedStrings.contains(words[i])) {
                    return false;
                } else {
                    map.put(pattern.charAt(i), words[i]);
                    usedStrings.add(words[i]);
                }
            } else if (!fromMap.equals(words[i])) {
                return false;
            }
        }
        return true;
    }
}
```
