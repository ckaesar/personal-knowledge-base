#### 二叉树的最小深度

> 题目描述：给定一个二叉树，找出其最小深度。
>
> 最小深度是从根节点到最近叶子节点的最短路径上的节点数量。
>
> 说明：叶子节点是指没有子节点的节点。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 首先，如果root为null，直接返回0。
>
> 否则，调用递归方法`minDepth(TreeNode root, int curDepth)`，root为当前节点，curDepth为当前深度，递归过程如下：
>
> - 如果root为null，直接返回；
> - 否则，curDepth加1；
> - 然后判断如果root的左子树或者右子树有一边为null，则调用递归方法，参数为不为null的子树和curDepth，然后返回；
> - 如果root的左子树和右子树都不为null，则左右子树都要调用递归方法。
>
> 过程中需要判断当前深度和result哪个小，result取更小的一个，最后返回result即为数的最小深度。

```java
public class LeetCode_111 {
    public static int result = Integer.MAX_VALUE;

    public static int minDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        minDepth(root, 0);
        return result;
    }

    public static void minDepth(TreeNode root, int curDepth) {
        if (root == null) {
            return;
        }
        curDepth++;
        if (root.left == null && root.right == null) {
            if (curDepth < result) {
                result = curDepth;
            }
            return;
        }
        if (root.left == null && root.right != null) {
            minDepth(root.right, curDepth);
            return;
        }
        if (root.left != null && root.right == null) {
            minDepth(root.left, curDepth);
            return;
        }
        minDepth(root.left, curDepth);
        minDepth(root.right, curDepth);
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(2);
        root.right = new TreeNode(3);
        root.right.right = new TreeNode(4);
        root.right.right.right = new TreeNode(5);
        root.right.right.right.right = new TreeNode(6);
        System.out.println(minDepth(root));
    }
}
```

> 【每日寄语】 *有一天早晨我扔掉了所有的昨天，从此我的脚步就轻盈了。* 

