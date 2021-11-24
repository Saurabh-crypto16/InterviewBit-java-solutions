```java
import java.math.BigInteger;

public class Solution {
    private long nCp(int n, int p) {
        long ans = (long)1;
        for(long i=n; i>(long)(p); i--) {
            ans *= i;
            ans %= 1000000007;
        }
        long denom = 1;
        for(int i=(n-p); i>=1; i--) {
            denom *= (long)(i);
            denom %= 1000000007;
        }
        ans *= BigInteger.valueOf(denom).modInverse(BigInteger.valueOf(1000000007)).longValue();
        ans %= 1000000007;
        // System.out.println(n+"C"+p+" = "+ans);
        return (ans);
    }
    public int solve(int A) {
        if(A<=2) {
            return 1;
        }
        
        int height = (int)(Math.log(A)/Math.log(2)) + 1;
        int maxAtHeight = (int)Math.pow(2, height) - 1;
        int A1 = Math.min(A-1 - ((int)Math.pow(2, (height-2)) - 1), ((int)Math.pow(2, (height -1)) -1));
        int A2 = A - A1 -1;
        // System.out.println("A="+A+", A1="+A1+", A2="+A2+", height="+height);
        return (int)((((nCp((A-1), A1)  * (long)solve(A1))% 1000000007) * (long)solve(A2)) % 1000000007);
    }
}
```
