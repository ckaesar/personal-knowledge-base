#### 二叉树的最大深度

> 题目描述：给定一个二叉树，找出其最大深度。
>
> 二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。
>
> 说明: 叶子节点是指没有子节点的节点。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 首先，记录一个全局的结果result。然后调用一个递归方法，递归方法包含2个参数，一个是当前的节点root，一个是当前的深度curDepth，如果root为空，则判断curDepth是否大于result，如果大于，更新result为curDepth；如果root不为空，则将curDepth加1，然后递归调用root的左右子节点，直到递归完成，返回result即为树的最大深度。

```java
public class LeetCode_104 {
    public static int result = 0;

    public static int maxDepth(TreeNode root) {
        maxDepth(root, 0);
        return result;
    }

    public static void maxDepth(TreeNode root, int curDepth) {
        if (root == null) {
            if (curDepth > result) {
                result = curDepth;
            }
            return;
        }
        curDepth++;
        maxDepth(root.left, curDepth);
        maxDepth(root.right, curDepth);
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(1);
        root.right = new TreeNode(2);
        System.out.println(maxDepth(root));
    }
}
```

> 【每日寄语】 *坎坷路途，给身边一份温暖；风雨人生，给自己一个微笑。没有什么大不了的事情，在时间面前，都是小事。* 

