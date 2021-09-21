```java
/* formula = number of vowels * number of consonents*/

public class Solution {
    public int solve(String A) {
        char ch[]=A.toCharArray();
        int ans=0;
        for(int i=0;i<ch.length;i++){
            if(ch[i]=='a' || ch[i]=='e' || ch[i]=='i' || ch[i]=='o' || ch[i]=='u'){
                ans++;
            }
        }
        return (ans*(ch.length-ans))%1000000007;
    }
}

//OR

public class Solution {
    public int solve(String A) {
        //Map<Integer,Integer> vowelMap = new HashMap<>();
        //Map<Integer,Integer> consonantMap = new HashMap<>();
        int vowelsCount=0, consonantsCount=0;
        int ans = 0;
        for(int i=0; i<A.length(); i++){
            if(A.charAt(i)=='a' || A.charAt(i)=='e' || A.charAt(i)=='i' || 
            A.charAt(i)=='o' || A.charAt(i)=='u'){
                vowelsCount++;
                ans = (ans + consonantsCount) % 1000000007;
            }
            else{
                consonantsCount++;
                ans = (ans + vowelsCount) % 1000000007;
            }
        }
        return ans;
    }
}

```
