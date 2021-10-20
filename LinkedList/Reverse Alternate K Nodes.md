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
    public ListNode solve(ListNode A, int B) {
        if(A==null) return null;
    
        ListNode curr=A,prev=null, next=A;
        int i=1;
        // reverse k nodes
        while(i<=B && curr!=null)
        {
            next=curr.next;
            curr.next=prev;
            prev=curr;
            curr=next;
            i++;
        }

        A.next=next;
        i=1;
        //move k nodes
        while(i<B&&curr!=null)
        {
            curr=curr.next;
            i++;
        }

        if(curr!=null)
        curr.next=solve(curr.next,B);
            
        return prev;
    }
}
```
