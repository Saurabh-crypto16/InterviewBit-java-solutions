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
    List<Integer> list=new ArrayList<>();
    public void inOrder(TreeNode node){
        if(node==null)return;
        inOrder(node.left);
        list.add(node.val);
        inOrder(node.right);
    }
    public int t2Sum(TreeNode root, int k) {
        if(root==null)  return 0;
        inOrder(root);
        int low=0,high=list.size()-1;
        while(low<high){
            if(list.get(low)+list.get(high)==k) return 1;
            else if(list.get(low)+list.get(high)>k){
                high-=1;
            }
            else{
                low+=1;
            }
        }
        return 0;
    }
}

```
