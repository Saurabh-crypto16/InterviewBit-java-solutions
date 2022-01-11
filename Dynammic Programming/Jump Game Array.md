```java
public class Solution {
    public int canJump(ArrayList<Integer> A) {
        int lastGoodPos=A.size()-1;

        for(int i=A.size()-1;i>=0;i--){
            if(i+A.get(i)>=lastGoodPos){
                lastGoodPos=i;
            }
        }

        return lastGoodPos==0 ? 1 : 0;
    }
}

```
