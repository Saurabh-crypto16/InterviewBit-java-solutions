```java
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */

 /*
 Start from root and add the left child of every node to queue and right child 
 value to arraylist till right is null
 Then poll from queue and repeat step 1 till queue is empty
 */
public class Solution {
    public ArrayList<Integer> solve(TreeNode A) {
        Queue<TreeNode> q=new LinkedList<>();
        ArrayList<Integer> al=new ArrayList<Integer>();
        q.offer(A);

        while(!q.isEmpty()){
            TreeNode curr=q.poll();
            al.add(curr.val);
            if(curr.left!=null) q.offer(curr.left);

            while(curr.right!=null){
                curr=curr.right;
                if(curr.left!=null) q.offer(curr.left);
                al.add(curr.val);
            }
        }

        return al;
    }
}
```
