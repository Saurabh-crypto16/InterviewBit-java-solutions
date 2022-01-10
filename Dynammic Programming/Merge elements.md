```java
public class Solution {
    public int solve(ArrayList<Integer> A) {
        int n=A.size();
        int prefix[]=new int[n+1];
        
        for(int i=1;i<=n;i++){
            prefix[i]=prefix[i-1]+A.get(i-1);
        }

        int dp[][]=new int[n][n];
        //using gap tech to fill the values diagonally in dp array
        for(int gap=1;gap<n;gap++){
            int i=0;
            int j=i+gap;
            for(;j<n;i++,j++){
                dp[i][j]=Integer.MAX_VALUE;
                for(int k=i;k<j;k++){
                    dp[i][j]=Math.min(dp[i][j],prefix[j+1]-prefix[i]+dp[i][k]+dp[k+1][j]);
                    /*
                    A = [1, 2, 3, 4]

                    splitting at idx (0,0) + (1,3) -> (i,k) + (k+1,j)
                    (prefix[1]-prefix[0])+(prefix[4]-prefix[1])+(dp[0][0]+dp[1][3])

                    splitting at idx (0,1) + (2,3) -> (i,k) + (k+1,j)
                    (prefix[2]-prefix[0])+(prefix[4]-prefix[2])+(dp[0][1]+dp[2][3])

                    splitting at idx (0,2) + (3,3) -> (i,k) + (k+1,j)
                    (prefix[3]-prefix[0])+(prefix[4]-prefix[3])+(dp[0][2]+dp[3][3])
                    */
                }
            }
        }

        return dp[0][n-1];
    }
}

```
