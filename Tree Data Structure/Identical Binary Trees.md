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
    public int isSameTree(TreeNode A, TreeNode B) {
        if(A==null || B==null){
            return A==B ? 1 : 0;
        }

        return ((A.val==B.val) && isSameTree(A.left,B.left)==1 && isSameTree(A.right,B.right)==1) ? 1 : 0;
    }
}

```
