```java
/*
Max sum of non adjacent elements of array concept
*/
public class Solution {
    public int solve(ArrayList<ArrayList<Integer>> A) {
        int n=A.size();
        int dp[][]=new int[n][3];

        dp[0][0]=A.get(0).get(0);
        dp[0][1]=A.get(0).get(1);
        dp[0][2]=A.get(0).get(2);

        for(int i=1;i<n;i++){
            dp[i][0]=A.get(i).get(0)+Math.min(dp[i-1][1],dp[i-1][2]);
            dp[i][1]=A.get(i).get(1)+Math.min(dp[i-1][0],dp[i-1][2]);
            dp[i][2]=A.get(i).get(2)+Math.min(dp[i-1][0],dp[i-1][1]);
        }

        return Math.min(dp[n-1][0],Math.min(dp[n-1][1],dp[n-1][2]));
    }
}

```
