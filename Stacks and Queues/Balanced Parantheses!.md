```java
public class Solution {
    public int solve(String A) {
        char ch[]=A.toCharArray();
        Stack<Character> st=new Stack<>();
        for(char c: ch){
            if(c=='('){
                st.push(c);
            }else{
                if(st.isEmpty())    return 0;
                else st.pop();
            }
        }
        return st.isEmpty() ? 1 : 0;
    }
}
```
