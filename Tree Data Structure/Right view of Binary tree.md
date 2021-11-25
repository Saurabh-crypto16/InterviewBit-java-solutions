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
        ArrayList<Integer> res=new ArrayList<>();
        rightView(A,res,0);
        return res;
    }
    public void rightView(TreeNode node,ArrayList<Integer> res,int currDepth){
        if(node==null){
            return;
        }

        if(currDepth==res.size()){
            res.add(node.val);
        }

        rightView(node.right,res,currDepth+1);
        rightView(node.left,res,currDepth+1);
    }
}
```
