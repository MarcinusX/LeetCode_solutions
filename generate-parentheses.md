# [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/description/) [Medium]

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:
```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

## [Java solution](https://leetcode.com/submissions/detail/141448540/)
```
class Solution {
    public List<String> generateParenthesis(int n) {
        if (n == 0) {
            return Arrays.asList("");
        }
        Node node = new Node('(');
        updateNode(node, n-1, 1);
        
        List<String> result = new LinkedList<>();
        nodeToList(result, "", node);
        return result;
    }
    
    void nodeToList(List<String> resultList, String base, Node node) {
        base = base + node.c;
        if (node.left == null && node.right == null) {
            resultList.add(base);
        }
        if (node.left != null) {
            nodeToList(resultList, base, node.left);
        }
        if (node.right != null) {
            nodeToList(resultList, base, node.right);
        }
    }
    
    void updateNode(Node parentNode, int ableToOpen, int ableToClose) {
        if (ableToOpen != 0) {
            parentNode.left = new Node('(');
            updateNode(parentNode.left, ableToOpen-1, ableToClose+1);
        }
        if (ableToClose != 0) {
            parentNode.right = new Node(')');
            updateNode(parentNode.right, ableToOpen, ableToClose-1);
        }
    }
    
    static class Node {
        char c;
        Node left;
        Node right;
        Node(char c) {
            this.c = c;
        }
    }
}
```
