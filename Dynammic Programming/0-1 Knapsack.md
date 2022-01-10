```java
public class Solution {
    public int solve(ArrayList<Integer> vals, ArrayList<Integer> wt, int C) {
        int n=vals.size();
        int dp[][]=new int[n+1][C+1];

        for(int i=1;i<dp.length;i++){
            for(int j=1;j<dp[0].length;j++){
                if(j>=wt.get(i-1)){
                    int remainingCap=j-wt.get(i-1);
                    
                    if(dp[i-1][remainingCap]+vals.get(i-1)>dp[i-1][j]){
                        dp[i][j]=dp[i-1][remainingCap]+vals.get(i-1);
                    }else{
                        dp[i][j]=dp[i-1][j];
                    }
                }else{
                    dp[i][j]=dp[i-1][j];
                }
            }
        }

        return dp[n][C];
    }
}

```
