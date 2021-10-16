```java
public class Solution {
    public int solve(String A) {
        if(A.length()<=1)   return A.length();
        Stack<Character> st=new Stack<>();
        int ans=0;
        for(char c: A.toCharArray()){
            if(c=='('){
                st.push(c);
            }else if(c==')'){
                if(st.isEmpty())    ans++;
                else {
                    st.pop();
                }
            }
        }
        ans+=st.size();
        return ans;
    }
}
```
