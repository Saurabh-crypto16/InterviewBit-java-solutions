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
    public ArrayList<Integer> solve(TreeNode root, int B) {
        ArrayList<Integer> ans=new ArrayList<Integer>();
        Queue<TreeNode> q=new LinkedList<>();
        q.offer(root);
        
        while(!q.isEmpty()){
            int size=q.size();
            boolean booleanx=false;
            for(int i=0;i<size;i++){
                TreeNode temp=q.poll();
                if((temp.left!=null && temp.left.val==B) || (temp.right!=null && temp.right.val==B)){
                    booleanx=true;
                }else{
                    if(temp.left!=null)     q.offer(temp.left);
                    if(temp.right!=null)    q.offer(temp.right);
                }
            }
            if(booleanx){
                while(!q.isEmpty()){
                    ans.add(q.poll().val);
                }
            }
        }
        
        return ans;
    }
}

 ```
