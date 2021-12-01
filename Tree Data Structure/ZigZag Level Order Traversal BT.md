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
    public ArrayList<ArrayList<Integer>> zigzagLevelOrder(TreeNode root) {
        ArrayList<ArrayList<Integer>> res=new ArrayList<>();
        if(root==null)  return res;

        Queue<TreeNode> q=new LinkedList<>();
        q.offer(root);
        boolean flag=true;
        while(!q.isEmpty()){
            int size=q.size();
            ArrayList<Integer> row=new ArrayList<>();
            for(int i=0;i<size;i++){
                TreeNode node=q.poll();
                if(flag){
                    row.add(node.val);
                }else{
                    row.add(0,node.val);
                }

                if(node.left!=null){
                    q.offer(node.left);
                }
                if(node.right!=null){
                    q.offer(node.right);
                }
            }
            flag=!flag;
            res.add(row);
        }
        return res;
    }
}

```
