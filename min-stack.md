# [Min Stack](https://leetcode.com/problems/min-stack/description/) [Easy]

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

push(x) -- Push element x onto stack.  
pop() -- Removes the element on top of the stack.  
top() -- Get the top element.  
getMin() -- Retrieve the minimum element in the stack.  
Example:
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

## [Java solution](https://leetcode.com/submissions/detail/144897276/)
```
class MinStack {

    Stack<Long> stack;
    Long min;
    /** initialize your data structure here. */
    public MinStack() {
        min = null;
        stack = new Stack<>();
    }
    
    public void push(int x) {
        if (stack.isEmpty()) {
            min = (long)x;
        }
        stack.push(Long.valueOf((long)x - (long)min));
        if ((long)x < min) {
            min = (long)x;
        }
    }
    
    public void pop() {
        if (!stack.isEmpty()) {
            Long val = stack.pop();
            if (val < 0) {
                min = (min - val);
            }
        }
    }
    
    public int top() {
        Long val = stack.peek();
        return val > 0 ? val.intValue() + min.intValue() : min.intValue();
    }
    
    public int getMin() {
        return min.intValue();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```
