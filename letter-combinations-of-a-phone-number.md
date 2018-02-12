# [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/) [Medium]


Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

![image](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)


```
Input:Digit string "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```
**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.

## [Java solution](https://leetcode.com/submissions/detail/140560736/)
```
class Solution {
    
    private static final Map<Character, List<Character>> map;
    static {
        Map<Character, List<Character>> mMap = new HashMap<>();
        mMap.put('2', Arrays.asList('a','b','c'));
        mMap.put('3', Arrays.asList('d','e','f'));
        mMap.put('4', Arrays.asList('g','h','i'));
        mMap.put('5', Arrays.asList('j','k','l'));
        mMap.put('6', Arrays.asList('m','n','o'));
        mMap.put('7', Arrays.asList('p','q','r','s'));
        mMap.put('8', Arrays.asList('t','u','v'));
        mMap.put('9', Arrays.asList('w','x','y','z'));
        map = Collections.unmodifiableMap(mMap);
    }
    
    public List<String> letterCombinations(String digits) {
        int cases = 1;
        int numDigits = digits.length();
        for (int i = 0; i < numDigits; i++) {
            cases *= digitToNumberOfCases(digits.charAt(i));
        }
        
        if (cases == 0 || cases == 1) {
            return new ArrayList<>();
        }
        
        
        char[][] res = new char[cases][numDigits];
        
        for (int digitIndex = 0; digitIndex < numDigits; digitIndex++) {
            // System.out.println("digitIndex "+digitIndex);
            List<Character> letters = map.get(digits.charAt(digitIndex));
            int totalCycles = res.length / cases;
            for (int cycle = 0; cycle < totalCycles; cycle++) {
                            // System.out.println("cycle "+cycle);

                int reps = cases / letters.size();
                for(int optionLetterIndex = 0; optionLetterIndex < letters.size(); optionLetterIndex++) {
                                // System.out.println("optionLetterIndex "+optionLetterIndex);

                    for (int i = 0; i < reps; i ++) {
                                    // System.out.println("i "+i);

                        res[cycle*cases+reps*optionLetterIndex+i][digitIndex] = letters.get(optionLetterIndex);
                    }
                }
            }
            cases /= letters.size();
        }
        
        
        List<String> result = new ArrayList<>();
        for (int i = 0; i < res.length; i++) {
            result.add(new String(res[i]));
        } 
        
        
        return result;
    }
    
    public int digitToNumberOfCases(char digit) {
        switch(digit) {
            case '2':
            case '3':
            case '4':
            case '5':
            case '6':
            case '8':
                return 3;
            case '7':
            case '9':
                return 4;
            default:
                return 0;
        }
    }
}
```
