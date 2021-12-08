```java
public class Solution {
    public int solve(String A) {
        int n=A.length(),dp[][]=new int[n][n];
        
        for(int g=0;g<n;g++){
            for(int i=0,j=g;j<n;i++,j++){
                if(g==0){
                    //1 length substr
                    dp[i][j]=1;
                }else if(g==1){
                    //2 length str
                    dp[i][j]=A.charAt(i)==A.charAt(j) ? 2 : 1;
                }else{
                    if(A.charAt(i)==A.charAt(j)){
                        dp[i][j]=2+dp[i+1][j-1];
                    }else{
                        //Consider str as c1-m-c2
                        //dp[i][j-1] = lps(c1,m)
                        //dp[i+1][j] = lps(m,c2)
                        dp[i][j]=Math.max(dp[i][j-1],dp[i+1][j]);
                    }
                }
            }
        }

        return dp[0][dp[0].length-1];
    }
}

```
