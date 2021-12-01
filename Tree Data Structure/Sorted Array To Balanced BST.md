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
    // DO NOT MODIFY THE ARGUMENTS WITH "final" PREFIX. IT IS READ ONLY
    public TreeNode sortedArrayToBST(final int[] A) {
        if(A.length==0) return null;
        return construct(A,0,A.length-1);
    }
    public TreeNode construct(int []A,int left,int right){
        if(left>right){
            return null;
        }

        int mid=left+(right-left)/2;
        TreeNode root=new TreeNode(A[mid]);
        root.left=construct(A,left,mid-1);
        root.right=construct(A,mid+1,right);

        return root;
    }
}
```
