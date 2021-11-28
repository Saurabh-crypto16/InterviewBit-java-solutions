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
    public int isSymmetric(TreeNode A) {
        return (A==null || isSymetric(A.left,A.right)) ? 1 : 0;
    }
    public boolean isSymetric(TreeNode left,TreeNode right){
        if(left==null || right==null){
            return left==right;
        }
        if(left.val!=right.val) return false;

        return (isSymetric(left.left,right.right) && isSymetric(left.right,right.left));
    }
}
```
