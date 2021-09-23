```java
/*  Algorithem: eg A=[1,3,5,4,2]
    Step 1 - Linearly traverse from back and find first i for which A[i]<A[i+1]. (3 at index 1)
    Step 2 - Linearly traverse from back to find j for which A[j]<A[i]. (2 at index 4)
    Step 3 - Swap index i and j
    Step 4 - Reverse the array from i+1 to end
*/

public class Solution {
    public ArrayList<Integer> nextPermutation(ArrayList<Integer> A) {
        int i=A.size()-2;
        while(i>=0 && A.get(i)>=A.get(i+1)) i--;

        if(i>=0){
            int j=A.size()-1;
            while(A.get(j)<=A.get(i))   j--;
            Collections.swap(A,i,j);
        }
        reverse(A,i+1,A.size()-1);

        return A;
    }
    void reverse(ArrayList<Integer> A, int start, int end){
        while(start<end){
            Collections.swap(A,start,end);
            start++;
            end--;
        }
    }
}
```
