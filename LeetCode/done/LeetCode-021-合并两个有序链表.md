#### 合并两个有序链表

> 题目描述：将两个升序链表合并为一个新的 升序 链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/merge-two-sorted-lists/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：指针遍历

> - 首先，如果l1为空，返回l2；如果l2为空，返回l1
> - 然后，当l1和l2不都为空的时候，同时遍历2个链表，比较当前节点的值，哪个小，就把哪个链表的值取出放入结果result里，然后这个链表往后移一位，直到把2个链表遍历完成，返回result

```java
public class LeetCode_021 {
    public static ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null) {
            return l2;
        }
        if (l2 == null) {
            return l1;
        }
        ListNode result = new ListNode(-1);
        ListNode next = result;
        while (l1 != null || l2 != null) {
            if (l1 == null) {
                next.next = l2;
                break;
            }
            if (l2 == null) {
                next.next = l1;
                break;
            }
            if (l1.val > l2.val) {
                next.next = new ListNode(l2.val);
                l2 = l2.next;
                next = next.next;
                continue;
            } else {
                next.next = new ListNode(l1.val);
                l1 = l1.next;
                next = next.next;
                continue;
            }
        }
        return result.next;
    }

    public static void main(String[] args) {
        ListNode l1 = new ListNode(1);
        l1.next = new ListNode(2);
        l1.next.next = new ListNode(4);
        ListNode l2 = new ListNode(1);
        l2.next = new ListNode(3);
        l2.next.next = new ListNode(4);

        ListNode result = mergeTwoLists(l1, l2);
        while (result != null) {
            System.out.print(result.val + " ");
            result = result.next;
        }
    }
}
```

> 【每日寄语】 *世上所有的惊喜和好运，等于你的人品乘以你的努力。* 

