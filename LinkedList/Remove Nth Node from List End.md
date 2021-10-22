```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }

 Brute force: Find size of list then iterate to (size-B)th node then delete its next node

 Better: move fast pointer to Bth node then move both fast and slow pointers till fast.next==null then delete the node next to slow 
 */
public class Solution {
    public ListNode removeNthFromEnd(ListNode A, int B) {
        if (A == null) {
            return A;
        }
        ListNode curr = A;
        int count = 0;
        
        //finding size of list
        while (curr != null) {
            curr = curr.next;
            count++;
        }
        if (B >= count) {
            return A.next;
        }
        
        ListNode slow=A, fast=A;

        for(int i=1;i<=B;i++)   fast=fast.next;
        while(fast.next!=null){
            fast=fast.next;
            slow=slow.next;
        }
        slow.next=slow.next.next;

        return A;
    }
}

```
