```java
# Java Solution
public class Solution {
    public int solve(ArrayList<Integer> A) {
        // Initialize suffix-array
        int n=A.size();
        int maxSuffArr[] = new int[n + 1];
    
        // Set the last element
        maxSuffArr[n] = 0;
    
        // Calculate suffix-array containing maximum
        // value for index i, i+1, i+2, ... n-1 in
        // arr[i]
        for(int i = n - 1; i >= 0; --i)
            maxSuffArr[i] = Math.max(maxSuffArr[i + 1],A.get(i));
    
        int ans = 0;
    
        // Initialize set container
        TreeSet<Integer> lowValue = new TreeSet<Integer>();
    
        // Insert minimum value for first comparison
        // in the set
        lowValue.add(Integer.MIN_VALUE);
    
        for(int i = 0; i < n - 1; ++i)
        {
            if (maxSuffArr[i + 1] >A.get(i))
            {
                //lower(E e) method returns the greatest element in this set 
                //strictly less than the given element, or null if there is no 
                //such element.
                ans = Math.max(ans, lowValue.lower(A.get(i)) + A.get(i) + maxSuffArr[i + 1]);
    
                // Insert arr[i] in set<> for further
                // processing
                lowValue.add(A.get(i));
            }
        }
    return ans;
    }
}
```
