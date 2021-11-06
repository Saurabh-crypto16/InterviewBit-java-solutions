```java
public class Solution {
    String max;
    public String solve(String A, int B) {
        max=A;
        findMax(A,B);
        return max;
    }
    public void findMax(String str,int k){
        if(Integer.parseInt(str)>Integer.parseInt(max)){
            max=str;
        }
        
        if(k==0)    return;

        for(int i=0;i<str.length()-1;i++){
            for(int j=i+1;j<str.length();j++){
                if(str.charAt(j)>str.charAt(i)){
                    str=swap(str,i,j);
                    findMax(str,k-1);
                    str=swap(str,i,j);
                }
            }
        }
    }
    String swap(String str, int i, int j){
        char ith=str.charAt(i);
        char jth=str.charAt(j);

        String left=str.substring(0,i);
        String middle=str.substring(i+1,j);
        String right=str.substring(j+1);

        return left+jth+middle+ith+right;
    }
}

```
