```java

/*

Navie solution- Sort both the arrays using merge sort then find the median

Better solution: Divide a into l1(left half) and r1(right half) and b into l2(left half) and r2(right half). 
Partitio is correct only if last element of l1 <= first element of r1  &&  last element of l2 is <= first element of r1.
If above condition is satisfied then we check if merged array is even or odd size and according to that we get the median 
    Odd: Math.max(last element of l1, last element of l2)
    Even: ( Math.max(last element of l1, last element of l2) + Math.min(first element of r1, first element of r2) ) / 2.0

*/


public class Solution {
	// DO NOT MODIFY BOTH THE LISTS
	public double findMedianSortedArrays(final List<Integer> A, final List<Integer> B) {
		int n=A.size(), m=B.size();
		if(n>m) return findMedianSortedArrays(B,A);
		int start = 0;
        int end = n;
		int realmidinmergedarray = (n + m + 1) / 2;	//size of left part
		while(start<=end){
			int mid = (start + end) / 2;
            int leftAsize = mid;
            int leftBsize = realmidinmergedarray - mid;
			int leftA = (leftAsize > 0) ? A.get(leftAsize - 1) : Integer.MIN_VALUE; 
            int leftB = (leftBsize > 0) ? B.get(leftBsize - 1) : Integer.MIN_VALUE;
            int rightA = (leftAsize < n) ? A.get(leftAsize) : Integer.MAX_VALUE;
            int rightB = (leftBsize < m) ? B.get(leftBsize) : Integer.MAX_VALUE;
			if (leftA <= rightB && leftB <= rightA) {
                if ((m + n) % 2 == 0)
                    return (Math.max(leftA, leftB) + Math.min(rightA, rightB)) / 2.0;
                else 	return Math.max(leftA, leftB);
            }
			else if (leftA > rightB) 	end = mid - 1;
            else	start = mid + 1;
		}
		return 0.0;
	}
}
```
