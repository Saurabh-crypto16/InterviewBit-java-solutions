```java
public class Solution {
    public int solve(ArrayList<Integer> A) {
        // Create an empty stack
        Stack<Integer> s = new Stack<Integer>();
        // Initialize current root as minimum possiblevalue
        int root = Integer.MIN_VALUE,n=A.size();
        // Traverse given array
        for (int i = 0; i < n; i++) {
            // If we find a node who is on right side
            // and smaller than root, return false
            if (A.get(i) < root) {
                return 0;
            }
            // If pre[i] is in right subtree of stack top,
            // Keep removing items smaller than pre[i]
            // and make the last removed item as new
            // root.
            while (!s.empty() && s.peek() < A.get(i)) {
                root = s.pop();
            }
            // At this point either stack is empty or
            // pre[i] is smaller than root, push pre[i]
            s.push(A.get(i));
        }
        return 1;
    }
}

```
