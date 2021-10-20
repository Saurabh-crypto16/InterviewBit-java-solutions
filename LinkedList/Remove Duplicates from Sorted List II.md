```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }
 */
public class Solution {
    public ListNode deleteDuplicates(ListNode A) {
        ListNode dummy=new ListNode(0);
        dummy.next=A;
        ListNode prev=dummy;

        while(A!=null){
            if(A.next!=null && A.val==A.next.val){
                while(A.next!=null && A.val==A.next.val){
                    A=A.next;
                }
                prev.next=A.next;
            }else{
                prev=prev.next;
            }
            A=A.next;
        }
        return dummy.next;
    }
}
```
