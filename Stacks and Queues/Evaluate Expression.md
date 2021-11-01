```java
public class Solution {
    public int evalRPN(ArrayList<String> A) {
        Stack<Integer> st=new Stack<>();
        for(String s: A){
            if(s.equals("+")){
                int op1=st.pop();
                int op2=st.pop();
                st.push(op2+op1);
            }else if(s.equals("-")){
                int op1=st.pop();
                int op2=st.pop();
                st.push(op2-op1);
            }else if(s.equals("*")){
                int op1=st.pop();
                int op2=st.pop();
                st.push(op2*op1);
            }else if(s.equals("/")){
                int op1=st.pop();
                int op2=st.pop();
                st.push(op2/op1);
            }else{
                st.push(Integer.valueOf(s));
            }
        }
        return st.pop();
    }
}

```
