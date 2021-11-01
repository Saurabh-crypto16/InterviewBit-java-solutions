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


/*
One stack solution - keep a min variable which will contain the next min.
Whenever we get a value smaller than curr_min store (value+(value-curr_min)) in stack in place of curr value
While poping when we get a val less than curr min then curr_min = curr_min+(curr_min - st.peek()) and pop out the previous min 
*/
class Solution {
    Stack<Integer> st=new Stack<>();
    int min=Integer.MAX_VALUE;
    public void push(int x) {
        if(st.isEmpty()){
            st.push(x);
            min=x;
        }else if(x>=min){
            st.push(x);
        }else{
            st.push(x+x-min);
            min=x;
        }
    }

    public void pop() {
        if(!st.isEmpty()){
            if(st.peek()>=min)  st.pop();
            else{
                int original_value=min;
                min = 2 * min - st.pop();
                //return original_value;
            }
        }
    }

    public int top() {
        if(st.isEmpty())    return -1;
        else if(st.peek()>=min)  return st.peek();
        else{
            return min;
        }
    }

    public int getMin() {
        if(st.isEmpty())    return -1;
        return min;
    }
}

```
