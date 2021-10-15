```java
public class Solution {
  public int solve(String A) {

        if (A.length() == 1)
            return 0;

        int start = 0; int mid;
        int end  = A.length()-1;
        mid = start + (end-start)/2;
        while (!isPalindromic(A, start, end)){
            start = mid;
            mid = start + (end-start)/2;

            if ((end - start) == 1 && A.charAt(start) != A.charAt(end)){
                start = end;
                break;
            }
        }

        return start;
    }

    public boolean isPalindromic(String A, int start, int end){

        while (start <  end){
            if (A.charAt(start) != A.charAt(end))
                return false;
            start++;
            end--;
        }
        return true;
    }
}
```
