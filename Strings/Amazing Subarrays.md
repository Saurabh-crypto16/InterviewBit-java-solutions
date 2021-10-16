```java
public class Solution {
    public int solve(String A) {
        int ans=0;
        for(int i=0;i<A.length();i++){
            char ch=A.charAt(i);
            if(ch=='A' || ch=='E' || ch=='I' || ch=='O' || ch=='U' || 
                ch=='a' || ch=='e' || ch=='i' || ch=='o' || ch=='u' ){
                ans+=(A.length()-i);
            }
        }
        return ans%10003;
    }
}
```
