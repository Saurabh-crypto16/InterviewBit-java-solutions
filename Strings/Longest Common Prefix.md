```java
/* 
Set the first string of list as prefix and then iterate over all the remaining strings and 
each time update the prefix with current string
*/

public class Solution {
    public String longestCommonPrefix(ArrayList<String> A) {
        if(A.size()==0) return "";
        String prefix=A.get(0);
        if(A.size()==1) return prefix;

        for(int i=1;i<A.size();i++){
            while(A.get(i).indexOf(prefix)!=0)  prefix=prefix.substring(0,prefix.length()-1);
        }

        return prefix;
    }
}

//OR
 
public class Solution {
    public String longestCommonPrefix(ArrayList<String> A) {
        int count = -1;
        for(int i = 0; i < A.get(0).length(); i++) {
            char c = A.get(0).charAt(i);
            int j;
            for(j = 1; j < A.size(); j++) {
                if(i >= A.get(j).length() || A.get(j).charAt(i) != c) break; 
            }
            if(j == A.size()) count++;
            else break;
        }
        
        return A.get(0).substring(0,count+1);
    }
}
```
