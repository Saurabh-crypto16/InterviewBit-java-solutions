```java
public class Solution {
    public int seats(String A) {
		int n = A.length();
		if(n < 2){
			return 0;
		}

		int[] arr = new int[n];
		int lastIndex = 0;
		for(int i = 0; i < n; i++){
			if(A.charAt(i) == 'x'){
				arr[lastIndex++] = i;
			}
		}

		lastIndex--;
		int medIndex = (lastIndex+1)/2;
		int ans = 0, MOD = 10000003;
		for(int i = 0; i < lastIndex+1; i++){
			ans = (ans % MOD + (Math.abs(arr[medIndex] - arr[i]) % MOD) 
					- Math.abs(medIndex - i) % MOD) % MOD;
		}

		return ans % MOD;
    }
}

```
