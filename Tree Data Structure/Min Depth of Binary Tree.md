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
    public int minDepth(TreeNode root) {
        if(root==null)
           return 0;
        Queue<TreeNode> q=new LinkedList<TreeNode>();
        q.add(root);
        int count=1;
        while(q.size()>0)
        {
            int size=q.size();
            for(int i=0;i<size;i++)
            {
                TreeNode temp=q.remove();
                if(temp.left==null && temp.right==null)
                    return count;
                if(temp.left!=null)  
                    q.add(temp.left);
                if(temp.right!=null)
                    q.add(temp.right);
            }
            count++;
        }
        return count;
    }
}

```
