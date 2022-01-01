```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int isMatch(final String A, final String B) {
        int m = B.length(),n = A.length();
        boolean[][] dp = new boolean[m + 1][n + 1];
        for (int i = m; i >= 0; i--) {
            for (int j = n; j >= 0; j--) {
                if (i == m && j == n) {
                    dp[i][j] = true;
                } else if (i == m) {
                    dp[i][j] = false;
                } else if (j == n) {
                    char bh = B.charAt(i);
                    if (bh == '*') {
                        dp[i][j] = dp[i + 1][j];
                    }
                } else {
                    char ah = A.charAt(j);
                    char bh = B.charAt(i);
                    if (bh == '*') {
                        dp[i][j] = dp[i + 1][j] || dp[i][j + 1];
                    } else if (bh == '?') {
                        dp[i][j] = dp[i + 1][j + 1];
                    } else if (bh == ah) {
                        dp[i][j] = dp[i + 1][j + 1];
                    }
                }
            }
        }
        return dp[0][0] ? 1 : 0;
    }
}

```
