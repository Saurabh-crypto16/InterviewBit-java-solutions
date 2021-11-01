```java
public class Solution {
    public ArrayList<Integer> prevSmaller(ArrayList<Integer> A) {
        Stack<Integer> st=new Stack<>();
        ArrayList<Integer> ans=new ArrayList<>();
        for(int i: A){
            while(!st.isEmpty() && st.peek()>=i){
                st.pop();
            }
            if(!st.isEmpty()){
                ans.add(st.peek());
            }else{
                ans.add(-1);
            }
            st.push(i);
        }
        return ans;
    }
}

```
