```java
public class Solution {
    public int solve(String A) {
        int start = 0;
        int end = A.length() - 1;
        while (start <= end) {
            //finds the non palindrome part in middle
            if (A.charAt(start) == A.charAt(end)) {
                start++;
                end--;
            }
            else {
                //when a non palindrome part if found we check if only 1 extra letter is there
                if (isPalin(A, start + 1, end) || isPalin(A, start, end - 1)) {
                    return 1;
                }
                else {
                    return 0;
                }
            }
        }
        return A.length() % 2 != 0 ? 1 : 0;
    }

    private boolean isPalin(String a, int start, int end) {
        while (start <= end) {
            if (a.charAt(start++) != a.charAt(end--)) {
                return false;
            }
        }
        return true;
    }
}
```
