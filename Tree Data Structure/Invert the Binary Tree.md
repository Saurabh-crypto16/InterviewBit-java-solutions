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
    public TreeNode invertTree(TreeNode A) {
        if(A==null){
            return A;
        }

        TreeNode left=invertTree(A.left);
        TreeNode right=invertTree(A.right);

        //swaping
        A.left=right;
        A.right=left;

        return A;
    }
}
```
