```java
/*
Keep adding the numbers till u keep getting D as you get I then reverse add the numbers
*/

public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public ArrayList<Integer> findPerm(final String A, int B) {
        ArrayList<Integer> ans=new ArrayList<Integer>();
        int start=1, end=0, n=A.length();
        for(int i=0;i<n;i++){
            end++;
            if(A.charAt(i)=='I'){
                for(int j=end;j>=start;j--) ans.add(j);
                start=end+1;
            }
        }
        end++;
        for(int j=end;j>=start;j--)  ans.add(j);
        return ans;
    }
}

```
