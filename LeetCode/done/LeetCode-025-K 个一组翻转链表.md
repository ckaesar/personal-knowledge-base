#### K 个一组翻转链表

> 题目描述：给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。
>
> k 是一个正整数，它的值小于或等于链表的长度。
>
> 如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。
>
> 进阶：
>
> 你可以设计一个只使用常数额外空间的算法来解决此问题吗？
> 你不能只是单纯的改变节点内部的值，而是需要实际进行节点交换。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/reverse-nodes-in-k-group/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：利用栈

> - 首先，如果`k=1`或者**head**为空或者**head**没有后继节点，直接返回空；
> - 否则，遍历head链表，利用一个栈**kListNode**，每次把k个节点推入栈中，然后再依次把k个节点从栈中取出，并且链表按取出的顺序排列，这样直到把链表遍历完成，即完成的所有节点的翻转。
>
> 注意点：开始记录了一个空节点**newHead**记录头结点，这样当遍历完成后直接返回**newHead**的下一个节点即为翻转后的头节点。

```java
import java.util.Stack;

public class LeetCode_025 {
    public static ListNode reverseKGroup(ListNode head, int k) {
        if (k == 1 || head == null || head.next == null) {
            return head;
        }

        ListNode newHead;
        ListNode pre = new ListNode(-1);
        newHead = pre;
        pre.next = head;
        int count = 0;
        ListNode next = head;
        Stack<ListNode> kListNode = new Stack<>();
        while (next != null || count == k) {
            if (count == k) {
                while (!kListNode.isEmpty()) {
                    pre.next = kListNode.pop();
                    pre = pre.next;
                }
                pre.next = next;
                count = 0;
            } else {
                if (next != null) {
                    kListNode.push(next);
                    next = next.next;
                    count++;
                }
            }
        }
        return newHead.next;
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);
        ListNode result = reverseKGroup(head, 3);
        while (result != null) {
            System.out.print(result.val + " ");
            result = result.next;
        }
    }
}
```

> 【每日寄语】 *不是每一个贝壳里都有珍珠，但珍珠一定出现在贝壳中，不是每个人努力都会成功，但成功的人一定很努力。* 

