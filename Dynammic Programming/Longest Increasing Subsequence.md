```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length]; //Stores tails of the subsequences of index +1 lengths
        Arrays.fill(dp, Integer.MAX_VALUE); 

        int lastFilledTailLength = 0;
        for (int i = 0; i < nums.length; i++) {
            int key = nums[i];
            int index = binarySearch(key, dp, i);
            lastFilledTailLength = Math.max(lastFilledTailLength, index+1);
            dp[index] = key; //replace the next largest with the current value. 
                             //This index is 0 for start and i+1 if its largest
        }
        return lastFilledTailLength;
    }
    //Binary searches 0 to the currentIndex and returns next greater index for key
    private int binarySearch(int key, int[] dp, int end) {
        int lo = 0;
        int hi = end;
        while (lo <= hi) {
            int mid = lo + (hi-lo)/2;
            if (dp[mid] == key) {
                return mid;
            } else if (key < dp[mid]) {
                hi = mid -1;
            } else {
                lo = mid + 1;
            }
        }
        return lo; 
    }
}
```
