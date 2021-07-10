#### 二叉树的前序遍历

> 题目描述：给你二叉树的根节点 `root` ，返回它节点值的 **前序** 遍历。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/binary-tree-preorder-traversal/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 初始化一个结果集result，然后按照以下顺序进行递归处理：
>
> - 首先将root节点的值放到result里；
> - 然后将root节点的左子树的处理结果放到result里；
> - 最后将root节点的右子树的处理结果放到result里；
> - 当root为空时，返回空的result。
>
> 最后返回结果集result，即为树的前序遍历结果。

> 说明：和中序遍历的过程类似，参照 **LeetCode-094-二叉树的中序遍历**。

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_144 {
    public static List<Integer> preorderTraversal(TreeNode root) {
        if (root == null) {
            return new ArrayList<>();
        }
        List<Integer> result = new ArrayList<>();
        result.add(root.val);
        result.addAll(preorderTraversal(root.left));
        result.addAll(preorderTraversal(root.right));
        return result;
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(1);
        root.right = new TreeNode(2);
        root.right.left = new TreeNode(3);
        for (Integer integer : preorderTraversal(root)) {
            System.out.print(integer + " ");
        }
    }
}
```

> 【每日寄语】 *每一个清晨，记得告诉自己：这世界上没有奇迹，只有你自己努力的轨迹；这世界上没有运气，只有你自己坚持的勇气。* 

