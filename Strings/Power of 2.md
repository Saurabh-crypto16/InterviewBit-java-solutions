```java
/*
binary of 2^k is 1000...(k times 0)
if binary of value of n is 100000 then n-1 is 011111 
n & (n-1) is 0 if all 0


BigInteger.ONE = BigInteger constant 1
BigInteger.ZERO = BigInteger constant 0
*/
import java.math.BigInteger;
public class Solution {
    public int power(String A) {
        BigInteger a = new BigInteger(A);
        
        //if value of a is 0 or 1
        if(a.compareTo(BigInteger.ONE)==0 || a.compareTo(BigInteger.ZERO)==0)
            return 0;
        
        //testBit(int n)-returns true if and only if the designated bit is set.
        for(int i=0;i<a.bitLength()-1;i++){
            if(a.testBit(i))    return 0;
        }
        
        //only last bit should be set in case of power of 2
        return a.testBit(a.bitLength()-1) ? 1 : 0;
    }
}

```
