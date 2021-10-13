```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int isNumber(final String A) {
        int res = 0;
        if(A.charAt(A.length()-1)=='.' || A.contains("f"))  return 0;
        try{
            if(A.length() > 2) {
                if(A.charAt(A.length() - 2) == 'e')    return 0;
            }
            Double.parseDouble(A);
            res = 1;
        }
        catch(Exception e){   
        }
        finally{
            return res;
        }
    }
}
```
