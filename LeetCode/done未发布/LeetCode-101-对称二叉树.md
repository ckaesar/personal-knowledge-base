#### 对称二叉树

> 题目描述：给定一个二叉树，检查它是否是镜像对称的。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/symmetric-tree/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 首先判断root如果为空或者root没有左右子节点，则直接返回true；然后调用递归方法`isSymmetric(TreeNode left, TreeNode right)`判断左右子树是否相等，判断逻辑是判断左右子节点的值是否相等，如果相等，则继续判断左子树的左子树和右子树的右子树是否相等而且左子树的右子树和右子树的左子树是否相等，直到递归完整棵树，判断完成，返回结果。

```java
public class LeetCode_101 {
    public static boolean isSymmetric(TreeNode root) {
        if (root == null || (root.left == null && root.right == null)) {
            return true;
        }
        return isSymmetric(root.left, root.right);
    }

    public static boolean isSymmetric(TreeNode left, TreeNode right) {
        if (left == null && right == null) {
            return true;
        }
        if ((left == null && right != null) || (left != null && right == null)) {
            return false;
        }
        return left.val == right.val && isSymmetric(left.left, right.right) && isSymmetric(left.right, right.left);
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(1);
        root.left = new TreeNode(2);
        root.right = new TreeNode(2);
        root.left.left = new TreeNode(3);
        root.right.right = new TreeNode(3);

        System.out.println(isSymmetric(root));
    }
}
```

> 【每日寄语】 *生活中最大的幸福是坚信有人爱着我们。* 

