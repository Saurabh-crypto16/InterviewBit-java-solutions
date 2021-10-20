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
    public int solve(ListNode A, int B) {
        int ans=0,n=0;
        ListNode curr=A;
        while(curr!=null){
            n++;
            curr=curr.next;
        }
        
        if(n/2+1-B>=1){
            for(int i=1;i<=(n/2+1-B);i++){
            ans=A.val;
            A=A.next;
            }
            return ans;
        }else{
            return -1;
        }
    }
}

```
