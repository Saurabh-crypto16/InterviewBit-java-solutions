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
    public ArrayList<Integer> inorderTraversal(TreeNode A) {
        ArrayList<Integer> al=new ArrayList<>();
        inorder(A,al);
        return al;
    }
    public void inorder(TreeNode A,ArrayList<Integer> al){
        if(A==null){
            return;
        }
        
        inorder(A.left,al);
        al.add(A.val);
        inorder(A.right,al);
    }
}
```
