# [Word Ladder](https://leetcode.com/problems/word-ladder/description/#) [Medium]

Given two words (beginWord and endWord), and a dictionary's word list, find the length of shortest transformation sequence from beginWord to endWord, such that:

Only one letter can be changed at a time.
Each transformed word must exist in the word list. Note that beginWord is not a transformed word.
For example,

Given:  
beginWord = `"hit"`  
endWord = `"co4g"`  
wordList = `["hot","dot","dog","lot","log","cog"]`  
As one shortest transformation is `"hit" -> "hot" -> "dot" -> "dog" -> "cog"`,  
return its length 5.

Note:  
* Return 0 if there is no such transformation sequence.
* All words have the same length.
* All words contain only lowercase alphabetic characters.
* You may assume no duplicates in the word list.
* You may assume beginWord and endWord are non-empty and are not the same.

## [Java solution](https://leetcode.com/submissions/detail/143541858/)
```
class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        if (!wordList.contains(endWord)){
            return 0;
        }
        
        int wordLength = beginWord.length();
        Set<String> begin = new HashSet<>();
        Set<String> end = new HashSet<>();
        Set<String> used = new HashSet<>();
        
        begin.add(beginWord);
        end.add(endWord);
        
        int depth = 1;
        
        while (!begin.isEmpty() && !end.isEmpty()) {
            //always check smaller set
            if (begin.size() > end.size()) {
                Set<String> temp = begin;
                begin = end;
                end = temp;
            }
            
            Set<String> temp = new HashSet<>();
            
            for (String word : begin) {
                for(String testedWord : wordList) {
                    if (!used.contains(testedWord)) {
                        int diff = 0;
                        for (int letter = 0; letter < wordLength; letter++) {
                            if (word.charAt(letter) != testedWord.charAt(letter)) {
                                diff++;
                            }
                        }
                        if (diff == 1) {
                            if (end.contains(testedWord)) {
                                return depth+1;
                            } else {
                                temp.add(testedWord);
                            }
                        }
                    }
                }
                used.add(word);
            }
            
            begin = temp;
            depth++;
            
        }
        
        return 0;
    }

}
```
