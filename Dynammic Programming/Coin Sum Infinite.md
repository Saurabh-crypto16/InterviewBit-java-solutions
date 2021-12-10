```java
public class Solution {
    public int coinchange2(ArrayList<Integer> coins, int amount) {
        int dp[]=new int[amount+1];
        dp[0]=1;
        
        for(int coin: coins){
            //calculating number of ways to form amount using current coin
            for(int i=coin;i<=amount;i++){
                dp[i]=((dp[i]% 1000007)+(dp[i-coin]% 1000007))% 1000007;
            }
        }

        return dp[amount];
    }
}

 ```
