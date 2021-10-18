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
    public ListNode partition(ListNode A, int B) {
        ListNode less=new ListNode(0);
        ListNode more=new ListNode(0);
        ListNode less_head=less, more_head=more;

        while(A!=null){
            if(A.val<B){
                less_head.next=A;
                less_head=less_head.next;
            }else{
                more_head.next=A;
                more_head=more_head.next;
            }
            A=A.next;
        }

        more_head.next=null;
        less_head.next=more.next;
        return less.next;
    }
}
```
