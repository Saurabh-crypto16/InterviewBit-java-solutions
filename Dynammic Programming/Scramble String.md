```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    /*
    Break both the strings at ith index
    if left substr of A is scrambles str of left part of B AND
    right substr of A is scrambles str of right part of B
    OR if left substr of A is scrambles str of right part of B AND
    right substr of A is scrambles str of left part of B AND
    then we can say that B is scrambles str of A 
    */
    public int isScramble(final String A, final String B) {
        if(A.length()!=B.length())
            return 0;
        if(A.equals(B))
            return 1;

        int n=A.length();
        boolean dp[][][]=new boolean[n][n][n+1];
        //len is the length of substr we have to consider
        for(int len=1;len<=n;len++){
            for(int i=0;i<=n-len;i++){
                for(int j=0;j<=n-len;j++){
                    if(len==1){
                        dp[i][j][len]=A.charAt(i)==B.charAt(j);
                    }else{
                        for(int k=1;k<len && !dp[i][j][len];k++){
                            dp[i][j][len]=(dp[i][j][k] && dp[i+k][j+k][len-k]) ||
                                    (dp[i][j+len-k][k] && dp[i+k][j][len-k]);
                        }
                    }
                }
            }
        }
        return (dp[0][0][n]) ? 1 : 0;
    }
}
```
