```java
/*
We have to maintain a decreasing order in the deque
We store the indices rather than the values in the deque

*/

public class Solution {
    // DO NOT MODIFY THE LIST. IT IS READ ONLY
    public ArrayList<Integer> slidingMaximum(final List<Integer> A, int B) {
        if (A.size() == 0 || B == 0) {
            return new ArrayList<>();
        }

        ArrayList<Integer> list = new ArrayList<>();
        Deque<Integer> deque = new ArrayDeque<>();

        for (int i = 0; i < A.size(); i++) {
            //checking the size of subarray concerned
            //if size of subarray > B then pop from front
            while (!deque.isEmpty() && deque.peekFirst() <= i - B) {
                deque.pollFirst();
            }

            //checking if new element is smaller than last element then push it at last
            //else pop last element till larger element is found
            while (!deque.isEmpty() && A.get(deque.peekLast()) < A.get(i)) {
                deque.pollLast();
            }

            //max element of sublist is always the first element in dq
            deque.offerLast(i);
            if (i >= B - 1) {
                list.add(A.get(deque.peekFirst()));
            }
        }
        return list;
    }
}
```
