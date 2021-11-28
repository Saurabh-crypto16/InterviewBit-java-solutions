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
public class Solution {
    public ArrayList<Integer> postorderTraversal(TreeNode A) {
        ArrayList<Integer> al=new ArrayList<>();
        postorder(A,al);
        return al;
    }
    public void postorder(TreeNode A,ArrayList<Integer> al){
        if(A==null){
            return;
        }
        
        postorder(A.left,al);
        postorder(A.right,al);
        al.add(A.val);
    }
}
```
