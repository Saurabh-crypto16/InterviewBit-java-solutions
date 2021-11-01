```java
/*
Two Stack solution where we keep 2 stacks. In one of the stack we only keep element if pushed value is less than peek of minStack
While poping elements if current poped element is equal to top of minStack then we pop the minStack top also 
*/
class Solution {
    Stack<Integer> minStack = new Stack<Integer>();
    Stack<Integer> stack = new Stack<Integer>();
    public Solution() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }
    
    public void push(int x) {
        stack.push(x);
        if(minStack.isEmpty() || x < minStack.peek()) 
            minStack.push(x);
    }

    public void pop() {
        if(!stack.isEmpty() && !minStack.isEmpty()) {
            if(minStack.peek().equals(stack.peek()))
                minStack.pop();
            stack.pop();
        }
    }

    public int top() {
        if(!stack.isEmpty())
            return stack.peek();
        return -1;
    }

    public int getMin() {
        if(!minStack.isEmpty())
            return minStack.peek();
        return -1;
    }
}

```
