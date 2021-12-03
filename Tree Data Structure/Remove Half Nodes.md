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
    public TreeNode solve(TreeNode A) {
        TreeNode curr=A;
        if(curr==null)  return A;

        if(curr.left!=null){
            curr.left=solve(curr.left);
        }
        if(curr.right!=null){
            curr.right=solve(curr.right);
        }

        if((curr.left==null && curr.right!=null) || (curr.left!=null && curr.right==null)){
            if(curr.left!=null){
                curr=solve(curr.left);
            }else if(curr.right!=null){
                curr=solve(curr.right);
            }
        }

        return curr;
    }
}

```
