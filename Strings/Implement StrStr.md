```java
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int strStr(final String A, final String B) {
        int i=0,j=0;
        while(i<A.length() && j<B.length()){
            if(A.charAt(i)==B.charAt(j)){
                i++;
                j++;
            }else{
                //when char mismatchs start from the next character 
                //after match starting character in A and start B from 0
                i=i-j+1;     
                j=0;
            }
        }
        
        if(j==B.length())   return i-j;
        return -1;
    }
}


//2nd solution USING KMP ALGO
public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public int strStr(final String txt, final String pat) {
        if (pat.length() == 0) {
            return 0;  // return 0 because no pattern to search
        }
        
        int[] lps = computeLPS(pat); // compute LPS array
        
        int i = 0;
        int j = 0;
        while (i < txt.length()) { // loop till text length
            if (txt.charAt(i) == pat.charAt(j)) { // if pattern char matches with text char
                j++;
                i++;
                if (j == pat.length()) { // if pattern length equals to j means we have found one pattern
                    return (i-j);  // index of pattern will be i-j beacause i is at last index of matched pattern 
                }
            } else {
                if (j != 0) {
                    j = lps[j-1]; // try for longest pattern
                } else {
                    i++; // ignore and loop to next char
                } 
            }
        }
        return -1; // no match found
    }
    private int[] computeLPS(String a) {
        int i = 1;
        int j = 0;
        
        int arr[] = new int[a.length()];
        
        while (i < a.length()) {
            if (a.charAt(i) == a.charAt(j)) {
                arr[i++] = ++j;
            } else {
                if (j != 0) {
                    j = arr[j-1];
                } else { 
                    i++;
                }
            }
        }
        return arr;
    }
}
```
