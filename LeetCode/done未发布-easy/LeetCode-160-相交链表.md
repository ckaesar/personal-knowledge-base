#### 相交链表

> 题目描述：给你两个单链表的头节点 headA 和 headB ，请你找出并返回两个单链表相交的起始节点。如果两个链表没有交点，返回 null 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/intersection-of-two-linked-lists/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：HashSet

> 利用java的`HashSet`去重，遍历2个链表headA和headB，将每个结点放入`HashSet`里notRepeatNodes，如果能放进去，说明未相交，继续遍历下一个结点；如果放不进去，由于已说明headA和headB不存在环，说明此结点是相交结点，返回当前结点。最后如果都遍历完了还没找到相交结点，说明2个链表不相交，直接返回null。

```java
import java.util.HashSet;
import java.util.Set;

public class LeetCode_160 {
    public static ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        Set<ListNode> notRepeatNodes = new HashSet<>();
        ListNode nextA = headA;
        ListNode nextB = headB;
        while (nextA != null || nextB != null) {
            if (nextA != null) {
                if (!notRepeatNodes.add(nextA)) {
                    return nextA;
                } else {
                    nextA = nextA.next;
                }
            }
            if (nextB != null) {
                if (!notRepeatNodes.add(nextB)) {
                    return nextB;
                } else {
                    nextB = nextB.next;
                }
            }
        }
        return null;
    }

    public static void main(String[] args) {
        ListNode headA = new ListNode(1);
        headA.next = new ListNode(9);
        headA.next.next = new ListNode(1);

        ListNode headB = new ListNode(3);

        ListNode commonNode = new ListNode(2);

        headA.next.next.next = commonNode;
        headB.next = commonNode;
        commonNode.next = new ListNode(4);

        ListNode result = getIntersectionNode(headA, headB);
        if (result == null) {
            System.out.println("不相交");
        } else {
            System.out.println(result.val);
        }
    }
}
```

> 【每日寄语】 *怀着一颗宽容的心去生活，再拥挤的世界也会变得无限宽广，再平凡的人生也会变得充满阳光。* 

