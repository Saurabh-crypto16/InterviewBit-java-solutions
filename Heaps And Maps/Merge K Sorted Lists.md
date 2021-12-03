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
	public ListNode mergeKLists(ArrayList<ListNode> a) {
		PriorityQueue<Integer> pq=new PriorityQueue<>();

		for(ListNode head: a){
			while(head!=null){
				pq.offer(head.val);
				head=head.next;
			}
		}

		ListNode head=new ListNode(-1),dummy=head;
		while(!pq.isEmpty()){
			head.next=new ListNode(pq.remove());
			head=head.next;
		}

		return dummy.next;
	}
}

```
