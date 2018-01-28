# [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/) [Easy]

Given a string containing just the characters `(`, `)`, `{`, `}`, `[` and `]`, determine if the input string is valid.

The brackets must close in the correct order, `()` and `()[]{}` are all valid but `(]` and `([)]` are not.

## [Java solution](https://leetcode.com/submissions/detail/134598500/)
```
import java.util.EmptyStackException;
import java.util.Stack;

class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (int i=0; i<s.length(); i++) {
            char c = s.charAt(i);
            if (c=='{' || c=='[' || c=='(') {
                stack.push(c);
            } else {
                Character fromStack;
                try {
                    fromStack = stack.pop();
                } catch (EmptyStackException e) {
                    return false;
                }
                if ((c == '}' && fromStack!='{') || (c == ')' && fromStack!='(') || (c == ']' && fromStack!='[')) {
                    return false;
                }
            }

        }
        return stack.empty();
    }
}
```
