#### 翻转二叉树

> 题目描述：翻转一棵二叉树。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/invert-binary-tree/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 用递归的方法将二叉树翻转，具体递归过程如下：
>
> - 如果root节点为null或者root没有左右子节点，则直接返回root；
> - 否则，首先用temp暂存root的right子树，将root的right指向递归处理root的left子树后的结点，将root的left指向递归处理temp后的结点。
>
> 递归完成后即得到翻转后的二叉树。

```java
import java.util.LinkedList;
import java.util.Queue;

public class LeetCode_226 {
    public static TreeNode invertTree(TreeNode root) {
        if (root == null || (root.left == null && root.right == null)) {
            return root;
        }
        TreeNode temp = root.right;
        root.right = invertTree(root.left);
        root.left = invertTree(temp);
        return root;
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(4);
        root.left = new TreeNode(2);
        root.right = new TreeNode(7);
        root.left.left = new TreeNode(1);
        root.left.right = new TreeNode(3);
        root.right.left = new TreeNode(6);
        root.right.right = new TreeNode(9);

        invertTree(root);
        Queue<TreeNode> nodes = new LinkedList<>();
        nodes.add(root);
        while (nodes.size() > 0) {
            TreeNode cur = nodes.poll();
            System.out.print(cur.val + " ");
            if (cur.left != null) {
                nodes.add(cur.left);
            }
            if (cur.right != null) {
                nodes.add(cur.right);
            }
        }
        for (TreeNode node : nodes) {
            System.out.print(node.val + " ");
        }
    }
}
```

> 【每日寄语】 *将来的你，一定会感谢现在拼命的自己！* 

