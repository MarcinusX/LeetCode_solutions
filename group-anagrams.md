# [Group Anagrams](https://leetcode.com/problems/group-anagrams/description/) [Medium]

Given an array of strings, group anagrams together.

For example, given: `["eat", "tea", "tan", "ate", "nat", "bat"]`,  
Return:
```
[
  ["ate", "eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

## [Java solution](https://leetcode.com/submissions/detail/142663391/)
```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for (int i = 0; i < strs.length; i++) {
            char[] characters = strs[i].toCharArray();
            Arrays.sort(characters);
            String sorted = new String(characters);
            
            if (!map.containsKey(sorted)) {
                List list = new ArrayList<>();
                list.add(strs[i]);
                map.put(sorted, list);
            } else {
                map.get(sorted).add(strs[i]);
            }
        }
        
        return new ArrayList<List<String>>(map.values());
    }
}
```
