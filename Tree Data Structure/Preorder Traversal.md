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
    public ArrayList<Integer> preorderTraversal(TreeNode A) {
        ArrayList<Integer> al=new ArrayList<>();
        preorder(A,al);
        return al;
    }
    public void preorder(TreeNode A,ArrayList<Integer> al){
        if(A==null){
            return;
        }
        
        al.add(A.val);
        preorder(A.left,al);
        preorder(A.right,al);
    }
}

```
