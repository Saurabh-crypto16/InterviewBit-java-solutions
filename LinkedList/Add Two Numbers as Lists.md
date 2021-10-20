```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }

 Ask questions to interviewer to kill time about edge cases 
 like what if one list smaller thatn other and 
 what if both are of equal length
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode A, ListNode B) {
        ListNode temp=new ListNode(0);
        ListNode ans=temp;
        int carry=0;

        while(A!=null || B!=null){
            int sum=0;
            if(A!=null){ 
                sum+=A.val;
                A=A.next;
            }
            if(B!=null){
                sum+=B.val;
                B=B.next;
            }
            
            sum+=carry;
            ListNode curr=new ListNode(sum%10);
            carry=sum/10;
            temp.next=curr;
            temp=temp.next;
        }
        if(carry>0){
            ListNode curr=new ListNode(carry);
            temp.next=curr;
            temp=temp.next;
        }
        return ans.next;
    }
}
```
