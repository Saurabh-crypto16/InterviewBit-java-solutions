```java
public class Solution {
    public int braces(String A) {
        Stack<Character> st=new Stack<>();
        for(char c: A.toCharArray()){
            if(c==')'){
                int count=0;
                while(!st.isEmpty() && st.peek()!='(') {
                    st.pop();
                    count++;
                }
                //if there is only 1 operand inside bracket eg: (a)
                if(count<=1)    return 1;   
                st.pop();
            }else{
                st.push(c);
            }
        }
        return 0;
    }
}

```
