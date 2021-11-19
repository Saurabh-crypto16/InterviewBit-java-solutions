```java
/*
Prefix[i] stores the number of prefixes which has ‘i’ odd numbers in it. We increase the count of odd numbers if the array element is an odd one. 
When the count of odd numbers exceeds or is equal to m, add the number of prefixes which has “(odd-m)” numbers to the answer. 
At every step odd>=m, we calculate the number of subarrays formed till a particular index with the help of prefix array. 
prefix[odd-m] provides us with the number of prefixes which has “odd-m” odd numbers, which is added to the count to get the number of subarrays till the index. 
*/

public class Solution {
    public int solve(ArrayList<Integer> A, int B) {
        int count = 0,n=A.size();
        int prefix[] = new int[n + 1];
        int odd = 0;
 
        // Traverse in the array
        for (int i = 0; i < n; i++){
            prefix[odd]++;

            // If array element is odd
            if ((A.get(i) & 1) == 1)
                odd++;
 
            // When number of odd
            // elements >= B
            if (odd >= B)
                count += prefix[odd - B];
        }
 
        return count;
    }
}
```
