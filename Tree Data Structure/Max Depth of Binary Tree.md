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
    public int maxDepth(TreeNode A) {
        if(A==null)     return 0;
        if(A.left==null && A.right==null)   return 1;
        
        return 1+Math.max(maxDepth(A.left),maxDepth(A.right));
    }
}
```
