#### 相同的树

> 题目描述：给你两棵二叉树的根节点 `p` 和 `q` ，编写一个函数来检验这两棵树是否相同。
>
> 如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/same-tree/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：递归

> 使用递归的方法，递归方式如下：
>
> - 首先，如果p和q都为null，则返回true；
> - 如果p和q只有一个为null，则返回false；
> - 如果p和q都不为null，如果p和q的值不相等，则返回false；如果p和q的值相等，则递归判断p和q的左右子树是不是都相等。
>
> 递归结束，即可得到结果。

```java
public class LeetCode_100 {
    public static boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }
        if ((p == null && q != null) || (p != null && q == null)) {
            return false;
        }
        return p.val == q.val && isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }

    public static void main(String[] args) {
        TreeNode p = new TreeNode(1);
        p.left = new TreeNode(2);
        p.right = new TreeNode(3);

        TreeNode q = new TreeNode(1);
        q.left = new TreeNode(2);
        q.right = new TreeNode(3);

        System.out.println(isSameTree(p, q));
    }
}
```

> 【每日寄语】 *凡事尽力，结果随缘，心怀感恩，知足常乐。* 

