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
    public ListNode solve(ListNode A) {
        ListNode p1=A;
        ListNode p2=A;

        while(p1!=null){
            if(p1.val==0){
                int temp=p1.val;
                p1.val=p2.val;
                p2.val=temp;
                p2=p2.next;
            }
            p1=p1.next;
        }
        return A;
    }
}

```
