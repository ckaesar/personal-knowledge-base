#### 环形链表

> 题目描述：给定一个链表，判断链表中是否有环。
>
> 如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。
>
> 如果链表中存在环，则返回 true 。 否则，返回 false 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/linked-list-cycle/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：Set去重

> 首先，如果head为null或者head只有一个结点，直接返回false；
>
> 否则，遍历head，利用HashSet判断是否有环，appeared表示遍历过的结点，遍历过程如下：
>
> - 将head结点添加到appeared里，如果返回false，表示结点已存在，说明有环存在，直接返回true；如果返回true，表示结点不存在，继续遍历下一个结点。
> - 遍历结束，如果没有环存在，返回false。

```java
import java.util.HashSet;
import java.util.Set;

public class LeetCode_141 {
    public static boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }
        Set<ListNode> appeared = new HashSet<>();
        while (head != null) {
            if (!appeared.add(head)) {
                return true;
            }
            head = head.next;
        }
        return false;
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        System.out.println(hasCycle(head));
    }
}
```

> 【每日寄语】 *不恋尘世浮华，不写红尘纷扰，不叹世道苍凉，不惹情思哀怨。* 

