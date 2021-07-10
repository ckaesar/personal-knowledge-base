#### 路径总和

> 题目描述：给你二叉树的根节点 root 和一个表示目标和的整数 targetSum ，判断该树中是否存在 根节点到叶子节点 的路径，这条路径上所有节点值相加等于目标和 targetSum 。
>
> 叶子节点 是指没有子节点的节点。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/path-sum/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 首先，如果root为null，直接返回false。
>
> 否则，调用递归方法`hasPathSum(TreeNode root, int targetSum, int curSum)`，root为当前节点，targetSum为目标和，curSum当前路径上的累加和，递归过程如下：
>
> - 如果root为null，直接返回；
> - 否则，curSum累加当前节点的值；
> - 然后判断如果root的左子树或者右子树有一边为null，则调用递归方法，参数为不为null的子树和curSum，然后返回；
> - 如果root的左子树和右子树都不为null，则左右子树都要调用递归方法。
>
> 过程中当到达子节点时需要判断当前路径的和curSum和targetSum是否相等，如果相等，则将result更新为true，最后返回result。

> 说明：该题的解法过程和 **LeetCode-111-二叉树的最小深度** 完全一样。

```java
public class LeetCode_112 {
    public static boolean result = false;

    public static boolean hasPathSum(TreeNode root, int targetSum) {
        if (root == null) {
            return false;
        }
        hasPathSum(root, targetSum, 0);
        return result;
    }

    public static void hasPathSum(TreeNode root, int targetSum, int curSum) {
        if (root == null) {
            return;
        }
        curSum += root.val;
        if (root.left == null && root.right == null) {
            if (curSum == targetSum) {
                result = true;
            }
            return;
        }
        if (root.left == null && root.right != null) {
            hasPathSum(root.right, targetSum, curSum);
            return;
        }
        if (root.left != null && root.right == null) {
            hasPathSum(root.left, targetSum, curSum);
            return;
        }
        hasPathSum(root.left, targetSum, curSum);
        hasPathSum(root.right, targetSum, curSum);
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(1);
        root.left = new TreeNode(2);
        root.right = new TreeNode(3);
        System.out.println(hasPathSum(root, 5));
        System.out.println(hasPathSum(root, 4));
    }
}
```

> 【每日寄语】 *收集每一个快乐的瞬间，用它来回击每一个糟糕的日子。* 

