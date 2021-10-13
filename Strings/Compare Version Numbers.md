```java
/*
Split the Strings at the . and then compare
*/
public class Solution {
    public int compareVersion(String A, String B) {
        String s1[]=A.split("\\.");
        String s2[]=B.split("\\.");

        for(int i=0;i<Math.max(s1.length,s2.length);i++){
            double v1=i<s1.length?Double.parseDouble(s1[i]):0;
            double v2=i<s2.length?Double.parseDouble(s2[i]):0;

            if(v1>v2)   return 1;
            if(v2>v1)   return -1;
        }
        return 0;
    }
}
```
