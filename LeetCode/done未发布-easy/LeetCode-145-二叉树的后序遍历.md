#### 二叉树的后序遍历

> 题目描述：给定一个二叉树，返回它的 *后序* 遍历。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/binary-tree-postorder-traversal/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 初始化一个结果集result，然后按照以下顺序进行递归处理：
>
> - 首先将root节点的左子树的处理结果放到result里；
> - 然后将root节点的右子树的处理结果放到result里；
> - 最后将root节点的值放到result里；
> - 当root为空时，返回空的result。
>
> 最后返回结果集result，即为树的后续遍历结果。

> 说明：和中序遍历的过程类似，参照 **LeetCode-094-二叉树的中序遍历**。

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_145 {
    public static List<Integer> postorderTraversal(TreeNode root) {
        if (root == null) {
            return new ArrayList<>();
        }
        List<Integer> result = new ArrayList<>();
        result.addAll(postorderTraversal(root.left));
        result.addAll(postorderTraversal(root.right));
        result.add(root.val);
        return result;
    }

    public static void main(String[] args) {
        TreeNode root = new TreeNode(1);
        root.right = new TreeNode(2);
        root.right.left = new TreeNode(3);
        for (Integer integer : postorderTraversal(root)) {
            System.out.print(integer + " ");
        }
    }
}
```

> 【每日寄语】 *未来不是岁数，未来是礼物，读万卷书才能看得清皓月繁星。* 

