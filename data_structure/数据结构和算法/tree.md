# 树

## 二叉树

每个节点的最多有两个分支的树结构，分支通常被称为左子树，右子树，二叉树具有左右次序。
二叉树的第i层对多有2的(i-1)次方个节点。(与2的n次方类比，只是因为2的零次方开始的)
深度为k的二叉树最多存在2的k+1次方-1个节点(定义根节点所在深度k0 = 0)。(用等比求和公式对比 比例系数为2,只是根据节点是0开始的)
叶子节点n0 = 非叶子节点n2 + 1
深度为k，有2的k+1次方-1个节点为满二叉树。
出最后一层，其余层都是满的，或者右边连续缺少节点，为完全二叉树
具有n个节点的完全二叉树的深度为log2n+1。
顺序
i为索引，左孩子2n+1，右孩子2n+2，父节点(i-1)/2

```java
先序遍历非递归
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
            if(root==null){
            return Collections.emptyList();
        }
        Stack<TreeNode> stack = new Stack<>();
        List<Integer> list = new ArrayList<>();
        stack.push(root);
        while(!stack.isEmpty()){
            list.add(stack.peek().val);
            TreeNode node = stack.pop();
            if(node.right!=null){
                stack.push(node.right);
            }
            if(node.left!=null){
                stack.push(node.left);
            }
        }
        return list;
    }
}
```