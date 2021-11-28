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
    public TreeNode solve(TreeNode root1, TreeNode root2) {
        if(root1==null)     return root2;
        if(root2==null)     return root1;
        
        root1.val+=root2.val;
        root1.left=solve(root1.left,root2.left);
        root1.right=solve(root1.right,root2.right);
        
        return root1;
    }
}

```
