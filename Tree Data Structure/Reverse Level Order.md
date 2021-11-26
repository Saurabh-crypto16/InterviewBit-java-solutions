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
    public ArrayList<Integer> solve(TreeNode A) {
        ArrayList<ArrayList<Integer>> res=new ArrayList<>();
        Queue<TreeNode> q=new LinkedList<>();
        q.offer(A);

        while(!q.isEmpty()){
            int size=q.size();
            ArrayList<Integer> al=new ArrayList<>();
            for(int i=0;i<size;i++){
                TreeNode curr=q.poll();
                al.add(curr.val);
                if(curr.left!=null){
                    q.offer(curr.left);
                }
                if(curr.right!=null){
                    q.offer(curr.right);
                }
            }
            res.add(al);
        }

        ArrayList<Integer> ans=new ArrayList<>();
        for(int i=res.size()-1;i>=0;i--){
            for(int val: res.get(i)){
                ans.add(val);
            }
        }

        return ans;
    }
}
```
