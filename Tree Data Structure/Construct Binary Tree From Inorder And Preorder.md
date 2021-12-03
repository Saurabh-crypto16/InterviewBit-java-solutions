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
    public TreeNode buildTree(ArrayList<Integer> pre, ArrayList<Integer> in) {
        Map<Integer,Integer> inMap=new HashMap<>();
        for(int i=0;i<in.size();i++){
            inMap.put(in.get(i),i);
        }

        TreeNode root=build(pre,0,pre.size()-1,in,0,in.size()-1,inMap);
        return root;
    }
    public TreeNode build(ArrayList<Integer> pre,int pStart,int pEnd,ArrayList<Integer> in,int iStart,int iEnd,
            Map<Integer,Integer> inMap){
        if(pStart>pEnd || iStart>iEnd){
            return null;
        }

        TreeNode root=new TreeNode(pre.get(pStart));
        int inRoot=inMap.get(root.val); //index of root value in inOrder list
        int numsLeft=inRoot-iStart; //number of elements left of root in inOrder list

        root.left=build(pre,pStart+1,pStart+numsLeft,in,iStart,inRoot-1,inMap);
        root.right=build(pre,pStart+numsLeft+1,pEnd,in,inRoot+1,iEnd,inMap);

        return root;
    }
}
```
